---
title: "HOW TO: Configure LDAP for SUDO Support on Ubuntu Server 9.10 (Karmic Koala)"
date: 2010-03-04
forum: Outdated Tutorials &amp; Tips
---

### Post by hackajar on 2010-03-04
**Ubuntu 9.10 (Karmic Koala) SUDO-LDAP Walk-through**

**[COLOR=DarkRed]Table of Contents:[/COLOR]**[INDENT][B]Background
Assumptions
Server Configuration
Client Configuration[/B]
**Reference**
[/INDENT]**[COLOR=Sienna]Background:[/COLOR]**

There are many threads and documentation regarding inital setup of OpenLDAP with HDB on Ubuntu.  However, non fully address enabling SUDO access for users in a 100% LDAP environment (that is, no local UNIX account available).  This walk-through should address this lack of documentation.

**[COLOR=Sienna]Assumptions:[/COLOR]**


[LIST=1]
[*] You have already installed OpenLDAP for Ubuntu Server 9.10 -
[LIST]
[*][https://help.ubuntu.com/9.10/serverguide/C/openldap-server.html](https://help.ubuntu.com/9.10/serverguide/C/openldap-server.html)
[*][http://ubuntuforums.org/showthread.php?t=1313472](http://ubuntuforums.org/showthread.php?t=1313472)
[/LIST]
 
[*]Your current "Base" is ***"dc=example,dc=com"***
[*]Your LDAP Administrator is ***"dn=admin,dc=example,dc=com"***
[*]Your LDAP Server is listening on ***"127.0.0.1"***
[/LIST]
 **[COLOR=DarkRed]Server Configuration[/COLOR]**

**1.) **Install sudo-ldap package[INDENT] **I. **You will need to drop fully into root mode for this part!
```
sudo su
```**II.** Turn off SUDO safety switch
```
export SUDO_FORCE_REMOVE=yes
```**III.** Get package
```
apt-get install sudo-ldap
```**IV.** Turn on SUDO Safety switch
```
export SUDO_FORCE_REMOVE=no
```**V.** Drop back to user-land mode
```
exit
```[/INDENT]**2.) **Prime LDAP to support SUDO functions with the sudo.schema[INDENT]**I.** Create a directory to work out of
```
mkdir ~/sudoWork
```**II.** Copy the sudo Schema into the LDAP schema repository
```
sudo cp /usr/share/doc/sudo-ldap/schema.OpenLDAP /etc/ldap/schema/sudo.schema
```**III. **Create a conversion file for schema
```
sudo echo "include /etc/ldap/schema/sudo.schema" > ~/sudoWork/sudoSchema.conf
```**IV.** Now run the "Schema" to "LDIF" command *slapcat*
```
slapcat -f ~/sudoWork/sudoSchema.conf -F /tmp/ -n0 -s "cn={0}sudo,cn=schema,cn=config" > ~sudoWork/cn\=sudo.ldif
```**V.**  Clean-up outputted file (it will contain items that will break existing database if not removed!)
```
vi ~/sudoWork/cn\=sudo.ldif
```... And insure top of file looks EXACTLY like this:
```
dn: cn=sudo,cn=schema,cn=config
objectClass: olcSchemaConfig
cn: sudo
```... And insure bottom of file has ALL of the following removed:
**NOTE:** Your "Timestamp" line will be different time!  This is OK!
```
structuralObjectClass: olcSchemaConfig
entryUUID: 10dae0ea-0760-102d-80d3-f9366b7f7757
creatorsName: cn=config
createTimestamp: 20080826021140Z
entryCSN: 20080826021140.791425Z#000000#000#000000
modifiersName: cn=config
modifyTimestamp: 20080826021140Z
```**VI. **Now load this schema into the LDAP server
```
ldapadd -x -D cn=admin,cn=config -W -f ~/sudoWork/cn\=sudo.ldif
```**SUPPORT: **This is where stuff breaks a lot!  *You cannot move forward in How-To unless Step 2 is complete!  *Reply to thread for support help!

**VII.** Add Sudo Schema Index support
**[COLOR=Red]WARNING: [/COLOR]**Take note of the double ">>" in line, you do NOT want to accidentally blow out your configuration file!
```
sudo echo "index    sudoUser    eq" >> /etc/ldap.conf
```**VIII.** Reload your LDAP for changes to take effect
```
sudo /etc/init.d/slapd restart
```[/INDENT]**3.) **Build and Deploy the SUDO LDAP Container[INDENT]**I.** Create the file ~/sudoWork/sudoMaster.ldif ...
```
vi ~/sudoWork/sudoMaster.ldif
```...And populate it with the following lines:
```
dn: ou=SUDOers,dc=example,dc=com
objectClass: top
objectClass: organizationalUnit
ou: SUDOers
serviceSearchDescriptor: sudoers: ou=sudoers,dc=example,dc=com
```**II. ** Now convert your old /etc/sudoers configuration into LDAP modules
```
sudo su
``````
SUDOERS_BASE=ou=SUDOers,dc=example,dc=com
``````
export SUDOERS_BASE
```**[COLOR=Red]WARNING: [/COLOR]**Take note of the double    ">>" in line, you do NOT want to accidentally blow out your  file!```
perl /usr/share/doc/sudo-ldap/sudoers2ldif /etc/sudoers >> ~/sudoWork/sudoMaster.ldif
exit
```**III. **Now lets load configuration into LDAP
```
ldapadd -f ~/sudoWork/sudoMaster.ldif -h 127.0.0.1 -D cn=admin,dc=example,dc=com -W -x
```[/INDENT]**[COLOR=DarkRed]Client Configuration[/COLOR]**[COLOR=DarkRed][COLOR=Black]

**1.) **Install LDAP Client Configuration
[/COLOR][/COLOR][INDENT]**I. **Get LibNSS-LDAP package
[COLOR=SeaGreen]**TIP! **[/COLOR]Have your LDAP IP, Base Name, Admin Account and Admin Password Handy before executing this command
```
sudo apt-get install libnss-ldap
```...nCurses based setup screen will ask you information about your LDAP setup
**II.** Enable LDAP Support in PAM system
```
sudo auth-client-config -t nss -p lac_ldap
```**III.** Verify PAM based LDAP Support
```
sudo pam-auth-update
```[/INDENT][COLOR=DarkRed][COLOR=Black]
**NOTE:** Skip Step 2 for installation on the LDAP server as we already did this above![/COLOR]
[/COLOR]**2.) **Install sudo-ldap package[INDENT] **I. **You will need  to drop fully into root mode for this part!
```
sudo su
```**II.** Turn off SUDO safety switch
```
export SUDO_FORCE_REMOVE=yes
```**III.** Get package
```
apt-get install sudo-ldap
```**IV.** Turn on SUDO Safety  switch
```
export SUDO_FORCE_REMOVE=no
```**V.** Drop back to user-land  mode
```
exit
```[/INDENT][COLOR=DarkRed][COLOR=Black]**3.) **Manually setup sudo redirection from /etc/sudoers to LDAP directory
[/COLOR][/COLOR][INDENT]**I. **Add support for sudo extentions in /etc/ldap.conf
**[COLOR=Red]WARNING: [/COLOR]**Take note of the double     ">>" in line, you do NOT want to accidentally blow out your  file!
```
sudo echo "sudoers_base ou=SUDOers,dc=example,dc=com" >> /etc/ldap.conf
```**II.** Symbolically link Sudo Ldap Config file to main LDAP config file
**NOTE: **This is not obvious in ANY documentation I have reviewed, only support forums reveled this
```
sudo ln -s /etc/ldap.conf /etc/sudo-ldap.conf
```**III. **Add support for sudo / ldap communication in NS Switch configuration
**[COLOR=Red]WARNING: [/COLOR]**Take note of the double     ">>" in line, you do NOT want to accidentally blow out your  file!
```
sudo echo "sudoers: ldap" >> /etc/nsswitch.conf
```[/INDENT]**[COLOR=DarkRed]Reference[/COLOR]**

***OpenLDAP Server Installation Guide (official)*** [https://help.ubuntu.com/9.10/serverguide/C/openldap-server.html](https://help.ubuntu.com/9.10/serverguide/C/openldap-server.html)
[I][B]
HowTo: OpenLDAP and Karmic[/B][/I] [http://ubuntuforums.org/showthread.php?t=1313472](http://ubuntuforums.org/showthread.php?t=1313472)
[I][B]
SUDO LDAP ReadMe File[/B][/I] [http://www.gratisoft.us/sudo/readme_ldap.html](http://www.gratisoft.us/sudo/readme_ldap.html)
[I][B]
SUDO LDAP Manual[/B][/I] [http://www.gratisoft.us/sudo/man/sudoers.ldap.html#configuring_nsswitch_conf](http://www.gratisoft.us/sudo/man/sudoers.ldap.html#configuring_nsswitch_conf)
[LEFT][I][B]
Can't get sudo to work with ldap[/B][/I] [http://ubuntuforums.org/showthread.php?t=803212](http://ubuntuforums.org/showthread.php?t=803212)
[I][B]
sudo-ldap: should use alternative config file [patch][/B][/I] [http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=430826](http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=430826)


[/LEFT]

---

### Post by Squeazer on 2010-04-13
Oh wow, great guide! Altough i'm having a problem with step 3 of step 3 :). When i tipe in
```
ldapadd -f sudoWork/sudoMaster.ldif -h 127.0.0.1 -D cn=admin,dc=prvi-dijak,dc=si -W -x
```
(i deleted ~/ in every entry since it gave me problems) It gives me this result:
```
ldapadd -f sudoWork/sudoMaster.ldif -h 127.0.0.1 -D cn=admin,dc=prvi-dijak,dc=si -W -x 
Enter LDAP Password:
ldapadd: attributeDescription "dn": (possible missing newline after line 7, entry "ou=SUDOers,dc=prvi-dijak,dc=si"?)
adding new entry "ou=SUDOers,dc=prvi-dijak,dc=si"
ldap_add: Type or value exists (20)
        additional info: objectClass: value #0 provided more than once


```

Any ideas?


Oh, and a few more issues i noticed:
Problem 1: It said permission denied on:
```
sudo echo "index    sudoUser    eq" >> /etc/ldap.conf
```
so i manually inserted the line (index    sudoUser    eq) at the end of the file.
Problem 2: You have a typo in the "sudo /etc/init.d/sldap restart" command. Should be like this "sudo /etc/init.d/slapd restart" i assume (slapd instead of sldap).


Great tutorial BTW!!!


EDIT:

My sudoMaster.ldif starts like this:
```
dn: ou=SUDOers,dc=prvi-dijak,dc=si
objectClass: top
objectClass: organizationalUnit
ou: SUDOers
serviceSearchDescriptor: sudoers: ou=sudoers,dc=prvi-dijak,dc=si
dn: cn=defaults,ou=SUDOers,dc=prvi-dijak,dc=si
objectClass: top
objectClass: sudoRole
cn: defaults
description: Default sudoOption's go here
sudoOption: env_reset

```

I'm guessing there's supposed to be a break somewhere there? Not after serviceSearchDescriptor, that gives a "attribute type undefined" error.

---

### Post by hackajar on 2010-04-13
Try the following:

* Blow out (delete) SudoMaster file
* Create same file again with steps, stopping before the perl command step.
* Run THAT file into ldap (step 3 of 3)
* Run perl command on NEW output file
* Run THAT file into ldap (like in step 3 of 3).

Hopefully this will fix your issue.

P.S. since you already ran master file, you may get a notice that stuff is already added, you can ignore this message if it comes up.

---

### Post by Squeazer on 2010-04-13
Still no go. I get this message:

```
ldapadd -f sudoWork/sudoMaster.ldif -h 127.0.0.1 -D cn=admin,dc=prvi-dijak,dc=si -W -x
Enter LDAP Password:
adding new entry "ou=SUDOers,dc=prvi-dijak,dc=si"
ldap_add: Undefined attribute type (17)
        additional info: serviceSearchDescriptor: attribute type undefined
```

P.S. I am running the latest version of OpenLDAP - 2.4

---

### Post by hackajar on 2010-04-13
Ah-ha!

Recheck that everything was done correctly in section 2:II-VI.  This error is a result of the sudo scheme not being correctly initialized on the server.  It is VERY important that step 2:V is followed to a T. ;)

---

### Post by Squeazer on 2010-04-13
Hmm, will do, could you just give me a command to delete the old scheme from the LDAP server, since when i try to add the new one it prints out:

```
ldapadd -x -D cn=admin,cn=config -W -f sudoWork/cn\=sudo.ldif
Enter LDAP Password:
adding new entry "cn=sudo,cn=schema,cn=config"
ldap_add: Other (e.g., implementation specific) error (80)
        additional info: olcAttributeTypes: Duplicate attributeType: "1.3.6.1.4.1.15953.9.1.1"

```

Or will ldapadd add the scheme anyway?

---

### Post by Squeazer on 2010-04-13
ok, i manually deleted the schema, added it again (i was carefull) and the same thing. When i try to add the file (just those 5 lines) i get the "attribute type undefined" error.

---

### Post by hackajar on 2010-04-13
Try double checking that all standard scheme are installed correctly:

[http://ubuntuforums.org/showthread.php?t=1313472](http://ubuntuforums.org/showthread.php?t=1313472)

```

ldapadd -Y EXTERNAL -H ldapi:/// -f /etc/ldap/schema/cosine.ldif
ldapadd -Y EXTERNAL -H ldapi:/// -f /etc/ldap/schema/inetorgperson.ldif
ldapadd -Y EXTERNAL -H ldapi:/// -f /etc/ldap/schema/nis.ldif

```

---

### Post by Squeazer on 2010-04-13
yes, they all are, I followed that tutorial. These are the schemas I have installed:

cn={0}core.ldif
cn={1}cosine.ldif
cn={2}inetorgperson.ldif
cn={3}nis.ldif
cn={4}sudo.ldif

I also did this if it makes any difference: [http://www.youtube.com/watch?v=kSCx3tzC0cA](http://www.youtube.com/watch?v=kSCx3tzC0cA)

---

### Post by Squeazer on 2010-04-14
Well, i can manualy create (and i did) the organisational unit in phpLDAPadmin but i see no way of adding the serviceSearchDescriptor attribute. Is there a way to do it?
EDIT:
LDAPsoft Ldap Amin Tool (windows) doesn't list that attribute either, so perhaps i'm missing a schema for that? I'm really just getting started with LDAP and i'm kinda lost.

---

### Post by Squeazer on 2010-04-14
Ok, this is stupid. The way i gave my users sudo was:

when you login with a user account that is based in ldap and type in "groups", the user account will show that it belongs to an LDAP based group (naturaly). Now if that group is in the sudoers file the system will alow him to excecute the sudo command. If i used a group "admin" the system gave me problems, so i just created a new group in my ldap database called SUDOers (posix group) and added it to the sudoers file (sudo visudo).
I'm sorry to say this but this tutorial is meaningless (i dont know much about LDAP so if the way you did it gives you something more, i apoloagise).
I DO however admire you, as you tried to help me in my struggles to set this thing up :).

P.S. I am still in the process of testing my theory, and it has worked so far. I will write here again with further results.

---

### Post by hackajar on 2010-04-14
I have attempted to recreate your error, and cannot :(

It appears that we have reached the end of both our understanding with what is going on here.

---

### Post by Squeazer on 2010-04-15
Indeed. Well, i'm not going to bother myself with this anymore since i got what i wanted. One more question tough, since i've been having problems with an "admin" group. This is not a big issue, i just want to know hy it happens. If i put my LDAP user into a posix group named "admin", when i log in it says that i'm logged in with a different user than the one i actually am. I still get into that users home dir, it just shows that i'm not that user, but a local admin user called "pgmadmin" (pgmadmin@myip$) that is in a local group called "admin". Why is this happening?

P.S. In step 2 / IV you are missing a leading slash at the end (~sudoWork/cn\=sudo.ldif)

---

### Post by sumerset on 2010-04-16
Hello everyone,

I need some help setting a ldap cache proxy on ubuntu.

I have configured the ldap.conf for proxy and using the pcache overlay. I also have some filters and proxy templates set to save the searches.

However it seems that the server is not caching the search results.

I'm testing this using a ldap explorer connected to the proxy and using wireshark set to capture packets in the tcp port 389.

From what i can see the proxy is always connecting to the ldap server to retrieve the responses, instead of using the local cache.

Another problem i have is the binding between the cache proxy and the ldap server. It never seems to work.

I would appreciate if someone could help me. Thanks in advance.

Currently i have the following ldap.conf

> 
include /etc/ldap/schema/core.schema
include /etc/ldap/schema/cosine.schema
include /etc/ldap/schema/inetorgperson.schema
include /etc/ldap/schema/nis.schema
pidfile /var/run/slapd/slapd.pid
argsfile /var/run/slapd/slapd.args
loglevel none
modulepath /usr/lib/ldap
moduleload back_ldap
moduleload pcache
moduleload back_bdb
################
# LDAP Backend #
################
database ldap
uri "ldap://192.168.1.62"
suffix "dc=example,dc=com"
rootdn "dc=example, dc=com"
rootpw example
#tls start
#idassert-bind bindmethod=simple binddn="cn=admin,dc=example,dc=net" credentials="example" mode=none
#idassert-authzFrom "dn.subtree:dc=example,dc=com"

overlay pcache
proxycache bdb 1000000 1 1000 1200
directory /var/lib/ldap/cache
cachesize 1000000

index uid eq
index mail eq
index uidNumber eq
index gidNumber eq
index memberUid eq
index description eq
index sn eq
index cn pres,eq,sub
#index cn eq
index objectclass,queryid eq

proxycachequeries 1000000
proxyattrset 0 uid mail cn sn givenName objectClass
proxytemplate (uid=) 0 600
proxytemplate (cn=) 0 600
proxytemplate (objectclass=) 0 600
proxytemplate (mail=) 0 600
proxytemplate (&(uid=)(mail=)) 0 600
proxytemplate (&(uid=)(objectclass=)) 0 600
proxytemplate (&(objectclass=)(cn)) 0 600
proxytemplate (&(uid=)(objectclass=)(cn)) 0 600


---

### Post by melba on 2010-04-21
Hi hackajar,

I follow your instructions in the howto yesterday.

At the point to play in the sudoMaster.ldif-file via ldapadd, the util breaks with the Errormsg:

```
slapd[12873]: Entry (ou=SUDOers,dc=linformatik,dc=lan), attribute 'serviceSearchDescriptor' not allowed
```When comment out the line with the "serviceSearchDesciptor" the ldapadd-utility play in the sudoMaster.ldif without an error.

I think it was not a good idea to comment out the line while now i can`t do a sudo command.

When i try a sudo-command, i`ve become following errormsg:

```
sudo: ldap_sasl_bind_s(): Can't contact LDAP server
sudo: no valid sudoers sources found, quitting

```Can you help me, my System to repair, so that i can do sudo-commands.

I have no idea to rollback to the localy sudo and no idea to set sudo-ldap correctly that i can do commands as sudo-user.

Changes i must done in the LDAP-Configuration can I do as cn=admin.

Finally, your How To is very helpfully for me.

Thanks

---

### Post by shylux on 2010-09-28
Hello
I follow the Tutorial an all comands work fine.
But now, if i want to sudo with a ldap user i get this error:
```
sudo: setreuid(ROOT_UID, user_uid): Operation not permitted
```
Can anyone help?

---

### Post by arthur.duarte on 2010-12-24
This tutorial seems to be awesome!

But I had the same problem with the attribute not being able to be added.

So I relied on a script that could pull the members from a group in LDAP and insert it on the sudoers files.

Each time I add or remove, the script sync a new sudoers files with the new users.

Thank You.

---

### Post by cvalentine02 on 2011-03-21
> **Squeazer said:**
> Oh wow, great guide! Altough i'm having a problem with step 3 of step 3 :). When i tipe in
```
ldapadd -f sudoWork/sudoMaster.ldif -h 127.0.0.1 -D cn=admin,dc=prvi-dijak,dc=si -W -x
```(i deleted ~/ in every entry since it gave me problems) It gives me this result:
```
ldapadd -f sudoWork/sudoMaster.ldif -h 127.0.0.1 -D cn=admin,dc=prvi-dijak,dc=si -W -x 
Enter LDAP Password:
ldapadd: attributeDescription "dn": (possible missing newline after line 7, entry "ou=SUDOers,dc=prvi-dijak,dc=si"?)
adding new entry "ou=SUDOers,dc=prvi-dijak,dc=si"
ldap_add: Type or value exists (20)
        additional info: objectClass: value #0 provided more than once


```

I successfully followed the tutorial for setting up SAMBA + LDAP: [http://tuxnetworks.blogspot.com/2010/07/howto-samba-ldap-on-1004-lucid-short.html](http://tuxnetworks.blogspot.com/2010/07/howto-samba-ldap-on-1004-lucid-short.html). I made minor mods to allow notebook users to login with locally cached LDAP database while working remotely.

I got the same errors as mentioned above by Squeazer. This is after changing the ldapadd method used to match the tutorial. Not sure if this helps, but the issue may rely in the details of how this was setup.

I had to reinstall sudo & used Squeaker's SUDOers LDAP group. All is fine with this much simpler method. The only real disadvantage is that I must add this to all LDAP clients in order to use the group, but with only a handful of clients, the pain is minimal.

---

