<!-- BEGIN_ANSIBLE_DOCS -->

# Ansible Role: trippsc2.nexus.ce_install
Version: 1.1.0

This role installs Nexus Repository Manager Community Edition on Linux systems.

A reverse proxy should be configured prior to running this role.


## Requirements

| Platform | Versions |
| -------- | -------- |
| Debian | <ul><li>trixie</li></ul> |
| EL | <ul><li>10</li><li>9</li><li>8</li></ul> |
| Ubuntu | <ul><li>resolute</li><li>noble</li><li>jammy</li></ul> |

## Dependencies

| Collection |
| ---------- |
| ansible.posix |
| community.general |
| trippsc2.general |

## Role Arguments
|Option|Description|Type|Required|Choices|Default|
|---|---|---|---|---|---|
| nexus_ce_configure_selinux | <p>If `true`, the role will configure SELinux to allow Nexus Repository Manager Community Edition.</p><p>On EL systems, this will default to `true`.</p><p>On Debian-based systems, this will default to `false`.</p> | bool | no |  |  |
| nexus_ce_configure_firewall | <p>If `true`, the role will configure the host firewall to allow Nexus Repository Manager Community Edition.</p> | bool | no |  | {{ nexus_ce_listen_on_all_interfaces }} |
| nexus_ce_firewall_type | <p>The type of firewall to configure.</p><p>On EL and Debian systems, this will default to `firewalld`.</p><p>On Ubuntu systems, this will default to `ufw`.</p> | str | no | <ul><li>firewalld</li><li>ufw</li></ul> |  |
| nexus_ce_version | <p>The version of Nexus Repository Manager Community Edition to install.</p><p>If not specified, the latest version will be installed.</p> | str | no |  |  |
| nexus_ce_perform_upgrade | <p>If `true`, the role will perform an upgrade of the Nexus Repository Manager Community Edition.</p><p>If `false`, the role will install the Nexus Repository Manager Community Edition only if it is not already installed.</p> | bool | no |  | False |
| nexus_ce_cleanup_old_versions | <p>If `true`, the role will cleanup old versions of Nexus Repository Manager Community Edition after the installation.</p><p>If `false`, the role will not cleanup old versions of Nexus Repository Manager Community Edition after the installation.</p> | bool | no |  | True |
| nexus_ce_download_base_path | <p>The base path to download the Nexus Repository Manager Community Edition tarball.</p><p>If not specified, the role will use the default path of `/tmp`.</p> | path | no |  |  |
| nexus_ce_os_user | <p>The user as which Nexus Repository Manager Community Edition will run.</p> | str | no |  | nexus |
| nexus_ce_os_group | <p>The group as which Nexus Repository Manager Community Edition will run.</p> | str | no |  | nexus |
| nexus_ce_os_home | <p>The home directory of the user as which Nexus Repository Manager Community Edition will run.</p> | path | no |  | /home/{{ nexus_ce_os_user }} |
| nexus_ce_install_path | <p>The symbolic link to the currently installed version of Nexus Repository Manager Community Edition.</p><p>A version path will be created in the same directory as the symbolic link.</p> | path | no |  | /opt/nexus |
| nexus_ce_data_path | <p>The path to the data directory for Nexus Repository Manager Community Edition.</p> | path | no |  | /var/lib/nexus |
| nexus_ce_heap_size_in_mb | <p>The heap size for Nexus Repository Manager Community Edition in megabytes.</p> | int | no |  | 2703 |
| nexus_ce_timezone | <p>The timezone for Nexus Repository Manager Community Edition.</p> | str | no |  | UTC |
| nexus_ce_tmp_path | <p>The path to the temporary directory for Nexus Repository Manager Community Edition.</p><p>On EL systems, this will default to `/var/tmp/nexus`.</p><p>On Debian-based systems, this will default to `/tmp/nexus`.</p> | path | no |  |  |
| nexus_ce_skip_onboarding_wizard | <p>If `true`, the role will skip the onboarding wizard for Nexus Repository Manager Community Edition.</p> | bool | no |  | True |
| nexus_ce_listening_port | <p>The port on which Nexus Repository Manager Community Edition will listen.</p> | int | no |  | 8081 |
| nexus_ce_listen_on_all_interfaces | <p>If `true`, the role will listen on all interfaces for Nexus Repository Manager Community Edition.</p><p>If `false`, the role will listen on the loopback interface for Nexus Repository Manager Community Edition.</p> | bool | no |  | False |
| nexus_ce_encryption_keys_path | <p>The path to the JSON file containing the Nexus Repository Manager Community Edition encryption keys.</p> | path | no |  | {{ nexus_ce_data_path }}/keys/encryption.json |
| nexus_ce_encryption_key_id | <p>The ID of the encryption key to use for Nexus Repository Manager Community Edition.</p> | str | yes |  |  |
| nexus_ce_encryption_keys | <p>A list of encryption keys to use for Nexus Repository Manager Community Edition.</p> | list of dicts of 'nexus_ce_encryption_keys' options | yes |  |  |
| nexus_ce_admin_password | <p>The password for the Nexus Repository Manager Community Edition admin user.</p><p>If not specified, the default password will not be changed.  It can be found at `{{ nexus_ce_data_path }}/admin.password`.</p> | str | no |  |  |
| nexus_ce_remove_default_repositories | <p>If `true`, the role will remove the default repositories from Nexus Repository Manager Community Edition.</p> | bool | no |  | True |

### Options for nexus_ce_encryption_keys
|Option|Description|Type|Required|Choices|Default|
|---|---|---|---|---|---|
| id | <p>The ID of the encryption key.</p> | str | yes |  |  |
| key | <p>The secret key for the encryption key.</p> | str | yes |  |  |


## License
MIT

## Author and Project Information
Jim Tarpley (@trippsc2)
<!-- END_ANSIBLE_DOCS -->
