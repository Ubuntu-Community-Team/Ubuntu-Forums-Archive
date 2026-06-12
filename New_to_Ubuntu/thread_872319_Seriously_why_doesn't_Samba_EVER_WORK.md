---
title: "Seriously why doesn't Samba EVER WORK?"
date: 2008-07-27
forum: New to Ubuntu
---

### Post by CryptiniteDemon on 2008-07-27
You know I follow all these stupid guides and amazingly enough samba never seems to work for me.  Two weeks ago I could see my whole network and I had a folder shared over the network that all the windows and linux machines could see.  But that lasted for like a day.  And I can't figure out why my freaking linux machines with samba server on them most of the time never show up when I'm browsing the network either on a windows or linux machine?  Seriously, WTF?  

Can someone please tell me what I'm doing wrong because it's driving me insane.  Here's my samba conf for the machine that has the shared folder.
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
# Any line which starts with a ; (semi-colon) or a # (hash) 
# is a comment and is ignored. In this example we will use a #
# for commentary and a ; for parts of the config file that you
# may wish to enable
#
# NOTE: Whenever you modify this file you should run the command
# "testparm" to check that you have not made any basic syntactic 
# errors. 
#

#======================= Global Settings =======================

[global]
usershare owner only = False

## Browsing/Identification ###

# Change this to the workgroup/NT-domain name your Samba server will part of
   workgroup = BRANDES

# server string is the equivalent of the NT Description field
   server string = %h server (Samba, Ubuntu)

# Windows Internet Name Serving Support Section:
# WINS Support - Tells the NMBD component of Samba to enable its WINS Server
;   wins support = yes

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
;   bind interfaces only = true



#### Debugging/Accounting ####

# This tells Samba to use a separate log file for each machine
# that connects
   log file = /var/log/samba/log.%m

# Cap the size of the individual log files (in KiB).
   max log size = 1000

# If you want Samba to only log through syslog then set the following
# parameter to 'yes'.
;   syslog only = no

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
;   security = user

# You may wish to use password encryption.  See the section on
# 'encrypt passwords' in the smb.conf(5) manpage before enabling.
   encrypt passwords = true

# If you are using encrypted passwords, Samba will need to know what
# password database type you are using.  
   passdb backend = tdbsam

   obey pam restrictions = yes

;   guest account = nobody
   invalid users = root

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

# This option controls how nsuccessful authentication attempts are mapped 
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
;   logon path = \\%N\%U\profile

# The following setting only takes effect if 'domain logons' is set
# It specifies the location of a user's home directory (from the client
# point of view)
;   logon drive = H:
;   logon home = \\%N\%U

# The following setting only takes effect if 'domain logons' is set
# It specifies the script to run during logon. The script must be stored
# in the [netlogon] share
# NOTE: Must be store in 'DOS' file format convention
;   logon script = logon.cmd

# This allows Unix users to be created on the domain controller via the SAMR
# RPC pipe.  The example command creates a user account with a disabled Unix
# password; please adapt to your needs
; add user script = /usr/sbin/adduser --quiet --disabled-password --gecos "" %u

########## Printing ##########

# If you want to automatically load your printer list rather
# than setting them up individually then you'll need this
;   load printers = yes

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
   socket options = TCP_NODELAY

# The following parameter is useful only if you have the linpopup package
# installed. The samba maintainer and the linpopup maintainer are
# working to ease installation and configuration of linpopup and samba.
;   message command = /bin/sh -c '/usr/bin/linpopup "%f" "%m" %s; rm %s' &

# Domain Master specifies Samba to be the Domain Master Browser. If this
# machine will be configured as a BDC (a secondary logon server), you
# must set this to 'no'; otherwise, the default behavior is recommended.
;   domain master = auto

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
# to enable the default home directory shares.  This will share each
# user's home directory as \\server\username
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
# with access to the samba server.  Un-comment the following parameter
# to make sure that only "username" can connect to \\server\username
# This might need tweaking when using external authentication schemes
;   valid users = %S

# Un-comment the following and create the netlogon directory for Domain Logons
# (you need to configure Samba to act as a domain controller too.)
;[netlogon]
;   comment = Network Logon Service
;   path = /home/samba/netlogon
;   guest ok = yes
;   read only = yes
;   share modes = no

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
   browseable = yes
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
# Replace 'ntadmin' with the name of the group your admin users are
# members of.
;   write list = root, @ntadmin

# A sample share for sharing your CD-ROM with others.
;[cdrom]
;   comment = Samba server's CD-ROM
;   read only = yes
;   locking = no
;   path = /cdrom
;   guest ok = yes

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

### Post by dmizer on 2008-07-27
You have no shares defined.  Your shared folder configuration goes below this section:
```
#======================= Share Definitions =======================
```
there's no directory defined for sharing.

please see the first link in my sig for how to correctly configure /etc/samba/smb.conf

---

### Post by steveneddy on 2008-07-27
I've never had to edit a samba config file.

That's weird.

---

### Post by Dr Small on 2008-07-27
> **steveneddy said:**
> I've never had to edit a samba config file.

That's weird.
... and I haven't used Samba in ages.

---

### Post by CryptiniteDemon on 2008-07-27
> **dmizer said:**
> You have no shares defined.  Your shared folder configuration goes below this section:
```
#======================= Share Definitions =======================
```
there's no directory defined for sharing.

please see the first link in my sig for how to correctly configure /etc/samba/smb.conf

See that's the thing.  If I right click on a folder and share it, should it automatically put that in?  I know it was defined in there before, because a few weeks ago I saw it in there.  

But that still doesn't explain why the host computer (which is ubuntu) doesn't show up on the network.

---

### Post by Dr Small on 2008-07-27
> **CryptiniteDemon said:**
> See that's the thing.  If I right click on a folder and share it, should it automatically put that in?  I know it was defined in there before, because a few weeks ago I saw it in there.  

But that still doesn't explain why the host computer (which is ubuntu) doesn't show up on the network.
Well, if that's how Samba is supposed to work, it never worked properly for me, when I used it. I meerly typed in the IP address of the machine I wanted to connect to (in Nautilus) and connected. The machines never showed up for me in the network places thingy.

Dr Small

---

### Post by UbuntuNerd on 2008-07-27
Im sorry samba is not working for you I had some similar problems I was just wondering did you install or configure any kind of firewall in any of the Ubuntu machines?

When I first Installed samba everything was great but my shares would come on and off do to my firewall blocking it maybe is something you need to check on!!!

---

### Post by ptn107 on 2008-07-27
The share folder extension in nautilus does NOT use the smb.conf file.  If you use the older shares-admin application that was included with earlier versions of Ubuntu, then that will add the shares to smb.conf.  In either case, they will NOT show up in Places -> Network.  No matter what you do about it.  It's a bug.  You can, however, manually connect to shares via Places -> Connect to Server.  Or use smbclient on the command line.

[https://bugs.launchpad.net/ubuntu/+source/samba/+bug/208531](https://bugs.launchpad.net/ubuntu/+source/samba/+bug/208531)

---

### Post by dmizer on 2008-07-28
> **CryptiniteDemon said:**
> But that still doesn't explain why the host computer (which is ubuntu) doesn't show up on the network.

It doesn't show up because there is no netbios name set for your server.  In addition to the "workgroup = BRANDES" option, you'll need to include a "netbios name = your-server-name" option.  Difficult to find a server in a network when the server doesn't have a name.

You really should take a look at the samba server howto linked in my sig if you want to configure your share correctly.

Edit:
Samba has undergone a variety of updates recently. Most likely in answer to the growing number of bugs filed against it.  This really is a good thing because it means that developers are spending some serious time on fixing the problems.  In the interim, you may frequently run into breakage as a result of the updates.

Your best bet for avoiding this is to simply use the CLI configuration method for sharing your files, rather than trying to rely on the GUI/Nautilus option.

---

### Post by Mumbly on 2008-07-28
A few years ago I just started using Webmin to setup all my Samba shares/printers. Easy and intuitive to use, and my current shares have been up and available for the better part of a year.

---

### Post by ptn107 on 2008-07-28
I really recommend Using Samba (3rd edition) by O'Reilly.  The online documentation on the Samba website helps tremendously as well.

Using Samba 3rd Edition
ISBN-10: 0596007698
ISBN-13: 978-0596007690

Other useful tidbits:
[http://us4.samba.org/samba/docs/](http://us4.samba.org/samba/docs/)
[http://us4.samba.org/samba/docs/man/Samba-HOWTO-Collection/](http://us4.samba.org/samba/docs/man/Samba-HOWTO-Collection/)

---

