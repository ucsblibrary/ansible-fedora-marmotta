# ansible-fedora-marmotta

Install [Fedora](http://www.fedora-commons.org) and
[Marmotta](https://marmotta.apache.org) as Tomcat servlets on
RHEL/CentOS.

## Variables

### General

- `project_base` the directory root for Fedora and Marmotta data;
  defaults to `/opt`.

- `install_path` the directory root for downloading files; defaults to `tmp`.

- `tomcat` the root of the Tomcat installation; defaults to `/usr/share/tomcat`.

- `psql_host` the hostname of the PostgreSQL server to be used by
  Fedora and Marmotta; defaults to `localhost`.

### Fedora

- `fedora_base_path` the REST API root; defaults to `prod`

- `fedora_ver` the version of Fedora to install; defaults to `4.7.5`.

- `fedora_256` the SHA-256 of the Fedora download.

- `ispn_pass` the password for Fedora’s PostgreSQL role (set this
  yourself, obviously).

- `ispn_user` the name of Fedora’s PostgreSQL role; defaults to
  `fcrepo`

- `fedora_fs` a dict defining the mount point for the volume Fedora
  will write binary data to; defaults to `{ mount_point: "{{ project_base }}/fedora—data" }`.

- `fedora_subdirectory` the directory within the
  `fedora_fs.mount_point` where this instance of Fedora should write to.

### Marmotta

- `marmotta_ver` the version of Marmotta to install; defaults to
  `3.3.0`

- `marmotta_256` the SHA-256 of the Marmotta tarball.

- `marmotta_home` the root directory for the Marmotta installation;
  defaults to `{{ project_base }}/marmotta`.

- `marmotta_pg_pass` the password for Marmotta’s PostgreSQL role (set this
  yourself, obviously).

- `marmotta_pg_user` the name of Marmotta’s PostgreSQL role; defaults
  to `marmotta`.

Example Playbook
----------------

```yaml
- hosts: all
  roles:
    - role: ucsblibrary.fedora-marmotta
      become: yes
      fedora_ver: 4.7.0
      fedora_256: 1f478176649cb8cfff423e9aad839ece1cb1fff0ee5b3db2cbf3b0d5449486ca
      fedora_data_root: /fedora
```

License
-------

```
This software is Copyright © 2017 The Regents of the University of
California. All Rights Reserved.

Permission to copy, modify, and distribute this software and its
documentation for educational, research and non-profit purposes,
without fee, and without a written agreement is hereby granted,
provided that the above copyright notice, this paragraph and the
following three paragraphs appear in all copies.

Permission to make commercial use of this software may be obtained by
contacting:

Technology Transfer Office
9500 Gilman Drive, Mail Code 0910
University of California
La Jolla, CA 92093-0910
(858) 534-5815
invent@ucsd.edu

This software program and documentation are copyrighted by The Regents
of the University of California. The software program and
documentation are supplied "as is", without any accompanying services
from The Regents. The Regents does not warrant that the operation of
the program will be uninterrupted or error-free. The end-user
understands that the program was developed for research purposes and
is advised not to rely exclusively on the program for any reason.

IN NO EVENT SHALL THE UNIVERSITY OF CALIFORNIA BE LIABLE TO ANY PARTY
FOR DIRECT, INDIRECT, SPECIAL, INCIDENTAL, OR CONSEQUENTIAL DAMAGES,
INCLUDING LOST PROFITS, ARISING OUT OF THE USE OF THIS SOFTWARE AND
ITS DOCUMENTATION, EVEN IF THE UNIVERSITY OF CALIFORNIA HAS BEEN
ADVISED OF THE POSSIBILITY OF SUCH DAMAGE. THE UNIVERSITY OF
CALIFORNIA SPECIFICALLY DISCLAIMS ANY WARRANTIES, INCLUDING, BUT NOT
LIMITED TO, THE IMPLIED WARRANTIES OF MERCHANTABILITY AND FITNESS FOR
A PARTICULAR PURPOSE.  THE SOFTWARE PROVIDED HEREUNDER IS ON AN "AS
IS" BASIS, AND THE UNIVERSITY OF CALIFORNIA HAS NO OBLIGATIONS TO
PROVIDE MAINTENANCE, SUPPORT, UPDATES, ENHANCEMENTS, OR MODIFICATIONS.
```
