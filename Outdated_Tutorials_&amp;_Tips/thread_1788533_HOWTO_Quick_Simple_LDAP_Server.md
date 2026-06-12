---
title: "HOWTO: Quick Simple LDAP Server"
date: 2011-06-22
forum: Outdated Tutorials &amp; Tips
---

### Post by slooksterpsv on 2011-06-22
Downloaded Ubuntu 11.04 64-bit Server
Installing using the hostname: slookytech
No Proxy
Setup LAMP server.
Set mysql root password.
Reboot.
Login.

Run the following:
```

sudo apt-get install slapd ldap-utils migrationtools
sudo rm -R /etc/ldap/slapd.d
sudo dpkg-reconfigure slapd

```
Set your settings in slapd:
Omit OpenLDAP server configuration - No
DNS Domain name: slookytech.local
Name of org: Slookytech
Password - of course put in what you need
BDB
Do you want your db to be removed when slapd is purged? - No
Move old database? - Yes
Allow LDAPv2 Protocol? - No
```

sudo /etc/init.d/slapd restart

```
Make sure you can search for you ldap server via:
```

ldapsearch -x -b dc=slookytech,dc=local

```

Next modify /etc/migratetools/migrate_common.ph - I use pico but you can sub in vi or vim if needed:
```

sudo pico /etc/migrationtools/migrate_common.ph

```
Change where I put slookytech.local to yours, and dc=slookytech,dc=local its down below:
```

$DEFAULT_MAIL_DOMAIN = "slookytech.local";
$DEFAULT_BASE = "dc=slookytech,dc=local"; 

```
Now do:
```

cd /usr/share/migrationtools/
sudo ./migrate_group.pl /etc/group ~/group.ldif
sudo ./migrate_passwd.pl /etc/passwd ~/passwd.ldif 

```
Now create a file with:
```

dn: ou=People, dc=slookytech, dc=local
ou: People
objectclass: organizationalUnit

dn: ou=Group, dc=slookytech, dc=local
ou: Group
objectclass: organizationalUnit 

```
Changing the dc= with what reflects on your ldap server. Save it as: people_group.ldif in your home folder, now run:
```

sudo ldapadd -x -W -D "cn=admin,dc=slookytech,dc=local" -f ~/people_group.ldif
sudo ldapadd -x -W -D "cn=admin,dc=slookytech,dc=local" -f ~/group.ldif
sudo ldapadd -x -W -D "cn=admin,dc=slookytech,dc=local" -f ~/passwd.ldif 

```
Server config finished.

The server was the easy part, the client, however, was not. Check back in a while to see if I've uploaded the client part.

---

