---
title: "Configuring Samba"
date: 2012-12-29
forum: New to Ubuntu
---

### Post by 90Ninety on 2012-12-29
This is my first experience with Linux . I have installed Ubuntu 12.10 x64 Desktop , for the purpose of file sharing at home for starters . 


 I have followed this guide 
[http://www.bit-tech.net/bits/2007/06/05/build_your_own_server/4]("http://www.bit-tech.net/bits/2007/06/05/build_your_own_server/4")
I had got to page 4 ( File sharing) 

I have stumbled at a hurdle >  we change our working directory to those of Samba, by typing cd /etc/samba which simply means Change Directory to /etc/samba.
As soon as I enter 'cd /etc/samba' I get an error :
> bash: cd/etc/samba: No such file or directory

 I had googled the error and found someone with the same here:[http://https://answers.launchpad.net/ubuntu/+source/samba/+question/112878]("http://https://answers.launchpad.net/ubuntu/+source/samba/+question/112878")

On this latter link Jon (jcv) said on 2010-12-10:> I had this issue and got it working with the help of this link.[https://lists.ubuntu.com/archives/ubuntu-server-bugs/2008-July/004520.html]("https://lists.ubuntu.com/archives/ubuntu-server-bugs/2008-July/004520.html")


 Within that link was some commands as follows :
sudo touch /etc/samba/smb.conf
sudo dpkg-reconfigure samba-common
sudo dpkg-reconfigure windbind
sudo apt-get -f install

I opened terminal and typed in all the commands - 1,2 & 4 actually done something , 3 returned an error which I cannot remember 

Anyhow I returned ( In vain ) thinking this might have solved the  issue . However I still get the error:> bash: cd /etc/samba: No such file or directory

I have tried re-installing samba , though I cannot seem to be able to change into its directory , as mentioned in the Bit-tech guide ( in above link) 


I have since studied other guides and taken further steps , though , this guide seems most popular and many have referenced it on forums

---

### Post by Cheesemill on 2012-12-29
If you are actually typing
```
cd/etc/samba
```then that isn't a valid command, your missing the space after cd.
You should be typing
```
cd /etc/samba
```Also I really wouldn't use that guide if I were you, it was written in 2007 for a version of Ubuntu which is no longer supported (7.04) and an awful lot has changed in the world of Linux in the last five and a half years. Ubuntu 7.04 used Samba version 3.0.24 whereas 12.10 uses version 3.6.6.

Instead I would use the official documentation for your version of Ubuntu:
[https://help.ubuntu.com/12.10/serverguide/samba-fileserver.html](https://help.ubuntu.com/12.10/serverguide/samba-fileserver.html)

---

### Post by windscape on 2012-12-29
Hi,

There is an error in your command. The command should be ```
cd /etc/samba
```

---

### Post by 90Ninety on 2012-12-29
> 
You should be typing
```
cd /etc/samba
```

I am, just a typo in the post ( now edited )  



> Also I really wouldn't use that guide if I were you, it was written in 2007 for a version of Ubuntu which is no longer supported (7.04) and an awful lot has changed in the world of Linux in the last five and a half years. Ubuntu 7.04 used Samba version 3.0.24 whereas 12.10 uses version 3.6.6.



Instead I would use the official documentation for your version of Ubuntu:
[https://help.ubuntu.com/12.10/serverguide/samba-fileserver.html](https://help.ubuntu.com/12.10/serverguide/samba-fileserver.html)

Thanks , though I do not feel the official documentation is Noobie friendly , it doesn't break down the steps enough for the technically challenged imho . For example I am trying to decipher the steps  have stumbled on the very first configuration step.    . However  the first step deciphered ,from what I can gather :

First, edit the following key/value pairs in the [global] section of /etc/samba/smb.conf:
Erm in other words this means open terminal and type:
sudo  (hit enter)
/etc/samba/smb.conf (hit enter)


 I tried this and got permission denied :/

---

### Post by Cheesemill on 2012-12-29
If your using the Desktop version of Ubuntu you can use gedit to edit the file. Open a terminal and type:
```
gksudo gedit /etc/samba/smb.conf
```

This is the only file you have to edit to configure samba.

---

### Post by 90Ninety on 2012-12-29
Thanks Cheesemill 

 > Configuration step 1First, edit the following key/value pairs in the [global] section of /etc/samba/smb.conf:

   workgroup = EXAMPLE
   ...
   security = user
The security parameter is farther down in the [global] section, and is commented by default. Also, change EXAMPLE to better match your environment.

The security parameter is missing , should this be of concern, or should I move on to next step? 

 Also where is the Samba manual?

---

### Post by Cheesemill on 2012-12-29
> **90Ninety said:**
> The security parameter is missing , should this be of concern, or should I move on to next step?
It is there, I've just checked. It's under the authentication heading on line 102.
 > Also where is the Samba manual?
[http://www.samba.org/samba/docs/man/Samba-HOWTO-Collection/](http://www.samba.org/samba/docs/man/Samba-HOWTO-Collection/)

But I wouldn't recommend reading it, it's highly technical.

---

### Post by 90Ninety on 2012-12-29
> **Cheesemill said:**
> It is there, I've just checked. It's under the authentication heading on line 102.
 
.

Cool Ok  , so:
 *workgroup =  WORKGROUP   * [COLOR=Navy]Change to anything I like right ( in this case joegroup) [/COLOR]
 *Security = user*      [COLOR=Navy]so this I assume I change to my username (joe) ?  [/COLOR]
 so moving onto Step 2 
> Create a new section at the bottom of the file, or uncomment one of the examples, for the directory to be shared:         
  [share]     comment = Ubuntu File Server Share     path = /srv/samba/share     browsable = yes     guest ok = yes     read only = no     create mask = 0755 
[COLOR=Navy]Doh....  Can you decipher this or break it down a little ? Ok I have the samba.conf file open , so I assume you need to add the above text to the file no?[/COLOR]

---

### Post by Cheesemill on 2012-12-29
Correct, just add it to the end of the file.

---

### Post by 90Ninety on 2012-12-29
> **90Ninety said:**
> Cool Ok  , so:
 *workgroup =  WORKGROUP   * [COLOR=Navy]Change to anything I like right ( in this case joegroup) [/COLOR]
 *Security = user*      [COLOR=Navy]so this I assume I change to my username (joe) ?  [/COLOR]
 so moving onto Step 2 
[COLOR=Navy]Doh....  Can you decipher this or break it down a little ? Ok I have the samba.conf file open , so I assume you need to add the above text to the file no?[/COLOR]

So basically you add this text to the smb.conf
[share]
comment = Ubuntu File Server Share 
    path = /srv/samba/share
    browsable = yes
    guest ok = yes
    read only = no
    create mask = 0


[COLOR=Blue]though shouldn't I change it to [/COLOR]
[share]
comment = /[COLOR=Blue]media/disk1[/COLOR]
    path = /srv/samba/share
    browsable = yes
    guest ok = yes
    read only = no
    create mask = 0



Basically I want to share the Disk1 amongst my local computers

---

### Post by Cheesemill on 2012-12-29
The comment can be whatever you want, it's the path declaration that you need to change.

---

### Post by 90Ninety on 2012-12-29
> **Cheesemill said:**
> The comment can be whatever you want, it's the path declaration that you need to change.
OK the path has changed to my mounted EXT4 partitions (disk , disk1 named media) See attachment

---

### Post by BertN45 on 2012-12-29
> **90Ninety said:**
> OK the path has changed to my mounted EXT4 partitions (disk , disk1 named media) See attachment

What samba shows is that you have a folder "Media" on disk1, is that so? If not edit that line and ommit "/Media". That should give you access to the whole of disk1. With the newer releases it is not needed to change anything in smb.conf anymore.

Better stick to this Samba utility it is much easier to use then the command line and for home use it is perfect. I use it too and it is the only thing I use.

---

### Post by 90Ninety on 2012-12-29
I get another error when using the Samba GUI :

Some lines coudn't be understood while reading the configuration file/etc/samba/smb.conf. These 
52:     include = /etc/samba/dhcp.confmay be unkown configuration directives for samba plugins but could also be configuration errors 
Details :
52: Include = /etc/samba/dhcp.conf

I have tried to attach my samba config text for scrutiny . But you guessed got another error  

Thanks

---

### Post by 90Ninety on 2012-12-29
Right I've followed the official guide .See attached picture 

Basically I've managed to share the partitions using the Samba config . However how can I get my windoze pcs to talk with these partitions ? 

 I can enter my UBUntu's PC IP address in the browser - see attached 2nd  image 

Any suggestions ?

---

### Post by Cheesemill on 2012-12-30
You browse to file shares using Windows Explorer (the file manager), not Internet Explorer (the web browser).

---

### Post by Horbo on 2012-12-30
> **90Ninety said:**
> This is my first experience with Linux . I have installed Ubuntu 12.10 x64 Desktop , for the purpose of file sharing at home for starters . 


 I have followed this guide 
[http://www.bit-tech.net/bits/2007/06/05/build_your_own_server/4](http://www.bit-tech.net/bits/2007/06/05/build_your_own_server/4)
I had got to page 4 ( File sharing) 


Four pages?  Good grief.

Try this guide instead, short, and all gui: [http://ubuntuforums.org/showthread.php?t=1685718](http://ubuntuforums.org/showthread.php?t=1685718)

---

### Post by Morbius1 on 2012-12-30
Might I make a suggestion? You are following so many HowTo's that your smb.conf may be a mess. What would help is if you tell us what the current state of your system is and you can do that by posting the output of the following commands:
```
testparm -s
``````
net usershare info --long
```[COLOR=Blue]*Don't be alarmed if you get no response from the second command. *[/COLOR]

Some of the things you are quoting are incorrect like this one from the official Ubuntu documentation on Samba:
> Not all the available options are included in the default configuration file.  See the smb.conf man page or the          [Samba HOWTO Collection]("http://samba.org/samba/docs/man/Samba-HOWTO-Collection/") for more details.         First, edit the following key/value pairs in the [global] section of          /etc/samba/smb.conf:         

[LIST=1]
[*]      workgroup = EXAMPLE    ...    security = user 
                   The security parameter is farther down in the [global] section, and is commented by default.         Also, change EXAMPLE to better match your environment.
[/LIST]
Smb.conf is a file used to add to or override the default settings of Samba. It is not the default samba configuration itself. "security = user" is the default setting of samba which is why it's commented out with a "[COLOR=Blue]**#**[/COLOR]" in smb.conf ( [COLOR=Blue]and btw it's set to user not your user name[/COLOR] ). I didn't read through the whole thing to see what else is inaccurate so I think the best bet is just for you to tell us how things are currently set up.

---

### Post by 90Ninety on 2012-12-30
> **Horbo said:**
> Four pages?  Good grief.

Try this guide instead, short, and all gui: [http://ubuntuforums.org/showthread.php?t=1685718](http://ubuntuforums.org/showthread.php?t=1685718)

OK I followed the guide , maybe not correctly . Basically I copied the gateway address from my Windows PC , into the gateway address on server , is this correct ?

Please see attached file , it pictures both my Windows and linux network settings for scrutiny

---

### Post by 90Ninety on 2012-12-30
Ok with the above gudie ( thanks Horbo [http://ubuntuforums.org/showthread.php?t=1685718]("http://ubuntuforums.org/showthread.php?t=1685718"))

 Ican now access folders and drives on my sever from the Windows LAN PC's . I done this by entering the ip address of the Server into the windows PC -phew. 

 
 Now another hurdle , since I have changed the network settings on the server, I can no longer load webpages , please see attachment in last post to see what Im doing wrong . Any reason why I cannot now use the web on the server?

---

### Post by 90Ninety on 2012-12-30
> Might I make a suggestion? You are following so many HowTo's that your  smb.conf may be a mess. What would help is if you tell us what the  current state of your system is and you can do that by posting the  output of the following commands:
 	Code:
 	testparm -s 


[COLOR=Navy]Ok As below : 
[/COLOR]
```
testparm -s
Load smb config files from /etc/samba/smb.conf
rlimit_max: increasing rlimit_max (1024) to minimum Windows limit (16384)
Can't find include file /etc/samba/dhcp.conf
Processing section "[printers]"
Processing section "[print$]"
Processing section "[disk1]"
Processing section "[disk]"
WARNING: The security=share option is deprecated
Loaded services file OK.
Server role: ROLE_STANDALONE
[global]
    workgroup = JOEGROUP
    server string = Home server (Samba, Ubuntu)
    security = SHARE
    encrypt passwords = No
    map to guest = Bad User
    obey pam restrictions = Yes
    guest account = joe
    pam password change = Yes
    passwd program = /usr/bin/passwd %u
    passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .
    unix password sync = Yes
    syslog = 0
    log file = /var/log/samba/log.%m
    max log size = 1000
    dns proxy = No
    usershare allow guests = Yes
    usershare owner only = No
    panic action = /usr/share/samba/panic-action %d
    idmap config * : backend = tdb
    guest ok = Yes

[printers]
    comment = All Printers
    path = /var/spool/samba
    create mask = 0700
    printable = Yes
    print ok = Yes
    browseable = No

[print$]
    comment = Printer Drivers
    path = /var/lib/samba/printers
    valid users = joe
    read only = No

[disk1]
    comment = media/disk1
    path = /media/disk1
    valid users = joe
    read only = No
    create mask = 00

[disk]
    comment = Media disk0
    path = /media/disk
    read only = No

```
> Suggestion 2 
 	Code:
 	net usershare info --long 


```
joe@homeserve:~$ net usershare info --long
[media]
path=/media/disk1
comment=
usershare_acl=Everyone:F,
guest_ok=y

[disk]
path=/media/disk
comment=
usershare_acl=Everyone:F,
guest_ok=n

[Tubby]
path=/media/disk/Tubby
comment=
usershare_acl=Everyone:F,
guest_ok=n
```

---

### Post by 90Ninety on 2012-12-30
My Samba.conf file is included below for close scrutiny , is this set up right?

```
Sample configuration file for the Samba suite for Debian GNU/Linux.
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
    workgroup = joegroup

# server string is the equivalent of the NT Description field
    server string = Home server (Samba, Ubuntu)

# Windows Internet Name Serving Support Section:
# WINS Support - Tells the NMBD component of Samba to enable its WINS Server
#   wins support = no

# WINS Server - Tells the NMBD components of Samba to be a WINS Client
# Note: Samba can be either a WINS Server, or a WINS Client, but NOT both
;   wins server = w.x.y.z

# If we receive WINS server info from DHCP, override the options above. 
    include = /etc/samba/dhcp.conf

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
    security = share

# You may wish to use password encryption.  See the section on
# 'encrypt passwords' in the smb.conf(5) manpage before enabling.
    encrypt passwords = no

# If you are using encrypted passwords, Samba will need to know what
# password database type you are using.  
;    passdb backend = tdbsam

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
;    printing = cups
;   printcap name = cups

############ Misc ############

# Using the following line enables you to customise your configuration
# on a per machine basis. The %m gets replaced with the netbios name
# of the machine that is connecting

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
;    usershare max shares = 100

# Allow users who've been granted usershare privileges to create
# public shares, not just authenticated ones
    usershare allow guests = yes

    usershare owner only = false
    guest ok = yes
    guest account = joe

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
;    guest ok = no
;    read only = yes
    create mask = 0700

# Windows clients look for this share name as a source of downloadable
# printer drivers
[print$]
    comment = Printer Drivers
    path = /var/lib/samba/printers
;    browseable = yes
    writeable = yes
    valid users = joe
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

# The next two parameters show how to auto-mount a CD-ROM when the
#    cdrom share is accesed. For this to work /etc/fstab must contain
#    an entry like this:
#
#       /dev/scd0   /cdrom  iso9660 defaults,noauto,ro,user   0 0
#
# The CD-ROM gets unmounted automatically after the connection to the
#
# If you don't want to use auto-mounting/unmounting make sure the CD
#    is mounted on /cdrom
#
;   preexec = /bin/mount /cdrom
;   postexec = /bin/umount /cdrom

[disk1]
    comment = media/disk1
    path = /media/disk1
;    browseable = yes
    writeable = yes
    create mask = 0
    valid users = joe

[disk]
    path = /media/disk
    writeable = yes
;    browseable = yes
    guest ok = yes
    comment = Media disk0
```

---

### Post by Morbius1 on 2012-12-30
I actually see may things that are wrong with it but you claim it works so I would leave it alone ;)

My theory is that these two mistakes cancelled each other out:
> 
security = SHARE
encrypt passwords = NoNo one still living knows how share level security works though so it's just a guess on my part.

Since you followed 2 ( maybe 3 ) different howto's you have multiple shares using 2 different samba methods on the same target folder:

This is a classic samba share. It's accessible and writeable only to the user joe:
> [disk1] 
    comment = media/disk1     
path = /media/disk1 
;    browseable = yes     
writeable = yes     
create mask = 0     
valid users = joeThis is a Samba Usershare ( created through the file manager ). It's accessible and writeable to everyone and your Aunt Agnes:
> [media] 
path=/media/disk1 
comment= 
usershare_acl=Everyone:F, guest_ok=y2 different share names however so Samba will honor your wishes to both but not exactly sure what your intent is on the target directory: /media/disk1.

Anyway, this was more of a rant really. You claim this all works so "don't fix it if it ain't broke" I always say. You seem to have bigger problems if you can't connect to the internet. Sorry , can't help you with that.

---

### Post by BertN45 on 2012-12-30
What all of this proves is: Never start using complex CLI instructions, if you have no clue, what you are doing. Insist on the use of the GUI in that case. If you had stayed with the Samba utility, none of this would have been necessary.  

I have 45 of years of experience with the CLI, starting from the IBM-360 main frame days. Nowadays even I, if I see a CLI instruction for Linux, that is longer then 1 page, I skip it as too complex and retarded and continue to search for simpler GUI solutions. Often there is a small program or script available that can assist you in that work like e.g. the Samba Utility. 

There is an unhealthy habit in the Ubuntu user community to brag about the use of the CLI. It is old fashioned and any normal user should try to avoid it, since its use is only justifiable in a limited number of cases. 

For any new user, clearly specify your desktop and version number and don't use any CLI that is more then a few command lines. Remember some of the people responding do not really master the CLI either and just repeat something that worked in their circumstances. Many of those prescriptions people refer to are based on releases that are two or more years old and if you can't understand it, you might mess up your system completely.

Since the stone age of computing the big problem with the CLI have been the typos made by you or the typos made in the prescription given to you.

---

### Post by BertN45 on 2012-12-30
> **90Ninety said:**
> Ok with the above gudie ( thanks Horbo [http://ubuntuforums.org/showthread.php?t=1685718]("http://ubuntuforums.org/showthread.php?t=1685718"))

 Ican now access folders and drives on my sever from the Windows LAN PC's . I done this by entering the ip address of the Server into the windows PC -phew. 

 
 Now another hurdle , since I have changed the network settings on the server, I can no longer load webpages , please see attachment in last post to see what Im doing wrong . Any reason why I cannot now use the web on the server?

A web issue is completely independent from SAMBA file server. Don't touch smb.conf anymore. If you want http pages to be displayed [COLOR="Red"]from[/COLOR] your server you have to install the Apache web server and ask for help with that. I propose you open a separate thread in that case.

---

### Post by BertN45 on 2012-12-30
If you can't load the internet pages [COLOR="Red"]onto[/COLOR] your server, you have probably made an error at the moment you defined the static addresses, see my attachement. Be aware that there is a small chance your router might re-assign the same static address through DHCP again to another PC. It depends on the design of the wifi router. If that ever happens, you can change the range of DHCP addresses the router assigns and make sure your static address(es) are outside that range.

I expect the issue is with the DNS addresses, I use the Google DNS server 8.8.8.8 and my wifi router DNS server.

Don't look at my somewhat unusual net-mask.

---

### Post by Horbo on 2012-12-30
> **90Ninety said:**
> Ok with the above gudie ( thanks Horbo [http://ubuntuforums.org/showthread.php?t=1685718](http://ubuntuforums.org/showthread.php?t=1685718))

 Ican now access folders and drives on my sever from the Windows LAN  PC's . I done this by entering the ip address of the Server into the  windows PC -phew. 
 
 Now another hurdle , since I have changed the network settings on the  server, I can no longer load webpages , please see attachment in last  post to see what Im doing wrong . Any reason why I cannot now use the  web on the server?

You have used 192.168.0.1  (your gateway) as your DNs server on the samba server.
However  (assuming it is correct) the windows machine has 192.168.4.100 and  192.168.8.100 as DNS servers.  Seems a little unusual to me, but try changing the DNS server setting (but leave the gateway as is) on the samba server to 192.168.4.100 and see if you can open web pages then.

> **BertN45 said:**
> What all of this proves is: Never start using complex CLI instructions, if you have no clue, what you are doing. Insist on the use of the GUI in that case. If you had stayed with the Samba utility, none of this would have been necessary.  

I have 45 of years of experience with the CLI, starting from the IBM-360 main frame days. Nowadays even I, if I see a CLI instruction for Linux, that is longer then 1 page, I skip it as too complex and retarded and continue to search for simpler GUI solutions. 

I don't have 45 years experience, but I do have a degree in computer science, and I am the same: any solution requiring dozens of CLI commands gets ignored by me - I just can't be bothered.

---

### Post by 90Ninety on 2012-12-31
> There is an unhealthy habit in the Ubuntu user community to brag about  the use of the CLI. It is old fashioned and any normal user should try  to avoid it, since its use is only justifiable in a limited number of  cases. Very true , people seem to get an ego using CLI.. 

 Right next hurdle . I now have my Ubuntu 12.10 desktop server networked and talikng with the windows client machines . I went back a few steps , changed connection mode to DCHP (automatic) and it seems to have fixed itself . I will refrain from using manual/static IP settings for now 

 At the moment I have a securtiy issue , the only  way I can  access my server is buy checking the 'Allow guest access' option on the drives . However if I uncheck and try to access  the same drives again , I am prompted for my login details , which every time I enter , windoze tells me its the wrong details , Iam not too worried though .. However why arent my log in details working? I have two user accounts on the Ubuntu machine and have tried my log in details many times , for folder access what gives?

---

### Post by Morbius1 on 2012-12-31
> the only  way I can  access my server is buy checking the 'Allow guest  access' option on the drives . However if I uncheck and try to access   the same drives again , I am prompted for my login details , which every  time I enter , windoze tells me its the wrong details , Iam not too  worried though .. However why arent my log in details working? I have  two user accounts on the Ubuntu machine and have tried my log in details  many times , for folder access what gives?     Two different sets of credentials.

Let's say you have a user on your Linux server box called: morbius. That user can log into the local box itself with username = morbius and a password = morbiuspw.

The Samba server knows nothing of that user or password so you need to add morbius to the samba password database by using this command:
```
sudo smbpasswd -a morbius
```It will ask you for sudos's password first then it will ask you for the password you want to give morbius for samba purposes. It can be the same password morbius would use to log into the box itself or it can be something different - that's up to you since you are the System Administrator.

[COLOR=Blue]*EDIT: Since the conversation has moved somewhat to CLI vs GUI I apologize for offering a CLI solution for this issue but It's the one I'm more comfortable with personally. And there is one other thing I would point out:*[/COLOR]

[COLOR=Blue]*The OP is using 2 different methods to create samba shares. Some shares are in /etc/samba/smb.conf and some shares are in /var/lib/samba/usershares. Both will work but as you can see above they might conflict with one another. **If you only use** the Nautilus method to create shares then adding users to the samba database can only be done via CLI*[/COLOR] [COLOR=Blue]*since the Nautilus method has no way of doing that.*[/COLOR]

---

### Post by 90Ninety on 2012-12-31
Thanks Morbius , you're cool 

 May aswell close this thread , as I will open an unrelated one next 


Thanks guys , Ubuntu's really pushed me out the comfort zone but I am beginning to see its potential

---

### Post by BertN45 on 2013-01-01
Don't apologize since the smbpasswd is one of the rare occasions where you need the CLI ):P

---

### Post by 90Ninety on 2013-01-17
Oh for the love of god , I am having a love hate relationship with Ubuntu . Allmost losing my hair now 

 I decded to re-install Ubuntu , due to a hardware upgrade and have stumbled at this hurdle again 


 All  im trying to acheive, is to share folders over the Lan on my Ubuntu 12.10 x64 machine , so my windoze PCs can access my files

Now I managed to install Samba , however the GUI will Not launch , I double click it and nothing happens 

 I have run opened and added shares (texts/scripts) at the bottom of my samba.conf file . However My windoze pc cannot open the share files . 
I've also tried changing the permissions on folders and partitions but errors appear, I get the 'Could not change the permissions of folder'  error 

 This is supposed to be simple and I am just finding this hard 

Any suggestions ? I have followed the guides and done the steps , please help

---

### Post by Morbius1 on 2013-01-18
I really don't know why you are following any guides. All you needed to do is:

[1] Make believe you were sitting in front of a WinXP machine.
[2] Open your file manager, right click a folder, and select "Sharing Options"
If you didn&#8217;t have Samba installed it would have installed it for you.

Anywho, by now you  should realize what you need to do next ..... Please post the output of the following commands:
```
testparm -s
``````
net usershare info --long
```

---

### Post by 90Ninety on 2013-01-19
> I really don't know why you are following any guides. All you needed to do is:

[1] Make believe you were sitting in front of a WinXP machine.
[2] Open your file manager, right click a folder, and select "Sharing Options"
If you didn’t have Samba installed it would have installed it for you.
 I want to share a drive partiton though I cannot even create a folder on the EXt 4 partition for some reason , neither can I get to any kind of Sharing options . I am confused .  When I right click the drive , go to properties I sharing options  ,however all is not smooth - See attached pictures 

> Please post the output of the following commands:
     Code:
     testparm -s 
     Code:
     net usershare info --long 
           testparm -s;

```
joe@Homeserve:~$ testparm -s
Load smb config files from /etc/samba/smb.conf
rlimit_max: increasing rlimit_max (1024) to minimum Windows limit (16384)
Processing section "[printers]"
Processing section "[print$]"
Processing section "[share]"
Processing section "[share]"
Processing section "[sharedfolder]"
Loaded services file OK.
WARNING: 'workgroup' and 'netbios name' must differ.
Server role: ROLE_STANDALONE
[global]
    workgroup = HOMESERVE
    server string = %h server (Samba, Ubuntu)
    map to guest = Bad User
    obey pam restrictions = Yes
    pam password change = Yes
    passwd program = /usr/bin/passwd %u
    passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .
    unix password sync = Yes
    syslog = 0
    log file = /var/log/samba/log.%m
    max log size = 1000
    dns proxy = No
    usershare allow guests = Yes
    panic action = /usr/share/samba/panic-action %d
    idmap config * : backend = tdb

[printers]
    comment = All Printers
    path = /var/spool/samba
    create mask = 0700
    printable = Yes
    print ok = Yes
    browseable = No

[print$]
    comment = Printer Drivers
    path = /var/lib/samba/printers

[share]
    comment = Big Drive
    path = /dev/sda4
    read only = No
    create mask = 0755
    guest ok = Yes

[sharedfolder]
    path = /home/joe/sharedfolder
    valid users = USERNAME
    read only = No
    guest ok = Yes
joe@Homeserve:~$ 

```The following command did nothing , just a blinking cursor:confused:
net usershare info --long

---

### Post by Morbius1 on 2013-01-19
[1] Sharing Options looks like the attachment below. If you don't have it's because you don't have something installed which should have been placed there by default when you originally installed your system. Don't worry about it - at this point it's not worth fixing.

[2] You can't share /dev/sda4. This will never work:
> [share]     
comment = Big Drive     
path = /dev/sda4     
read only = No     
create mask = 0755     
guest ok = YesIt's not a sharable entity. You have to mount the partition to a real mount point. This brings up a whole other set of questions:

Please post the output of each of the following commands:
```
cat /etc/fstab
sudo blkid -c /dev/null
mount
```

---

### Post by 90Ninety on 2013-01-19
joe@Homeserve:~$ cat /etc/fstab
UUID=cac8f8f3-62bc-448d-ba11-d516771cd456 / ext4 defaults 0 1
UUID=965799b0-b889-4163-8fe1-e33c6be5b2b0 swap swap sw 0 0
joe@Homeserve:~$ sudo blkid -c /dev/null
[sudo] password for joe: 
/dev/sda1: UUID="cac8f8f3-62bc-448d-ba11-d516771cd456" TYPE="ext4" 
/dev/sda3: UUID="2d06b42c-15b5-4063-b1cf-b8b3b8f473a6" TYPE="ext4" 
/dev/sda4: UUID="2006fbe6-1993-4c74-b7d5-80197cafbdb0" TYPE="ext4" 
/dev/sda5: UUID="965799b0-b889-4163-8fe1-e33c6be5b2b0" TYPE="swap" 
joe@Homeserve:~$ mount
/dev/sda1 on / type ext4 (rw)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
udev on /dev type devtmpfs (rw,mode=0755)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
tmpfs on /run type tmpfs (rw,noexec,nosuid,size=10%,mode=0755)
none on /run/lock type tmpfs (rw,noexec,nosuid,nodev,size=5242880)
none on /run/shm type tmpfs (rw,nosuid,nodev)
none on /run/user type tmpfs (rw,noexec,nosuid,nodev,size=104857600,mode=0755)
gvfsd-fuse on /run/user/joe/gvfs type fuse.gvfsd-fuse (rw,nosuid,nodev,user=joe)
joe@Homeserve:~$

---

### Post by Morbius1 on 2013-01-19
Let's say you really want to share the partition designated as /dev/sda4.

[1] Create a mount point for sda4 to live in:
```
sudo mkdir /media/Data
```[2] Add a line to the end of /etc/fstab:
```
UUID=2006fbe6-1993-4c74-b7d5-80197cafbdb0 /media/Data ext4 defaults,noatime 0 2
```[3] You do not have the partition mounted so use the following command which will test for errors and if there are none mount /dev/sda4 to /media/Data:
```
sudo mount -a
```[4] Now Fix your smb.conf from this:
> [share]     
comment = Big Drive     
[COLOR=Blue]**path = /dev/sda4     **[/COLOR]
read only = No     
create mask = 0755     
guest ok = YesTo This:
> [share]     
comment = Big Drive     
[COLOR=Blue]**path = /media/Data**[/COLOR]
read only = No     
create mask = 0755     
guest ok = YesAnd restart samba:
```
sudo service smbd restart
```Whether or not you or the samba client guest can actually write to the mounted partition is entirely dependant of what the Linux permissions are on the mounted partition. You can find that out by running the following command:
```
 ls -dl /media/Data
```
[COLOR=Blue]*Don't do that if the partition is not mounted. Do that only after the partition is mounted. *[/COLOR]

---

### Post by quarkhirad on 2013-01-19
just wanted to say thanks guys you have saved me a tun of searching and reading.

Just a friendly suggestion. I think someone should right a manual for samba like the one given in [https://help.ubuntu.com/12.10/serverguide/samba-fileserver.html](https://help.ubuntu.com/12.10/serverguide/samba-fileserver.html) but not so technical a more newbie thing.Though i got through it due to my courses in btech.

---

### Post by 90Ninety on 2013-01-19
Ok I had done the steps , though I do not think this is the solution . It seems I do not own permissions of the partitions (for whatever reason) 
As you can see from the attached  screen shot on the media/joe/1.2TB partition  properties window , permissions tab 'you are not the owner , so you cannot change the permissions '( *strangely the  code 2006fbe6-1993-4c74-b7d5-80197cafbdb0 given to the partition*) 
This is my second Ubuntu installation in a week, ive spent hours scouring the net for soluton for file sharing and Im still none the wiser 

 how do I get the permissions back ?

---

### Post by Morbius1 on 2013-01-20
> Ok I had done the steps , though I do not think this is the solutionIf you had done those steps then this line is in fstab:
> UUID=2006fbe6-1993-4c74-b7d5-80197cafbdb0 /media/Data ext4 defaults,noatime 0 2And this is your share definition in /etc/samba/smb.conf:
> [share]     
comment = Big Drive     
[COLOR=Blue]**path = /media/Data**[/COLOR]
read only = No     
create mask = 0755     
guest ok = Yes                      You have either run the "sudo mount -a" and "sudo service smbd restart " commands or in your case rebooted the box.
> As you can see from the attached  screen shot on the media/joe/1.2TB  partition  properties window , permissions tab 'you are not the owner ,  so you cannot change the permissions '( *strangely the  code 2006fbe6-1993-4c74-b7d5-80197cafbdb0 given to the partition*) 

[1] There should be no /media/joe/1.2TB it's now /media/Data - See above. You either didn't do the steps above, didn't restart the services, or didn't reboot your box.

[2] The permissions issue was already addressed:
> Whether or not you or the samba client guest can actually write to the  mounted partition is entirely dependant of what the Linux permissions  are on the mounted partition. You can find that out by running the  following command:
          ```
 ls -dl /media/Data
```[COLOR=Blue]*Don't do that if the partition is not mounted. Do that only after the partition is mounted. *[/COLOR]
[3] The screenshot shows you trying to share the partition using the sharing tab - you no longer have to do that it's already shared in smb.conf.

[COLOR=Blue]*If I wanted to be reckless I would suggest doing a :*[/COLOR]
```
sudo chown joe /media/Data
```But I no longer know:

** If it's really mounted to /media/Data as you stated above.
** What's in sda4 - If it's another operating system a chown will mess everything up.

---

### Post by 90Ninety on 2013-01-24
> If you had done the steps then this line is in fstab:
     Quote:
                                                 UUID=2006fbe6-1993-4c74-b7d5-80197cafbdb0 /media/Data ext4 defaults,noatime 0 2                      
          
[SIZE=4][COLOR=Red]Correct Checked :D
[/COLOR][/SIZE]
> And this is your share definition in /etc/samba/smb.conf:
     Quote:
                                                 [share]     
comment = Big Drive     
[COLOR=Blue]**path = /media/Data**[/COLOR]
read only = No     
create mask = 0755     
guest ok = Yes                      
[1]

[SIZE=4][COLOR=Red]Correct Checked :p[/COLOR][/SIZE]

> You have either run the "sudo mount -a" and "sudo service smbd restart " commands or in your case rebooted the box.
 [SIZE=4][COLOR=Red]Correct Checked
[/COLOR][/SIZE]> There should be no /media/joe/1.2TB it's now /media/Data - See above.  You either didn't do the steps above, didn't restart the services, or  didn't reboot your box.[SIZE=4][COLOR=Red]Correct Checked[/COLOR][/SIZE]
> Whether or not you or the samba client guest can actually write to the   mounted partition is entirely dependant of what the Linux permissions   are on the mounted partition. You can find that out by running the   following command:
               Code:
      ls -dl /media/Data
[SIZE=4][COLOR=Red]After entering the above [SIZE=4]c[/SIZE]ode into terminal , I get the following output : 
drwxr-xr-x 3 joe root 4096 Jan 16 23:18 /media/Data

Which means nothing to me unfortunatel[SIZE=4]y , [SIZE=4][SIZE=4]a[/SIZE]p[SIZE=4]a[/SIZE]rt from that I am the owner ;)
[/SIZE][/SIZE][/COLOR][/SIZE]
> [SIZE=4][COLOR=Red][SIZE=4][SIZE=4][SIZE=2][COLOR=Black]The screenshot shows you trying to share the partition using the sharing  tab - you no longer have to do that it's already shared in smb.conf.[/COLOR][/SIZE]
[/SIZE][/SIZE][/COLOR][/SIZE]
[SIZE=4][COLOR=Red][SIZE=4]This is odd , it seems the GUI [SIZE=4]doesn&#8217;t[/SIZE] [SIZE=4]talk to samb[SIZE=4]a , as the GUI simply doesn't allow [SIZE=4]me to[/SIZE] [SIZE=4]ch[SIZE=4]ange the permissions. More [SIZE=4]importantly[/SIZE] [SIZE=4]h[/SIZE]owever I am the owner [/SIZE][/SIZE][/SIZE][/SIZE][/SIZE][/COLOR][/SIZE]

---

### Post by 90Ninety on 2013-01-24
Morbius - Thanks very much 

  I am now able to network my Windows pc to my ubuntu pc , now I just need to get around the permissions issue , I can share my files and folders but cannot create folders or manipulate my ubuntu server from my windows PC . Ideally i'd like to save my windoze stuff onto my Ubuntu PC . However I get a permissions issue , which I do not  mind entirely  , however I cannot get past it as Im not even prompted for samba or Ubuntu security  details 

How can I allow the Windows users to write and change folders on Ubuntu file server/desktop ? I would like users to use a password when doing so , for security measures 


Thanks

---

### Post by Morbius1 on 2013-01-24
This is your share definition:
> [share]     
comment = Big Drive     
path = /media/Data
read only = No     
create mask = 0755     
guest ok = Yes                                            These are the permissions:
> drwxr-xr-x 3 joe root 4096 Jan 16 23:18 /media/DataThe last 3 characters ( r-x ) tell you what others ( which corresponds to a samba guest ) can do. They can read ( r ) and open the folder ( x ) but they cannot write ( - ).

You have 2 options:

[1] Change permissions on the target folder to allow others to write:
```
chmod 777 /media/Data
```[2] Change the share to make everyone on the network appear to be you - for that share anyway. This solves a number of permissions issues since all saved files will be owned by "joe":
> [share]     
comment = Big Drive     
path = /media/Data
read only = No     
[COLOR=Blue]**force user = joe**[/COLOR]
guest ok = Yes                                            Again, unfortunately every change to smb.conf requires a samba restart so your network will have a fit for a few minutes until you are able to connect again so be patient:
```
sudo service smbd restart
```

---

### Post by 90Ninety on 2013-03-18
I'm back , I eventually got the connection working, had been using it for allmost two months . However today for whatever reason I am unable to connect to my Ubuntu Desktop/Fileserver machine  Any ideas?

---

