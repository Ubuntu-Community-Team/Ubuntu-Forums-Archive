---
title: "Network computers share intermittently"
date: 2014-01-07
forum: New to Ubuntu
---

### Post by kaurie on 2014-01-07
I have a home network and share files from two computers

The "Ubuntu (12.04)" (64 bit operating system) is called CLINO
The "Windows 7" (64 bit operating system) is called WINO

WINO always sees the shared files in CLINO

WHILE At boot up CLINO always saw the shared files on WINO  - after a day the link was lost and I have to reboot CLINO to restore it

I was messing about the other day (trying to fix another problem) and completely lost (from CLINO) the link to WINO.
> smbtree


showed me \\WINO but no files

I read somewhere that dhclient eth0 might show me something helpful so in desperation tryed it 

> 
 sudo dhclient eth0
Rather than invoking init scripts through /etc/init.d, use the service(8)
utility, e.g. service smbd reload

Since the script you are attempting to invoke has been converted to an
Upstart job, you may also use the reload(8) utility, e.g. reload smbd
RTNETLINK answers: File exists


So I tried 
> 
sudo service smbd reload


I now can see the shared files on WINO from CLINO

My questions are

[LIST=1]
[*]Was I just lucky
[*]When I loose the WINO files again should I just use the sudo service smbd reload command
[*]Is there anyway of "keeping" the link so that I dont have to use "sudo service smbd reload"
[/LIST]

---

### Post by tfrue on 2014-01-07
I'm not too sure on how to configure and share folders with Samba using the GUI, but I can give you some information with the terminal.

I use Samba to share folders across my network, but I would like to see the output of ```
cat /etc/samba/smb.conf
```

---

### Post by kaurie on 2014-01-07
Thanks for the reply

here it is

> cat /etc/samba/smb.conf
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

### Post by tfrue on 2014-01-07
You don't have any shares defined, which doesn't really suprise me lol, but I'm not too sure on how to configure and share folders with Samba using the GUI, but I can give you some information with the terminal.
I use Samba to share folders across my network, so with Samba you define shares in the config file, smb.conf, and pass options through those shares. A share looks like:
```
[Window's]
comment= Window Share
path= /share/win
read only= no
etc...
```

To edit smb.conf, type:
```
sudo vim /etc/samba/smb.conf

Scroll all the way to the bottom and press 'i' and type:
[CODE][Share]
comment= New Share
path= /media/share
browseable= yes
writeable= yes
read only= no
guest ok= no  #I want to note that the last two are optional but are implemented if you want security, and if you do, you need to uncomment the line 'security=user' under the Authentication header. 
valid users= your username

```
To save and exit, press 'esc', hold shift and press 'z' twice. Or type a semi-colon, then type 'wq' 

If you decide to use the valid users option, you will type: 
```
sudo smbpasswd -a your username
``` 

Then you need to restart the samba processes by typing:
```
sudo service smbd restart
and
sudo service nmbd restart
``` 
You should then be able to access the shares from your Window's and Linux machines!

Good Luck and let me know if you have any problems

Chris

---

### Post by tfrue on 2014-01-07
To uncomment the ;security=user, just delete the ; in front of the sentece and save the file.And you can use nano or what ever text editor

---

### Post by bab1 on 2014-01-07
My guess is that the OP is using usershares (created using the GUI.  You can see the usershares with this command```
 net usershare info --long
```

But the root  problem may be in the method of displaying the shares.  But lets see a little more debug from CLINO using ```
smbtree -d3
```

---

### Post by kaurie on 2014-01-08
I am sorry first I have made a mistake in the orginal post and the WINDOWS machine is called NU-WINO - (There is also a Vista Windows machine called PIP on the network and a few other things as well including a laser printer and an epson printer) Note that the lazer printer always seems to be connected.
I am also sorry that I have not replied earlier and my replies in the next 12 hours will be very spotty. - I have to have a colonoscopy in a few hours and things are really rushed 

This situation is really weird - Five minutes ago I could not see NU-WINO when clicking on the home folder in the "Dash" and using the "GO Network" command.
I could not see the "Windows Network" Icon but when clicked nothing happened

After using a combination of
[LIST=1]
[*]sudo service smbd restart
[*]sudo service nmbd restart
[*]smbtree -d3
[*]smbtree
[/LIST]


On Folder network (on clicking) First the Workgroup icon and also the WINO icon appears and once again I can see the folders I want to acess.


Now while I am writing this post the Nu-Wino icon is still there but the folders are no longer there
On the other hand the PIP icon gives folders that I can acess.

I have done a smbtree -d3
```
smbtree -d3
lp_load_ex: refreshing parameters
Initialising global parameters
rlimit_max: increasing rlimit_max (1024) to minimum Windows limit (16384)
params.c:pm_process() - Processing configuration file "/etc/samba/smb.conf"
Processing section "[global]"
added interface eth0 ip=fe80::221:86ff:fe13:dd80%eth0 bcast=fe80::ffff:ffff:ffff:ffff%eth0 netmask=ffff:ffff:ffff:ffff::
added interface eth0 ip=192.168.1.101 bcast=192.168.1.255 netmask=255.255.255.0
Enter lpa's password: 
tdb(/var/run/samba/gencache.tdb): tdb_open_ex: could not open file /var/run/samba/gencache.tdb: Permission denied
resolve_lmhosts: Attempting lmhosts lookup for name WORKGROUP<0x1d>
resolve_lmhosts: Attempting lmhosts lookup for name WORKGROUP<0x1d>
name_resolve_bcast: Attempting broadcast lookup for name WORKGROUP<0x1d>
Got a positive name query response from 192.168.1.101 ( 192.168.1.101 )
Connecting to host=192.168.1.101
Connecting to 192.168.1.101 at port 445
Doing spnego session setup (blob length=58)
got OID=1.3.6.1.4.1.311.2.2.10
got principal=NONE
Got challenge flags:
Got NTLMSSP neg_flags=0x608a8215
NTLMSSP: Set final flags:
Got NTLMSSP neg_flags=0x60088215
NTLMSSP Sign/Seal - Initialising with flags:
Got NTLMSSP neg_flags=0x60088215
name_resolve_bcast: Attempting broadcast lookup for name __MSBROWSE__<0x1>
Got a positive name query response from 192.168.1.101 ( 192.168.1.101 )
resolve_lmhosts: Attempting lmhosts lookup for name WORKGROUP<0x1d>
resolve_lmhosts: Attempting lmhosts lookup for name WORKGROUP<0x1d>
name_resolve_bcast: Attempting broadcast lookup for name WORKGROUP<0x1d>
Got a positive name query response from 192.168.1.101 ( 192.168.1.101 )
Connecting to host=192.168.1.101
Connecting to 192.168.1.101 at port 445
Doing spnego session setup (blob length=58)
got OID=1.3.6.1.4.1.311.2.2.10
got principal=NONE
Got challenge flags:
Got NTLMSSP neg_flags=0x608a8215
NTLMSSP: Set final flags:
Got NTLMSSP neg_flags=0x60088215
NTLMSSP Sign/Seal - Initialising with flags:
Got NTLMSSP neg_flags=0x60088215
WORKGROUP
resolve_lmhosts: Attempting lmhosts lookup for name WORKGROUP<0x1d>
resolve_lmhosts: Attempting lmhosts lookup for name WORKGROUP<0x1d>
name_resolve_bcast: Attempting broadcast lookup for name WORKGROUP<0x1d>
Got a positive name query response from 192.168.1.101 ( 192.168.1.101 )
Connecting to host=192.168.1.101
Connecting to 192.168.1.101 at port 445
Doing spnego session setup (blob length=58)
got OID=1.3.6.1.4.1.311.2.2.10
got principal=NONE
Got challenge flags:
Got NTLMSSP neg_flags=0x608a8215
NTLMSSP: Set final flags:
Got NTLMSSP neg_flags=0x60088215
NTLMSSP Sign/Seal - Initialising with flags:
Got NTLMSSP neg_flags=0x60088215
	\\PIP            		PIP
Connecting to host=PIP
resolve_lmhosts: Attempting lmhosts lookup for name PIP<0x20>
resolve_lmhosts: Attempting lmhosts lookup for name PIP<0x20>
resolve_wins: Attempting wins lookup for name PIP<0x20>
resolve_wins: WINS server resolution selected and no WINS servers listed.
resolve_hosts: Attempting host lookup for name PIP<0x20>
resolve_hosts: getaddrinfo failed for name PIP [No address associated with hostname]
name_resolve_bcast: Attempting broadcast lookup for name PIP<0x20>
Got a positive name query response from 192.168.1.108 ( 192.168.1.108 )
Connecting to 192.168.1.108 at port 445
Doing spnego session setup (blob length=46)
got OID=1.3.6.1.4.1.311.2.2.10
got principal=<null>
Got challenge flags:
Got NTLMSSP neg_flags=0x628a8215
NTLMSSP: Set final flags:
Got NTLMSSP neg_flags=0x60088215
NTLMSSP Sign/Seal - Initialising with flags:
Got NTLMSSP neg_flags=0x60088215
		\\PIP\SHOUT          	
		\\PIP\SHINN          	
		\\PIP\Public         	
		\\PIP\Media          	
		\\PIP\J              	
		\\PIP\IPC$           	Remote IPC
		\\PIP\D$             	Default share
		\\PIP\C$             	Default share
		\\PIP\ADMIN$         	Remote Admin
	\\NU-WINO        		
Connecting to host=NU-WINO
resolve_lmhosts: Attempting lmhosts lookup for name NU-WINO<0x20>
resolve_lmhosts: Attempting lmhosts lookup for name NU-WINO<0x20>
resolve_wins: Attempting wins lookup for name NU-WINO<0x20>
resolve_wins: WINS server resolution selected and no WINS servers listed.
resolve_hosts: Attempting host lookup for name NU-WINO<0x20>
resolve_hosts: getaddrinfo failed for name NU-WINO [No address associated with hostname]
name_resolve_bcast: Attempting broadcast lookup for name NU-WINO<0x20>
Got a positive name query response from 192.168.1.106 ( 192.168.1.106 )
Connecting to 192.168.1.106 at port 445
Doing spnego session setup (blob length=293)
got OID=1.3.6.1.4.1.311.2.2.30
got OID=1.3.6.1.4.1.311.2.2.10
got principal=<null>
Got challenge flags:
Got NTLMSSP neg_flags=0x628a8215
NTLMSSP: Set final flags:
Got NTLMSSP neg_flags=0x60088215
NTLMSSP Sign/Seal - Initialising with flags:
Got NTLMSSP neg_flags=0x60088215
SPNEGO login failed: Logon failure
	\\EPSOND883B7    		
Connecting to host=EPSOND883B7
resolve_lmhosts: Attempting lmhosts lookup for name EPSOND883B7<0x20>
resolve_lmhosts: Attempting lmhosts lookup for name EPSOND883B7<0x20>
resolve_wins: Attempting wins lookup for name EPSOND883B7<0x20>
resolve_wins: WINS server resolution selected and no WINS servers listed.
resolve_hosts: Attempting host lookup for name EPSOND883B7<0x20>
resolve_hosts: getaddrinfo failed for name EPSOND883B7 [No address associated with hostname]
name_resolve_bcast: Attempting broadcast lookup for name EPSOND883B7<0x20>
Got a positive name query response from 192.168.1.107 ( 192.168.1.107 )
Connecting to 192.168.1.107 at port 445
		\\EPSOND883B7\MEMORYCARD     	EPSON
		\\EPSOND883B7\IPC$           	IPC Service
	\\CLINO          		CLINO server (Samba, Ubuntu)
Connecting to host=CLINO
resolve_lmhosts: Attempting lmhosts lookup for name CLINO<0x20>
resolve_lmhosts: Attempting lmhosts lookup for name CLINO<0x20>
resolve_wins: Attempting wins lookup for name CLINO<0x20>
resolve_wins: WINS server resolution selected and no WINS servers listed.
resolve_hosts: Attempting host lookup for name CLINO<0x20>
Connecting to 127.0.1.1 at port 445
Doing spnego session setup (blob length=58)
got OID=1.3.6.1.4.1.311.2.2.10
got principal=NONE
Got challenge flags:
Got NTLMSSP neg_flags=0x608a8215
NTLMSSP: Set final flags:
Got NTLMSSP neg_flags=0x60088215
NTLMSSP Sign/Seal - Initialising with flags:
Got NTLMSSP neg_flags=0x60088215
		\\CLINO\Music          	
		\\CLINO\SWORK          	
		\\CLINO\Dell-Laser-Printer-1700n	Dell Laser Printer 1700n
		\\CLINO\Generic-PCL-Laser	Generic PCL Laser
		\\CLINO\IPC$           	IPC Service (CLINO server (Samba, Ubuntu))
		\\CLINO\print$         	Printer Drivers

```


smbtree gives
```
smbtree 
Enter lpa's password: 
WORKGROUP
	\\PIP            		PIP
		\\PIP\SHOUT          	
		\\PIP\SHINN          	
		\\PIP\Public         	
		\\PIP\Media          	
		\\PIP\J              	
		\\PIP\IPC$           	Remote IPC
		\\PIP\D$             	Default share
		\\PIP\C$             	Default share
		\\PIP\ADMIN$         	Remote Admin
	\\NU-WINO        		
	\\EPSOND883B7    		
		\\EPSOND883B7\MEMORYCARD     	EPSON
		\\EPSOND883B7\IPC$           	IPC Service
	\\CLINO          		CLINO server (Samba, Ubuntu)
		\\CLINO\Music          	
		\\CLINO\SWORK          	
		\\CLINO\Dell-Laser-Printer-1700n	Dell Laser Printer 1700n
		\\CLINO\Generic-PCL-Laser	Generic PCL Laser
		\\CLINO\IPC$           	IPC Service (CLINO server (Samba, Ubuntu))
		\\CLINO\print$         	Printer Drivers
```

I have just retsarted smbd and back NU-WINO Comes

```
lpa@CLINO:~$ sudo service smbd restart
lpa@CLINO:~$ sudo service nmbd restart

```

NU-WINO has just come back again.

Any advice would be appreciated.

---

### Post by bab1 on 2014-01-08
> **kaurie said:**
> I am sorry first I have made a mistake in the orginal post and the WINDOWS machine is called NU-WINO - (There is also a Vista Windows machine called PIP on the network and a few other things as well including a laser printer and an epson printer) Note that the lazer printer always seems to be connected.

What shares seem to go away and on which machine are we viewing these shares.  By this i mean you have several combinations:
[LIST]
[*]  Windows shares not showing up on the Ubuntu machine 
[*]  Ubuntu (Samba) shares not showing up on a Windows machine
[*]  Windows shares not showing up on a Windows machine
[*]  Ubuntu (Samba) shares not showing up on the Ubuntu machine
[/LIST]
> 

I am also sorry that I have not replied earlier and my replies in the next 12 hours will be very spotty. - I have to have a colonoscopy in a few hours and things are really rushed 

This situation is really weird - Five minutes ago I could not see NU-WINO when clicking on the home folder in the "Dash" and using the "GO Network" command.
I could not see the "Windows Network" Icon but when clicked nothing happened

After using a combination of
[LIST=1]
[*]sudo service smbd restart
[*]sudo service nmbd restart
[*]smbtree -d3
[*]smbtree
[/LIST]


On Folder network (on clicking) First the Workgroup icon and also the WINO icon appears and once again I can see the folders I want to acess.


Now while I am writing this post the Nu-Wino icon is still there but the folders are no longer there
On the other hand the PIP icon gives folders that I can acess.


This is typical of a Windows or Samba server that is misconfigured.  When the Samba Server first enters the network it announces itself and if there is no duplication it is added to the Master Browse List (held by the Master Browser).  If the Master Browser looses contact with those shares they are deleted.  This is what is happening.  They are announced by then go away.  See below in red.
> 

I have done a smbtree -d3
```
smbtree -d3
lp_load_ex: refreshing parameters
Initialising global parameters
rlimit_max: increasing rlimit_max (1024) to minimum Windows limit (16384)
params.c:pm_process() - Processing configuration file "/etc/samba/smb.conf"
Processing section "[global]"
added interface eth0 ip=fe80::221:86ff:fe13:dd80%eth0 bcast=fe80::ffff:ffff:ffff:ffff%eth0 netmask=ffff:ffff:ffff:ffff::
added interface eth0 ip=192.168.1.101 bcast=192.168.1.255 netmask=255.255.255.0
Enter lpa's password: 
tdb(/var/run/samba/gencache.tdb): tdb_open_ex: could not open file /var/run/samba/gencache.tdb: Permission denied

name_resolve_bcast: Attempting broadcast lookup for name WORKGROUP<0x1d>
Got a positive name query response from 192.168.1.101 ( 192.168.1.101 )
Connecting to host=192.168.1.101
Connecting to 192.168.1.101 at port 445
Doing spnego session setup (blob length=58)
got OID=1.3.6.1.4.1.311.2.2.10
got principal=NONE
Got challenge flags:
Got NTLMSSP neg_flags=0x608a8215
NTLMSSP: Set final flags:
Got NTLMSSP neg_flags=0x60088215
NTLMSSP Sign/Seal - Initialising with flags:
Got NTLMSSP neg_flags=0x60088215

name_resolve_bcast: Attempting broadcast lookup for name __MSBROWSE__<0x1>[COLOR="#FF0000"]<-Master Browser[/COLOR]
Got a positive name query response from 192.168.1.101 ( 192.168.1.101 )
name_resolve_bcast: Attempting broadcast lookup for name WORKGROUP<0x1d>
Got a positive name query response from 192.168.1.101 ( 192.168.1.101 )
Connecting to host=192.168.1.101
Connecting to 192.168.1.101 at port 445
Doing spnego session setup (blob length=58)
got OID=1.3.6.1.4.1.311.2.2.10
got principal=NONE
Got challenge flags:
Got NTLMSSP neg_flags=0x608a8215
NTLMSSP: Set final flags:
Got NTLMSSP neg_flags=0x60088215
NTLMSSP Sign/Seal - Initialising with flags:
Got NTLMSSP neg_flags=0x60088215

WORKGROUP
name_resolve_bcast: Attempting broadcast lookup for name WORKGROUP<0x1d>
Got a positive name query response from 192.168.1.101 ( 192.168.1.101 )
Connecting to host=192.168.1.101
Connecting to 192.168.1.101 at port 445
Doing spnego session setup (blob length=58)
got OID=1.3.6.1.4.1.311.2.2.10
got principal=NONE
Got challenge flags:
Got NTLMSSP neg_flags=0x608a8215
NTLMSSP: Set final flags:
Got NTLMSSP neg_flags=0x60088215
NTLMSSP Sign/Seal - Initialising with flags:

Got NTLMSSP neg_flags=0x60088215
	\\PIP            		PIP
Connecting to host=PIP

resolve_hosts: Attempting host lookup for name PIP<0x20>[COLOR="#FF0000"]<- Can't find the IP address via hosts (hostname)[/COLOR]
resolve_hosts: getaddrinfo failed for name PIP [No address associated with hostname]

name_resolve_bcast: Attempting broadcast lookup for name PIP<0x20>[COLOR="#FF0000"]<-Found by bcast however[/COLOR]
Got a positive name query response from 192.168.1.108 ( 192.168.1.108 )
Connecting to 192.168.1.108 at port 445
Doing spnego session setup (blob length=46)
got OID=1.3.6.1.4.1.311.2.2.10
got principal=<null>
Got challenge flags:
Got NTLMSSP neg_flags=0x628a8215
NTLMSSP: Set final flags:
Got NTLMSSP neg_flags=0x60088215
NTLMSSP Sign/Seal - Initialising with flags:
Got NTLMSSP neg_flags=0x60088215  [COLOR="#FF0000"]<- and all is displayed[/COLOR]
		\\PIP\SHOUT          	
		\\PIP\SHINN          	
		\\PIP\Public         	
		\\PIP\Media          	
		\\PIP\J              	
		\\PIP\IPC$           	Remote IPC
		\\PIP\D$             	Default share
		\\PIP\C$             	Default share
		\\PIP\ADMIN$         	Remote Admin

	\\NU-WINO        		
Connecting to host=NU-WINO

resolve_hosts: Attempting host lookup for name NU-WINO<0x20>[COLOR="#FF0000"]<- Same hostname failure here[/COLOR]
resolve_hosts: getaddrinfo failed for name NU-WINO [No address associated with hostname]
name_resolve_bcast: Attempting broadcast lookup for name NU-WINO<0x20>[COLOR="#FF0000"]<-again found by bcast however[/COLOR]
Got a positive name query response from 192.168.1.106 ( 192.168.1.106 )
Connecting to 192.168.1.106 at port 445
Doing spnego session setup (blob length=293)
got OID=1.3.6.1.4.1.311.2.2.30
got OID=1.3.6.1.4.1.311.2.2.10
got principal=<null>
Got challenge flags:
Got NTLMSSP neg_flags=0x628a8215
NTLMSSP: Set final flags:
Got NTLMSSP neg_flags=0x60088215
NTLMSSP Sign/Seal - Initialising with flags:
Got NTLMSSP neg_flags=0x60088215
SPNEGO login failed: Logon failure[COLOR="#FF0000"]<- But we have an authentication failure[/COLOR]

	\\EPSOND883B7    		
Connecting to host=EPSOND883B7

resolve_hosts: Attempting host lookup for name EPSOND883B7<0x20>COLOR="#FF0000"]<- Same hostname failure here[/COLOR]
resolve_hosts: getaddrinfo failed for name EPSOND883B7 [No address associated with hostname]
name_resolve_bcast: Attempting broadcast lookup for name EPSOND883B7<0x20>
Got a positive name query response from 192.168.1.107 ( 192.168.1.107 )
Connecting to 192.168.1.107 at port 445
		\\EPSOND883B7\MEMORYCARD     	EPSON
		\\EPSOND883B7\IPC$           	IPC Service

	\\CLINO          		CLINO server (Samba, Ubuntu)
Connecting to host=CLINO

resolve_hosts: Attempting host lookup for name CLINO<0x20>
Connecting to 127.0.1.1 at port 445
Doing spnego session setup (blob length=58)
got OID=1.3.6.1.4.1.311.2.2.10
got principal=NONE
Got challenge flags:
Got NTLMSSP neg_flags=0x608a8215
NTLMSSP: Set final flags:
Got NTLMSSP neg_flags=0x60088215
NTLMSSP Sign/Seal - Initialising with flags:
Got NTLMSSP neg_flags=0x60088215
		\\CLINO\Music          	
		\\CLINO\SWORK          	
		\\CLINO\Dell-Laser-Printer-1700n	Dell Laser Printer 1700n
		\\CLINO\Generic-PCL-Laser	Generic PCL Laser
		\\CLINO\IPC$           	IPC Service (CLINO server (Samba, Ubuntu))
		\\CLINO\print$         	Printer Drivers

```


smbtree gives
```
smbtree 
Enter lpa's password: 
WORKGROUP
	\\PIP            		PIP
		\\PIP\SHOUT          	
		\\PIP\SHINN          	
		\\PIP\Public         	
		\\PIP\Media          	
		\\PIP\J              	
		\\PIP\IPC$           	Remote IPC
		\\PIP\D$             	Default share
		\\PIP\C$             	Default share
		\\PIP\ADMIN$         	Remote Admin
	\\NU-WINO        		
	\\EPSOND883B7    		
		\\EPSOND883B7\MEMORYCARD     	EPSON
		\\EPSOND883B7\IPC$           	IPC Service
	\\CLINO          		CLINO server (Samba, Ubuntu)
		\\CLINO\Music          	
		\\CLINO\SWORK          	
		\\CLINO\Dell-Laser-Printer-1700n	Dell Laser Printer 1700n
		\\CLINO\Generic-PCL-Laser	Generic PCL Laser
		\\CLINO\IPC$           	IPC Service (CLINO server (Samba, Ubuntu))
		\\CLINO\print$         	Printer Drivers
```

I have just retsarted smbd and back NU-WINO Comes
No way to authenticate NU-WINO -- see above in red> 

```
lpa@CLINO:~$ sudo service smbd restart
lpa@CLINO:~$ sudo service nmbd restart

```

NU-WINO has just come back again.

Any advice would be appreciated.

It appears that NU-WINO is not configured correctly, The Ubuntu host (CLINO) seems to be fine.  I would fix the authentication problem before we go any further.

---

