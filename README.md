# base

[![Build Status](https://travis-ci.org/sweeperio/chef-base.svg?branch=master)](https://travis-ci.org/sweeperio/chef-base)

A cookbook for all machines. This should be put at the top of the run list for almost all machines.

## What This Does

* Sets up apt cookbook
* Installs packages defined in `node["base"]["packages"]` (see attributes)
* Installs [runit]
* Configures chef-client to run periodically (see attributes)

[runit]: http://smarden.org/runit/

## Attributes

Attribute|Description|Default
---------|-----------|-------
`node["base"]["packages"]` | An array of apt packages to be installed | `[]`
`node["base"]["git"]["version"]` | The version of git to install | `2.6.4`
`node["base"]["git"]["checksum"]` | The sha256 checksum of the version's tarball | `08e3ccdba87ca55140c8155a07e147f6c1cdd7b574690e960763b18474fd05ed`


### Chef-Client Attributes

These are using [the defaults], but the two below really should/must be set.

Attribute|Description|Default
---------|-----------|-------
`node["chef_client"]["server_url"]` | The URL for your chef server | `http://localhost:4000`
`node["chef_client"]["validation_client_name"]` | The validator name | `chef-validator`

[defaults]: https://github.com/cookbooks/chef-client

## Contributing

To do any of the things, you'll need [ChefDK] and [Vagrant] installed.

* Lint: `chef exec rubocop`
* Run Specs: `chef exec rspec`
* Run Integration Tests: `chef exec kitchen test` (will destroy and recreate box)

It's faster to run `chef exec kitchen converge && chef exec kitchen verify` while developing. Just make sure to run test

### The Rest, You Already Know

1. Fork this repo and create a branch
1. Add tests that will fail without your code, and pass with it
1. Use Chef idioms and helpers
1. Push your branch and submit a pull request
on a clean box before pushing.

[ChefDK]: https://downloads.chef.io/chef-dk/
[Vagrant]: https://www.vagrantup.com/
