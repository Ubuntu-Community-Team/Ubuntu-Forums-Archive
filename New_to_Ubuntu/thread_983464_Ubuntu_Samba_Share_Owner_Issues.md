---
title: "Ubuntu Samba Share Owner Issues"
date: 2008-11-15
forum: New to Ubuntu
---

### Post by Ice Dragon on 2008-11-15
Hi all,
I have a samba share setup on an Ubuntu computer I have.

Whenever anyone puts files on that share (its set to allow everyone read/write access), that file is locked and the owner is "nobody", and even though the file is on my own ubuntu computer, I cannot access it.

I know I can go into terminal and chown -r me /theshare and that will solve the problem, but i dont want to have to do this for every file that someone copies over. Cant it be set to default let everyone have full access to all files in that shared folder?

---

### Post by Iowan on 2008-11-15
I suspect it can be done - start by posting your /etc/samba/smb.conf.

---

### Post by Kellemora on 2008-11-15
Hi ID

I hope Iowan can come up with a solution, we've had this same problem for 3 months now!

Our Temporary Fix is that no one puts a file on any computer other than their own, and into a shared directory.

From there, whoever needs it can Fetch it from that computer and it no longer looses it's permissions.

Also, a simple Crontab file can Fetch all the Shares and put them where they belong and they work just fine that way too!

In our case, the computer that holds client data fetches all the client files every 5 minutes so everyone can look to the same place to find them.

Not how we like it, but it works!

TTUL
Gary

---

### Post by Ice Dragon on 2008-11-15
> **Iowan said:**
> I suspect it can be done - start by posting your /etc/samba/smb.conf.

Sure, hopefully this help...

> 
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

## Browsing/Identification ###

# Change this to the workgroup/NT-domain name your Samba server will part of
	workgroup = WORKGROUP

# server string is the equivalent of the NT Description field
	server string = %h server (Samba, Ubuntu)

# Windows Internet Name Serving Support Section:
# WINS Support - Tells the NMBD component of Samba to enable its WINS Server
;	wins support = no

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
;	syslog only = no

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
	security = user

# You may wish to use password encryption.  See the section on
# 'encrypt passwords' in the smb.conf(5) manpage before enabling.
	encrypt passwords = true

# If you are using encrypted passwords, Samba will need to know what
# password database type you are using.  
	passdb backend = tdbsam

	obey pam restrictions = yes

;	guest account = nobody
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
;	logon path = \\%n\%u\profile

# The following setting only takes effect if 'domain logons' is set
# It specifies the location of a user's home directory (from the client
# point of view)
;   logon drive = H:
;	logon home = \\%n\%u

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
;	load printers = yes

# lpr(ng) printing. You may wish to override the location of the
# printcap file
;   printing = bsd
;   printcap name = /etc/printcap

# CUPS printing.  See also the cupsaddsmb(8) manpage in the
# cupsys-client package.
;	printing = cups
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
;	socket options = tcp_nodelay

# The following parameter is useful only if you have the linpopup package
# installed. The samba maintainer and the linpopup maintainer are
# working to ease installation and configuration of linpopup and samba.
;   message command = /bin/sh -c '/usr/bin/linpopup "%f" "%m" %s; rm %s' &

# Domain Master specifies Samba to be the Domain Master Browser. If this
# machine will be configured as a BDC (a secondary logon server), you
# must set this to 'no'; otherwise, the default behavior is recommended.
;	domain master = auto

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
;	usershare max shares = 100

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
	browseable = no
	path = /var/spool/samba
	printable = yes
;	guest ok = no
;	read only = yes
	create mask = 0700

# Windows clients look for this share name as a source of downloadable
# printer drivers
[print$]
	comment = Printer Drivers
	path = /var/lib/samba/printers
;	browseable = yes
;	read only = yes
;	guest ok = no
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

[Upload]
	comment = Put Stuff On The Server
	path = /home/administrator/Upload
	writeable = yes
;	browseable = yes
	guest ok = yes

[usb1tb]
	comment = USB 1TB Backup Drive 01
	path = /media/usb1tb
;	writeable = No
;	browseable = yes
	guest ok = yes

[ftp]
	comment = FTP Server Files
	path = /home/ftp
	writeable = yes
;	browseable = yes
	guest ok = yes

[Programming]
	comment = Programming Files
	path = /home/administrator/Programming
	writeable = yes
	browseable = no
	guest ok = yes

[web]
	comment = Web Server Files
	path = /var/www
	writeable = yes
;	browseable = yes
	guest ok = yes


---

### Post by Ice Dragon on 2008-11-15
> **Kellemora said:**
> Hi ID

I hope Iowan can come up with a solution, we've had this same problem for 3 months now!

Our Temporary Fix is that no one puts a file on any computer other than their own, and into a shared directory.

From there, whoever needs it can Fetch it from that computer and it no longer looses it's permissions.

Also, a simple Crontab file can Fetch all the Shares and put them where they belong and they work just fine that way too!

In our case, the computer that holds client data fetches all the client files every 5 minutes so everyone can look to the same place to find them.

Not how we like it, but it works!

TTUL
Gary

That is a decent suggestion, but maybe im just a bit of a stickler, it seems to me that stuff like this should be setup by a default installation already working you know?

All im asking is that a machines administrator account have access to all files on his computer =P

Dont get me wrong i absolutely love ubuntu, but as a new user who is trying desperately to learn all the ins and outs, it is frustrating when something that was beyond simple in windows, gives me all kinds of trouble in linux. I dont like it most of all because while im patient and work through things, I know the majority of people who i want to recommend ubuntu to, are not.

Im waiting until Ubuntu 9.04 to install it for my mom and dad on their home network, hoping that some of the issues from 8.04 will be worked out by then.

---

### Post by graywind on 2008-11-16
It sounds like permissions aren't a big concern and what you are looking for is mostly just free for all write access to those directories you want to share with other users, without authentication.

I'd be a little wary about what that might mean for say your web server that you could put an executable script on or expose some configuration, or anonymous ftp access that someone could do bad things with....but as long as you understand what you are asking for...here goes.

If you just want one user on the local machine to have ownership instead of nobody, you could just set:

```

[global]
guest account = theuseryouwanthere

```

If however you need more than one local user on the machine to have access, you can open it up to everyone with this:

```

[global]
guest ok = yes
create mask = 0777
directory mask = 0777

```

This basically means that anyone can do anything over samba or logged in locally to the machine for those directories shared. Let me know if this is what you were looking for. :)

---

### Post by yousellstuff on 2008-11-16
if you ever need a clone script of a big website like facebook or you tube, just go to [www.clonedscripts.info](www.clonedscripts.info)

---

### Post by Kellemora on 2008-11-16
Hi Gray

That's all and good except:

Gnome (Nautilus) uses /var/lib/samba to fetch it's configuration files, NOT smb.conf and /var/lib/samba configuration file is in Binary and NOT editable by humanoids.

So far, the only way I've found to get a change to the smb.conf file to be permanent is to reboot THREE TIMES in succession.

When you boot up the pooter, it looks to /var/lib/samba NOT to smb.conf

But, if you boot up twice in a short period of time, it's like the pooter says, ut oh, why did he do that, I had better look at smb.conf and see what's up.

So it does and runs the smb.conf file for this session only.  Next time you boot, you're back to the old /var/lib/samba binary again.

I know this is not logical, but it seems to me that by editing smb.conf, then booting up three times, it follows the above routine, but on the third bootup rewrites the /var/lib/samba binary file so the changes you made in smb.conf will now take effect.

So, the next time you power down and bring the system back up again, it still uses your updated smb.conf because it overwrote the /var/lib/samba binary file.

Not the proper way of wording it, but his is how it appears to be functioning.  I say that because the only way I've got the changes made to smb.conf to do anything at all differently was to make the changes then boot up three times in quick succession.  After that things will work just fine until we get another update.  Then I have to start all over again getting all 8 of our machines humming together again.

TTUL
Gary

---

### Post by graywind on 2008-11-16
I wonder if my success has to do with placing these features under [global] and the settings do trickle down. I do setup my share via the gui as that is all I have been using, the only change I have made was to make sure the guest access writes a certain way. Perhaps I'll try a few reboots and see if I can break my solution.

In regards to preserving the configuration during updates....honestly I'm not sure whats going on there, anyone else wanna take a whack at that?

Anywho, reboot time :D

---

### Post by bab1 on 2008-11-17
Samba uses /etc/samba/smb.conf before looking for any settings in /var/lib/samba.  Ice dragons smb.conf file has no shares configured (manually) so Samba looks to the /var/lib/samba files.

The reason guests (anonymous users) files are owned by "nobody" is because that are mapped that way.  The manual directives (smb.conf) are:```
# This option controls how unsuccessful authentication attempts are mapped
# to anonymous connections
map to guest = bad user

guest account = nobody

```
I'll bet that the /var/lib/samba files also follow this.

To have files ownd by the various users, one should add them the the smbuser database by:```
sudo smbpasswd -a <new user>
```
This means that the user is no  longer guest and the "bad user" directive does not apply.

Once again, if you create shares using Nautilus the /etc/samba/smb file is only used to set the WORKGROUP directive.

Samba is complex and has many features, but it is manageable if one reads up on it.  When it is all said and done the [**Samba.org**]("http://www.samba.org/samba/docs/") site has the best documentation

---

### Post by Kellemora on 2008-11-17
Hi Bab

Explain this if you can?

3 different hard drives (mirrors of each other).
Smb.conf is IDENTICAL on each.
Plug #1 in, LAN works fine!
Plug #2 in place of #1, LAN works fine!
Plug #3 in, no LAN at all!
Plug either #1 or #2 in, LAN is back up and works fine.

No changes to smb.conf will get the LAN running using HD #3.
and changes made to smb.conf do not seem to affect drives #1 and #2, the LAN just works, no problems.

OK, let's take the same three hard drives and move to a different computer.
Plug in #1, it resets the hardware, LAN works fine.
Plug in #2, it resets the hardware, LAN works fine.
Plug in #3, it resets the hardware, LAN don't work.

It's things like this that have turned my hair gray, hi hi.........

For weeks I kept thinking I was doing something wrong somewhere, that's why I tried mirroring drives so they were identical.
Also tried loading completely from scratch several times.
That one hard drive would never let a LAN work on any machine.
So now it's just used as an internal backup drive on an old WinDOZE box.

As far as the rest of the machines in the office, the LAN works fine, when it works.  And if it goes down, we no longer change anything, just go around and reboot each computer three times in succession and everything starts working again.  After we wait 12 to 15 minutes after the last computer boots up for the network to repopulate itself.  Then we have no problems.  Unless we get one of those security updates, then it's back to rebooting every Ubuntu machine in the office three times again.

Weird I know!

TTUL
Gary

---

