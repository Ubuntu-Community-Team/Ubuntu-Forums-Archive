---
title: "Adding Samba LDAP objects error..."
date: 2013-07-09
forum: New to Ubuntu
---

### Post by anondude on 2013-07-09
Hi.
As I've mentioned in another post, I'm exploring/learning Ubuntu Server (12.04LTS).
In this particular case I'm exploring SAMBA integration with LDAP. Following the manual, I reached section 2.2.3-Adding Samba LDAP objects where I am now stuck. I've read manuals/guides/bug reports, figured out the issue with "configure.pl" file. I followed this procedure:

$ apt-get source smbldap-tools
$ perl ./smbldap-tools-0.9.7/smbldap-config.pl
 $ cd smbldap-tools-0.9.7/
$ ./configure
$ make
$ ./smbldap-config.cmd

I'm stuck on the last command. Running smbldap-config.cmd gives me these errors:

./smbldap-config.cmd: line 31: use: command not found
./smbldap-config.cmd: line 32: use: command not found
./smbldap-config.cmd: line 35: syntax error near unexpected token `{'
./smbldap-config.cmd: line 35: `if ($< != 0) {'

As an extra note, I did all this as 'root' user to be sure I didn't have any permissions issues.

Does anyone know what I'm doing wrong?

Thanks in advance!

---

### Post by anondude on 2013-07-10
Bump.

Anyone?

---

