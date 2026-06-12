---
title: "Samba User Not Working"
date: 2015-07-19
forum: New to Ubuntu
---

### Post by Russell_Challis on 2015-07-19
Hi,

I'm not sure if this is the right place to post or not but I am new to ubuntu :) I have been trying to build a simple NAS type server for my home network with a 1tb hdd and multiple partitions which I have already performed and linked into ubuntu. The shares work when I login to my root account but when I try and login to the shares with any other account I have made it just does not accept the credentials. Any help will be great :)

I have attached a copy of my smb.conf file

```

#
# Sample configuration file for the Samba suite for Debian GNU/Linux.
#
#
# This is the main Samba configuration file. You should read the
# smb.conf(5) manual page in order to understand the options listed
# here. Samba has a huge number of configurable options most of which 
# are not shown in this example
#
# Some options that are often worth tuning have been included as
# commented-out examples in this file.
#  - When such options are commented with ";", the proposed setting
#    differs from the default Samba behaviour
#  - When commented with "#", the proposed setting is the default
#    behaviour of Samba but the option is considered important
#    enough to be mentioned here
#
# NOTE: Whenever you modify this file you should run the command
# "testparm" to check that you have not made any basic syntactic 
# errors. 
# A well-established practice is to name the original file
# "smb.conf.master" and create the "real" config file with
# testparm -s smb.conf.master >smb.conf
# This minimizes the size of the really used smb.conf file
# which, according to the Samba Team, impacts performance
# However, use this with caution if your smb.conf file contains nested
# "include" statements. See Debian bug #483187 for a case
# where using a master file is not a good idea.
#


#======================= Global Settings =======================


[global]


## Browsing/Identification ###


# Change this to the workgroup/NT-domain name your Samba server will part of
   workgroup = WORKGROUP


# server string is the equivalent of the NT Description field
   server string = %h server (Samba, Ubuntu)


# Windows Internet Name Serving Support Section:
# WINS Support - Tells the NMBD component of Samba to enable its WINS Server
#   wins support = no


# WINS Server - Tells the NMBD components of Samba to be a WINS Client
# Note: Samba can be either a WINS Server, or a WINS Client, but NOT both
;   wins server = w.x.y.z


# This will prevent nmbd to search for NetBIOS names through DNS.
   dns proxy = no


# What naming service and in what order should we use to resolve host names
# to IP addresses
;   name resolve order = lmhosts host wins bcast


#### Networking ####


# The specific set of interfaces / networks to bind to
# This can be either the interface name or an IP address/netmask;
# interface names are normally preferred
;   interfaces = 127.0.0.0/8 eth0


# Only bind to the named interfaces and/or networks; you must use the
# 'interfaces' option above to use this.
# It is recommended that you enable this feature if your Samba machine is
# not protected by a firewall or is a firewall itself.  However, this
# option cannot handle dynamic or non-broadcast interfaces correctly.
;   bind interfaces only = yes






#### Debugging/Accounting ####


# This tells Samba to use a separate log file for each machine
# that connects
   log file = /var/log/samba/log.%m


# Cap the size of the individual log files (in KiB).
   max log size = 1000


# If you want Samba to only log through syslog then set the following
# parameter to 'yes'.
#   syslog only = no


# We want Samba to log a minimum amount of information to syslog. Everything
# should go to /var/log/samba/log.{smbd,nmbd} instead. If you want to log
# through syslog you should set the following parameter to something higher.
   syslog = 0


# Do something sensible when Samba crashes: mail the admin a backtrace
   panic action = /usr/share/samba/panic-action %d




####### Authentication #######


# "security = user" is always a good idea. This will require a Unix account
# in this server for every user accessing the server. See
# /usr/share/doc/samba-doc/htmldocs/Samba3-HOWTO/ServerType.html
# in the samba-doc package for details.
#   security = user


# You may wish to use password encryption.  See the section on
# 'encrypt passwords' in the smb.conf(5) manpage before enabling.
   encrypt passwords = true


# If you are using encrypted passwords, Samba will need to know what
# password database type you are using.  
   passdb backend = tdbsam


   obey pam restrictions = yes


# This boolean parameter controls whether Samba attempts to sync the Unix
# password with the SMB password when the encrypted SMB password in the
# passdb is changed.
   unix password sync = yes


# For Unix password sync to work on a Debian GNU/Linux system, the following
# parameters must be set (thanks to Ian Kahan <<kahan@informatik.tu-muenchen.de> for
# sending the correct chat script for the passwd program in Debian Sarge).
   passwd program = /usr/bin/passwd %u
   passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .


# This boolean controls whether PAM will be used for password changes
# when requested by an SMB client instead of the program listed in
# 'passwd program'. The default is 'no'.
   pam password change = yes


# This option controls how unsuccessful authentication attempts are mapped
# to anonymous connections
   map to guest = bad user


########## Domains ###########


# Is this machine able to authenticate users. Both PDC and BDC
# must have this setting enabled. If you are the BDC you must
# change the 'domain master' setting to no
#
;   domain logons = yes
#
# The following setting only takes effect if 'domain logons' is set
# It specifies the location of the user's profile directory
# from the client point of view)
# The following required a [profiles] share to be setup on the
# samba server (see below)
;   logon path = \\%N\profiles\%U
# Another common choice is storing the profile in the user's home directory
# (this is Samba's default)
#   logon path = \\%N\%U\profile


# The following setting only takes effect if 'domain logons' is set
# It specifies the location of a user's home directory (from the client
# point of view)
;   logon drive = H:
#   logon home = \\%N\%U


# The following setting only takes effect if 'domain logons' is set
# It specifies the script to run during logon. The script must be stored
# in the [netlogon] share
# NOTE: Must be store in 'DOS' file format convention
;   logon script = logon.cmd


# This allows Unix users to be created on the domain controller via the SAMR
# RPC pipe.  The example command creates a user account with a disabled Unix
# password; please adapt to your needs
; add user script = /usr/sbin/adduser --quiet --disabled-password --gecos "" %u


# This allows machine accounts to be created on the domain controller via the 
# SAMR RPC pipe.  
# The following assumes a "machines" group exists on the system
; add machine script  = /usr/sbin/useradd -g machines -c "%u machine account" -d /var/lib/samba -s /bin/false %u


# This allows Unix groups to be created on the domain controller via the SAMR
# RPC pipe.  
; add group script = /usr/sbin/addgroup --force-badname %g


########## Printing ##########


# If you want to automatically load your printer list rather
# than setting them up individually then you'll need this
#   load printers = yes


# lpr(ng) printing. You may wish to override the location of the
# printcap file
;   printing = bsd
;   printcap name = /etc/printcap


# CUPS printing.  See also the cupsaddsmb(8) manpage in the
# cupsys-client package.
;   printing = cups
;   printcap name = cups


############ Misc ############


# Using the following line enables you to customise your configuration
# on a per machine basis. The %m gets replaced with the netbios name
# of the machine that is connecting
;   include = /home/samba/etc/smb.conf.%m


# Most people will find that this option gives better performance.
# See smb.conf(5) and /usr/share/doc/samba-doc/htmldocs/Samba3-HOWTO/speed.html
# for details
# You may want to add the following on a Linux system:
#         SO_RCVBUF=8192 SO_SNDBUF=8192
#   socket options = TCP_NODELAY


# The following parameter is useful only if you have the linpopup package
# installed. The samba maintainer and the linpopup maintainer are
# working to ease installation and configuration of linpopup and samba.
;   message command = /bin/sh -c '/usr/bin/linpopup "%f" "%m" %s; rm %s' &


# Domain Master specifies Samba to be the Domain Master Browser. If this
# machine will be configured as a BDC (a secondary logon server), you
# must set this to 'no'; otherwise, the default behavior is recommended.
#   domain master = auto


# Some defaults for winbind (make sure you're not using the ranges
# for something else.)
;   idmap uid = 10000-20000
;   idmap gid = 10000-20000
;   template shell = /bin/bash


# The following was the default behaviour in sarge,
# but samba upstream reverted the default because it might induce
# performance issues in large organizations.
# See Debian bug #368251 for some of the consequences of *not*
# having this setting and smb.conf(5) for details.
;   winbind enum groups = yes
;   winbind enum users = yes


# Setup usershare options to enable non-root users to share folders
# with the net usershare command.


# Maximum number of usershare. 0 (default) means that usershare is disabled.
;   usershare max shares = 100


# Allow users who've been granted usershare privileges to create
# public shares, not just authenticated ones
   usershare allow guests = yes


#======================= Share Definitions =======================


# Un-comment the following (and tweak the other settings below to suit)
# to enable the default home directory shares. This will share each 
# user's home director as \\server\username
;[homes]
;   comment = Home Directories
;   browseable = no


# By default, the home directories are exported read-only. Change the
# next parameter to 'no' if you want to be able to write to them.
;   read only = yes


# File creation mask is set to 0700 for security reasons. If you want to
# create files with group=rw permissions, set next parameter to 0775.
;   create mask = 0700


# Directory creation mask is set to 0700 for security reasons. If you want to
# create dirs. with group=rw permissions, set next parameter to 0775.
;   directory mask = 0700


# By default, \\server\username shares can be connected to by anyone
# with access to the samba server. Un-comment the following parameter
# to make sure that only "username" can connect to \\server\username
# The following parameter makes sure that only "username" can connect
#
# This might need tweaking when using external authentication schemes
;   valid users = %S


# Un-comment the following and create the netlogon directory for Domain Logons
# (you need to configure Samba to act as a domain controller too.)
;[netlogon]
;   comment = Network Logon Service
;   path = /home/samba/netlogon
;   guest ok = yes
;   read only = yes


# Un-comment the following and create the profiles directory to store
# users profiles (see the "logon path" option above)
# (you need to configure Samba to act as a domain controller too.)
# The path below should be writable by all users so that their
# profile directory may be created the first time they log on
;[profiles]
;   comment = Users profiles
;   path = /home/samba/profiles
;   guest ok = no
;   browseable = no
;   create mask = 0600
;   directory mask = 0700


[printers]
   comment = All Printers
   browseable = no
   path = /var/spool/samba
   printable = yes
   guest ok = no
   read only = yes
   create mask = 0700


# Windows clients look for this share name as a source of downloadable
# printer drivers
[print$]
   comment = Printer Drivers
   path = /var/lib/samba/printers
   browseable = yes
   read only = yes
   guest ok = no
# Uncomment to allow remote administration of Windows print drivers.
# You may need to replace 'lpadmin' with the name of the group your
# admin users are members of.
# Please note that you also need to set appropriate Unix permissions
# to the drivers directory for these users to have write rights in it
;   write list = root, @lpadmin


# A sample share for sharing your CD-ROM with others.
;[cdrom]
;   comment = Samba server's CD-ROM
;   read only = yes
;   locking = no
;   path = /cdrom
;   guest ok = yes




[multimedia]
	writeable = yes
	path = /multimedia
	force group = users
	create mask = 0770
	comment = Challis Multimedia
	directory mask = 0770
	valid users = rchallis,echallis,mchallis,achallis,@achallis,@adm,@echallis,@mchallis,@users


[rchallis]
comment = Russell Challis
path = /rchallis
read only = no
writeable = yes
create mask = 0770
directory mask = 0770
valid users = rchallis
force group = users


[shared]
comment = Challis Shared
path = /shared
read only = no
writeable = yes
create mask = 0770
directory mask = 0770
valid users = rchallis echallis achallis mchallis
force group = users


[echallis]
	writeable = yes
	path = /echallis
	force group = users
	create mask = 0770
	comment = Emma Challis
	directory mask = 0770
	valid users = users,@users


[mchallis]
comment = Mark Challis
path = /mchallis
read only = no
writeable = yes
directory mask = 0770
create mask = 0770
valid users = rchallis mchallis
force group = users


[achallis]
comment = Annette Challis
path = /achallis
read only = no
writeable = yes
directory mask = 0770
create mask = 0770
valid users = rchallis achallis
force group = users


[public]
comment = Public Share
path = /shared/Public
read only = no
writeable = yes
directory mask = 0770
create mask = 0770
browseable = yes
valid users = echallis rchallis
force group = users


[webserver]
comment = Web Server
path = /var/www
read only = no
writeable = yes
directory mask = 0770
create mask = 0770
valid users = rchallis


# The next two parameters show how to auto-mount a CD-ROM when the
#	cdrom share is accesed. For this to work /etc/fstab must contain
#	an entry like this:
#
#       /dev/scd0   /cdrom  iso9660 defaults,noauto,ro,user   0 0
#
# The CD-ROM gets unmounted automatically after the connection to the
#
# If you don't want to use auto-mounting/unmounting make sure the CD
#	is mounted on /cdrom
#
;   preexec = /bin/mount /cdrom
;   postexec = /bin/umount /cdrom



```

---

### Post by bab1 on 2015-07-19
> **Russell_Challis said:**
> Hi,

I'm not sure if this is the right place to post or not but I am new to ubuntu :) I have been trying to build a simple NAS type server for my home network with a 1tb hdd and multiple partitions which I have already performed and linked into ubuntu. 

By " linked into ubuntu", do you mean that you have mounted the partitions via fstab so that when the system is booted up they are always mounted at the same location.  Post the output of this command so we may see what you have done so far```
df -h
```

...That should list all the mounted partitions.

> 
The shares work when I login to my root account but when I try and login to the shares with any other account I have made it just does not accept the credentials.

Are you logging into the machine locally as the root user?  You should should never have to login as the root user to use any part of Ubuntu. The local user (whoever that is) doesn't need Samba anyway.  I don't think you mean that, do you?  What did you do to create the Samba users credentials?  Post the output of ```
sudo pdbedit -L
```
...This will list all the Samba users.> 

```
...

[multimedia]
	writeable = yes
	path = /multimedia
	force group = users
	create mask = 0770
	comment = Challis Multimedia
	directory mask = 0770
[COLOR="#FF0000"]	valid users = rchallis,echallis,mchallis,achallis,@achallis,@adm,@echallis,@mchallis,@users
[/COLOR]

[rchallis]
comment = Russell Challis
path = /rchallis
read only = no
writeable = yes
create mask = 0770
directory mask = 0770
valid users = rchallis
force group = users


[shared]
comment = Challis Shared
path = /shared
read only = no
writeable = yes
create mask = 0770
directory mask = 0770
valid users = rchallis echallis achallis mchallis
force group = users


[echallis]
	writeable = yes
	path = /echallis
	force group = users
	create mask = 0770
	comment = Emma Challis
	directory mask = 0770
	valid users = users,@users


[mchallis]
comment = Mark Challis
path = /mchallis
read only = no
writeable = yes
directory mask = 0770
create mask = 0770
valid users = rchallis mchallis
force group = users


[achallis]
comment = Annette Challis
path = /achallis
read only = no
writeable = yes
directory mask = 0770
create mask = 0770
valid users = rchallis achallis
force group = users


[public]
comment = Public Share
path = /shared/Public
read only = no
writeable = yes
directory mask = 0770
create mask = 0770
browseable = yes
valid users = echallis rchallis
force group = users


[webserver]
comment = Web Server
path = /var/www
read only = no
writeable = yes
directory mask = 0770
create mask = 0770
valid users = rchallis
```
Can you explain why you configured the shares in the manor you have?  Specifically why you created all those individual directories off of the / (root) directory.  What is the reasoning behind all the "valid users".  Normally the valid users are one or two users.  If more than that, the users are added to a common group such as the *users group*.  Using the [multimedia] share as an example, why do the individual users have to be added if they are all in one of the groups listed.

I think you should simplify the whole Samba share and Samba user arrangement.

---

### Post by Russell_Challis on 2015-07-25
Ok thanks for the advice. I am very new to samba sharing so was setting it up following tutorials off the web which have obvioustly been a bit wrong. On my local machine I a logged in using the root ubuntub account because that is the only account which alloes me in. I have set the partitions to mount on startup and thatbis working because my root account allows me to connect to the partitions. I will post the results of your requests when I return home in a few hours.

---

### Post by Russell_Challis on 2015-07-25
I just cannot get anything to work so I have completely wiped my server and started from a fresh. I have installed samba and that is it. I followed this guide as I used on my raspberry pi but I assume it will work with ubuntu as well... [http://www.howtogeek.com/139433/how-to-turn-a-raspberry-pi-into-a-low-power-network-storage-device/](http://www.howtogeek.com/139433/how-to-turn-a-raspberry-pi-into-a-low-power-network-storage-device/)

Attached in a screenshot of my config. The only option I have changed is "security = user" by removing the #.

I would like it to work with multiple users ideally but currently the only user which allows me to do anything is the root one so I would like to get it working so that non-root users can actually access folders. [IMG]http://russellchallis.co.uk/screenshot.png[/IMG]

---

### Post by bab1 on 2015-07-25
> **Russell_Challis said:**
> I just cannot get anything to work so I have completely wiped my server and started from a fresh. I have installed samba and that is it. I followed this guide as I used on my raspberry pi but I assume it will work with ubuntu as well... [http://www.howtogeek.com/139433/how-to-turn-a-raspberry-pi-into-a-low-power-network-storage-device/](http://www.howtogeek.com/139433/how-to-turn-a-raspberry-pi-into-a-low-power-network-storage-device/)

Raspian is based on Debian not Ubuntu.  There are differences.  What distro are you using for your Samba server?
> 
The only option I have changed is "security = user" by removing the #.
It's easier for me to help you if you post the output as text using the [noparse]```
 
``` [/noparse] blocks.  You can click on the [SIZE=5]**# **[/SIZE] icon at the top of the advanced editor and just past the ***text*** inside the blocks.  
> 
I would like it to work with multiple users ideally but currently the only user which allows me to do anything is the root one so I would like to get it working so that non-root users can actually access folders.
Multiple users is a fairly simple feature to configure.  It has more to do with the file system than Samba itself.Samba provides authentication (who are you?) whilst the file system provides the authorization (you can do that).  Most likely having root access only is because you are creating the file system directories as the local hosts root user.  I setup the local user accounts to match the remote user accounts on the client machines.  Then I create the file system for the data with those users having access.  Lastly I create the Samba share.

I don't understand this> "On my local machine I a logged in using the root ubuntub account because that is the only account which alloes me in."...When Ubuntu is installed, a user is created that has the ability to use sudo and there is no direct access to logging in as root.

Why are you using /media for the Samba shares?  Typically this location is for removable media that uses udev to provide the mounting routines.  Are you trying to share a USB connected device?

Post the output (separately and in text) of these commands```
df -h

sudo pdbedit -L

getent passwd | grep ^100
```...the last command has nothing to do with passwords.  Passwd is the name of the file that holds all the listings of the users.  I want to see what users you have that have user Id's that start with 100 (i.e. 1000, 1001, 1002, etc.)

Once I can see what we have I can advise you on the next steps (e.g. adding the users and group and configuring the file system of the server).

---

### Post by Russell_Challis on 2015-07-25
Sorry, I mean that I am logging in using the account that is setup during the installation of ubuntu server.

The output of the "df -h" command is
```

rchallis@challisnet:~$ df -h
Filesystem      Size  Used Avail Use% Mounted on
/dev/sda2        68G  1.1G   63G   2% /
udev            209M  4.0K  209M   1% /dev
tmpfs            87M  896K   86M   2% /run
none            5.0M     0  5.0M   0% /run/lock
none            216M     0  216M   0% /run/shm
/dev/sda10      241G  188M  228G   1% /multimedia
/dev/sda5        19G  176M   18G   1% /rchallis
/dev/sda6        19G  172M   18G   1% /echallis
/dev/sda7        19G  172M   18G   1% /achallis
/dev/sda8        19G  172M   18G   1% /mchallis
/dev/sda9        78G  634M   73G   1% /shared
rchallis@challisnet:~$



```

"sudo pbdedit -L"
```

rchallis@challisnet:~$ sudo pdbedit -L
[sudo] password for rchallis:
nobody:65534:nobody
master:1001:
russell:1002:
rchallis:1000:Russell Challis
rchallis@challisnet:~$



```

"getent passwd | grep ^100

It did not return anything and just went to the part where I can enter a command.

---

### Post by Vladlenin5000 on 2015-07-25
I think bab1 is under the impression you want multiple users to access a given share or shares, as I was in the beginning but it's the other way around, isn't it?
I mean, you have multiple _local_ users in that machine and you want the shares to work irrespective of the who's logged at that moment...

---

### Post by bab1 on 2015-07-25
> **Russell_Challis said:**
> Sorry, I mean that I am logging in using the account that is setup during the installation of ubuntu server.

Which can be any user.  The installer also adds that user to the sudoers group.  This is what I wanted to find out with the command *getent*.  I should have just asked for you to post the output of this```
getent passwd | grep 100
```  I usually just look at the entire file.  I was trying to limit the output to just the mortal users.  On my machine I get this ```
bill:x:1000:1000:Bill Baggins,,,:/home/bill:/bin/bash
eloise:x:1001:1001:Eloise Baggins,,,:/home/eloise:/bin/bash
```
> 

The output of the "df -h" command is
```

rchallis@challisnet:~$ df -h
Filesystem      Size  Used Avail Use% Mounted on
/dev/sda2        68G  1.1G   63G   2% /
udev            209M  4.0K  209M   1% /dev
tmpfs            87M  896K   86M   2% /run
none            5.0M     0  5.0M   0% /run/lock
none            216M     0  216M   0% /run/shm
[COLOR="#FF0000"]/dev/sda10      241G  188M  228G   1% /multimedia
/dev/sda5        19G  176M   18G   1% /rchallis
/dev/sda6        19G  172M   18G   1% /echallis
/dev/sda7        19G  172M   18G   1% /achallis
/dev/sda8        19G  172M   18G   1% /mchallis
/dev/sda9        78G  634M   73G   1% /shared[/COLOR]
rchallis@challisnet:~$
```
Wow! Why all the little partitions on the disk sda (see red above)?  You don't need separate partitions for the data to be isolated.  Where is the first partition (sda1).  The most efficient method would be to place everything on one partition.  Are you aware that each partition has a default *reserved space * of 5% that the users can't access for storage?

It would help if you can explain what your ultimate goal is.  if this is just for file sharing then we can limit the user home directory size.  On the other hand if you are going to provide a private share for each user then we should allow for larger home directories.  > 


"sudo pbdedit -L"
```

rchallis@challisnet:~$ sudo pdbedit -L
[sudo] password for rchallis:
nobody:65534:nobody
[COLOR="#800080"]**master:1001:**[/COLOR]
[COLOR="#FF0000"]russell:1002:
rchallis:1000:Russell Challis[/COLOR]
rchallis@challisnet:~$

```

Why the above in red?  What is the account in purple for?

I think we need to know how many real human users there are on you network.  The network clients can be Windows or Linux or Apple, but the accounts on those machines should have the same name and password as the accounts you will create on the Ubuntu/Samba server.  Then we can create private (a single user), semi private (a few users), and public (all the users on the network) shares.

---

### Post by bab1 on 2015-07-25
> **Vladlenin5000 said:**
> I think bab1 is under the impression you want multiple users to access a given share or shares, as I was in the beginning but it's the other way around, isn't it?
I mean, you have multiple _local_ users in that machine and you want the shares to work irrespective of the who's logged at that moment...
I don't think that at all.  Who is logged in to the server has nothing to do with what shares are available.  You do not need Samba shares as a local (to the Samba server) user 

What I do  believe is that the local users on Ubuntu should match the users on the various clients for easy administration.  If not you have to map the client user to the local Linux/Samba user.

To summarize:  You need Linux users and Samba users on the Ubuntu/Samba host and matching (in some way) users on the various clients to successfully manage the Samba shares and the underlying Linux file system.  it really is not a 1 to many or many to 1 situation here at all.

Its easy to have a Samba share that any user logged in can access *_without using guest access and lousy open to all permissions_* (e.g 777).

---

### Post by Russell_Challis on 2015-07-28
Hi,

Sorry I have been away for a few days. I will try to explain exactly what I would like to do and then it might make it a bit easier. Basically I would like to have individual "areas" where different users can store their personal data without everyone else being able to access it. I would then like 2 shared drives which everyone has access to expect a "visitor" account which I would like to only be able to access a completely different drive "public" but the other users can add and remove files like the 2 shared drives I already have. I would like 6 network users with the ability to have their own storage areas. What I would like is to be able to then login to different computers with the different usernames and passwords depending on the permissions which I grant the user. I only made the partitions because I couldn't think of any other way to make windows show the drives as varying in storage space depending on how much data the user has on their drive. 


Here is the result of the ```
 [COLOR=#000000][FONT=Ubuntu Mono]getent passwd | grep 100 
``` command[/FONT][/COLOR]
```

libuuid:x:100:101::/var/lib/libuuid:/bin/sh
rchallis:x:1000:1000:Russell Challis,,,:/home/rchallis:/bin/bash
master:x:1001:1001::/home/master:/bin/sh
russell:x:1002:1003::/home/russell:/bin/sh



```


I hope that all makes sense :)

---

### Post by bab1 on 2015-07-28
> **Russell_Challis said:**
> Sorry I have been away for a few days. I will try to explain exactly what I would like to do and then it might make it a bit easier. 

Basically I would like to have individual "areas" where different users can store their personal data without everyone else being able to access it.

Samba can do that easily.  There is a "share" that is designed just for that.  It shares only the logged in users private directory.  The share name is [homes] and you only need to create one [homes] share for all the users.  The Linux (Ubuntu in this case)  /home directory  is what is made available for the specific user  user.  In your case it could be either the user russell (/home/russel) or rchallis (/home/rchallis).  I normally use this scheme:  If the user normally logs in locally (to the host machine) I use a first name only username (e.g. russell) If the user never logs in locally then they are a network user and I use the first initial/last name (e.g rchallis).  This way I know if I am looking at a local user or a network user in the logs.  Questions on this aspect of the setup?
>  
I would then like 2 shared drives which everyone has access to expect a "visitor" account which I would like to only be able to access a completely different drive "public" but the other users can add and remove files like the 2 shared drives I already have. 

Samba does not share "drives".  In Linuxspeak a drive is a physical device (i.e the HDD or SSD or even a flash drive).  In Samba or Windows sharing you "share" a folder on a partition and Windows calls this a drive.  Of course they also call a partition a drive as in C: or D: drive.  It' simpler to call them by there Linux or Samba names.  You can certainly "share a directory (a folder) and all the sub-directories.  We can have private shares (the [homes] share described above) or semi-private shares where a few users can use a common directory or we can as you say have a "Public share that is open for all users.

I'm not at all clear what you mean by "shared drives".  Are these external HDD's with a single partition that you have shared the root folder?  Or perhaps these are just shared folders on the HDD that the OS and Samba are installed.
> 
I would like 6 network users with the ability to have their own storage areas. 
The [homes] share for the network users ...> 
What I would like is to be able to then login to different computers with the different usernames and passwords depending on the permissions which I grant the user.
Whatever these different computers are, if the user is going to use Samba, that user must also have a Linux account and a Samba account along with the login to the different computers.  These also are the network users...> 
I only made the partitions because I couldn't think of any other way to make windows show the drives as varying in storage space depending on how much data the user has on their drive.

Are you intending to limit the users storage space?  In Linux it is done by partition.  There is a tremendous price to pay for doing this.  Complexity and the loss of "reserved space" that each partition requires.  It's 5% of the partition size.  This is on each partition!

For a small network, be it home or a small business, I would just cap a single partition and advise the users or the situation. You are the sys admin so you can check the partition usage and see who is the "data hog". 
> 


Here is the result of the command
```
getent passwd | grep 100

libuuid:x:100:101::/var/lib/libuuid:/bin/sh
rchallis:x:1000:1000:Russell Challis,,,:/home/rchallis:/bin/bash
master:x:1001:1001::/home/master:/bin/sh
russell:x:1002:1003::/home/russell:/bin/sh

```


So we need to describe the network users vs the local users.  IMO only admins should be local users on a server.

We need to design the file system and partition setup that we will use for the server.  I keep all data at /srv/share and at /home if I'm using the [homes] share.

We need to reinstall Ubuntu or at the very least delete the extra partitions and resize the remaining partition.  My scheme for the drive you show would be like this```

/dev/sda1 = /   (20 GB if a Ubuntu desktop or 10GB if Ubuntu server)
/sda2 = swap   (2XRAM available if desktop or 4GB if server)
/sda3 = /home (120 GB for all /home 
/sda4 = /srv     (160 (or the space left) for the data storage
```
Note that this is just an estimate based upon what I see as a 300GB HDD and the needs you have expressed.

Why the separate /home and /srv?  Pure and simple.  It allows you to reinstall the OS without disturbing the users home directories or their data at /srv/share.

The users data is separated by Linux access and Samba authentication.

---

