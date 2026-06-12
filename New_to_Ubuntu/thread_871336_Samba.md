---
title: "Samba"
date: 2008-07-26
forum: New to Ubuntu
---

### Post by anderskitson on 2008-07-26
I am a little stumped recently, It all started when all of a sudden I could not print to a printer shared from a windows machine. I haven't been able to print for a few days now. I however could share files either way. I was on a different work group however, the printing did work fine before hand, and I can not point to anything that has been done on either end of the machines. I tried to change my workgroup in my smb.conf file to the same one the other computers  on the windows network are on, but I then could no longer file share. The only thing that has changed, is that the router and other computers are setup with open dns now. I dont see how this could be an issue, but I dont know enough to be sure. Any help would be greatly appreciated.

---

### Post by ejpyle on 2008-07-26
> **anderskitson said:**
> I am a little stumped recently, It all started when all of a sudden I could not print to a printer shared from a windows machine. I haven't been able to print for a few days now. I however could share files either way. I was on a different work group however, the printing did work fine before hand, and I can not point to anything that has been done on either end of the machines. I tried to change my workgroup in my smb.conf file to the same one the other computers  on the windows network are on, but I then could no longer file share. The only thing that has changed, is that the router and other computers are setup with open dns now. I dont see how this could be an issue, but I dont know enough to be sure. Any help would be greatly appreciated.


What version of Windows OS you running? 32 or 64?

---

### Post by superprash2003 on 2008-07-26
ensure that both pcs are able to ping each other first

---

### Post by anderskitson on 2008-07-26
@superprash2003
They can Ping each other fine, there ip's are
192.168.75.198 and 192.168.75.106 so they look to be within the correct network range, or whatever you call that. All of this was working earlier. I can still get file sharing working if I switch my workgroup  name back to WORKGROUP, which doesn't make sense, because the windows workgroup name that the rest of the house is on is something else

@ejpyle 32 bit xp home

---

### Post by bab1 on 2008-07-27
What is the name of the house workgroup?  

Send us the output of```
cat /etc/samba/smb.conf
```

---

### Post by anderskitson on 2008-07-27
The work group name is KITSON

> #======================= Global Settings =======================

[global]

## Browsing/Identification ###

# Change this to the workgroup/NT-domain name your Samba server will part of
   workgroup = KITSON

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

---

### Post by bab1 on 2008-07-27
I am looking at your smb.conf file.  I have a couple of questions.  [LIST=2]
[*]Is the printer attached to the Ubuntu box?
[*]Did you set up Samba at all?  
[/LIST]

I don't see any file shares or Samba user security ie:```
# "security = user" is always a good idea. This will require a Unix account
# in this server for every user accessing the server. See
# /usr/share/doc/samba-doc/htmldocs/Samba3-HOWTO/ServerType.html
# in the samba-doc package for details.
[COLOR="Red"];[/COLOR] [COLOR="Blue"]security = user[/COLOR]
```

I also see that the printer is not browsable ie:```
[printers]
comment = All Printers
[COLOR="Red"]browseable = no[/COLOR]
path = /var/spool/samba
printable = yes
guest ok = no
read only = yes
create mask = 0700
```

If the printer is attached to the Windows box then I am not so sure that you need or use Samba.  Your problem may be in the implementation of  the smbfs client for Ubuntu.

---

### Post by anderskitson on 2008-07-27
The Printer is attached to the windows machine and I can browse and see it and install it, but it just wont connect and print. I am assuming I setup samba at one point because I can right click on a folder and share it on the network. I am not sure what security information I would need to enter, I never had to do that before.

When I look in synaptic the installed files are
samba
samba-common

---

### Post by bab1 on 2008-07-27
I'll bet you are installing a "Windows printer via Samba".  You do not need Samba to share a Windows hosted printer.  Linux uses CUPS (Common Unix Printing System) to do that.  You can get to the config page from you web browser.  In the navigation  bar type:```
[COLOR="Blue"]**http://localhost:631**[/COLOR]
```  
You can also install through System ->Administration ->Printing. See: [[COLOR="Purple"]Sharing a Windows Printer[/COLOR]]("http://www.willmer.com/kb/2005/05/printing-to-windows-xp-printer-from-ubuntu/") and [[COLOR="Green"]Sharing a Windows Printer 2[/COLOR]]("http://raldztech.blogspot.com/2005/12/share-windows-xp-printer-to-linux.html")

Be sure to "share" the printer on the Windows host.

---

### Post by anderskitson on 2008-07-27
allright, well I am not sure how to get cups working properly. I tried a lpr/lpr hosted printer with 
> lpd://192.168.75.106/SamsungLaser
I have a static Ip on the windows machine, and the host name of the printer is SamsungLaser

I am nit familiar with cups so I need some help setting it up. 

In regards to samba, I did have it working that way at one point, but If cups works thats great, Although I would still like to get files sharing working again. The windows machine can see my machine and view my files on there work group, but I cant even see them from my computer, which I used to be able to.

---

### Post by bab1 on 2008-07-27
Lets deal with the printer and then we will get to the file sharing.  Have you tried the web based interface for cups (localhost:631)?  I do not have a printer attached to a computer.  Mine has it's own built in print server, but I am sure we can do this.

---

### Post by anderskitson on 2008-07-27
Yes thats what I tried was the web based interface, I selected lpr/lpr hosted printer in a drop down menu. Then I entered this as the device url

lpd://192.168.75.106/SamsungLaser 
it does not seem to like that so I tried

lpd://Antec-AMD-Slim/SamsungLaser (antecamdslim is the host name)

Neither worked

---

### Post by bab1 on 2008-07-27
I belive we will have to use IPP instead of LPD.  I need to find the printer data for you.  What is the exact model of the printer?

---

### Post by anderskitson on 2008-07-27
Samsung scx-4521

---

### Post by bab1 on 2008-07-27
Are we using XP on the windows side?  It looks like we have to set up the printer to be IPP aware in Windows.  Did you see my PM to you?

---

