# Mac Collection for Ansible

[![MIT licensed][badge-license]][link-license]
[![CI][badge-gh-actions]][link-gh-actions]

This collection includes helpful Ansible roles and content to help with macOS automation. I adapted this from geerlingguy's collection for my own use. For a good example of the original collection's usage, see the [Mac Dev Playbook](https://github.com/geerlingguy/mac-dev-playbook).

Roles included in this collection (click on the link to see the role's README and documentation):

  - `ryan-bell-gea.mac.homebrew` ([documentation](https://github.com/ryan-bell-gea/ansible-collection-mac/blob/master/roles/homebrew/README.md))

## Installation

Install via Ansible Galaxy:

```
ansible-galaxy collection install geerlingguy.mac
```

Or include this collection in your playbook's `requirements.yml` file:

```
---
collections:
  - name: ryan-bell-gea.mac
```

For a real-world example, see geerlingguy's [Mac Dev Playbook's requirements file](https://github.com/geerlingguy/mac-dev-playbook/blob/master/requirements.yml).

### Role Requirements

Requires separate installation of the `elliotweiser.osx-command-line-tools` role. Because Ansible collections are not able to depend on roles, you will need to make sure that role is installed either by manually installing it with the `ansible-galaxy` command, or adding it under the `roles` section of your `requirements.yml` file:

```yaml
---
roles:
  - name: elliotweiser.osx-command-line-tools

collections:
  - name: geerlingguy.mac
```

## Usage

Here's an example playbook which installs some Mac Apps (assuming you are signed into the App Store), CLI tools via Homebrew, and Cask Apps using Homebrew:

```yaml
- hosts: localhost
  connection: local
  gather_facts: false

  vars:
    homebrew_installed_packages:
      - node
      - nvm
      - redis
      - ssh-copy-id
      - pv

    homebrew_cask_apps:
      - docker
      - firefox
      - google-chrome
      - vlc

  roles:
    - geerlingguy.mac.homebrew
```

For a real-world usage example, see geerlingguy's [Mac Dev Playbook](https://github.com/geerlingguy/mac-dev-playbook).

See the full documentation for each role in the role's README, linked above.

## License

MIT

## Author

This collection was adapted by ryan-bell-gea. The original was created by [Jeff Geerling](https://www.jeffgeerling.com), author of [Ansible for DevOps](https://www.ansiblefordevops.com).

[badge-gh-actions]: https://github.com/geerlingguy/ansible-collection-mac/workflows/CI/badge.svg?event=push
[link-gh-actions]: https://github.com/ryan-bell-gea/ansible-collection-mac/actions?query=workflow%3ACI
[badge-license]: https://img.shields.io/github/license/geerlingguy/ansible-collection-mac.svg
[link-license]: https://github.com/geerlingguy/ansible-collection-mac/blob/master/LICENSE
