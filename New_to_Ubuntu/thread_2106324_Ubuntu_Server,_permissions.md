---
title: "Ubuntu Server, permissions"
date: 2013-01-18
forum: New to Ubuntu
---

### Post by Craig71 on 2013-01-18
Hi guys, I'm a real newbie here, and an almost total Linux virgin.

I'm trying to set up a home server using Ubuntu Server 12.10.

I have installed it fine, and am able to ssh into it from my main (windows 7) pc.

I've installed Samba and Webmin, but when I access the shared directories from windows, I can't make new folders, or copy files etc. I've googled until I really don't understand anything of what I'm reading now, and I'm after either an idiot-proof guide to setting this up, or help to understand what I've done wrong.

Any help is much appreciated.

---

### Post by WASHAD on 2013-01-18
I'm not an Ubuntu expert by any means, and what I am going to recommend might earn me some dirty looks, but here goes. 

You may have a permissions problem on the folder that you want to share. 

So, from SSH, can you determine the location of the folders that you want to share? If so, use the cd command to get you to the folder just above the share folder. For example, if I am sharing "/home/steve/documents/shared_folder", then I would "cd /home/steve/documents"

Once there, type the command "chmod -R 777 shared_folder". That is going to give EVERYONE permission to do anything they like with that folder and everything within that folder. See if that fixes your problem. If so, report back and we can talk giving the shared folder the appropriate permissions. 

Cheers.

---

### Post by CharlesA on 2013-01-18
> **WASHAD said:**
> I'm not an Ubuntu expert by any means, and what I am going to recommend might earn me some dirty looks, but here goes. 

You may have a permissions problem on the folder that you want to share. 

Agreed.

You can check the samba logs in /var/log/samba/ to see what the problem is.

---

### Post by Craig71 on 2013-01-19
Cheers guys, I've tried the chomd command - no joy.

To be honest, I've got myself into such a mess now with the various test folders & users I've set up, I'm very confused. I think I'm going to delete the shares I have done & start from scratch. I've read somewhere that Webmin shouldn't be used to set up samba shares - is this right, and can anyone point me in the direction of a good, foolproof guide?

I had been following this guide:[http://linuxhomeserverguide.com/](http://linuxhomeserverguide.com/)

---

### Post by CharlesA on 2013-01-19
That's a decent page, but I had a hell of a time setting up Samba originally, and I wrote up a guide to it. You can find it [here]("http://charlesa.net/tutorials/debian/debiansamba.php").

I gave up on using Webmin back in 9.04, as I found it was easier to just manage stuff via SSH, but that is just me, of course. :p

The log should tell you what the problem is.

---

### Post by Craig71 on 2013-01-19
Thanks dude. How do I view the log file? I get the message that '/var/log/samba is a directory'

---

### Post by CharlesA on 2013-01-19
Any text editor would allow you to view the logs.

```
ls /var/log/samba
```

```
nano /var/log/samba/somefile
```

Tail works too.

```
tail /var/log/samba/somefile
```

---

### Post by Craig71 on 2013-01-20
Hi mate, strangely it appears to be working now - sort of anyway. I can make folders, copy files over, and indeed play files from the server from either of the two Win7 pc's on the network. I also have a Raspberry Pi running XBMC that for some reason just refuses to connect. It sees the Samba shares, but asks for a username & password. I've tried every combination of the Samba users/passwords in there, but nothing works.

Here is the out put from that log: 

> cores            log.192.168.1.6  log.craig-pc  log.nmbd      log.raspbmc
log.192.168.1.4  log.192.168.1.8  log.media-pc  log.openelec  log.smbd


---

### Post by Craig71 on 2013-01-21
Anyone? It's driving me crazy, and I don't have the knowledge to work out what I've done wrong!

---

### Post by CharlesA on 2013-01-21
Usernames and passwords are case sensitive. How are you trying to connect from the Pi?

---

### Post by Craig71 on 2013-01-21
I'm only using lower case logins & passwords. I'm using Raspbmc media player on the Pi, through a homeplug network. The Pi can 'see' the share, but won't accept any combinations of the users/passwords I've created.

I had previously streamed from the main windows 7 pc to the Pi with no problems.

---

### Post by CharlesA on 2013-01-21
Try using the IP address and inputting a workgroup if you do not have one already set.

[http://choorucode.com/2012/08/18/how-to-access-windows-shared-folder-from-raspbmc/](http://choorucode.com/2012/08/18/how-to-access-windows-shared-folder-from-raspbmc/)

You could also try it from another *nix box and see if it'll connect.

---

### Post by Craig71 on 2013-01-22
Hi mate, and thanks for your continued help.

I've tried the above method, no joy unfortunately. It's very odd, as the other instance of XBMC I have - on a Win7 machine, connects easily & doesn't even ask for a username or passsword.

---

### Post by CharlesA on 2013-01-22
Are you sure you didn't have the other one set up for guest access? I do not believe that prompts for a username/password.

---

### Post by Craig71 on 2013-01-23
Sorry mate, I'm really confused now - how do I check that?

Also, my intention is to put in a bigger hard drive into the server and transfer all my media onto that - the one in there at the moment is only a little 80gb one.

Would it be easier to do that first - and set it up so that anyone on the local network can do anything to it?

---

### Post by CharlesA on 2013-01-23
That setting would be the /etc/samba/smb.conf

As far as installing a larger drive, you should probably do it before you start messing with configuration.

Will you be using the new drive as a storage drive or as the OS drive?

---

### Post by Morbius1 on 2013-01-23
We need someplace to start. Please post the output of the following command:
```
testparm -s
```

---

### Post by Craig71 on 2013-01-23
Hi guys, here is the output of the testparm -s command: 

CharlesA - I'll be using the new disc purely as a media disc. i was hoping to get an understanding of samba sharing first, but hey ho. I'll be getting the new disc tomorrow, but I'd still like to know what I've done wrong, and how to make sure the new disc is set up right. 



[HTML]craig@server:~$ testparm -s
Load smb config files from /etc/samba/smb.conf
rlimit_max: increasing rlimit_max (1024) to minimum Windows limit (16384)
Processing section "[printers]"
Processing section "[print$]"
Processing section "[mediaonserver]"
WARNING: The security=share option is deprecated
Loaded services file OK.
WARNING: You have some share names that are longer than 12 characters.
These may not be accessible to some older clients.
(Eg. Windows9x, WindowsMe, and smbclient prior to Samba 3.0.)
Server role: ROLE_STANDALONE
[global]
        netbios name = SERVERMAIN
        server string = %h server (Samba, Ubuntu)
        security = SHARE
        map to guest = Bad User
        obey pam restrictions = Yes
        pam password change = Yes
        passwd program = /usr/bin/passwd %u
        passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .
        unix password sync = Yes
        syslog = 0
        log file = /var/log/samba/log.%m
        max log size = 1000
        add machine script = /usr/sbin/useradd -s /bin/false -d /home/nobody
        dns proxy = No
        wins support = Yes
        usershare allow guests = Yes
        panic action = /usr/share/samba/panic-action %d
        winbind use default domain = Yes
        winbind trusted domains only = Yes
        idmap config * : backend = tdb
        path = /media/MediaShare
        read only = No

[printers]
        comment = All Printers
        path = /var/spool/samba
        read only = Yes
        create mask = 0700
        printable = Yes
        print ok = Yes
        browseable = No

[print$]
        comment = Printer Drivers
        path = /var/lib/samba/printers
        read only = Yes

[mediaonserver]
        comment = mediaonmainserver
        valid users = craigtest, craigpc, craig, pi
        guest ok = Yes
[/HTML]

---

### Post by CharlesA on 2013-01-23
> **Craig71 said:**
> 
CharlesA - I'll be using the new disc purely as a media disc. i was hoping to get an understanding of samba sharing first, but hey ho. I'll be getting the new disc tomorrow, but I'd still like to know what I've done wrong, and how to make sure the new disc is set up right.

You should be fine. The only thing you would really need to change is where samba is sharing files from but that is an easy fix.

According to your smb.conf file you have guest access enabled for that share, but I do not know if it will work the way you want it to.

---

### Post by Craig71 on 2013-01-23
So there's nothing obvious that's making the Pi unable to connect? Weird.

---

### Post by Morbius1 on 2013-01-23
You have an unconventional smb.conf for sure - winbind references , You set it up to be a WINS server, SHARE level security instead of the default USER, and the path is in the [global] section for some reason:
> 
winbind trusted domains only = Yes 
idmap config * : backend = tdb [COLOR=Blue]
path = /media/MediaShare[/COLOR] 
read only = NoAnywho, What's the permissions of the target folder:
```
ls -dl /media/MediaShare
```

---

### Post by Craig71 on 2013-01-23
Unconventional? God knows how I've managed to mess that up, I just wanted something simple! (can you tell I don't really know what I'm doing?)

anyway, the output of that last command is: 

[HTML]drwxrwxrwx 7 root root 4096 Jan 20 08:26 /media/MediaShare
[/HTML]

---

### Post by Morbius1 on 2013-01-23
This one is a head scratcher isn't it.

Um ... Since it's in /media I'm assuming it's a mount point for a partition? Is it actually mounted?
This command should tell you if it mounted to /media/MediaShare
```
mount
```

---

### Post by CharlesA on 2013-01-23
> **Morbius1 said:**
> This one is a head scratcher isn't it.


Indeed. I am puzzled with it too. Worst case, roll back to a default smb.conf and reconfigure it manually.

---

### Post by Craig71 on 2013-01-23
I'm lost, I'll be honest: 

[HTML]/dev/mapper/server-root on / type ext4 (rw,errors=remount-ro)
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
/dev/sda1 on /boot type ext2 (rw)
/dev/mapper/server-MediaShare on /media/MediaShare type ext4 (rw)
[/HTML]

---

### Post by dannyboy79 on 2013-01-23
are you using ecryptfs or LVM? its showing /dev/mapper

also, with SHARE level security it's more tricky then USER level security because In share-level security, the client authenticates itself separately for each share. It sends a password along with each tree connection request (share mount), but it does not explicitly send a username with this operation. The client expects a password to be associated with each share, independent of the user. This means that Samba has to work out what username the client probably wants to use, because the username is not explicitly sent to the SMB server. Where the list of possible user names is not provided, Samba makes a UNIX system call to find the user account that has a password that matches the one provided from the standard account database. On a system that has no name service switch (NSS) facility, such lookups will be from the /etc/passwd database.

---

### Post by Craig71 on 2013-01-23
I'm 'using' LVm through webmin. Though I don't really know if this is best for me, I had just blindly followed this guide: [http://linuxhomeserverguide.com/](http://linuxhomeserverguide.com/)

---

### Post by dannyboy79 on 2013-01-23
i think it's your valid users line that is messing things up along with SHARE level security. Do you just want it to be username less and password less sharing in your internal home network?

---

### Post by CharlesA on 2013-01-23
> **dannyboy79 said:**
> i think it's your valid users line that is messing things up along with SHARE level security. Do you just want it to be username less and password less sharing in your internal home network?

I think you might be right.

Here's what my smb.conf file looks like - the only thing I changed was adding the share definitions.

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
   printing = bsd
   printcap name = /dev/null

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

;[printers]
;   comment = All Printers
;   browseable = no
;   path = /var/spool/samba
;   printable = yes
;   guest ok = no
;   read only = yes
;   create mask = 0700

# Windows clients look for this share name as a source of downloadable
# printer drivers
;[print$]
;   comment = Printer Drivers
;   path = /var/lib/samba/printers
;   browseable = yes
;   read only = yes
;   guest ok = no
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
#       cdrom share is accesed. For this to work /etc/fstab must contain
#       an entry like this:
#
#       /dev/scd0   /cdrom  iso9660 defaults,noauto,ro,user   0 0
#
# The CD-ROM gets unmounted automatically after the connection to the
#
# If you don't want to use auto-mounting/unmounting make sure the CD
#       is mounted on /cdrom
#
;   preexec = /bin/mount /cdrom
;   postexec = /bin/umount /cdrom

[Software]
        read list = htpc
        invalid users = clone
        path = /array/software
        write list = charles
        comment = Software Folder
        create mode = 664
        directory mode = 775

[Win]
        browseable = no
        invalid users = clone,htpc
        path = /array/win
        write list = charles
        comment = Windows Stuff
        create mode = 660
        directory mode = 770

[PC]
        browseable = no
        invalid users = clone,htpc
        path = /home/charles/pc
        write list = charles
        create mode = 660
        directory mode = 770

```

---

### Post by Craig71 on 2013-01-23
> **dannyboy79 said:**
>  Do you just want it to be username less and password less sharing in your internal home network?

Yes please! The easier the better!

---

### Post by dannyboy79 on 2013-01-23
> **Craig71 said:**
> Yes please! The easier the better!im sorry, it's actually not possible to technically have a usernameless and passwordless samba share BUT it can map users to the nobody account and still allow it access. I am not at home at the moment but when I get home i'll post my smb.conf file. I know I use USER level security, which means usernames need to be on the server and the same as on the client, IF that's not possible then you can use guest accounts which map to user nobody and or there is even a way to use a username map file where it maps a certain user from the client to a user on the server. does your Pi have a user on it and password?

---

### Post by Craig71 on 2013-01-23
I don't really know if there's a user as such on the Pi. I did create a user for samba called pi - password pi. 

I'm only using XBMC on this pi, so the user may just be XBMC?

---

### Post by dannyboy79 on 2013-01-23
Ok, now is there a pi user on your ubuntu samba server?

---

### Post by Craig71 on 2013-01-23
Yes, as long as I've done it right. Seems strange it wont connect. Here is a grab of the users: 

[IMG]http://img.photobucket.com/albums/v115/seymour71/Capture.png[/IMG]

---

### Post by CharlesA on 2013-01-23
Did you already set the password for pi?

---

### Post by Craig71 on 2013-01-23
Yep. Can't login with either of the other usernames & passwords either.

---

### Post by Morbius1 on 2013-01-23
Edit /etc/samba/smb.conf directly and

**[COLOR=Blue]In the [global] section[/COLOR]** of smb.conf find the following lines and put # signs in front of them so they look like this:
> #security = SHARE
#add machine script = /usr/sbin/useradd -s /bin/false -d /home/nobody
#winbind use default domain = Yes
#winbind trusted domains only = Yes
#path = /media/MediaShare
#read only = NoThen go into your share and make it look like this:
```
[mediaonserver]         
comment = mediaonmainserver  
path = /media/MediaShare       
guest ok = yes
force user = craig
read only = no
```Save the file and restart samba:
```
sudo service smbd restart
```This will create a guest accessible share. [COLOR=Blue]You no longer need any users _except nobody_[/COLOR] [COLOR=Blue]in the samba database [/COLOR]so remove the rest like this:
```
sudo smbpasswd -x craig
```If done correctly when you run the following command you should only get a listing for "nobody":
```
sudo pdbedit -w -L
```Now try to access the share. It should not ask for a username and password.[I]

Note: 
Windows users automatically pass usernames and passwords and if they are not in the samba password database the "map to guest = Bad User" line will convert them to "nobody" automatically because the default guest account is set to "nobody". Linux users will always come across as nobody until they are asked for credentials. The "force user = craig" will insure that anything you save to that share will have the Linux user craig ( which I am assuming is you ) as owner as it converts the user "nobody" to "craig" when saving and accessing files.[/I]

*Note2: The "craig" in force user is the Linux user craig. The craig you are removing from smbpasswd is just a reference to him.*

---

### Post by Craig71 on 2013-01-24
:popcorn::p:D:D

Yes! It works! It Works! Thank you so much dude. I only understand around 40% of how you did it - though I do really appreciate the time you've taken to try to explain it.

I have now got the extra drive, and some more ram for the server, so over the next day or so, I'll be upgrading it.

A couple of (hopefully last) questions. When I put the new drive in the server, which would be the easiest way to allow the same 'everyone welcome' access you've done her for me? And also, will I need to format the new drive?

Thanks again mate.:D

---

### Post by Morbius1 on 2013-01-24
Yes, you will need to format the drive. 

You can use the share definition above as a template for the new partition - just change the path and the share name:
> 
[[COLOR=Blue]mediaonserver2[/COLOR]]          
comment = [COLOR=Blue]mediaonmainserver2[/COLOR]   
path = [COLOR=Blue]/media/MediaShare2[/COLOR]        
guest ok = yes 
force user = craig 
read only = noTo have the partition automount you will also need a new entry in /etc/fstab - but that's another topic ;)

---

### Post by CharlesA on 2013-01-24
> **Morbius1 said:**
> 
To have the partition automount you will also need a new entry in /etc/fstab - but that's another topic ;)

Indeed, but there is some good documentation for it here:
[https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab)

Or the OP could just create a new thread asking about it.

---

### Post by Craig71 on 2013-01-25
Hi guys, daft question - what file system should I use for the new drive? I'm not going to partition it - just have separate folders for music, films etc.

---

### Post by Morbius1 on 2013-01-25
> **Craig71 said:**
> Hi guys, daft question - what file system should I use for the new drive? 
I don't know how this system is set up so if it's a dual boot with Windows then NTFS is your only choice.

If it's an all Linux box then I suggest ext4.
> I'm not going to partition it - just have separate folders for music, films etc.
This may sound like just semantics but you have to create a partition even if it's only one before you can format it. I would use GParted to do both.

After it's formatted - let's say it's ext4 - you need to add a line in fstab to have it automount at boot. Here again I would suggest using templates to do this sort of thing because I have found that utilities created to do this cause nothing but grief.

Here's a template for an ext4 partition:
```
UUID=076426af-cbc5-4966-8cd4-af0f5c879646 /media/Data2 ext4 defaults,noatime 0 2
```To use this template:

[COLOR=Blue]*** Note: If Gparted currently has the partition mounted unmount it first.*[/COLOR]

[1] Run the following command to find the correct UUID number for the new partition:
```
sudo blkid -c /dev/null
```[2] Create the mount point:
```
sudo mkdir /media/Data2
```[3] Add the template with the correct UUID and mount point to the end of /etc/fstab

[4] Run the following command to test for errors and if there are none mount the partition without requiring a reboot:
```
sudo mount -a
```Now that's it's mounted ( and only after it's mounted ) to /media/Data2 take possession of the partition:
```
sudo chown craig /media/Data2
```

---

### Post by Craig71 on 2013-01-25
Thanks dude. I believe I have created a partition for it: listed as /dev/sdb/1

If I use ext 4 formating, will my windows machine still be able to read & write from it?

---

### Post by Morbius1 on 2013-01-25
>  believe I have created a partition for it: listed as /dev/sdb/1Did you mean /dev/sdb1 ? That's the raw physical partition not the mount point.
>  If I use ext 4 formating, will my windows machine still be able to read & write from it?     If the Windows in question is part of a dual boot on the same box - No.

If the Windows is another machine on your home network - Yes.

Samba creates a virtual network file system that hides the true nature of the filesysten from the network client so it can be formatted in just about anything.

---

### Post by Craig71 on 2013-01-25
AH, I see - sort of. The server is a seperate box from the Windows one, so I'll do it as ext4.

---

### Post by dannyboy79 on 2013-01-25
yes, if windows is just going to be writing to it over the network, then you share it out just like the other share but with the new mount point. and windows will be able to write to it over the samba protocol. glad you're all set it seems

---

### Post by Craig71 on 2013-01-25
I'm running Ubuntu Server 'headless' can I still use ext4 - a quick google suggests is only used in Gparted? Or do I just use ext3?

---

### Post by Morbius1 on 2013-01-25
Let me answer it this way: Your other partition at /media/MediaShare and your OS itself at / is on an ext4 partition so I would bet it's safe to use ext4;)

---

### Post by Craig71 on 2013-01-25
Cheers dude. just done all that - seemed to go ok, but on rebooting, I get this message: 

[IMG]http://img.photobucket.com/albums/v115/seymour71/ERROR_zps04dd9d82.jpg[/IMG]

---

### Post by Craig71 on 2013-01-25
Man, I'm an idiot, I'd put the UUID for the wrong drive in!

Just rebooted, and everything seems ok *crosses fingers*

I'm doing this at work though, so I'll properly check it when I get home later & try to set up the new samba share.

---

### Post by CharlesA on 2013-01-25
> **Craig71 said:**
> Man, I'm an idiot, I'd put the UUID for the wrong drive in!

Just rebooted, and everything seems ok *crosses fingers*

I'm doing this at work though, so I'll properly check it when I get home later & try to set up the new samba share.
You should be ok. If you have any doubts, just run fsck from a livecd or force it on a reboot with this:

```
sudo touch /forcefsck
```

---

### Post by Craig71 on 2013-01-27
Thanks for all your help huys - it's now working fine!

I've even managed to use my Pi as a wireless dnla streamer, using this guide: 

[http://blog.scphillips.com/2013/01/using-a-raspberry-pi-with-android-phones-for-media-streaming/](http://blog.scphillips.com/2013/01/using-a-raspberry-pi-with-android-phones-for-media-streaming/)

I'm now just in the middle of the epic task of transfering all the videos from an external drive to my servers new internal one.

Thanks again guys!:p

---

