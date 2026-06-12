---
title: "Share Browsing?"
date: 2008-09-24
forum: New to Ubuntu
---

### Post by wlopatin on 2008-09-24
I am real beginner at linux but have been using MSwindows, etc for a long time, was a support analyst, developer, ran a help desk, even did some internet use teaching.  So I have some knowledge, maybe dangerous.

At home I have 2 pc's on a network, one is XP and the other is VISTA.  Now I have taken a very old pc to set up as a server.  I did some online research and found that XUBUNTU as recommended for such a feat.

I got it installed, along with SAMBA, to get it to be just a simple file server to the other pc's. I installed a second HD in this server and set up a shared folder on it as well.

Now here is my problem (or issue).

From either pc, I can map a drive to the share I set up on the xubuntu server but only is I use the IP address.  When I look into network neighborhood, I see the xubuntu server by name.  When I click on it, I get a message that I do not have permission.  Again, if I go to "map a drive" and just enter the IP address (//1.1.1.1/) and click the pull down button, I can see the share I set up along with my home share. I can map a drive and have full read/write access to it.

I have read many sets of instructions on how to set up SAMBA and windows browsing and I must be missing something because everything works properly only when I specify the IP address of the server and cannot access by name.

Any ideas of what I may be doing wrong.

Thanks in advance.

---

### Post by lwvmobile on 2008-09-24
I'm not a Samba expert by any means but I just(stayed at a Holiday Inn Express last night) installed samba on a new machine yesterday and don't have the same issue. I can browse right over from windows to the samba shares via NetBIOS name but I think that there is some issue with browsing windows shares in ubuntu, but I was unclear as to whether that was a Gnome issue when share browsing in ubuntu or a samba issue. Although an issue of that sort does seem to ring a bell. Maybe check to see if samba is configured for the same workgroup as the windows machines.

Anyway, for whats its worth here is a copy of my /etc/samba/smb.conf - The file where you specify your shares and other parameters.

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
   workgroup = WORKGROUP

# server string is the equivalent of the NT Description field
   server string = %h server (Soul Society, Serverz)

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
;   create mask = 0775

# Directory creation mask is set to 0700 for security reasons. If you want to
# create dirs. with group=rw permissions, set next parameter to 0775.
;   directory mask = 0775

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


[STT320NTFS]
   comment = STT320NTFS
   read only = no
   locking = no
   path = /media/STT320NTFS
   guest ok = no

[STT120NTFS]
   comment = STT120NTFS
   read only = no
   locking = no
   path = /media/STT120NTFS
   guest ok = no

[STT120EXT3]
   comment = STT120EXT3
   read only = no
   locking = no
   path = /media/STT120EXT3
   guest ok = no

[WD250EXT]
   comment = WD250EXT
   read only = no
   locking = no
   path = /media/WDEXT250
   guest ok = no

[HOME]
   comment = HOME
   read only = no
   locking = no
   path = /home
   guest ok = no

```

To me, what kind of stands out and may be worthwhile to check is the lines

```
# Allow users who've been granted usershare privileges to create
# public shares, not just authenticated ones
   usershare allow guests = yes

# File creation mask is set to 0700 for security reasons. If you want to
# create files with group=rw permissions, set next parameter to 0775.
;   create mask = 0775

# Directory creation mask is set to 0700 for security reasons. If you want to
# create dirs. with group=rw permissions, set next parameter to 0775.
;   directory mask = 0775

[print$]
   comment = Printer Drivers
   path = /var/lib/samba/printers
   _browseable = yes_
   read only = yes
   guest ok = no

```

Maybe one of those hold the key to fixing your issue. The other thing you might try is to configure in windows, the c:\windows\system32\drivers\etc\hosts file and link the NetBIOS name to the IP address and see if that fixes it.

The way I would approach it if I could help you in person would be to first try the windows hosts file entry - open the specified file in notepad and put an entry 10.0.0.100 hit tab and then put the host name, or it may be the other way around, but it has examples.

If that did not work, I would first copy a backup of your smb.conf using
```
cp /etc/samba/smb.conf /etc/samba/smb.bkp
```

and then open your smb.conf in a text editor - sorry, I don't know what xubuntu has for one graphically; but copy and paste my example over yours except for my shares and leave yours in, if that makes any sense.

Try and work along those lines and see if you have any luck.:popcorn:

---

### Post by lintoon on 2008-09-24
Maybe it's a conflict of usernames.  I had a similar situation a while back so I created a user on the windows box which was identical to the ubuntu user (username/password).  Log into windows as that user and try again.  There must be a "fix" for it but this works for me.

Have you added your users samba password using smbpasswd?
eg
sudo smbpasswd -a <username>
then restart samba by:
sudo /etc/init.d/samba restart

---

### Post by wlopatin on 2008-09-24
Thanks for the suggestions. I am sure that the workgroup name is correct and the SMB passwords have been entered, and my windows account is the same name and password as the SMB and XUBUNTU accounts.

I assume this is all correct since I can connect perfectly by specifying the IP address rather than the server name.  I want to use the server name because it is more convenient and the address may change via DHCP.

For reference here is my SMB.CONF:

[global]


        panic action = /usr/share/samba/panic-action %d
        workgroup = lopatin
        netbios name="Linux-server"
        invalid users=root
        security=share
        wins support = no
        log file= /var/log/samba.log
        log level =3
        max log size = 1000
        syslog = 1
        encrypt passwords = true
        passdb backend = smbpasswd
        socket options = TCP_NODELAY
        dns proxy = no
        passwd program = /usr/bin/passwd %u
        passwd chat = *Enter\snew\sUNIX\spassword:* $n\n
        *Retype\snew\sUNIX\spassword:* $n\n .
        obey pam restrictions = yes
        pam password = no
        null passwords = no
        hosts allow = 192.168.0.
        hosts deny = ALL
#Share Definitions

[homes]
   comment = Home Directories
   browseable = yes
        writable = yes
        security mask = 0700
   create mask = 0700




[ntfs]
path = /media/ntfs
available = yes
browsable = yes
public = yes
writable = yes

---

### Post by vagena on 2008-09-24
Do you want to be a blonde one day and a redhead the next? One way to do this is to dye your own hair and restyle it, but you can achieve the same effect with much less effort &#8722; just buy [lace wig](http://www.cosprops.com/lacewigs.html). To select a wig that would be indistinguishable from real [human hair wigs](http://www.cosprops.com/lace-human-hair-wigs-c-10.html) and become your favorite fashion accessory, though, you need to know a few insider tips. First of all, if youre worried that [full lace wig](http://www.cosprops.com/lacewigs.html) will look natural on your head, never fear! A properly made wig &#8722; even the quality synthetic varieties &#8722; can look totally realistic. Which is best &#8722; synthetic or human hair wigs? Wigs can be synthetic or made from real human hair. Synthetic [front lace wig](http://www.cosprops.com/lacewigs.html) is cheaper, but the very cheap ones you can find online dont look real enough. On the other hand, high quality synthetic [cosplay wigs](http://www.cosprops.com/cosplay-wigs-c-5.html) like Revlon, Raquel Welch or Paula Young wigs look very real. Also, synthetic wigs are easier to care for, as you dont need to restyle them every time you wash them.

---

### Post by _sAm_ on 2008-09-24
By servername you mean hostname - are you sure you are using the correct hostname? Just type in hostname in a terminal to see what the server has. 

You can test what other pc on your LAN will see from the samba share on Xbuntu with:
smbclient -L hostname -U% -username
(change hostname to the servers hostname and change to your username)

I had this problem and learned that my router was causing it. I dont know why, but after I entered the correct hostname and IP for my server on the ruter it started to work with hostname(and DHCP has worked since).

---

### Post by wlopatin on 2008-09-25
Thanks everyone for the help and suggestions.
I did check the hostname and it is correct as listed in the SMB.CONF file.
Last night, I added the IP address and name to the VISTA hosts file.  At that time, the SAMBA was acting as the master browser. With this setting I could map a drive on VISTA using the server name (linux-server) but it still did not appear in the network neighborhood, and now I could not see the XP pc.  On the XP pc, I still could still only map the drive using IP address.
I think I have to stop the SAMBA from being a master browser; I think I have the instructions on how to stop that.  Then I'll try again.

It still appears that something is wrong with my network browsing.  Again, I can map the drive using IP address from both VISTA and XP correctly.

I don't know what my router has to do with it. All systems are connected and getting IP addresses via its DHCP and there is no place for my to make any hostname entries anyway.

---

### Post by _sAm_ on 2008-09-25
> I did check the hostname and it is correct as listed in the SMB.CONF file.

The hostname for your Xbuntu server is in /etc/hostname (just type hostname in a terminal to see it).

---

### Post by wlopatin on 2008-09-25
> **_sAm_ said:**
> The hostname for your Xbuntu server is in /etc/hostname (just type hostname in a terminal to see it).

As I said, I did that and it is correct. At least it is the same as in the SMB.CONF and is what I was looking for.
So I am still at a loss as to why I do not see the name on the windows pc's in network neighborhood.  Again if I map to drive using the ip address, all works well.

---

### Post by wlopatin on 2008-09-26
I did some more web reading, maybe making me more dangerous but I really hate to just use the ip address for this simple function.

Anyway, I read something about browsing at SAMBA.ORG and it mentioned that when a windows pc browses, it is trying to connect via an account named GUEST.  Is this a clue?  Do I need an account named GUEST?  A unix account or a SAMBA account? how to do it?

Thanks for reading...

---

### Post by gpsmikey on 2008-09-26
While I don't have an answer to your question (I am working the same issues), you may find this interesting on your config file based on information from "The Official Samba-3 howto and reference guide" that I have been reading:

*The samba daemons re-read the configuration file continuously, so it is better to have a config file with no comments in it (per info in [#1 pg 6]).  Easiest way to do that is by maintaining a master file /etc/samba/smb.conf.master that you edit.  After you are done editing, create the new smb.conf file (and validate your changes at the same time) by running *
**“testparm –s smb.conf.master > smb.conf”**

This allows you to still have a fully commented config file for your use, but Samba only has to read the version without comments which is faster.

mikey

---

### Post by issih on 2008-09-26
This is almost certainly because you are using windows networking name resolution (netbios) which isn't supported by default in ubuntu. Ubuntu expects there to be a dns server running somewhere on the local network, windows does not, it uses broadcast packets.

Anyway, the simple solution is detailed in this thread:

[http://ubuntuforums.org/showthread.php?t=88206&highlight=nsswitch](http://ubuntuforums.org/showthread.php?t=88206&highlight=nsswitch)

follow that and you ought to be able to use host names instead of ip addresses to refer to the ubuntu machine.

Hope that helps

---

### Post by Kellemora on 2008-09-26
Hi WL

I'm a total Noob, but I noticed something in your smb.conf file that just MIGHT be a problem.  
It could also just be how it appeared here too.  Don't know!

In any case, what I saw is that the SPACES are missing before and after the equal sign in some of your entries.

Some files are VERY PARTICULAR about using spaces and/or not using spaces in a command.  Don't know if that's applicable to an smb.conf file or not, but it very well could be.

If I'm wrong I'm wrong!  But sometimes (rarely) something is obvious to me as a sore thumb.  Other things just go over my head swoosh! hi hi........

TTUL
Gary

---

### Post by taladan on 2008-09-26
try adding

```
guest ok = yes
```

at the end of your global declaration.

If that doesn't work, you may have to map the guest user in this manner:

```
guest account = nobody

```
and if that doesn't work, try taking out the line

```
hosts deny = ALL

```

Hope this works for you,

Tal

---

### Post by Mighty_Moose on 2008-09-27
Forgive me if I misunderstand what you're trying to do, but if all you want to be able to do is connect to your server via start->run->\\"hostname", then you may have a router issue. I had a similar problem just a few days ago, so try checking out this thread: 

[http://www.gs1.ubuntuforums.org/showthread.php?t=927540](http://www.gs1.ubuntuforums.org/showthread.php?t=927540)

Hopefully that helps!

---

### Post by wlopatin on 2008-09-29
Thanks everyone for the great suggestions.
Unfortunately, I had to go out of town for a few weeks and this will have to wait. I will try all the suggestions and report back what I find.

Thanks again.

---

