---
title: "Ubuntu Server 12.10 Samba+LDAP: Fail to add samba user."
date: 2013-02-19
forum: New to Ubuntu
---

### Post by IJselflearner on 2013-02-19
Hi Ubuntu Professionals,
 
 
I'm new to Ubuntu server and trying to configure a Domain Controller using Samba and OpenLDAP.
 
I have successfuly followed the setup guide for Network Authentication in Ubuntu Server Guide, already configured OpenLDAP ([[COLOR=#444444]https://help.ubuntu.com/12.10/server...ap-server.html[/COLOR]]("https://help.ubuntu.com/12.10/serverguide/openldap-server.html")) and Samba and LDAP ([[COLOR=#444444]https://help.ubuntu.com/12.10/server...amba-ldap.html[/COLOR]]("https://help.ubuntu.com/12.10/serverguide/samba-ldap.html")) so far but got stuck along the Samba Configuration, adding samba users:
 
~$ sudo smbldap-useradd -a -P client2
 
this is the response -->
 
Use of qw(...) as parentheses is deprecated at /usr/share/per15/smbldap_tools.pm
line 1423, <DATA> line 558.
Use of uninitialized value $value in substitution (s///) at /usr/share/per15/smbldap_tools.pm line 153, <CONFIGFILE> line 122.
Failed to execute: /usr/sbin/smbldap-passwd.cmd: no such file or directory at /usr/sbin/smbldap-useradd line 668.
 
Where did it possibly went wrong?
 
Anyone can guide me with the additional configuration that I need to do?
 
 
thanks in advance.
 
- ij -

---

