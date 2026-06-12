---
title: "Samba Trouble"
date: 2008-05-13
forum: New to Ubuntu
---

### Post by Littlehawk on 2008-05-13
I have Samba running on one Ubuntu machine. I tried to access it from a windows machine, and I see it is part of my windows workgroup because it shows up on the list of servers there.

I couldn't connect to the SAMBA server from the XP machine, so I thought I would try from my other client machine running Ubuntu 8.04. 

Still no luck connecting. On my client Ubuntu machine Using the file browser, I select File > Connect to Server. I choose Windows Share and type in the IP address of the SAMBA server machine (which is running 7.10). A file browser opens and shows the shared directory that I set up on the server and also shows the print$ folder. When I click on the share directory, I get a dialog to enter a username, domain, and password. The domain is already set to WORKGROUP. I tried my username and password with domain=WORKGROUP and that fails. I did the same again but changed the domain in the dialog to my local windows domain (which is what the XP machine seems to see the SAMBA server as part of), and still the connection fails.

I ran sudo modprobe smbfs on the client machine before doing all of this, but I'm not sure whether that was necessary. 

All this started when my USB devices stopped mounting, so I'm trying to move data over the network. It looked like a good idea at the time ](*,)

---

### Post by Xiong Chiamiov on 2008-05-13
The Samba tutorials I used are [this one]("https://help.ubuntu.com/community/SettingUpSamba") and [this one]("http://ubuntuforums.org/showthread.php?t=202605").  If you're going to be sharing between Linux machines, you should use [NFS]("https://help.ubuntu.com/community/SettingUpNFSHowTo"). (btw, that link does everything through config files and such to be *buntu-generic, but you can probably figure most of it out through the GUI somewhere)

---

### Post by Littlehawk on 2008-05-13
Oops! I don't know what I did to get this. But I went through the Network Settings dialog, in the General tab, and changed the Domain Name to my windows workgroup name and now I can't run sudo command. The network settings is the only thing I can think that I changed. I changed it back and the problem is still there. I rebooted and no luck.

Here's what's happening (for any command within sudo, apparently:
>  sudo ls
sudo: unable to resolve host jim-desktop-ubuntu
 

What happened???

<edit>
I found this thread:
[http://ubuntuforums.org/showthread.php?t=615579](http://ubuntuforums.org/showthread.php?t=615579)
and used gksudo gedit /etc/hosts to fix the problem.

Back to the SAMBA problem in the morning.

---

### Post by Terpsicore on 2008-05-13
I had the same problem and found this guide that solved all 

[http://www.europe.eclipse.co.uk/Ubuntu/Ubuntu-on-win-network.htm](http://www.europe.eclipse.co.uk/Ubuntu/Ubuntu-on-win-network.htm)

hope it helps you too..

---

### Post by Littlehawk on 2008-05-13
Well, I'm still having a problem. I tried this tutorial (thanks, by the way!):

> I had the same problem and found this guide that solved all

[http://www.europe.eclipse.co.uk/Ubun...in-network.htm](http://www.europe.eclipse.co.uk/Ubun...in-network.htm)

hope it helps you too..

I didn't follow it exactly, because I already have some of these steps done, and I don't know how to undo them. (Can I just remove SAMBA completely and start over?)

But the Samba server is letting both my Ubunto client and my XP client machine see the server and the shared folder in their file browsers.

I thought the problem might have to do with no enabling the user logname on the server so I made sure to run these again:

> 
sudo smbpasswd -L -a jim
sudo smbpasswd -L -e jim
 

<edit>
From the Ubunto client, I can't see the Sambe server in the file browser by looking at windows shares. (Go>Network>Windows Network>mydomain). I can see it when I access it using File>Connect to Server, select Windows Share as the service type and then enter the ip address of the server.

On the Ubunto client, when I right click on the shared folder and choose Mount, the dialog opens, asking for username, domain, and password. I enter the username and password that I set up through the smbpasswd command. I use the domain name that the file browser shows me when I drill down throughGo>Network>Windows Network>mydomain (but as I mentioned, I cant get down to the server that way)
</edit>

Is there a problem with special characters in the domain name? I have an at-sign (@) in mine. I saw in one screen last night that a %40 was substituted for the @. So I tried that and it didn't work either.

The XP client is basically responding the same way, except the domain name must be implicit in the connection, because it only asks for username and password.

Thanks for the help...

---

### Post by Kulgan on 2008-05-13
A peek at your smb.conf might help a litte :D

---

### Post by Littlehawk on 2008-05-13
Here is the smb.conf file on the server. Thanks.

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

## Browsing/Identification ###

# Change this to the workgroup/NT-domain name your Samba server will part of
   workgroup = WG@HOME

# server string is the equivalent of the NT Description field
   server string = %h server (Samba, Ubuntu)

# Windows Internet Name Serving Support Section:
# WINS Support - Tells the NMBD component of Samba to enable its WINS Server
;   wins support = no

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

# Put a capping on the size of the log files (in Kb).
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
security = user
username map = /etc/samba/smbusers

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
;   unix password sync = no

# For Unix password sync to work on a Debian GNU/Linux system, the following
# parameters must be set (thanks to Ian Kahan <<kahan@informatik.tu-muenchen.de> for
# sending the correct chat script for the passwd program in Debian Sarge).
   passwd program = /usr/bin/passwd %u
   passwd chat = *Enter\snew\sUNIX\spassword:* %n\n *Retype\snew\sUNIX\spassword:* %n\n *passwd:*password\supdated\ssuccessfully* .

# This boolean controls whether PAM will be used for password changes
# when requested by an SMB client instead of the program listed in
# 'passwd program'. The default is 'no'.
;   pam password change = no

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

# When using [print$], root is implicitly a 'printer admin', but you can
# also give this right to other users to add drivers and set printer
# properties
;   printer admin = @lpadmin


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
;
; The following was the default behaviour in sarge
; but samba upstream reverted the default because it might induce
; performance issues in large organizations
; See #368251 for some of the consequences of *not* having
; this setting and smb.conf(5) for all details
;
;   winbind enum groups = yes
;   winbind enum users = yes

#======================= Share Definitions =======================

# Un-comment the following (and tweak the other settings below to suit)
# to enable the default home directory shares.  This will share each
# user's home directory as \\server\username
;[homes]
;   comment = Home Directories
;   browseable = no

# By default, \\server\username shares can be connected to by anyone
# with access to the samba server.  Un-comment the following parameter
# to make sure that only "username" can connect to \\server\username
# This might need tweaking when using external authentication schemes
;   valid users = %S

# By default, the home directories are exported read-only. Change next
# parameter to 'yes' if you want to be able to write to them.
;   writable = no

# File creation mask is set to 0700 for security reasons. If you want to
# create files with group=rw permissions, set next parameter to 0775.
;   create mask = 0700

# Directory creation mask is set to 0700 for security reasons. If you want to
# create dirs. with group=rw permissions, set next parameter to 0775.
;   directory mask = 0700

# Un-comment the following and create the netlogon directory for Domain Logons
# (you need to configure Samba to act as a domain controller too.)
;[netlogon]
;   comment = Network Logon Service
;   path = /home/samba/netlogon
;   guest ok = yes
;   writable = no
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

wins support = no
[printers]
   comment = All Printers
   browseable = no
   path = /var/spool/samba
   printable = yes
   public = no
   writable = no
   create mode = 0700

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
;   writable = no
;   locking = no
;   path = /cdrom
;   public = yes

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

### Post by Littlehawk on 2008-05-13
I found a tutorial on the smb.conf file and replaced mine with this:

```

# Global Parameters

workgroup = wg@home
netbios name = Samba
encrypt passwords = yes

[homes]
read only = no
browseable = no

[picoshare]
path = /home/group
browseable = yes
write list = jim

```

Easier to read than the first one, but the results are identical as far as connecting from either client (Ubuntu or XP).

---

### Post by Kulgan on 2008-05-13
I was about to say... there aren't any shares... but there are now :D

If I understand the issue correctly, you can see the server correctly, as well as the list of shares, but not actually use any of them. 

Have you tried replacing the domain name with something sensible (ie no special chars) and performing a full reboot (restarting server might not cut it, in this case)?

Other than that, it should technically work, even if there are many parts of Samba that wont be used. 

If you think it may have something to do with anything you did to the configuration file, as you mentioned earlier, try a 
```
dpkg-reconfigure samba samba-common 
```
to set it back. Overwrite with the new file, of course. 

Would definitely have a stab at getting rid of the @ in the workgroup/domain first, though...

---

### Post by Littlehawk on 2008-05-13
Thanks. Kulgan. I changed the workgroup name to an alphabetic string on all of the computers here. That didn't work (I restarted samba daemon.)


I ran the reconfigure tool you recommended. 
```
dpkg-reconfigure samba samba-common
```

Still not working from either machine.

So I decided to remove all of the Samba packages from the server and then re-install them. 

>> From the XP client -- IT WORKS!! I can now log in from the XP client.
>> From the Ubuntu Client -- It is not seeing any workgroup in the windows network. 

In the mean time, I am now able to transfer the 5GB of files from the XP machine to the samba server, which is on a tiny pico-itx board.

So, at this point, I'm not really sure what was wrong, and I'll eventually have to understand it. But a clean re-install on the server seemed to fix part of the problem. Let's see if it holds up over time.

---

### Post by Kulgan on 2008-05-14
Just because it doesn't appear doesn't mean you can't connect. This may be just random (I think?) or because you have several network hops between the machines. You should be able to connect to it if you enter the path smb://workgroup/hostname into nautilus. (Should also be able to make a launcher so that you don't have to do that every time.)

---

