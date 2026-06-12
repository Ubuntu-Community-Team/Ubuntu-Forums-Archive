---
title: "[HOW TO] Ubuntu Server 9.04 PDC"
date: 2009-06-11
forum: Outdated Tutorials &amp; Tips
---

### Post by ingcabral on 2009-06-11
First of all, I want to thank the Ubuntu community. This is a brief guide with parts taken from this links:

[https://help.ubuntu.com/community/OpenLDAP-SambaPDC-OrgInfo-Posix](https://help.ubuntu.com/community/OpenLDAP-SambaPDC-OrgInfo-Posix)
and
[http://www.howtoforge.com/openldap-samba-domain-controller-ubuntu7.10](http://www.howtoforge.com/openldap-samba-domain-controller-ubuntu7.10)

Thanks all of you guys.

Intro:
    Following the previous guides you will find many differences for getting your PDC up and running. For further information, please refer to the links above, I'm just attempting to make a step-through step guide that will make your PDC work in less than 15 minutes. Worked for me the last three times I used this guide, with roaming profiles disabled.
For this example, we will be using the domain 'ubuntudom'. Replace the 'ubuntudom' entry with your own domain name! Files attached here are 100% working if you follow this tutorial step by step.
Hold your breath, here we go:

1) Install OpenLDAP ..

sudo apt-get --yes install slapd ldap-utils db4.2-util

1.1) Completely delete the slapd.d directory inside /etc/ldap/
1.2) Edit /etc/default/slapd and look for the line
    SLAPD_CONF=

     And add the following:
    SLAPD_CONF=/etc/ldap/slapd.conf

2) Install Samba documentation containing the Samba schema. Extract samba.schema and copy to the required system area for OpenLDAP.

sudo apt-get --yes install samba-doc
sudo gunzip /usr/share/doc/samba-doc/examples/LDAP/samba.schema.gz
sudo cp -v /usr/share/doc/samba-doc/examples/LDAP/samba.schema /etc/ldap/schema

3) Decide on an LDAP admin password and generate a SSHA hash key for it.

slappasswd

4) Create an init.ldif file. Name the 4 OUs Users, Groups, Computers and Idmap for use with smbldap-tools. - Remember to replace 'ubuntudom' with your domain name

```

dn: dc=ubuntudom
objectClass: dcObject
objectClass: organizationalUnit
dc: ubuntudom
ou: Ubuntudom

dn: cn=admin,dc=ubuntudom
objectClass: simpleSecurityObject
objectClass: organizationalRole
cn: admin
description: LDAP administrator
userPassword: {SSHA}paste-here-the-results-of-slappaswd 
# example: userPassword: {SSHA}iPFTqrtFrEET3DSQot2wxCuuljKA9vMU -- DELETE THIS LINE, FOR EXAMPLE PURPOSE


dn: ou=Users,dc=ubuntudom
objectClass: organizationalUnit
ou: Users

dn: ou=Groups,dc=ubuntudom
objectClass: organizationalUnit
ou: Groups

dn: ou=Computers,dc=ubuntudom
objectClass: organizationalUnit
ou: Computers

dn: ou=Idmap,dc=ubuntudom
objectClass: organizationalUnit
ou: Idmap

```

4) Modify /etc/ldap/slapd.conf for this site, and paste this .. - Remember to replace 'ubuntudom' with your domain name
```
# Remember to replace suffix "dc=ubuntudom" with your domain name
# Change the rootpw entry with the results from slappaswd (Must match the same you pasted on init.ldif)

# /etc/ldap/slapd.conf
# This is the main slapd configuration file. See slapd.conf(5) for more
# info on the configuration options.

#######################################################################
# Global Directives:

# Features to permit
#allow bind_v2

# Schema and objectClass definitions
include         /etc/ldap/schema/core.schema
include         /etc/ldap/schema/cosine.schema
include         /etc/ldap/schema/nis.schema
include         /etc/ldap/schema/inetorgperson.schema
include         /etc/ldap/schema/samba.schema
include         /etc/ldap/schema/misc.schema

# Where the pid file is put. The init.d script
# will not stop the server if you change this.
pidfile         /var/run/slapd/slapd.pid

# List of arguments that were passed to the server
argsfile        /var/run/slapd/slapd.args

# Read slapd.conf(5) for possible values
loglevel        0

# Where the dynamically loaded modules are stored
modulepath      /usr/lib/ldap
moduleload      back_bdb

# The maximum number of entries that is returned for a search operation
sizelimit 500

# The tool-threads parameter sets the actual amount of cpu's that is used
# for indexing.
tool-threads 1

#######################################################################
# Specific Backend Directives for bdb:
# Backend specific directives apply to this backend until another
# 'backend' directive occurs
backend         bdb
#checkpoint 512 30

#######################################################################
# Specific Backend Directives for 'other':
# Backend specific directives apply to this backend until another
# 'backend' directive occurs
#backend                <other>

#######################################################################
# Specific Directives for database #1, of type bdb:
# Database specific directives apply to this databasse until another
# 'database' directive occurs
database        bdb

# The base of your directory in database #1
suffix          "dc=ubuntudom"

# rootdn directive for specifying a superuser on the database. This is needed
# for syncrepl.
rootdn          "cn=admin,dc=ubuntudom"
rootpw {SSHA}iPFTqrtwr3yT3XGQot2wxCuuljKA9vMU

# Where the database file are physically stored for database #1
directory       "/var/lib/ldap"

# For the Debian package we use 2MB as default but be sure to update this
# value if you have plenty of RAM
dbconfig set_cachesize 0 2097152 0

# Sven Hartge reported that he had to set this value incredibly high
# to get slapd running at all. See http://bugs.debian.org/303057
# for more information.

# Number of objects that can be locked at the same time.
dbconfig set_lk_max_objects 1500
# Number of locks (both requested and granted)
dbconfig set_lk_max_locks 1500
# Number of lockers
dbconfig set_lk_max_lockers 1500

# Indexing options for database #1
#index           objectClass eq, pres
index ou,cn,sn,mail,givenname           eq,pres,sub
index uidNumber,gidNumber,memberUid     eq,pres
index loginShell                        eq,pres
index uniqueMember                      eq,pres
index uid                               pres,sub,eq
index displayName                       pres,sub,eq
index sambaSID                          eq
index sambaPrimaryGroupSID              eq
index sambaDomainName                   eq
index default                           sub
#index   uid         pres,eq,sub

# Save the time that the entry gets modified, for database #1
lastmod         on

# Where to store the replica logs for database #1
# replogfile    /var/lib/ldap/replog

# The userPassword by default can be changed
# by the entry owning it if they are authenticated.
# Others should not be able to see it, except the
# admin entry below
# These access lines apply to database #1 only
access to attrs=userPassword,shadowLastChange
        by dn="cn=admin,dc=ubuntudom" write
        by anonymous auth
        by self write
        by * none

# Ensure read access to the base for things like
# supportedSASLMechanisms.  Without this you may
# have problems with SASL not knowing what
# mechanisms are available and the like.
# Note that this is covered by the 'access to *'
# ACL below too but if you change that as people
# are wont to do you'll still need this if you
# want SASL (and possible other things) to work
# happily.
access to dn.base="" by * read

# The admin dn has full write access, everyone else
# can read everything.
access to *
        by dn="cn=admin,dc=ubuntudom" write
        by * read

# For Netscape Roaming support, each user gets a roaming
# profile for which they have write access to
#access to dn=".*,ou=Roaming,o=morsnet"
#        by dn="cn=admin,dc=example,dc=ch" write
#        by dnattr=owner write

#######################################################################
# Specific Directives for database #2, of type 'other' (can be bdb too):
# Database specific directives apply to this databasse until another
# 'database' directive occurs
#database        <other>

# The base of your directory for database #2
#suffix         "dc=debian,dc=org"
```




5) Initialise OpenLDAP database ..

sudo /etc/init.d/slapd stop
sudo rm -rf /var/lib/ldap/*
sudo slapadd -v -l init.ldif
/etc/ldap/slapd.conf: line 109: rootdn is always granted unlimited privileges.
/etc/ldap/slapd.conf: line 126: rootdn is always granted unlimited privileges.
 added: "dc=ubuntudom" (00000001)
 added: "cn=admin,dc=ubuntudom" (00000002)
 added: "ou=Users,dc=ubuntudom" (00000003)
 : : :
sudo chown -R openldap:openldap /var/lib/ldap
sudo /etc/init.d/slapd start
Confirm all is OK with a Search ..

ldapsearch -xLLL -b "dc=ubuntudom"
 dn: dc=ubuntudom
 objectClass: dcObject
 objectClass: organizationalUnit
 : : :


6) Install and Configure Samba

sudo apt-get --y install libtalloc1 smbclient samba libpam-smbpass

7) Create Samba folders that have not been automatically created ..

sudo mkdir -v /var/lib/samba/profiles
sudo chmod 777 /var/lib/samba/profiles
sudo mkdir -v -p /var/lib/samba/netlogon

8) Edit /etc/samba/smb.conf - so it looks EXACTLY like this but replacing your domain name

```
[global]
        # Domain name ..
        workgroup = UBUNTUDOM
        # Server name - as seen by Windows PCs ..
        netbios name = SERVERNAME
        # Be a PDC ..
        domain logons = Yes
        domain master = Yes
        # Be a WINS server ..
        wins support = true

        obey pam restrictions = Yes
        dns proxy = No
        os level = 35
        log file = /var/log/samba/log.%m
        max log size = 1000
        syslog = 0
        panic action = /usr/share/samba/panic-action %d
        pam password change = Yes

        # Allows users on WinXP PCs to change their password when they press Ctrl-Alt-Del
        unix password sync = no
        ldap passwd sync = yes

        # Printing from PCs will go via CUPS ..
        load printers = yes
        printing = cups
        printcap name = cups

        # Use LDAP for Samba user accounts and groups ..
        passdb backend = ldapsam:ldap://localhost

        # This must match init.ldif ..
        ldap suffix = dc=ubuntudom
        # The password for cn=admin MUST be stored in /etc/samba/secrets.tdb
        # This is done by running 'sudo smbpasswd -w'.
        ldap admin dn = cn=admin,dc=ubuntudom

        # 4 OUs that Samba uses when creating user accounts, computer accounts, etc.
        # (Because we are using smbldap-tools, call them 'Users', 'Computers', etc.)
        ldap machine suffix = ou=Computers
        ldap user suffix = ou=Users
        ldap group suffix = ou=Groups
        ldap idmap suffix = ou=Idmap
        # Samba and LDAP server are on the same server in this example.
        ldap ssl = no

        # Scripts for Samba to use if it creates users, groups, etc.
        add user script = /usr/sbin/smbldap-useradd -m '%u'
        delete user script = /usr/sbin/smbldap-userdel %u
        add group script = /usr/sbin/smbldap-groupadd -p '%g'
        delete group script = /usr/sbin/smbldap-groupdel '%g'
        add user to group script = /usr/sbin/smbldap-groupmod -m '%u' '%g'
        delete user from group script = /usr/sbin/smbldap-groupmod -x '%u' '%g'
        set primary group script = /usr/sbin/smbldap-usermod -g '%g' '%u'

        # Script that Samba users when a PC joins the domain ..
        # (when changing 'Computer Properties' on the PC)
        add machine script = /usr/sbin/smbldap-useradd -w '%u'

        # Values used when a new user is created ..
        # (Note: '%L' does not work properly with smbldap-tools 0.9.4-1)
    logon drive =
        logon home =
        logon path =
        logon script =


        # This is required for Windows XP client ..
        server signing = auto
        server schannel = Auto

[homes]
        comment = Home Directories
        valid users = %S
        read only = No
        browseable = No

[netlogon]
        comment = Network Logon Service
        path = /var/lib/samba/netlogon
        admin users = root
        guest ok = Yes
        browseable = No

[Profiles]
        comment = Roaming Profile Share
        # would probably change this to elsewhere in a production system ..
        path = /var/lib/samba/profiles
        read only = No
        profile acls = Yes
        browsable = No

[printers]
        comment = All Printers
        path = /var/spool/samba
        use client driver = Yes
        create mask = 0600
        guest ok = Yes
        printable = Yes
        browseable = No
        public = yes
        writable = yes
        admin users = root
        write list = root

[print$]
        comment = Printer Drivers Share
        path = /var/lib/samba/printers
        write list = root
        create mask = 0664
        directory mask = 0775
        admin users = root
```

9) Write password for the LDAP admin account (eg. cn=admin,dc=ubuntudom) into /etc/samba/secrets.tdb
sudo smbpasswd -W
 Setting stored password for "cn=admin,dc=ubuntudom" in secrets.tdb
 New SMB password:
 Retype new SMB password:

10) Restart Samba ..

sudo /etc/init.d/samba restart

11) Use the SMB client to check that the Samba server is responding correctly. 
smbclient -L localhost -U anonymous%
Anonymous login successful
Domain=[UBUNTUDOM] OS=[Unix] Server=[Samba 3.3.2]

    Sharename       Type      Comment
    ---------       ----      -------
    IPC$            IPC       IPC Service (Samba 3.3.2)
    print$          Disk      Printer Drivers Share

Anonymous login successful
Domain=[UBUNTUDOM] OS=[Unix] Server=[Samba 3.3.2]

    Server               Comment
    ---------            -------
               
    SERVERNAME          Samba 3.3.

    Workgroup            Master
    ---------            -------
    UBUNTUDOM                SERVERNAME

12) Install smbldap-tools and extract the configure.pl script.

sudo apt-get install smbldap-tools
sudo gunzip /usr/share/doc/smbldap-tools/configure.pl.gz
sudo chmod +x /usr/share/doc/smbldap-tools/configure.pl

13) Before configuring smbldap-tools, check that Samba is running and the Windows domain SID can be retrieved.

ps -e | grep -i "smb"
 4956 ? 00:00:00 smbd
 5096 ? 00:00:00 smbd
sudo net getlocalsid
 SID for domain SERVERNAME is: S-1-5-21-2899629268-4176875250-2352135513

14) Populate the LDAP database with essential Samba entries. This includes the creation of standard groups, such as Administrators and Domain Users.

sudo smbldap-populate
 Populating LDAP directory for domain UBUNTUDOM (S-1-5-21-2899629268-4176875250-2352135513)
 (using builtin directory structure)
 entry dc=ubuntudom already exist. 
 entry ou=Users,dc=ubuntudom already exist. 
 entry ou=Groups,dc=ubuntudom already exist. 
 entry ou=Computers,dc=ubuntudom already exist. 
 entry ou=Idmap,dc=ubuntudom already exist. 
 adding new entry: uid=root,ou=Users,dc=ubuntudom
 adding new entry: uid=nobody,ou=Users,dc=ubuntudom
 adding new entry: cn=Domain Admins,ou=Groups,dc=ubuntudom
 adding new entry: cn=Domain Users,ou=Groups,dc=ubuntudom
 adding new entry: cn=Domain Guests,ou=Groups,dc=ubuntudom
 adding new entry: cn=Domain Computers,ou=Groups,dc=ubuntudom
 adding new entry: cn=Administrators,ou=Groups,dc=ubuntudom
 adding new entry: cn=Account Operators,ou=Groups,dc=ubuntudom
 adding new entry: cn=Print Operators,ou=Groups,dc=ubuntudom
 adding new entry: cn=Backup Operators,ou=Groups,dc=ubuntudom
 adding new entry: cn=Replicators,ou=Groups,dc=ubuntudom
 entry sambaDomainName=UBUNTUDOM,dc=ubuntudom already exist. Updating it...
 Please provide a password for the domain root: 
 Changing UNIX and samba passwords for root
 New password: 
 Retype new password:

15) Following this, stop the LDAP server, run slapindex, and restart the LDAP server.

sudo /etc/init.d/slapd stop
 Stopping OpenLDAP: slapd.
sudo slapindex 
 WARNING!
 Runnig as root!
 There's a fair chance slapd will fail to start.
 Check file permissions!
 /etc/ldap/slapd.conf: line 128: rootdn is always granted unlimited privileges.
 /etc/ldap/slapd.conf: line 145: rootdn is always granted unlimited privileges.
# Correct the ownership of the index files ..
sudo chown openldap:openldap /var/lib/ldap/*
sudo /etc/init.d/slapd start
 Starting OpenLDAP: slapd

16) Add Test Account

sudo smbldap-useradd -a -m -P david

17) Add root and david to the Windows Administrators group and confirm ..

sudo /usr/sbin/smbldap-groupmod -m 'david' 'Administrators'
sudo /usr/sbin/smbldap-groupmod -m 'root' 'Administrators'

18) Add root and david to the Windows Administrators group and confirm .. 
sudo /usr/sbin/smbldap-groupmod -m 'david' 'Administrators'
smbldap-groupshow Administrators

19) Add LDAP Authentication on Clients
sudo apt-get --yes install ldap-auth-client
 LDAP server Uniform Resource Identifier: ldap://xxxx - enter the name of the LDAPServer here
# EXAMPLE: ldap://servername
 Distinguished name of the search base: dc=ubuntudom
 LDAP version to use: 3
 Make local root Database admin: Yes
 Does the LDAP database require login? No
 LDAP account for root: cn=admin,dc=ubuntudom
 LDAP root account password: <enter the LDAP admin password>
sudo auth-client-config -t nss -p lac_ldap
sudo pam-auth-update ldap

19) Test - see if the list of groups and users includes those users and groups in LDAP.

getent group
 : :
 - output will include Windows groups held in LDAP ..
 Domain Admins:*:512:root
 Domain Users:*:513:
 Domain Guests:*:514:
 Domain Computers:*:515:
 Administrators:*:544:root,david
 Account Operators:*:548:
 Print Operators:*:550:
 Backup Operators:*:551:
 Replicators:*:552:
 : :
getent passwd
 - output will include user accounts that only exist in LDAP (eg. david)

20) RESTART YOUR SERVER 

21) Join Windows XP PC to the Domain as ubuntudom\root and your root password

22) DONE!

Hope this guide works for everybody

Regards from Argentina,

Ariel

---

### Post by hambone79 on 2009-06-11
Great tutorial! Can't wait to try it on my home server this evening.

---

### Post by rickymarino on 2009-06-11
Sos Groso, Sabelo! 


Gracias :popcorn:

---

### Post by ghen on 2009-06-12
I'm wiping my 8.04 ldap+samba setup as we speak :o

(it was only testing environment anyway lol)

In your ldif file when you created your dcObject, you defined dc: ubuntudom .. if I want my dn to be dc=test,dc=local how would I define dc in that line? (I'm just going with test for now)

point 1: in your slapd.conf you set a rootpw {SSHA} ; you should note that it should change like the one in init.ldif

point 2: you never actually say to configure smbldap-tools so I just did it after step 13 and used mostly default settings (pretty straightforward)

point 3: you have a copy/paste error on step 18 ;)

note 1: defaultMaxPasswordAge can't be blank (by hitting . during configuration) if you don't want a max password age I guess it would require commenting out that line in /etc/smbldap-tools/smbldap.conf after the config is done... I just made mine 120 days to get past it.



edit: Uh oh, I got to point 19 and failed. everything was fine until that point, but getent group just doesn't respond correctly even after a reboot. I think it has something to do with the ldap-auth-client install, but I don't know how to reconfigure that. I guess I'll try reinstalling it.

well reinstall didn't work, and dpkg-reconfigure ldap-auth-config didn't work, so I had to edit the /etc/ldap.conf file manually. the host line was commented out so I uncommented it and rebooted. Now it works.

2.5 hours from fresh partitioning to joining computers to the domain!

---

### Post by ingcabral on 2009-06-12
Hi Ghen

Of course, the idea of this tutorial is to show how to quickly make it work under 9.04.
That's the reason for the which I said to follow the links for further information. If you read and follow the first one, you will be able to make it work under 8.04, as you need. That tutorial shows how to make it work under that release, and this one, under the new one, with the things that doesn't work under 9.04.

On the second line on slapd.conf, says 
             # Change the rootpw entry with the results from slappaswd (Must match the same you pasted on init.ldif), but I wasn't able to edit the first post, so I hoped that was about to be read :S

Please feel free to contribute and make your own tutorial if you didn't find this useful.

Best regards,

Ariel

> **ghen said:**
> I'm wiping my 8.04 ldap+samba setup as we speak :o

(it was only testing environment anyway lol)

In your ldif file when you created your dcObject, you defined dc: ubuntudom .. if I want my dn to be dc=test,dc=local how would I define dc in that line? (I'm just going with test for now)

point 1: in your slapd.conf you set a rootpw {SSHA} ; you should note that it should change like the one in init.ldif

point 2: you never actually say to configure smbldap-tools so I just did it after step 13 and used mostly default settings (pretty straightforward)

point 3: you have a copy/paste error on step 18 ;)

note 1: defaultMaxPasswordAge can't be blank (by hitting . during configuration) if you don't want a max password age I guess it would require commenting out that line in /etc/smbldap-tools/smbldap.conf after the config is done... I just made mine 120 days to get past it.



edit: Uh oh, I got to point 19 and failed. everything was fine until that point, but getent group just doesn't respond correctly even after a reboot. I think it has something to do with the ldap-auth-client install, but I don't know how to reconfigure that. I guess I'll try reinstalling it.

well reinstall didn't work, and dpkg-reconfigure ldap-auth-config didn't work, so I had to edit the /etc/ldap.conf file manually. the host line was commented out so I uncommented it and rebooted. Now it works.

2.5 hours from fresh partitioning to joining computers to the domain!

---

### Post by harpss1ngh on 2009-06-14
Hi, I'm using this guide to set up a PDC on ubuntu 9.04. I have followed your guide to the T. However, I recieve an error message when following step 4. I get the error message "No such file or directory". I have double checked all the steps up to that point and I'm still stuck on step 4.


Any suggestions?


Great tutorial by the way.

---

### Post by ingcabral on 2009-06-14
Hi!

You have to create the file and just paste the content.
E.g.: # sudo nano /etc/ldap/slapd.conf 
If the file doesn't exist, it will be saved when you close the editor (Ctrl-w)

If the problem persists, please post the results of the console and we'll try to figure it out!

Regards

> **harpss1ngh said:**
> Hi, I'm using this guide to set up a PDC on ubuntu 9.04. I have followed your guide to the T. However, I recieve an error message when following step 4. I get the error message "No such file or directory". I have double checked all the steps up to that point and I'm still stuck on step 4.


Any suggestions?


Great tutorial by the way.

---

### Post by ghen on 2009-06-15
> **ingcabral said:**
> 

Please feel free to contribute and make your own tutorial if you didn't find this useful.


No disrespect, this is a very easy to follow yet powerful guide. I wanted to try 9.04 as a samba/ldap server so thats why I wiped the other install :) I definitely found it useful and will probably use it as the main guide when my setup goes production. Thanks.

---

### Post by faustcoder on 2009-06-25
Wow, this is the simplest Samba PDC how-to I have ever seen... Thank you for the work and I look forward to testing this out. Hopefully I can add some info on roaming profiles, etc.

---

### Post by senor_smile on 2009-06-25
I am trying to implement your instructions.  I have created a brand new server install (9.04 64 bit). 

I followed the directions exactly, and am stuck at step 13:

> sudo smbldap-populate
Unable to open /etc/opt/IDEALX/smbldap-tools/smbldap.conf for reading !
Compilation failed in require at /usr/sbin/smbldap-populate line 31.
BEGIN failed--compilation aborted at /usr/sbin/smbldap-populate line 31.

Everything before this went as expected.

---

### Post by ingcabral on 2009-06-26
Hi!

I think the problem is caused because ldap tool were not configured.

So, the fix (I think) will be:

Run from the terminal
> dpkg-reconfigure slapd

And answer as follows:

No
Dns local name=ubuntudom
Name of the organization: ubuntudom
Admin pass: yourpass
OK
BDB
No
Yes
No

And that will get you the correct configuration under /etc/smbldap-tools/

Please let me know how did it go, we'll fix it!!

Regards,

> **senor_smile said:**
> I am trying to implement your instructions.  I have created a brand new server install (9.04 64 bit). 

I followed the directions exactly, and am stuck at step 13:



Everything before this went as expected.

---

### Post by senor_smile on 2009-06-27
Before I was able to read your answer, I tried all over.  This time, I installed 32 bit server (9.04) and opened the other pages your referenced to compare to your steps.  I did run the dpkg-reconfigure slapd command, and actually got it working.  I authenticated my first xp machine to a non windows 2003 server!  Thanks a million for the simple tutorial.  

I know very little about shell scripts, but I wonder how much of this could be put into a shell script to automate the process across several servers.

---

### Post by senor_smile on 2009-06-28
A million thanks to the op for this tutorial.  For those following it, I have made a few tweaks where I saw fit and put all of this into a shell script.  

I call it ldapinstall.sh. Make sure to
```
sudo chmod +x ldapinstall.sh
```
before running it.  I have tested it on ubuntu server 32-bit 8.04 and 9.04.  It has worked flawlessly thus far.  Let me know if anyone has questions/comments on it.  

```
#!/bin/bash         

echo "Must enter: sudo su before running this script"
echo "continue?:"
read continue
if [ $continue != "y" ]
	then exit 0
fi
clear
echo "Enter desired domain name: "
read DomainName
echo "Enter desired server(netbios) name: "
read servername

#1 ------------------------------
echo "1)install openldap"
#echo "Press any key to continue"
#read nullvar

apt-get --yes install slapd ldap-utils db4.2-util
rm -r /etc/ldap/slapd.d/
mv /etc/default/slapd /etc/default/slapd.bak
echo "
SLAPD_CONF=/etc/ldap/slapd.conf
SLAPD_USER=\"openldap\"
SLAPD_GROUP=\"openldap\"
SLAPD_PIDFILE=
SLAPD_SERVICES=\"ldap:/// ldapi:///\"
SLAPD_SENTINEL_FILE=/etc/ldap/noslapd
SLAPD_OPTIONS=\"\"
" >> /etc/default/slapd


#2 --------------------------------
echo "2) Install Samba documentation containing the Samba schema. Extract samba.schema and copy to the required system area for OpenLDAP."
#echo "Press any key to continue"
#read nullvar

apt-get --yes install samba-doc &&  gunzip /usr/share/doc/samba-doc/examples/LDAP/samba.schema.gz && cp -v /usr/share/doc/samba-doc/examples/LDAP/samba.schema /etc/ldap/schema


#3 ---------------------------------
echo "3) Decide on an LDAP admin password and generate a SSHA hash key for it."
#echo "Press any key to continue"
#read nullvar

export slappass=`slappasswd`




echo "4) Create an init.ldif file. Name the 4 OUs Users, Groups, Computers and Idmap for use with smbldap-tools. "
#echo "Press any key to continue"
#read nullvar

 
echo "
dn: dc=$DomainName
objectClass: dcObject
objectClass: organizationalUnit
dc: $DomainName
ou: $DomainName

dn: cn=admin,dc=$DomainName
objectClass: simpleSecurityObject
objectClass: organizationalRole
cn: admin
description: LDAP administrator
userPassword: $slappass 


dn: ou=Users,dc=$DomainName
objectClass: organizationalUnit
ou: Users

dn: ou=Groups,dc=$DomainName
objectClass: organizationalUnit
ou: Groups

dn: ou=Computers,dc=$DomainName
objectClass: organizationalUnit
ou: Computers

dn: ou=Idmap,dc=$DomainName
objectClass: organizationalUnit
ou: Idmap
">> /etc/ldap/init.ldif

mv /etc/ldap/slapd.conf /etc/ldap/slapd.conf.bak
echo "
# /etc/ldap/slapd.conf
# This is the main slapd configuration file. See slapd.conf(5) for more
# info on the configuration options.

#######################################################################
# Global Directives:

# Features to permit
#allow bind_v2

# Schema and objectClass definitions
include         /etc/ldap/schema/core.schema
include         /etc/ldap/schema/cosine.schema
include         /etc/ldap/schema/nis.schema
include         /etc/ldap/schema/inetorgperson.schema
include         /etc/ldap/schema/samba.schema
include         /etc/ldap/schema/misc.schema

# Where the pid file is put. The init.d script
# will not stop the server if you change this.
pidfile         /var/run/slapd/slapd.pid

# List of arguments that were passed to the server
argsfile        /var/run/slapd/slapd.args

# Read slapd.conf(5) for possible values
loglevel        0

# Where the dynamically loaded modules are stored
modulepath      /usr/lib/ldap
moduleload      back_bdb

# The maximum number of entries that is returned for a search operation
sizelimit 500

# The tool-threads parameter sets the actual amount of cpu's that is used
# for indexing.
tool-threads 1

#######################################################################
# Specific Backend Directives for bdb:
# Backend specific directives apply to this backend until another
# 'backend' directive occurs
backend         bdb
#checkpoint 512 30

#######################################################################
# Specific Backend Directives for 'other':
# Backend specific directives apply to this backend until another
# 'backend' directive occurs
#backend                <other>

#######################################################################
# Specific Directives for database #1, of type bdb:
# Database specific directives apply to this databasse until another
# 'database' directive occurs
database        bdb

# The base of your directory in database #1
suffix          \"dc=$DomainName\"

# rootdn directive for specifying a superuser on the database. This is needed
# for syncrepl.
rootdn          \"cn=admin,dc=$DomainName\"
rootpw $slappass

# Where the database file are physically stored for database #1
directory       \"/var/lib/ldap\"

# For the Debian package we use 2MB as default but be sure to update this
# value if you have plenty of RAM
dbconfig set_cachesize 0 2097152 0

# Sven Hartge reported that he had to set this value incredibly high
# to get slapd running at all. See [http://bugs.debian.org/303057](http://bugs.debian.org/303057)
# for more information.

# Number of objects that can be locked at the same time.
dbconfig set_lk_max_objects 1500
# Number of locks (both requested and granted)
dbconfig set_lk_max_locks 1500
# Number of lockers
dbconfig set_lk_max_lockers 1500

# Indexing options for database #1
#index           objectClass eq, pres
index ou,cn,sn,mail,givenname           eq,pres,sub
index uidNumber,gidNumber,memberUid     eq,pres
index loginShell                        eq,pres
index uniqueMember                      eq,pres
index uid                               pres,sub,eq
index displayName                       pres,sub,eq
index sambaSID                          eq
index sambaPrimaryGroupSID              eq
index sambaDomainName                   eq
index default                           sub
#index   uid         pres,eq,sub

# Save the time that the entry gets modified, for database #1
lastmod         on

# Where to store the replica logs for database #1
# replogfile    /var/lib/ldap/replog

# The userPassword by default can be changed
# by the entry owning it if they are authenticated.
# Others should not be able to see it, except the
# admin entry below
# These access lines apply to database #1 only
access to attrs=userPassword,shadowLastChange
        by dn=\"cn=admin,dc=$DomainName\" write
        by anonymous auth
        by self write
        by * none

# Ensure read access to the base for things like
# supportedSASLMechanisms.  Without this you may
# have problems with SASL not knowing what
# mechanisms are available and the like.
# Note that this is covered by the 'access to *'
# ACL below too but if you change that as people
# are wont to do you'll still need this if you
# want SASL (and possible other things) to work
# happily.
access to dn.base=\"\" by * read

# The admin dn has full write access, everyone else
# can read everything.
access to *
        by dn=\"cn=admin,dc=$DomainName\" write
        by * read

# For Netscape Roaming support, each user gets a roaming
# profile for which they have write access to
#access to dn=\".*,ou=Roaming,o=morsnet\"
#        by dn=\"cn=admin,dc=example,dc=ch\" write
#        by dnattr=owner write

#######################################################################
# Specific Directives for database #2, of type 'other' (can be bdb too):
# Database specific directives apply to this databasse until another
# 'database' directive occurs
#database        <other>

# The base of your directory for database #2
#suffix         \"dc=debian,dc=org\"
">> /etc/ldap/slapd.conf



#5
echo "5) Initialise OpenLDAP database .. "
#echo "Press any key to continue"
#read nullvar

/etc/init.d/slapd stop
rm -rf /var/lib/ldap/*
cd /etc/ldap
slapadd -v -l init.ldif
chown -R openldap:openldap /var/lib/ldap
/etc/init.d/slapd start
ldapsearch -xLLL -b "dc=$DomainName"


#6
echo "Install and Configure Samba"
#echo "Press any key to continue"
#read nullvar

apt-get -y install libtalloc1 smbclient samba libpam-smbpass


#7
echo "7) Create Samba folders that have not been automatically created .."
#echo "Press any key to continue"
#read nullvar

mkdir -v /var/lib/samba/profiles
chmod 777 /var/lib/samba/profiles
mkdir -v -p /var/lib/samba/netlogon

#8
echo "8) Edit /etc/samba/smb.conf - so it looks EXACTLY like this but replacing your domain name"
#echo "Press any key to continue"
#read nullvar

mv /etc/samba/smb.conf /etc/samba/smb.conf.bak
echo "
[global]
        # Domain name ..
        workgroup = $DomainName
        # Server name - as seen by Windows PCs ..
        netbios name = $servername
        # Be a PDC ..
        domain logons = Yes
        domain master = Yes
        # Be a WINS server ..
        wins support = true

        obey pam restrictions = Yes
        dns proxy = No
        os level = 35
        log file = /var/log/samba/log.%m
        max log size = 1000
        syslog = 0
        panic action = /usr/share/samba/panic-action %d
        pam password change = Yes

        # Allows users on WinXP PCs to change their password when they press Ctrl-Alt-Del
        unix password sync = no
        ldap passwd sync = yes

        # Printing from PCs will go via CUPS ..
        load printers = yes
        printing = cups
        printcap name = cups

        # Use LDAP for Samba user accounts and groups ..
        passdb backend = ldapsam:ldap://localhost

        # This must match init.ldif ..
        ldap suffix = dc=$DomainName
        # The password for cn=admin MUST be stored in /etc/samba/secrets.tdb
        # This is done by running 'sudo smbpasswd -w'.
        ldap admin dn = cn=admin,dc=$DomainName

        # 4 OUs that Samba uses when creating user accounts, computer accounts, etc.
        # (Because we are using smbldap-tools, call them 'Users', 'Computers', etc.)
        ldap machine suffix = ou=Computers
        ldap user suffix = ou=Users
        ldap group suffix = ou=Groups
        ldap idmap suffix = ou=Idmap
        # Samba and LDAP server are on the same server in this example.
        ldap ssl = no

        # Scripts for Samba to use if it creates users, groups, etc.
        add user script = /usr/sbin/smbldap-useradd -m '%u'
        delete user script = /usr/sbin/smbldap-userdel %u
        add group script = /usr/sbin/smbldap-groupadd -p '%g'
        delete group script = /usr/sbin/smbldap-groupdel '%g'
        add user to group script = /usr/sbin/smbldap-groupmod -m '%u' '%g'
        delete user from group script = /usr/sbin/smbldap-groupmod -x '%u' '%g'
        set primary group script = /usr/sbin/smbldap-usermod -g '%g' '%u'

        # Script that Samba users when a PC joins the domain ..
        # (when changing 'Computer Properties' on the PC)
        add machine script = /usr/sbin/smbldap-useradd -w '%u'

        # Values used when a new user is created ..
        # (Note: '%L' does not work properly with smbldap-tools 0.9.4-1)
    logon drive =
        logon home =
        logon path =
        logon script =


        # This is required for Windows XP client ..
        server signing = auto
        server schannel = Auto

[homes]
        comment = Home Directories
        valid users = %S
        read only = No
        browseable = No

[netlogon]
        comment = Network Logon Service
        path = /var/lib/samba/netlogon
        admin users = root
        guest ok = Yes
        browseable = No

[Profiles]
        comment = Roaming Profile Share
        # would probably change this to elsewhere in a production system ..
        path = /var/lib/samba/profiles
        read only = No
        profile acls = Yes
        browsable = No

[printers]
        comment = All Printers
        path = /var/spool/samba
        use client driver = Yes
        create mask = 0600
        guest ok = Yes
        printable = Yes
        browseable = No
        public = yes
        writable = yes
        admin users = root
        write list = root

[print$]
        comment = Printer Drivers Share
        path = /var/lib/samba/printers
        write list = root
        create mask = 0664
        directory mask = 0775
        admin users = root
">> /etc/samba/smb.conf


#9
echo "9) Write password for the LDAP admin account (eg. cn=admin,dc=ubuntudom) into /etc/samba/secrets.tdb"
#echo "Press any key to continue"
#read nullvar

smbpasswd -W

#10
echo "10) Restart Samba .."
#echo "Press any key to continue"
#read nullvar

/etc/init.d/samba restart

#11
echo "11) Use the SMB client to check that the Samba server is responding correctly." 
#echo "Press any key to continue"
#read nullvar

smbclient -L localhost -U anonymous%


#12
echo "12) Install smbldap-tools and extract the configure.pl script."
#echo "Press any key to continue"
#read nullvar

apt-get -y install smbldap-tools
gunzip /usr/share/doc/smbldap-tools/configure.pl.gz
chmod +x /usr/share/doc/smbldap-tools/configure.pl


#13
echo "13) Before configuring smbldap-tools, check that Samba is running and the Windows domain SID can be retrieved."
#echo "Press any key to continue"
#read nullvar

ps -e | grep -i "smb"
net getlocalsid


#14
echo "14) Populate the LDAP database with essential Samba entries. This includes the creation of standard groups, such as Administrators and Domain Users.

Accept defaults to the following questions except the 2 prompts for passwords, enter the LDAP admin password. 
"
#echo "Press any key to continue"
#read blankvar

/usr/share/doc/smbldap-tools/configure.pl
# either run this or 



#14)
echo "14) Populate the LDAP database with essential Samba entries. This includes the creation of standard groups, such as Administrators and Domain Users."
#echo "Press any key to continue"
#read blankvar

smbldap-populate

#-------
#dpkg-reconfigure slapd  moved from step 14
#-------

#15)
echo "15) Following this, stop the LDAP server, run slapindex, and restart the LDAP server."
#echo "Press any key to continue"
#read blankvar

/etc/init.d/slapd stop
slapindex
chown openldap:openldap /var/lib/ldap/* 
/etc/init.d/slapd start

#16)
echo "16) Add Test Account"
#echo "Press any key to continue"
#read blankvar

echo "Adding user david"
smbldap-useradd -a -m -P david
#password = david

#17) add test account
echo "add david and root as Administrators"
sudo /usr/sbin/smbldap-groupmod -m 'david' 'Administrators'
sudo /usr/sbin/smbldap-groupmod -m 'root' 'Administrators'

#18) prove test account
echo "prove test account"
smbldap-groupshow Administrators


#19
echo "19) add ldap auth on clients
	Answer with the following(write down if necessary):

	#ldap://$servername
	#dc=$DomainName
	#3
	#yes
	#no
	#cn=admin,dc=$DomainName
	#<enter the LDAP admin password>

Press Enter to continue.
"
read nullvar

apt-get -y install ldap-auth-client

	
auth-client-config -t nss -p lac_ldap
pam-auth-update ldap

#20)
getent group

#RESTART
echo "press any key to restart now"
read restartvar
shutdown now -r
```

---

### Post by geek-n-out on 2009-07-03
Hey guys I know this is a little bit of an old post, but I have a question....
 
I got quick fingers and messed up the ldap-auth-client install... Is there anyway to remove it and force it to let me reconfigure?  I have removed, but everytime I reinstall it just takes the old settings.  I'm assuming there is a file somewhere I can delete.  ):P

---

### Post by senor_smile on 2009-07-04
I am still new to openldap, and am trying to figure out the details of its functionality.  try the following: 

```
sudo dpkg-reconfigure ldap-auth-config
```

If that doesn't work, try editing the file /etc/ldap.conf manually.  Let us know if you're able to get it working.

---

### Post by glarance on 2009-07-04
Hi, I'm using this tutorial to set up a PDC on ubuntu 9.04.
I have followed your guide to the step 19 but the command
"getent group" give me only the common content of the /etc/group file 
and the command "getent passwd" give me only the common content of the /etc/passwd
I can't see the list of groups and users in LDAP.

May be it is the reason why when trying to add an XP machine to the domain I have an error saying : The following error happen when trying to join the domain "david" : logon failure : unknown username or bad password

Any suggestions?

thanks in advance, very good tutorial by the way.

---

### Post by glarance on 2009-07-04
sorry I moved too quickly through the threads I think [ghen]("http://www.uluga.ubuntuforums.org/member.php?u=689054")
gave the answer

---

### Post by ingcabral on 2009-07-04
Hi!!

Actually, you can, by running

> sudo apt-get autoremoveldap-auth-client 

That will wipe every .conf file from the installation. If you still want to download everything again (Since the debs will stil be there, on the cache) after that, run


> sudo apt-get clean

Hope it worked

Regards,

Ariel




> **geek-n-out said:**
> Hey guys I know this is a little bit of an old post, but I have a question....
 
I got quick fingers and messed up the ldap-auth-client install... Is there anyway to remove it and force it to let me reconfigure?  I have removed, but everytime I reinstall it just takes the old settings.  I'm assuming there is a file somewhere I can delete.  ):P

---

### Post by geek-n-out on 2009-07-05
Hey thanks for the reply... Good information to know for the future (not an ubuntu guru, but getting there).
 
So I reinstalled, got it all set up correctly, but now i'm getting a winlogon.exe error when trying to log in with my xpsp3 workstation.  Error code is 0xc000049, couldn't find much on google, but thought one of you all might have ran into it.
 
Thanks,
 
Jon

---

### Post by geek-n-out on 2009-07-12
Does anyone have a clue what that winlogon error might be?  I'm assuming it's just a simple compatibility issue between xpsp3 and Ubuntu 9.04, but I'm not finding much on it.  Any thoughts>

---

### Post by locovaca on 2009-07-13
Nice howto.  Not to rain on your parade, however, wiping out /etc/ldap/slapd.d and replacing it with slapd.conf is **not** the way to be setting things up.  slapd.conf is going away- not possibly, **is** going away.  Any new configurations should be done using /etc/ldap/slapd.d as that will be the only thing supported in the near future.  Unless, of course, you like setting up PDCs frequently :)

For more info, see these:

[https://wiki.ubuntu.com/OpenLdapCnConfigMigration](https://wiki.ubuntu.com/OpenLdapCnConfigMigration)
[http://www.openldap.org/doc/admin24/slapdconf2.html](http://www.openldap.org/doc/admin24/slapdconf2.html)
[http://www.zytrax.com/books/ldap/ch6/slapd-config.html](http://www.zytrax.com/books/ldap/ch6/slapd-config.html)
[https://help.ubuntu.com/8.10/serverguide/C/openldap-server.html](https://help.ubuntu.com/8.10/serverguide/C/openldap-server.html)

You're free to do what you want, but I'm working through upgrading my slapd.conf to slapd.d right now so that I don't get burned on my production server in the next upgrade that removes slapd.conf functionality.

---

### Post by Ketheres_Magnus on 2009-08-09
> **senor_smile said:**
> A million thanks to the op for this tutorial.  For those following it, I have made a few tweaks where I saw fit and put all of this into a shell script. ::edit::  


Wow! Senor_smile, you really made it too easy. Got the PDC up and running in mere moments.

/me deep bow to you.

Many thanks to you...

/me deep bow to locovaca

...and especially to locovaca for such an awesome post. Cheers!

---

### Post by snaidell on 2009-08-20
Hi Ingcabral, thank you for this HOW TO. It's a very easy step-by-step guide.
I had some problems during the configuration.

first in step 14 I had the same problem discribed by senor_smile, to solve that I had to create the two folowing files manually:

[I]/etc/smbldap-tools/smbldap_bind.conf

[/I]```
slaveDN="cn=admin,dc=ubuntudom"
slavePw="password"
masterDN="cn=admin,dc=ubuntudom"
masterPw="password"
```*/etc/smbldap-tools/smbldap.conf*

```
SID="your SID here"
sambaDomain="ubuntudom"
slaveLDAP="127.0.0.1"
slavePort="389"
masterLDAP="127.0.0.1"
masterPort="389"
ldapTLS="0"
verify=""
cafile=""
clientcert=""
clientkey=""
suffix="dc=ubuntudom"
usersdn="ou=Users,${suffix}"
groupsdn="ou=Groups,${suffix}"
computersdn="ou=Computers,${suffix}"
idmapdn="ou=Idmap,${suffix}"
sambaUnixIdPooldn="sambaDomainName=ubuntudom,${suffix}"
scope="sub"
hash_encrypt="SSHA"
crypt_salt_format=""
userLoginShell="/bin/bash"
userHome="/home/%U"
userHomeDirectoryMode="700"
userGecos="System User"
defaultUserGid="513"
defaultComputerGid="515"
skeletonDir="/etc/skel"
defaultMaxPasswordAge=""
userSmbHome=""
userProfile=""
userHomeDrive=""
with_smbpasswd="0"
smbpasswd="/usr/bin/smbpasswd"
with_slappasswd="0"
slappasswd="/usr/sbin/slappasswd" 
```

And the oder problem was in step 19 I had the same problem as ghen, but solved it with the solution gave by him.

Now I have it working just fine, but I wanna know how to set a kerberos authentication in this solution and how to set the machines that can joing the network (because the way it is any machine can joing with the right loging and password).

Thank you once more.

---

### Post by demolition on 2009-09-09
It's a great script, but I am not managing to make users enter the system, the User root function more other users registered you could not help me.


> **senor_smile said:**
> A million thanks to the op for this tutorial.  For those following it, I have made a few tweaks where I saw fit and put all of this into a shell script.  

I call it ldapinstall.sh. Make sure to
```
sudo chmod +x ldapinstall.sh
```before running it.  I have tested it on ubuntu server 32-bit 8.04 and 9.04.  It has worked flawlessly thus far.  Let me know if anyone has questions/comments on it.  

```
#!/bin/bash         

echo "Must enter: sudo su before running this script"
echo "continue?:"
read continue
if [ $continue != "y" ]
    then exit 0
fi
clear
echo "Enter desired domain name: "
read DomainName
echo "Enter desired server(netbios) name: "
read servername

#1 ------------------------------
echo "1)install openldap"
#echo "Press any key to continue"
#read nullvar

apt-get --yes install slapd ldap-utils db4.2-util
rm -r /etc/ldap/slapd.d/
mv /etc/default/slapd /etc/default/slapd.bak
echo "
SLAPD_CONF=/etc/ldap/slapd.conf
SLAPD_USER=\"openldap\"
SLAPD_GROUP=\"openldap\"
SLAPD_PIDFILE=
SLAPD_SERVICES=\"ldap:/// ldapi:///\"
SLAPD_SENTINEL_FILE=/etc/ldap/noslapd
SLAPD_OPTIONS=\"\"
" >> /etc/default/slapd


#2 --------------------------------
echo "2) Install Samba documentation containing the Samba schema. Extract samba.schema and copy to the required system area for OpenLDAP."
#echo "Press any key to continue"
#read nullvar

apt-get --yes install samba-doc &&  gunzip /usr/share/doc/samba-doc/examples/LDAP/samba.schema.gz && cp -v /usr/share/doc/samba-doc/examples/LDAP/samba.schema /etc/ldap/schema


#3 ---------------------------------
echo "3) Decide on an LDAP admin password and generate a SSHA hash key for it."
#echo "Press any key to continue"
#read nullvar

export slappass=`slappasswd`




echo "4) Create an init.ldif file. Name the 4 OUs Users, Groups, Computers and Idmap for use with smbldap-tools. "
#echo "Press any key to continue"
#read nullvar

 
echo "
dn: dc=$DomainName
objectClass: dcObject
objectClass: organizationalUnit
dc: $DomainName
ou: $DomainName

dn: cn=admin,dc=$DomainName
objectClass: simpleSecurityObject
objectClass: organizationalRole
cn: admin
description: LDAP administrator
userPassword: $slappass 


dn: ou=Users,dc=$DomainName
objectClass: organizationalUnit
ou: Users

dn: ou=Groups,dc=$DomainName
objectClass: organizationalUnit
ou: Groups

dn: ou=Computers,dc=$DomainName
objectClass: organizationalUnit
ou: Computers

dn: ou=Idmap,dc=$DomainName
objectClass: organizationalUnit
ou: Idmap
">> /etc/ldap/init.ldif

mv /etc/ldap/slapd.conf /etc/ldap/slapd.conf.bak
echo "
# /etc/ldap/slapd.conf
# This is the main slapd configuration file. See slapd.conf(5) for more
# info on the configuration options.

#######################################################################
# Global Directives:

# Features to permit
#allow bind_v2

# Schema and objectClass definitions
include         /etc/ldap/schema/core.schema
include         /etc/ldap/schema/cosine.schema
include         /etc/ldap/schema/nis.schema
include         /etc/ldap/schema/inetorgperson.schema
include         /etc/ldap/schema/samba.schema
include         /etc/ldap/schema/misc.schema

# Where the pid file is put. The init.d script
# will not stop the server if you change this.
pidfile         /var/run/slapd/slapd.pid

# List of arguments that were passed to the server
argsfile        /var/run/slapd/slapd.args

# Read slapd.conf(5) for possible values
loglevel        0

# Where the dynamically loaded modules are stored
modulepath      /usr/lib/ldap
moduleload      back_bdb

# The maximum number of entries that is returned for a search operation
sizelimit 500

# The tool-threads parameter sets the actual amount of cpu's that is used
# for indexing.
tool-threads 1

#######################################################################
# Specific Backend Directives for bdb:
# Backend specific directives apply to this backend until another
# 'backend' directive occurs
backend         bdb
#checkpoint 512 30

#######################################################################
# Specific Backend Directives for 'other':
# Backend specific directives apply to this backend until another
# 'backend' directive occurs
#backend                <other>

#######################################################################
# Specific Directives for database #1, of type bdb:
# Database specific directives apply to this databasse until another
# 'database' directive occurs
database        bdb

# The base of your directory in database #1
suffix          \"dc=$DomainName\"

# rootdn directive for specifying a superuser on the database. This is needed
# for syncrepl.
rootdn          \"cn=admin,dc=$DomainName\"
rootpw $slappass

# Where the database file are physically stored for database #1
directory       \"/var/lib/ldap\"

# For the Debian package we use 2MB as default but be sure to update this
# value if you have plenty of RAM
dbconfig set_cachesize 0 2097152 0

# Sven Hartge reported that he had to set this value incredibly high
# to get slapd running at all. See [http://bugs.debian.org/303057](http://bugs.debian.org/303057)
# for more information.

# Number of objects that can be locked at the same time.
dbconfig set_lk_max_objects 1500
# Number of locks (both requested and granted)
dbconfig set_lk_max_locks 1500
# Number of lockers
dbconfig set_lk_max_lockers 1500

# Indexing options for database #1
#index           objectClass eq, pres
index ou,cn,sn,mail,givenname           eq,pres,sub
index uidNumber,gidNumber,memberUid     eq,pres
index loginShell                        eq,pres
index uniqueMember                      eq,pres
index uid                               pres,sub,eq
index displayName                       pres,sub,eq
index sambaSID                          eq
index sambaPrimaryGroupSID              eq
index sambaDomainName                   eq
index default                           sub
#index   uid         pres,eq,sub

# Save the time that the entry gets modified, for database #1
lastmod         on

# Where to store the replica logs for database #1
# replogfile    /var/lib/ldap/replog

# The userPassword by default can be changed
# by the entry owning it if they are authenticated.
# Others should not be able to see it, except the
# admin entry below
# These access lines apply to database #1 only
access to attrs=userPassword,shadowLastChange
        by dn=\"cn=admin,dc=$DomainName\" write
        by anonymous auth
        by self write
        by * none

# Ensure read access to the base for things like
# supportedSASLMechanisms.  Without this you may
# have problems with SASL not knowing what
# mechanisms are available and the like.
# Note that this is covered by the 'access to *'
# ACL below too but if you change that as people
# are wont to do you'll still need this if you
# want SASL (and possible other things) to work
# happily.
access to dn.base=\"\" by * read

# The admin dn has full write access, everyone else
# can read everything.
access to *
        by dn=\"cn=admin,dc=$DomainName\" write
        by * read

# For Netscape Roaming support, each user gets a roaming
# profile for which they have write access to
#access to dn=\".*,ou=Roaming,o=morsnet\"
#        by dn=\"cn=admin,dc=example,dc=ch\" write
#        by dnattr=owner write

#######################################################################
# Specific Directives for database #2, of type 'other' (can be bdb too):
# Database specific directives apply to this databasse until another
# 'database' directive occurs
#database        <other>

# The base of your directory for database #2
#suffix         \"dc=debian,dc=org\"
">> /etc/ldap/slapd.conf



#5
echo "5) Initialise OpenLDAP database .. "
#echo "Press any key to continue"
#read nullvar

/etc/init.d/slapd stop
rm -rf /var/lib/ldap/*
cd /etc/ldap
slapadd -v -l init.ldif
chown -R openldap:openldap /var/lib/ldap
/etc/init.d/slapd start
ldapsearch -xLLL -b "dc=$DomainName"


#6
echo "Install and Configure Samba"
#echo "Press any key to continue"
#read nullvar

apt-get -y install libtalloc1 smbclient samba libpam-smbpass


#7
echo "7) Create Samba folders that have not been automatically created .."
#echo "Press any key to continue"
#read nullvar

mkdir -v /var/lib/samba/profiles
chmod 777 /var/lib/samba/profiles
mkdir -v -p /var/lib/samba/netlogon

#8
echo "8) Edit /etc/samba/smb.conf - so it looks EXACTLY like this but replacing your domain name"
#echo "Press any key to continue"
#read nullvar

mv /etc/samba/smb.conf /etc/samba/smb.conf.bak
echo "
[global]
        # Domain name ..
        workgroup = $DomainName
        # Server name - as seen by Windows PCs ..
        netbios name = $servername
        # Be a PDC ..
        domain logons = Yes
        domain master = Yes
        # Be a WINS server ..
        wins support = true

        obey pam restrictions = Yes
        dns proxy = No
        os level = 35
        log file = /var/log/samba/log.%m
        max log size = 1000
        syslog = 0
        panic action = /usr/share/samba/panic-action %d
        pam password change = Yes

        # Allows users on WinXP PCs to change their password when they press Ctrl-Alt-Del
        unix password sync = no
        ldap passwd sync = yes

        # Printing from PCs will go via CUPS ..
        load printers = yes
        printing = cups
        printcap name = cups

        # Use LDAP for Samba user accounts and groups ..
        passdb backend = ldapsam:ldap://localhost

        # This must match init.ldif ..
        ldap suffix = dc=$DomainName
        # The password for cn=admin MUST be stored in /etc/samba/secrets.tdb
        # This is done by running 'sudo smbpasswd -w'.
        ldap admin dn = cn=admin,dc=$DomainName

        # 4 OUs that Samba uses when creating user accounts, computer accounts, etc.
        # (Because we are using smbldap-tools, call them 'Users', 'Computers', etc.)
        ldap machine suffix = ou=Computers
        ldap user suffix = ou=Users
        ldap group suffix = ou=Groups
        ldap idmap suffix = ou=Idmap
        # Samba and LDAP server are on the same server in this example.
        ldap ssl = no

        # Scripts for Samba to use if it creates users, groups, etc.
        add user script = /usr/sbin/smbldap-useradd -m '%u'
        delete user script = /usr/sbin/smbldap-userdel %u
        add group script = /usr/sbin/smbldap-groupadd -p '%g'
        delete group script = /usr/sbin/smbldap-groupdel '%g'
        add user to group script = /usr/sbin/smbldap-groupmod -m '%u' '%g'
        delete user from group script = /usr/sbin/smbldap-groupmod -x '%u' '%g'
        set primary group script = /usr/sbin/smbldap-usermod -g '%g' '%u'

        # Script that Samba users when a PC joins the domain ..
        # (when changing 'Computer Properties' on the PC)
        add machine script = /usr/sbin/smbldap-useradd -w '%u'

        # Values used when a new user is created ..
        # (Note: '%L' does not work properly with smbldap-tools 0.9.4-1)
    logon drive =
        logon home =
        logon path =
        logon script =


        # This is required for Windows XP client ..
        server signing = auto
        server schannel = Auto

[homes]
        comment = Home Directories
        valid users = %S
        read only = No
        browseable = No

[netlogon]
        comment = Network Logon Service
        path = /var/lib/samba/netlogon
        admin users = root
        guest ok = Yes
        browseable = No

[Profiles]
        comment = Roaming Profile Share
        # would probably change this to elsewhere in a production system ..
        path = /var/lib/samba/profiles
        read only = No
        profile acls = Yes
        browsable = No

[printers]
        comment = All Printers
        path = /var/spool/samba
        use client driver = Yes
        create mask = 0600
        guest ok = Yes
        printable = Yes
        browseable = No
        public = yes
        writable = yes
        admin users = root
        write list = root

[print$]
        comment = Printer Drivers Share
        path = /var/lib/samba/printers
        write list = root
        create mask = 0664
        directory mask = 0775
        admin users = root
">> /etc/samba/smb.conf


#9
echo "9) Write password for the LDAP admin account (eg. cn=admin,dc=ubuntudom) into /etc/samba/secrets.tdb"
#echo "Press any key to continue"
#read nullvar

smbpasswd -W

#10
echo "10) Restart Samba .."
#echo "Press any key to continue"
#read nullvar

/etc/init.d/samba restart

#11
echo "11) Use the SMB client to check that the Samba server is responding correctly." 
#echo "Press any key to continue"
#read nullvar

smbclient -L localhost -U anonymous%


#12
echo "12) Install smbldap-tools and extract the configure.pl script."
#echo "Press any key to continue"
#read nullvar

apt-get -y install smbldap-tools
gunzip /usr/share/doc/smbldap-tools/configure.pl.gz
chmod +x /usr/share/doc/smbldap-tools/configure.pl


#13
echo "13) Before configuring smbldap-tools, check that Samba is running and the Windows domain SID can be retrieved."
#echo "Press any key to continue"
#read nullvar

ps -e | grep -i "smb"
net getlocalsid


#14
echo "14) Populate the LDAP database with essential Samba entries. This includes the creation of standard groups, such as Administrators and Domain Users.

Accept defaults to the following questions except the 2 prompts for passwords, enter the LDAP admin password. 
"
#echo "Press any key to continue"
#read blankvar

/usr/share/doc/smbldap-tools/configure.pl
# either run this or 



#14)
echo "14) Populate the LDAP database with essential Samba entries. This includes the creation of standard groups, such as Administrators and Domain Users."
#echo "Press any key to continue"
#read blankvar

smbldap-populate

#-------
#dpkg-reconfigure slapd  moved from step 14
#-------

#15)
echo "15) Following this, stop the LDAP server, run slapindex, and restart the LDAP server."
#echo "Press any key to continue"
#read blankvar

/etc/init.d/slapd stop
slapindex
chown openldap:openldap /var/lib/ldap/* 
/etc/init.d/slapd start

#16)
echo "16) Add Test Account"
#echo "Press any key to continue"
#read blankvar

echo "Adding user david"
smbldap-useradd -a -m -P david
#password = david

#17) add test account
echo "add david and root as Administrators"
sudo /usr/sbin/smbldap-groupmod -m 'david' 'Administrators'
sudo /usr/sbin/smbldap-groupmod -m 'root' 'Administrators'

#18) prove test account
echo "prove test account"
smbldap-groupshow Administrators


#19
echo "19) add ldap auth on clients
    Answer with the following(write down if necessary):

    #ldap://$servername
    #dc=$DomainName
    #3
    #yes
    #no
    #cn=admin,dc=$DomainName
    #<enter the LDAP admin password>

Press Enter to continue.
"
read nullvar

apt-get -y install ldap-auth-client

    
auth-client-config -t nss -p lac_ldap
pam-auth-update ldap

#20)
getent group

#RESTART
echo "press any key to restart now"
read restartvar
shutdown now -r
```

---

### Post by cinche on 2009-09-17
Thanks for this superb guide, I have been trying to get this working for days now with limited success, I think I have managed to replicate what this guide does myself but using the new slapd.d configuration, but my windows clients complain they cannot see the domain.

Can I ask in collaboration to this guide what settings you have for /etc/hosts, /etc/hostname and for dhcp, I am currently stuck with the PDC being a DHCP client along with all of the windows clients.  My intention was to update the DHCP server to point the nameserver at the PDC, but I don't know if this is feasible unless I can give the PDC a static IP. 

Any assistance with the network setup side or a pointer to another guide/tutorial would be appreciated, as I am still confused with the basics of what is the difference between ubuntudom.local and ubuntudom and why would I select one over the other.

Cheers/
Cinche

---

### Post by AlexanderDGreat on 2009-09-21
Hi, I may have a OFF topic, but I need your opinion guys.

I'm using an LTSP server. Is it necessary to have LDAP configured with it?

If yes, then what are the benefits of having LDAP together with LTSP?

If no, is LTSP enough?

I found this website to integrate both services: [http://www.ltsp.org/twiki/bin/view/Ltsp/LDAP](http://www.ltsp.org/twiki/bin/view/Ltsp/LDAP)

Thanks.

---

### Post by MocArt on 2009-10-10
Hi!  i`m from Russia, and so please sorry my english ;) i have 2 troubles:
1. When If i do by first HOWTO from [ingcabral]("http://ubuntuforums.org/member.php?u=834368") i stop on 13 unit
```

sudo smbldap-populate
Unable to open /etc/opt/IDEALX/smbldap-tools/smbldap.conf for reading !
Compilation failed in require at /usr/sbin/smbldap-populate line 31.
BEGIN failed--compilation aborted at /usr/sbin/smbldap-populate line 31. 
			 		
```
and when i do **dpkg-reconfigure slapd** that not work too :(

2. When If i do by Script from [senor_smile]("http://ubuntuforums.org/member.php?u=241761") i stop on 
```

13) Before configuring smbldap-tools, check that Samba is running and the Windows domain SID can be retrieved.
 3883 ?        00:00:00 smbd
[2009/10/11 15:56:12,  0] lib/smbldap.c:smbldap_connect_system(996)
  failed to bind to server ldap://localhost with dn="cn=admin,dc=DOMAIN" Error: Invalid credentials
        (unknown)

```

please help me !

p.s. OS Ubuntu 9.04 Server

---

### Post by ientzy on 2009-10-12
I need to make a BDC to this tutorial, can any1 help me with a how to? I try to make a clone to this server but i don`t know how to sync the users from master server.

---

### Post by lweflrelg on 2009-10-19
Hello,

Maybe it's not the right place to ask my question, but i'll try

I've set up Ubuntu 9.04 server as PDC/Samba3 with LDAP and windows clients work with domain as expected.
But now i got terrible headache trying browse domain smb shares with Ubuntu 9.04 =client=.

There are lot of great documents and threads covering Ubuntu as
PDC/LDAP
File server
Print server
Windows stations as clients of Ubuntu PDC (server)
Ubuntu stations as clients of Windows AD (Likewise)

but i didn't find any hint how to proper setup **Ubuntu 9.04 samba-client** with **Ubuntu 9.04 LDAP/samba server**.
Likewise works like magic but with AD only. It doesn't support NT4/Samba3 based domains

First, i tuned up Samba config (ROLE_DOMAIN_MEMBER)

i've done LDAP authentication covered here
[https://help.ubuntu.com/community/LDAPClientAuthentication](https://help.ubuntu.com/community/LDAPClientAuthentication)

and now i can login to PC with domain accs, folders automatically creates when i log in as new user, i see full lists of domain groups/users as a reply to "getent group" and "getent passwd".
But when i browse any domain shares, i get popup window to enter correct credentials.
Now i'm confused and stuck with question - what i have to do?
Do i need winbind to access domain smb shares?
Where i can find proper smb.conf example for my case?

Thanks beforehand

---

### Post by ientzy on 2009-10-20
> **lweflrelg said:**
> Hello,

Maybe it's not the right place to ask my question, but i'll try

I've set up Ubuntu 9.04 server as PDC with LDAP and windows clients work with domain as expected.
But now i got terrible headache trying browse domain smb shares with Ubuntu 9.04 =client=.

There are lot of great documents and threads covering Ubuntu as
PDC/LDAP
File server
Print server
Windows stations as clients of Ubuntu PDC (server)
Ubuntu stations as clients of Windows AD (Likewise)

but i didn't find any hint how to proper setup Ubuntu 9.04 as client of Ubuntu 9.04 server.
Likewise works like magic but with AD only. It doesn't support NT4/Samba3 based domains

First, i tuned up Samba config (ROLE_DOMAIN_MEMBER)

i've done LDAP authentication covered here
[https://help.ubuntu.com/community/LDAPClientAuthentication](https://help.ubuntu.com/community/LDAPClientAuthentication)

and now i can login to PC with domain accs, folders automatically creates when i log in as new user, i see full lists of domain groups/users as a reply to "getent group" and "getent passwd".
But when i browse any domain shares, i get popup window to enter correct credentials.
Now i'm confused and stuck with question - what i have to do?
Do i need winbind to access domain smb shares?
Where i can find proper smb.conf example for my case?

Thanks beforehand


I have Samba PDC with filesharing, and my settings for sharing look like this and all users from a specific group have full access to that sharing:


[Sharing 1]
   comment = Access Tools
   path = /<Custom folder>/<Sharing 1>
   valid users = @root @domain group @domain group 2
   ;invalid users = 
   create mask = 0660
   directory mask = 0771
   writable = yes
   browsable = yes



I hope to help u!

---

### Post by lweflrelg on 2009-10-20
> I hope to help u!     Thank you, mate but your config is simple file server example
I can't auth my smb-client against my domain.

Once again, =server= samba setup seems to be ok, since Windows XP SP3 machines works just perfect.

Now i'm in doubt about a way of login authentication - do i have to remove all ldap stuff from my client? Switch from ldap to winbind only?
Still didn't find anything except bunch of Linux+AD howtos and tutors

---

### Post by Cubus on 2009-11-02
I am aswell having this Problem:

```

sudo smbldap-populate
Unable to open /etc/opt/IDEALX/smbldap-tools/smbldap.conf for reading !
Compilation failed in require at /usr/sbin/smbldap-populate line 31.
BEGIN failed--compilation aborted at /usr/sbin/smbldap-populate line 31.

```

dpkg-reconfigure slapd did not solve it, I am using Ubuntu Server 8.04 x64.

Can I supply any further infos?

---

### Post by wiz561 on 2009-11-02
FYI, this worked great on Ubuntu Server 9.10 (Karmic Koala).

---

### Post by jonytrifulca on 2009-11-03
HI

   I solve the smbldap-populate problem doing this:

slappasswd

this command will ask for a password (twice) enter "12345" it will return an ssha hash in the following format:

{SSHA}XXXXXXXXXXXXXXXXXXXXXXXXXX

open /etc/ldap/slapd.conf
and add/edit the following:

rootdn cn=admin,dc=example,dc=local
rootpw {SSHA}XXXXXXXXXXXXXXXXXXXXXXXXXX


Now reboot or restart and the commands should run fine.


from this link [http://ubuntuforums.org/archive/index.php/t-640760-p-4.html](http://ubuntuforums.org/archive/index.php/t-640760-p-4.html) from the whoop user (thankS)!!

and the 19 step problem with getent group setting the IP of server instead nameserver in the ldap-auth-client configuration step (this 19 step)

So  I hope this can help someone ;)

and GREAT GREAT tutorial!!!! thanks!!!!!!!!!!!!!!!!!!!!!

---

### Post by abishur on 2009-11-10
I am also having the problem with smnldap-populate.  I'm using Ubuntu 9.10 when I run dpkg-reconfigure slapd I only get 3 yes no questions.  I've tried to manually create smbldap_bind.confand smbldap.conf but still no luck.  Any ideas?

---

### Post by abishur on 2009-11-16
[FONT=Arial][SIZE=2]Fixed it.  Some one else mentioned manually making the files, (that didn't work for my set up). Here's what I did to get it to work

[/SIZE][/FONT][INDENT][FONT=Arial][SIZE=2]          1.Getting smbldap-tools ready[/SIZE][/FONT]

[FONT=Arial][SIZE=2]          In a terminal window with root privileges browse to the examples directory[/SIZE][/FONT]

> [FONT=Arial][SIZE=2]cd /usr/share/doc/smbldap-tools/examples/      [/SIZE][/FONT]
[FONT=Arial][SIZE=2]         Then execute the following commands[/SIZE][/FONT]

> [FONT=Arial][SIZE=2]cp smbldap_bind.conf /etc/smbldap-tools/[/SIZE][/FONT]
[FONT=Arial][SIZE=2]cp smbldap.conf.gz /etc/smbldap-tools/[/SIZE][/FONT]
[FONT=Arial][SIZE=2]gzip -d /etc/smbldap-tools/smbldap.conf.gz      [/SIZE][/FONT][FONT=Arial][SIZE=2]

[/SIZE][/FONT][FONT=Arial][SIZE=2]Open up the smbldap-tools directory:[/SIZE][/FONT]

> [FONT=Arial][SIZE=2]cd /etc/smbldap-tools/[/SIZE][/FONT]
[FONT=Arial][SIZE=2]   2.Get your netSID for your domain[/SIZE][/FONT]

> [FONT=Arial][SIZE=2]net getlocalsid[/SIZE][/FONT][/INDENT][FONT=Arial][SIZE=2]
[/SIZE][/FONT][INDENT][FONT=Arial][SIZE=2] It will return something like:[/SIZE][/FONT]

> [FONT=Arial][SIZE=2]SID for domain SERVERNAME is:   S-1-5-21-2899629268-4176875250-2352135513[/SIZE][/FONT][FONT=Arial][SIZE=2]   Copy this number[/SIZE][/FONT]
[/INDENT][FONT=Arial][SIZE=2]
[/SIZE][/FONT][INDENT][FONT=Arial][SIZE=2]   3.Edit your smbldap.conf file[/SIZE][/FONT]

> [FONT=Arial][SIZE=2]gedit   /etc/smbldap-tools/smbldap.conf[/SIZE][/FONT][FONT=Arial][SIZE=2]   We need to make the following changes, but you cannot just copy and paste them into the file.  You need to search for them and make the adjustments.[/SIZE][/FONT]
[/INDENT][FONT=Arial][SIZE=2]
       [/SIZE][/FONT][INDENT]> SID="S-1-5-21-949328747-3404738746-3052206637" ## This line must have the same SID as when you ran "net getlocalsid"
sambaDomain="EXAMPLE"
ldapTLS="0"
suffix="dc=example,dc=local"
sambaUnixIdPooldn="sambaDomainName=EXAMPLE,${suffix}" ## Be careful with this section!!
userHome="/home/%U" ## This is found in the UNIX section.
userSmbHome=
userProfile=
userHomeDrive=
userScript=
mailDomain="example.local"    
[/INDENT][FONT=Arial][SIZE=2]
[/SIZE][/FONT][INDENT][FONT=Arial][SIZE=2]4.[/SIZE][/FONT][FONT=Arial][SIZE=2]Open the file /etc/smbldap-tools/smbldap_bind.conf file for editing:[/SIZE][/FONT]

> [FONT=Arial][SIZE=2]gedit   /etc/smbldap-tools/smbldap_bind.conf[/SIZE][/FONT]
[FONT=Arial][SIZE=2]Edit the file so the following is correct according to your setup[/SIZE][/FONT]

> [FONT=Arial][SIZE=2]slaveDN="cn=admin,dc=example,dc=local"[/SIZE][/FONT]
[FONT=Arial][SIZE=2] slavePw="12345"[/SIZE][/FONT]
[FONT=Arial][SIZE=2] masterDN="cn=admin,dc=example,dc=local"[/SIZE][/FONT]
[FONT=Arial][SIZE=2] masterPw="12345"    [/SIZE][/FONT][/INDENT][FONT=Arial][SIZE=2]
[/SIZE][/FONT][INDENT][FONT=Arial][SIZE=2]   5.Set the correct permission for the above two files[/SIZE][/FONT]
[/INDENT][INDENT]> chmod 0644 /etc/smbldap-tools/smbldap.conf       
chmod 0600 /etc/smbldap-tools/smbldap_bind.conf[/INDENT]

---

### Post by siate on 2009-11-17
Great tutorial !

---

### Post by abishur on 2009-11-18
> **siate said:**
> Great tutorial !
Thanks abishur because what you wrote really helped me since I had that problem. But here is the thing I followed every step of that HOW TO but I am not using that server as a PDC,in fact I want to share folders with samba in which the authentification and right access will be managed by LDAP.
Thus,the only diffrence I have between this HOW TO and my server is the :
#be a PDC ...
domain logons : No
domain master : no
#be a wins server 
wins support : No
wins server : 192.168.7.2
Do you think it can work ? Am I right to do it like that ?
Everything went "nearly" as expected but I can only connect the server with the root account and get access to the shared folders and files, the david account doesn't work and I tried to create another user to log in but it also doesn't work.How can I create users who wiil be able to connect the server ? Any ideas ?

[SIZE=2][FONT=Arial]No problem!  It's always frustrating to find a thread where the person obviously solved their problem, but didn't tell others how to do it.

Let me make sure I'm understanding what you want. Your setup is as follows
[/FONT][/SIZE]
[LIST=1]
[*]Computer A: Wins Server (and largely unimportant to the issue at hand if I understand samba and openLDAP)
[*]Computer B: LDAP Server using Samba as a means of Windows authentication
[/LIST]
And what you want to do is access the folders with other accounts in your LDAP directory.

***IF*** the above is correct, then I think I have a solution for you.  Go to 
[INDENT]> "Applications->Ubuntu Software Center"[/INDENT]In the search field, type in Samba and install the first one (it just says Samba)

This will install the samba GUI under
[INDENT]> "System->Administration->Samba[/INDENT]If you click on the [SIZE=3]**[COLOR=YellowGreen]+[/COLOR]**[/SIZE] sign at the top it will open up a dialog to add a new share (if you highlight an existing sharing and then click on the gear it will let you edit an existing share)

The second tab in this dialog says "Access" it will display a list of both local users and LDAP users.  You can either check the ones you want to access it or you can say "Allow access to everyone"

Now, if for ANY reason you don't see your ldap users, I would say there's a problem with authentication between Samba and LDAP.  If that's the case let me know and I probably know what's wrong with it.

Edit: Oh yeah, make sure to allow SAMBA access through your firewall if you have it turned on.  I forgot to do that the first time I set this up and reinstalled Linux 3 times before I realized what I was doing!

---

### Post by siate on 2009-11-19
First thank you, I think that what you seem to understand is right (forgive me for my bad english but I'm from Tahiti -> speak french there :S). 
Everything works fine now and the "application" you made me install is really simple and useful but I'm actually in an intership/work placement/training(I work in an enterprise for a limited period in order to get a diploma in the end) and what they want me to do is to manage the right acces with LDAP(everything else is good now).
Do you think it is possible ?
How do i do that ?

---

### Post by abishur on 2009-11-19
Ah, I see what you're saying.  You want to control access DIRECTLY from LDAP.  And to answer your question, that's what you are doing with the Samba application.
 
Explanation:
 
LDAP is a protocol for authentication and openLDAP is a program for Linux which uses the LDAP protocol.  It is, for all intents and purposes, Active Directory for Linux.
 
In a Windows based environment Active Directory is used to set up user account but it is not the means by which a folder or file is shared.  Windows has a built in File Sharing system which does that.  However!  Windows CAN control access by using user names and/or groups to tell who can and cannot access a specific resource shared on the network.
 
Taking that concept to Linux, openLDAP sets up users and groups.  Then Samba shares folders for Windows based computers to use.  In that Samba interface I had you install, the "Access" tab actually lists the users and groups you've set up in openLDAP.  So when you check a name in the Samba application it is actually using openLDAP.
 
Here's a step by step look at what (basically) happens
[LIST=1]
[*]Samba Shares a folder and gives a specific user in openLDAP access to it
[*]PC User attempts to access shared folder via Samba
[*]Samba checks the Access List (ACL) and confirms that the user name has permission to access the folder
[*]Samba forwarders the user name and password to openLDAP
[*]openLDAP confirms that the user has the correct user name/password combo
[*]Samba permits user to access shared folder.
[/LIST]This is also how Active Directory and Windows sharing work with each other.  Of course if the user doesn't have permission then Samba will reject them and if the wrong password is provided the openLDAP will reject them.
 
ALL of which is to say this: You already are using openLDAP to control folder access, but NO openLDAP is not capable of directly sharing folders because the LDAP protocol is not a file sharing protocol, it is an _authentication_protocol. :)  We must use Samba because it is the file sharing protocol, but it is authenticating folder access against openLDAP.

---

### Post by siate on 2009-11-19
Thanks a lot Abishur for replying so fast and for these very clear explanations. 
So I guess I'm done with it ?
I'm sorry to bother you again but you've just said that :
"In that Samba interface I had you install, the "Access" tab actually lists the users and groups you've set up in openLDAP. So when you check a name in the Samba application it is actually using openLDAP."
Well, I do have users list but I do not see group list in it so I can only manage right acces  by users. 
Should I be able to proceed by group ?
Maybe there is an "advanced" version of that samba application with more options?
Thanks a lot again.

---

### Post by abishur on 2009-11-19
ah, my bad, I misstyped.  It is possible to allow groups access to folders, but I don't know of any nice GUI interface that lets you do that.  To allow an entire group access to a shared resource you'll need to edit the smb.conf file itself.  Googling "Group access via Samba" returns some good hits.  [This site]("http://oreilly.com/catalog/samba/chapter/book/ch06_01.html") in particular has some easy to follow instructions for group access ifyou want to set it up.

---

### Post by siate on 2009-11-19
Ok then I'll make some researches to find out the easiest way to do it.
I was told that apache directory studio might be the solution(Apparently it can manage right access).
Thank you

---

### Post by abishur on 2009-11-22
For those interested, I've posted a new thread which takes these EXTREMELY good instructions and updated/cleaned them up for Ubuntu 9.10!  Thanks ingcabral for the excellent post!  [Here's my updated post.]("http://ubuntuforums.org/showthread.php?p=8343070")

---

### Post by evayroberto on 2009-12-01
I have tested all the ideas for avoid smbldap-populate error in this thread, and I continue with it. Any suggestions, please???

---

### Post by evayroberto on 2009-12-01
More tests...I have used configure.pl to configure, and now,when I try to populate, it gives different error
"can't extract first attr and value from suffix mydomain.local at /usar/smbldap-populate line 149.". I google it but nothing about it.
Please, gurus ;)

---

### Post by abishur on 2009-12-01
> **evayroberto said:**
> More tests...I have used configure.pl to configure, and now,when I try to populate, it gives different error
"can't extract first attr and value from suffix mydomain.local at /usar/smbldap-populate line 149.". I google it but nothing about it.
Please, gurus ;)
 
Have you followed the instructions in the new thread I mentioned? This thead is excellent, but needed some updating for 9.10.
 
Did you edit your smbldap.conf and smbldap_bind.conf files or just copy them to the correct location? Here are some quick things to check.

[LIST=1]
[*]In smbldap.conf, it's not enough to copy and paste the changes I mentioned earlier in the thread to the beginning of the file, you **MUST** find the correct spot and change the values there.
[*]In smbldap_bind.conf do you have the correct masterDN information typed in? Have you logged into ldap using this information and confirmed that it is working? If you cannot log into LDAP with the masterDN and masterPW you have entered into smbldap_bind.conf you have either put in the wrong information to the file, or you need to check over your LDAP settings again.
[*]The password store in smbldap_bind.conf **MUST BE** written in clear text, for example, if my password was pineapple, my line would read: masterPW = "pineapple" You cannot put in the scrambled version of your password you used for slapd.conf
[*]Did you add the smb password with [SIZE=2]smbpasswd -W?[/SIZE]
[*]Finally, are you certain you have slapd running?
[/LIST]If the above things don't work for you here's what I'd do:[LIST=1]
[*]Undo your changes to configure.pl (I've never had to mess with that and I would suggest restoring it to its original state)
[*]Look at the thread I posted and follow it step by step. I've made it very easy to follow and I've never had any problems with it.
[*]You may need to complete remove (not just remove COMPLETELY remove) slapd and smb and start over from scratch if its still not working. It's possible you made a mistake somewhere in your configuration that you just need to clear out.
[/LIST]

---

### Post by evayroberto on 2009-12-01
I'll try with your new guide...thanks for your efforts helping us, the newbies.;)

---

### Post by abishur on 2009-12-01
> **evayroberto said:**
> I'll try with your new guide...thanks for your efforts helping us, the newbies.;)
 
No problem, I had a HUGE problem getting all this set up too.  I've lost count of how many times I just had to wipe my computer clean and start from a fresh install.  (Which may or may not be a good idea if you don't have too much set up on it already)

---

### Post by bowenkanobe on 2010-02-28
> **abishur said:**
> No problem, I had a HUGE problem getting all this set up too. I've lost count of how many times I just had to wipe my computer clean and start from a fresh install. (Which may or may not be a good idea if you don't have too much set up on it already)
 
That's the wonderful thing about VMWare. It's so easy to just delete a virtual disk and start over.  :)
 
Still quite a noob with Ubuntu, but I'm trying, failing, tweaking, and learning.

---

### Post by lizdeika on 2010-03-01
> **ghen said:**
> I'm wiping my 8.04 ldap+samba setup as we speak :o

(it was only testing environment anyway lol)

In your ldif file when you created your dcObject, you defined dc: ubuntudom .. if I want my dn to be dc=test,dc=local how would I define dc in that line? (I'm just going with test for now)

point 1: in your slapd.conf you set a rootpw {SSHA} ; you should note that it should change like the one in init.ldif

point 2: you never actually say to configure smbldap-tools so I just did it after step 13 and used mostly default settings (pretty straightforward)

point 3: you have a copy/paste error on step 18 ;)

note 1: defaultMaxPasswordAge can't be blank (by hitting . during configuration) if you don't want a max password age I guess it would require commenting out that line in /etc/smbldap-tools/smbldap.conf after the config is done... I just made mine 120 days to get past it.



edit: Uh oh, I got to point 19 and failed. everything was fine until that point, but getent group just doesn't respond correctly even after a reboot. I think it has something to do with the ldap-auth-client install, but I don't know how to reconfigure that. I guess I'll try reinstalling it.

well reinstall didn't work, and dpkg-reconfigure ldap-auth-config didn't work, so I had to edit the /etc/ldap.conf file manually. the host line was commented out so I uncommented it and rebooted. Now it works.

2.5 hours from fresh partitioning to joining computers to the domain!
 Im  stack to on 19 , getent doesn't respond LDAP groups. What is correct  /etc/ldap.conf configuration ?

---

### Post by any.linux12 on 2010-03-12
hi!

I did all steps carefully but I get an error when I try to populate:


sudo smbldap-populate
Unable to open /etc/opt/IDEALX/smbldap-tools/smbldap.conf for reading !
Compilation failed in require at /usr/sbin/smbldap-populate line 31.
BEGIN failed--compilation aborted at /usr/sbin/smbldap-populate line 31.

And my /etc/opt is empty!

What did I miss?

thanks

---

### Post by ingcabral on 2010-03-12
> **any.linux12 said:**
> hi!

I did all steps carefully but I get an error when I try to populate:


sudo smbldap-populate
Unable to open /etc/opt/IDEALX/smbldap-tools/smbldap.conf for reading !
Compilation failed in require at /usr/sbin/smbldap-populate line 31.
BEGIN failed--compilation aborted at /usr/sbin/smbldap-populate line 31.

And my /etc/opt is empty!

What did I miss?

thanks


Hi,

please be aware that IDEALX is the example that comes by default when installing smbldaptools.
I don't have an ubuntu box to try this now (I'll try as I get home) but I'd suggest to use the reconfigure tool which is used somewhere in the tutorial, so you can define the domain name you are going to use.
I'll keep in touch!

Best,
Ariel

---

### Post by tchekote on 2010-03-23
hi, newbie here...

followed your step by step exactly...

I get a "no such file or directory" error here 

"sudo gunzip /usr/share/doc/samba-doc/examples/LDAP/samba.schema.gz"

checked the directory, no such file... 

since I am new newbie... I would appreciate you help..

thank you for a great step by step...

---

### Post by wmuzzi on 2010-06-10
Problems logging windows machines.

I can join the domain normally.

After restarting indicates that duplicate name exists on the network.

When I try to log in, indicates that the domain is unavailable.

I made two machines and get the message in both.

Thank you in advance.

---

### Post by pedis on 2010-09-08
Hi, thanx for the tuto, it works for windows users but how can I add a linux machine in my domain?

---

### Post by ingcabral on 2010-09-08
> **pedis said:**
> Hi, thanx for the tuto, it works for windows users but how can I add a linux machine in my domain?


Hi,

You can join your linux machine in the same way as you would when joining a Windows Domain.
I can't remember exactly how, but I remember that you have to edit your smb.conf file.

Let me know if you need help finding an instructive for doing so.

Regards,
Ariel

---

### Post by pedis on 2010-09-10
Hi Ariel, I think linux machines do not join domains directly but they authenticate against LDAP date base. It is done by editing nsswich.conf and pam-* files so the system does not look fr the user at /etc/passwd, but at the data base located on the server. The fact is I have tryied it but I am not able to log in my ubuntu desktop. Maybe I should add my machine to the data base.I don't know...
Anyway if I should edit the smb.conf file in a particular way I would thank you to explain it to me.
Thank you


Hola Ariel, creo que las maquinas linux no se unen directamente al dominio sino que se autentican contra la base de datos LDAP. Hay que editar los archivos nsswich.conf y los pam-* para que no busque el usuario en /etc/passwd, sino en la base de datos alojada en el server. La cosa es que lo he intentado asi pero no consigo loguearme en mi ubuntu desktop. Tal vez deberia añadir mi maquina linux a la base de datos. No se...
De todas formas si hay que editar el smb.conf de alguna manera en especial te agradeceria que lo comentaras.
Gracias

---

### Post by BarryDocks on 2010-10-06
got as far as step 14 but then got this error:
```
 smbldap-populate
Unable to open /etc/opt/IDEALX/smbldap-tools/smbldap.conf for reading !
Compilation failed in require at /usr/sbin/smbldap-populate line 31.
BEGIN failed--compilation aborted at /usr/sbin/smbldap-populate line 31.

```

would be grateful for suggestions?
Thanks

---

### Post by BarryDocks on 2010-10-07
Sorry duplicate post

---

