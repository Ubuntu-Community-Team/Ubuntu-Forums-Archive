---
title: "Can't write/create on second shared samba drive on windows pc"
date: 2013-05-05
forum: New to Ubuntu
---

### Post by jeanke2 on 2013-05-05
I've created 2 samba shared directories. One on the local disk of my server, the other one is an external disk (fat 32) which a mounted and applied chmod 777 already.
On my windows PC I can access both shares, but I can only create/write on the first share (local dir on my server). 
When I try to create folders or add images on the second share, it says I don't have the permissions...
Anyone an idea, as I'm a newbie on this? 

This my smb.con file:

```
## Sample configuration file for the Samba suite for Debian GNU/Linux.
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
[Local share]
   comment = Home
   browseable = yes
   read only = no
   path = /home/jeanke2
  
[Media share]
   comment = media drive 1
   browseable = yes
   read only = no
   path = /media/extmediadrive1/mediashare


# File creation mask is set to 0700 for security reasons. If you want to
# create files with group=rw permissions, set next parameter to 0775.
   create mask = 0777


# Directory creation mask is set to 0700 for security reasons. If you want to
# create dirs. with group=rw permissions, set next parameter to 0775.
   directory mask = 0777


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



```

---

### Post by squakie on 2013-05-05
I'm not on my Ubuntu system at the moment, so I can only guess:  I *think* /media is owned by root, so everything under it is probably only read/write if you are root.  I would doubt you are connecting to the share with a root id and password (*VERY*  *VERY* bad idea - if you are - DON'T), so I would *think* the result would be read only.  Just my guess.

EDIT:  I should probably explain my thought a little better.  The external drive has a file system, and of course root will own the file system.  I think the thing is having 1 or more folders on that drive for which you have assigned access.  I had a thread here not too long ago where I mentioned what I did in a similar situation.  Not only did I define folders there (of course, my external drive was in ext4, not NTFS), but I gave access rights either to 1 user or a group of users.  Then when the file system is remounted when the drive is attached again the access rights are still there and still apply.

---

### Post by bab1 on 2013-05-06
> **jeanke2 said:**
> I've created 2 samba shared directories. One on the local disk of my server, the other one is an external disk (fat 32) which a mounted and applied chmod 777 already.
On my windows PC I can access both shares, but I can only create/write on the first share (local dir on my server). 
When I try to create folders or add images on the second share, it says I don't have the permissions...
Anyone an idea, as I'm a newbie on this? 

You can't change fat32 permissions with chmod.  The vfat file system (fat32) has no user permissions knowledge.  The permissions you would see are applied by the command *mount *when the vfat partition is mounted.  If you allow the partition to be mounted automagically then you have to accept the arbitrary ownership parameters.  Ownership of vfat partitions are determined by the owner of the process doing the mount.  In this case it is the user root and the group root (root:root)  

I would not recommend you manually mount partitions in /media or its subdirectories that you are going to share with Samba.  The /media directory is really for removable media like flash drives.  The mount point is not what you see when you use the share anyway.  The share is defined by //SERVER_NAME/SHARE_NAME.  The Samba user needn't worry about the underlying mount point.

You could mount the vfat partiton at /mnt/external of something like that.  It it can be mounted via fstab at boot time if the drive is always attached.  If not you still should have an entry in fstab that allows a user to mount the partition at a later time.  Then you can create a script to mount this at the time you wish while explicitly declaring the user and group ownership and permissions.  The Samba create mask may not work at all.  You should set permissions and mask at mount time anyway.

See ```
man fstab  (for fstab settings)

man mount (for vfat mount entry parameters used in fstab)
 
```

The Ubuntu howtos are also helpfull.  See:

[[COLOR="#FF8C00"]https://help.ubuntu.com/community/Fstab[/COLOR]]("https://help.ubuntu.com/community/Fstab")

[[COLOR="#FF8C00"]https://help.ubuntu.com/community/Mount[/COLOR]]("https://help.ubuntu.com/community/Mount")

---

### Post by Morbius1 on 2013-05-06
> I've created 2 samba shared directories. One on the local disk of my  server, [COLOR=#0000cd]**the other one is an external disk (fat 32)**[/COLOR] which a mounted and  applied chmod 777 already.
> [Media share]
   comment = media drive 1
   browseable = yes
   read only = no
   path = /media/extmediadrive1/mediashare
What are the permissions of /media/extmediadrive1:
```
ls -dl /media/extmediadrive1
```

Unless you are doing this trough fstab that external disk will mount with you as owner and access limited to you alone. You have your share set up to require credentials to access so you can modify the share definition to make all these users appear to be you after they are allowed access:

> [Media share]
   comment = media drive 1
   browseable = yes
   read only = no
   path = /media/extmediadrive1/mediashare
   [COLOR=#0000cd]**force user = jeanke2**[/COLOR]
Then restart samba:
```
sudo service smbd restart
```

---

### Post by jeanke2 on 2013-05-06
I've mounted the hard drive into /mnt/mediashare1 as bab1 suggested.
I also tried remounting it giving different permission options like [FONT=Ubuntu Mono]sudo mount /dev/sdb1 /media/flash -o dmask=000,fmask=111.
[/FONT]Still no write permission when accessing the share from windows. Also tried "**force user = jeanke2**" ont it as morbius1 suggested.
Write permissions of the shared location at the moment: "*drwxr-xr-x 15 root root 32768 mei  4 22:13 /mnt/mediashare1/*".
The other samba share (directory in home folder) has no problems, I can access it and read/write on it.
So for now, I can still access the drive (shared external disk) on the windows pc, but still no write access.

---

### Post by bab1 on 2013-05-06
> **jeanke2 said:**
> I've mounted the hard drive into /mnt/mediashare1 as bab1 suggested.
I also tried remounting it giving different permission options like [FONT=Ubuntu Mono]sudo mount /dev/sdb1 /media/flash -o dmask=000,fmask=111.
[/FONT]Still no write permission when accessing the share from windows. Also tried "**force user = jeanke2**" ont it as morbius1 suggested.
Write permissions of the shared location at the moment: "*drwxr-xr-x 15 **[COLOR="#FF0000"]root root [/COLOR]**32768 mei  4 22:13 /mnt/mediashare1/*".
The other samba share (directory in home folder) has no problems, I can access it and read/write on it.
So for now, I can still access the drive (shared external disk) on the windows pc, but still no write access.

You need to add the uid and gid numbers for your users so you have ownership.  The dmask and fmask are the permissions but at the present time the owner is still **[COLOR="#FF0000"]root:root[/COLOR]**.

Edit.  You can find this uid/gid numbers like this ```
getent passwd <user_name>
```.  Mine starts out like this```
bab:x:1000:1000:
```...the first number is the UID and the second one is the GID

---

### Post by jeanke2 on 2013-05-07
Mounting with the correct [COLOR=#000000] uid/gid numbers[/COLOR] did the trick!
Tnx a lot!!

---

