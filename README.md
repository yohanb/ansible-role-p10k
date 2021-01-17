Role Name
=========

Ansible role for install powerlevel10k, Powerlevel10k is a theme for Zsh. It emphasizes speed, flexibility and out-of-the-box experience.

Requirements
------------

None.

Role Variables
--------------

Available variables are listed below, along with default values (see `defaults/main.yml`):

```yaml
# defaults file for ansible-role-p10k

# Powerlevel10k Git repository url
p10k_repository_url: 'https://github.com/romkatv/powerlevel10k.git'

# Install p10k for the following linux users
# Default: the linux user running Ansible
p10k_users:
  - "{{ ansible_user_id }}"

# Zsh plugin used, zsh, ohmyzsh, prezto, Zim, etc..
# All plugin names can be found here https://github.com/romkatv/powerlevel10k#installation
zsh_plugin: zsh

# Download p10k recommanded fonts from this urls
p10k_font_urls:
  - { url: 'https://github.com/romkatv/powerlevel10k-media/raw/master/MesloLGS%20NF%20Regular.ttf', name: 'Hack-Italic.ttf' }
  - { url: 'https://github.com/romkatv/powerlevel10k-media/raw/master/MesloLGS%20NF%20Bold.ttf', name: 'Hack-Bold.ttf' }
  - { url: 'https://github.com/romkatv/powerlevel10k-media/raw/master/MesloLGS%20NF%20Italic.ttf', name: 'Hack-BoldItalic.ttf' }
  - { url: 'https://github.com/romkatv/powerlevel10k-media/raw/master/MesloLGS%20NF%20Bold%20Italic.ttf', name: 'Hack-Regular.ttf' }
```

Dependencies
------------

None.

Example Playbook
----------------

Install powerlevel10K:

    - hosts: servers
      roles:
         - { role: diodonfrost.p10k }

Install powerlevel10k for ohmyzsh:

    - hosts: servers
      roles:
         - { role: diodonfrost.p10k, zsh_plugin: ohmyzsh }

Local Testing
-------------

This project uses [Molecule](http://molecule.readthedocs.io/) to aid in the
development and testing.

To develop or test you'll need to have installed the following:

* Linux (e.g. [Ubuntu](http://www.ubuntu.com/))
* [Docker](https://www.docker.com/)
* [Python](https://www.python.org/) (including python-pip)
* [Ansible](https://www.ansible.com/)
* [Molecule](http://molecule.readthedocs.io/)

### Testing with Docker ###

```shell
# Install requirements
pip install -r requirements-dev.txt

# Test ansible role with ubuntu 20.04
molecule test

# Test ansible role with centos 8
image=ansible-centos:8 molecule test

# Test ansible role with alpine-latest
image=ansible-alpine:latest molecule test

# Create ubuntu 20.048 instance
molecule create

# Apply role on ubuntu 20.04 instance
molecule converge

# Launch tests on centos-7 instance
molecule verify
```

License
-------

Apache 2

Author Information
------------------

This role was created in 2021 by diodonfrost.
