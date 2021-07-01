hdfs-dirs
==============

This role allows to deploy a list of configurable directories in HDFS.
Each directory entry has a mandatory `name` attribute, and following optional attributes:
* owner
* mode 
* acl 
* setfacl_raw
* parent_dirs
* become_user

Alternatively some of these atttributes can be set "globally" via related role vars, documented in the "Role Variables" section:
* hdfs_dir_default_owner
* hdfs_dir_default_mode 
* hdfs_dir_default_acl 
* hdfs_dir_default_parent_dirs

Requirements
------------

This role does not depend on any extra modules or other roles.

Role Variables
--------------

All the role vars explained in short, including their defaults. (However the code is the best doc!):

* `hdfs_root_user` (default: `hdfs`): the hdfs root user used as the `become_user`.
* `hdfs_dir_default_owner` (default: <undefined>): the default dir owner
* `hdfs_dir_default_mode` (default: <undefined>): the default dir mode
* `hdfs_dir_default_acl` (default: <undefined>): the default dir (extended) Hdfs ACL
* `hdfs_dir_default_parent_dirs` (default: <undefined>): if `true` dirs are created with the `-p` flag


Examples
----------------

Example config:
``` 
tenant: "team1"
hdfs_folders:
- name: "/data/{{ tenant1 }}"
  owner: "{{ tenant1 }}"
  mode: "0700"
  parent_dirs: True
- name: "/data/team2"
  owner: "team2"
  mode: "0700"
```
