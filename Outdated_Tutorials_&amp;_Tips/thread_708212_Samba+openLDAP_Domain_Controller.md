---
title: "Samba+openLDAP Domain Controller"
date: 2008-02-26
forum: Outdated Tutorials &amp; Tips
---

### Post by cpthk on 2008-02-26
Hi:

This is a guide combining knowledge from lots of tutorials and come up with the easiest way to setup a domain controller for windows. There is a complete tutorial from rickyjones here: [http://ubuntuforums.org/showthread.php?t=640760](http://ubuntuforums.org/showthread.php?t=640760) . Many thanks to  rickyjones, without his help I wouldn't able to come up this tutorial. If what you need is a quick start tutorial with the simplest setting as possible. This one is what you need. If you are trying to have a complete settings, you should probably go to the rickyjones one. This tutorial assume you understood the basic knowledge of linux. For example, you should know how to go to edit mode, save and quit in vim.(It's fairly simple) Some settings you will need to change to the way you like. Let's get started.

Ubuntu installed

Get root permission
```
sudo bash
```Edit /etc/hosts file
```
vim /etc/hosts
```update to:
```
127.0.0.1       localhost
127.0.1.1       pdc pdc.example.local

# The following lines are desirable for IPv6 capable hosts
::1     ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts

```

Update /etc/hostname file
```
vim /etc/hostname
```
update to:
```
pdc.example.local
```

Install needed package
```
apt-get install slapd ldap-utils samba smbldap-tools samba-doc
```
During the installation, you might get prompt to setup openLDAP admin password, just enter you one you like

Update openLDAP
```
dpkg-reconfigure slapd
```Settings:
```
No
DNS domain name: example.local
Name of your organization: example.local
Admin password: (Enter again from last step)
Confirm password: (Enter again from last step)
OK
BDB
No
Yes
No
```

Copy samba.schema to openLDAP folder
```
cp /usr/share/doc/samba-doc/examples/LDAP/samba.schema.gz /etc/ldap/schema/
gzip -d /etc/ldap/schema/samba.schema.gz
```

Edit /etc/ldap/slapd.conf
```
vim /etc/ldap/slapd.conf
```
Add
```
include /etc/ldap/schema/samba.schema
```
Update
```
access to attrs=userPassword,shadowLastChange,sambaNTPassword,sambaLMPassword
```
This step you might see "access to attribute", change to attrs.

Restart openLDAP
```
/etc/init.d/slapd restart
```

Copy required files
```
cp /usr/share/doc/smbldap-tools/examples/smbldap_bind.conf /etc/smbldap-tools/
cp /usr/share/doc/smbldap-tools/examples/smbldap.conf.gz /etc/smbldap-tools/
gzip -d /etc/smbldap-tools/smbldap.conf.gz
```

Get domain SID
```
net getlocalsid
```

Edit smbldap.conf
```
vim /etc/smbldap-tools/smbldap.conf
```
Update
```
SID="(Copy from last step)"
sambaDomain="EXAMPLE"
ldapTLS="0"
suffix="dc=example,dc=local"
sambaUnixIdPooldn="sambaDomainName=${sambaDomain},${suffix}"
userSmbHome=
userProfile=
userHomeDrive=
userScript=
;mailDomain="IDEALX.ORG"
```
All lines are included, you just have to update them.

Edit smbldap_bind.conf file
```
vim /etc/smbldap-tools/smbldap_bind.conf
```
Update
```
slaveDN="cn=admin,dc=example,dc=local"
slavePw="(Your openLDAP password)"
masterDN="cn=admin,dc=example,dc=local"
masterPw="(Your openLDAP password)"
```
All lines are included, you just have to update them.

Set file permission
```
chmod 0600 /etc/smbldap-tools/smbldap_bind.conf
```

Populate to openLDAP server
```
smbldap-populate
```
You might get prompt for openLDAP password, just enter the one you set.

Edit /etc/samba/smb.conf file
```
vim /etc/samba/smb.conf
```
Update
```
workgroup = EXAMPLE
security = user
passdb backend = ldapsam:ldap://localhost/
obey pam restrictions = no
;invalid users = root
domain logons = yes
```
Add
```
ldap admin dn = cn=admin,dc=example,dc=local
ldap suffix = dc=example, dc=local
ldap group suffix = ou=Groups
ldap user suffix = ou=Users
ldap machine suffix = ou=Computers
ldap idmap suffix = ou=Users
```
If root is not your manager account, add another line
```
admin users = USER_NAME
```

Restart samba
```
/etc/init.d/samba restart
```

Set openLDAP password for samba
```
smbpasswd -w (Your openLDAP password)
```

Until here, you are pretty much done.

Here is how to add users, you can use the text mode or GUI mode like phpldapadmin.

**Text Mode:**
Add user
```
smbldap-useradd -a -m USER_NAME
useradd -g GROUP USER_NAME
smbldap-passwd USER_NAME
```

Add machine account
```
smbldap-useradd -a -m MACHINE_NAME$
useradd –-g GROUP -–d /dev/null -–s /dev/null MACHINE_NAME$
```
Notice there is a $ sign after machine name.

**Install GUI Mode:**
```
apt-get install apache2 phpldapadmin
```
Edit /etc/apache2/httpd.conf
```
vim /etc/apache2/httpd.conf
```
Add
```
ServerName pdc.example.local
```
Restart apache
```
/etc/init.d/apache2 restart
```
Copy phpldapadmin to apache www directory
```
cp -R /usr/share/phpldapadmin/ /var/www/phpldapadmin
```
GUI Mode is really simple, you just have to open up the browser and go to [http://localhost/phpldapadmin/](http://localhost/phpldapadmin/) . Login as username cn=admin,dc=example,dc=local and your openLDAP password. Then you may add user or machine account throught the left side of the menu. If you are trying to add machine account. Click on "Create new entry here" under "ou=Computers", and select "Samba3 Machine".

After all the procedures, you may login your Windows client into the doamin. Right click on "My Computer" -> Properties -> Computer Name -> Either "Network ID" or "Change..."

If you have any question, I will try to answer you when I'm free. But since I am new to this too. My answer will be very limited. This tutorial I have tried myself on several computers. So I am pretty sure it works unless I missed something. There are lots of settings you need to study yourself since this is the easiest way of setting up. So I do not want to include them. For example the samba's netlogon and shares settings in smb.conf.

Changelogs:
2/26/2008 - First version

---

### Post by kwisher on 2008-04-13
Much thanks for this how-to.

When I entered the code below:

access to attrs=userPassword,shadowLastChange,sambaNTPassword,sambaLMPassword

I get an error that the access command cannot be found. Do you have any suggestions?

Also, from Linux how do you logon to a PDC? Is the PDC only beneficial to Window clients?

TIA

---

### Post by cpthk on 2008-04-16
do you mean you enter that line, and restart slapd and you get an error?

Yes, this is only for windows to login. Linux can use openssh to login.

---

### Post by Nevell on 2008-05-11
Crosspost:> Anybody use: [https://help.ubuntu.com/community/LDAP-Samba_PDC_(for_Linux_and_Windows](https://help.ubuntu.com/community/LDAP-Samba_PDC_(for_Linux_and_Windows)) ?
If this howto work fine, maybe whos help write community doc? Because community doc not finished, and i can't download *LDAPServer.tar.gz* (downloaded 0 byte - blank file), this file need for setup...

**P.S.** Some distribs have directory server packages:
Fedora Directory Server: [http://directory.fedoraproject.org/](http://directory.fedoraproject.org/)
Mandriva Directory Server: [http://mds.mandriva.org/](http://mds.mandriva.org/)
Where is **Ubuntu Directory Server**? ;)
[http://ubuntuforums.org/showpost.php?p=4936013&postcount=632](http://ubuntuforums.org/showpost.php?p=4936013&postcount=632)

---

### Post by gabrielvargas7 on 2008-10-29
OK, I do very good everything 
that only thing is that when I tried to change the password from windows compute, it is not allow.
so I solve it changing the follow line on 
smb.conf

   	
 unix password sync = yes
change to 
 unix password sync = no

this work for me

---

