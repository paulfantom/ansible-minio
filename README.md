<p><img src="https://avatars0.githubusercontent.com/u/695951?s=200&v=4" alt="minio logo" title="minio" align="right" height="60" /></p>

# Ansible Role: Minio

[![Build Status](https://travis-ci.org/atosatto/ansible-minio.svg?branch=master)](https://travis-ci.org/atosatto/ansible-minio)
[![License](https://img.shields.io/badge/license-MIT%20License-brightgreen.svg)](https://opensource.org/licenses/MIT)
[![Ansible Role](https://img.shields.io/badge/ansible%20role-atosatto.minio-blue.svg)](https://galaxy.ansible.com/atosatto/minio/)
[![GitHub tag](https://img.shields.io/github/tag/atosatto/ansible-minio.svg)](https://github.com/atosatto/ansible-minio/tags)

Install and configure the [Minio](https://minio.io/) S3 compatible object storage server
on RHEL/CentOS and Debian/Ubuntu.

## Requirements

None.

## Role Variables

Available variables are listed below, along with default values (see `defaults/main.yml`):

```yaml
minio_server_bin: /usr/local/bin/minio
minio_client_bin: /usr/local/bin/mc
```

Installation path of the Minio server and client binaries.

```yaml
minio_user: minio
minio_group: minio
```

Name and group of the user running the minio server.
**NB**: This role automatically creates the minio user and/or group if these does not exist in the system.

```yaml
minio_server_envfile: /etc/default/minio
```

Path to the file containing the minio server configuration ENV variables.

```yaml
minio_server_addr: ":9091"
```

The Minio server listen address.

```yaml
minio_server_datadirs: [ ]
```

Directories of the folder containing the minio server data
**NB**: This variable must always be set by the role, otherwise the minio service will not start.

```yaml
minio_server_make_datadirs: true
```

Create directories from `minio_server_datadirs` 

```yaml
minio_server_opts: ""
```

Additional CLI options that must be appended to the minio server start command.

```yaml
minio_access_key: ""
minio_secret_key: ""
```

Minio access and secret keys.

```yaml
minio_install_server: true
minio_install_client: true
```

Switches to disable minio server and/or minio client installation.

## Dependencies

None.

## Example Playbook

```yaml
- name: "Install Minio"
  hosts: all
  roles:
    - atosatto.minio
  vars:
    minio_server_datadirs: [ "/minio-test" ]
```

## Changelog

See [changelog](CHANGELOG.md).

## License

MIT
