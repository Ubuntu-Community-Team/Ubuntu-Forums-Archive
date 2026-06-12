---
title: "Linux machine visible from Windows 7 machine, but still can't access"
date: 2012-03-23
forum: New to Ubuntu
---

### Post by ButchMel on 2012-03-23
I'm setting up a file server with Ubuntu Server 10.04. 
 
Using Samba graphical interface (under Gnome GUI). 
 
I followed the following receipe, but might have missed something:
 
[http://www.liberiangeek.net/2011/10/filesharing-between-windows-and-ubuntu-11-10-oneiric-ocelot/](http://www.liberiangeek.net/2011/10/filesharing-between-windows-and-ubuntu-11-10-oneiric-ocelot/)
 
While I have shared folders on both machines, under Windows 7 I get an error 0x80070035 - the network path was not found. 
 
What am I missing?
 
Thanks,

---

### Post by mastablasta on 2012-03-23
> **ButchMel said:**
> While I have shared folders on both machines, under Windows 7 I get an error 0x80070035 - the network path was not found. 

 
you path is wrong. how did you get it?
 
Did you go to network places and then browse to your ubuntu shared folder/disk?

---

### Post by ButchMel on 2012-03-23
> **mastablasta said:**
> you path is wrong. how did you get it?
 
Did you go to network places and then browse to your ubuntu shared folder/disk?


As the tutorial suggests, I made sure that Samba was set to same WORKGROUP. I also made sure there were some folders shared on both machines (In Linux, I see the dual arrows on some of them, soI guess I did it correctly).  

I can't even browse to Ubuntu shared folders - the error message appears (in Windows) as soon as I double click the icon for the Ubuntu machine.

---

### Post by ButchMel on 2012-03-23
Ok, now I found that 'possibly' it is because I had enabled the firewall in Ubuntu (!!...why do firewall exist, I wonder !!)...
 
Now I can see the folders listing on Ubuntu (those for which share was enabled).  
 
But now I am prompted to enter my Windows network User name and password. And what I use to log on the Windows machine does not work.  So I try the user name I had created in Samba on the Ubuntu machine, and it does not work either.
 
I guess I'm slowly getting there... but damn! why I cannot access the folders I am (now) seeing from the Windows machine ?
 
Thanks,

---

### Post by Mark Phelps on 2012-03-24
> **ButchMel said:**
> As the tutorial suggests, I made sure that Samba was set to same homegroup. ..

Homegroups is something NEW with Win7.  What the tutorial mentions, and what you need ensure is the same is the Workgroup.

---

### Post by Morbius1 on 2012-03-24
If you can expand the Linux server to see it's shares and now you are confronted with a credentials denial there is a possibility that the problem isn't Samba but Linux file permissions.

We need to see how samba is set up. The HowTo you referenced mentions system-config-samba and in your posts you mentioned that the icons on the shared folders have double errors. System-config-samba doesn't do that so you are also using Samba usershares which might be conflicting. So if you post the output of both of these commands it might help with the diagnosis:
```
testparm -s
``````
net usershare info --long
```

---

### Post by ButchMel on 2012-03-24
> **Morbius1 said:**
>  So if you post the output of both of these commands it might help with the diagnosis:
```
testparm -s
``````
net usershare info --long
```

Morbius1, thanks for your reply. Here are the results of both tests:
 First one:

Load smb config files from /etc/samba/smb.conf
rlimit_max: rlimit_max (1024) below minimum Windows limit (16384)
Processing section "[printers]"
Processing section "[print$]"
Processing section "[Big_One]"
Processing section "[SONARData2]"
Processing section "[OLDWinVista]"
Loaded services file OK.
Server role: ROLE_STANDALONE
[global]
	workgroup = WAVE11
	server string = %h server (Samba, Ubuntu)
	security = SHARE
	encrypt passwords = No
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

[printers]
	comment = All Printers
	path = /var/spool/samba
	create mask = 0700
	printable = Yes
	browseable = No
	browsable = No

[print$]
	comment = Printer Drivers
	path = /var/lib/samba/printers

[Big_One]
	comment = Hard drive IDE
	path = /media/Big_One
	read only = No
	guest ok = Yes

[SONARData2]
	comment = From il Colosseo Family
	path = /media/SONARData2
	read only = No
	guest ok = Yes

[OLDWinVista]
	comment = From Il Colosseo Family Itoo
	path = /media/OLDWinVista
	read only = No
	guest ok = Yes

Second test:

 net usershare info --long
[armorial]
path=/media/SONARData2/armorial influencias musicais
comment=
usershare_acl=Everyone:F,
guest_ok=y

[videos from web]
path=/media/NetAccess_WD_MyBook/VIDEOS FROM WEB
comment=
usershare_acl=Everyone:F,
guest_ok=n

[iphonepics_backup_12sept2010]
path=/media/NetAccess_WD_MyBook/iPhonePics_backup_12sept2010
comment=
usershare_acl=Everyone:F,
guest_ok=y

[mes documents]
path=/media/Backup_WD_MyBook/Mes Documents
comment=
usershare_acl=Everyone:F,
guest_ok=n

[itunes main folder]
path=/media/NetAccess_WD_MyBook/iTunes Main Folder
comment=
usershare_acl=Everyone:F,
guest_ok=n

[old d or h]
path=/media/Backup_WD_MyBook/old D or H
comment=
usershare_acl=Everyone:F,
guest_ok=n

[cakewalk]
path=/media/SONARData2/Cakewalk Projects
comment=
usershare_acl=Everyone:F,
guest_ok=y

---

### Post by ButchMel on 2012-03-24
> **Mark Phelps said:**
> Homegroups is something NEW with Win7.  What the tutorial mentions, and what you need ensure is the same is the Workgroup.

Yes sorry, indeed, I meant ''workgroup''

---

### Post by Morbius1 on 2012-03-24
** Let's start with the easy stuff first:

Edit smb.conf as root:
```
gksu gedit /etc/samba/smb.conf
```Find and replace this:
> security = SHARE
    encrypt passwords = NoWith this:
```
security = User
encrypt passwords = Yes
```Then restart samba:
```
sudo service smbd restart
```That will get you back to the default settings. Even if your smb.conf was done perfectly the no on "encrypt passwords" would have stopped you cold.

** All of your shares are from /media and they look suspiciously like they are on NTFS partitions. If you would post the putput of this command we can see who owns them and what their permissions are:
```
ls -al /media
```** You are also sharing the same folders or at least subfolders using 2 different methods. We may eventually have to decide which ones to keep and which one to convert to the other method but let's see what the permissions are first.

---

### Post by ButchMel on 2012-03-25
Thanks very much for detailing. I made those changes and now, I get different behaviour in Windows. Not (yet) total success, but I can access content of *one* of the shared folders on the Ubuntu machine.
 
For the other shared folders, depending on which one: I either get a ''cannot access... you do not have permissions to access.....'' (without Windows popping me at all for a ID and Password....); or I do get the Ubuntu machine asking me credentials *then* Windows popping to ask me for ID and password - and yet, nothing works...) or I get both. But I only get access to one folder content... I guess we're getting somewhere, slowly.
 
Meanwhile, as you suggested, here is the output to the last command:
 
ls -al /media
total 128
drwxr-xr-x 8 root root 4096 2012-03-24 15:01 .
drwxr-xr-x 22 root root 4096 2012-03-22 19:31 ..
drwx------ 1 robert robert 49152 2012-03-11 22:22 Backup_WD_MyBook
drwxrwxrwx 1 root root 4096 2012-03-19 22:12 Big_One
-rw-r--r-- 1 root root 14 2012-03-19 21:17 .created_by_python-fstab
lrwxrwxrwx 1 root root 7 2012-03-04 22:23 floppy -> floppy0
drwxr-xr-x 2 root root 4096 2012-03-04 22:23 floppy0
drwx------ 1 robert robert 28672 2012-03-11 22:22 NetAccess_WD_MyBook
drwx------ 1 robert robert 16384 2012-03-22 18:59 OLDWinVista
drwx------ 1 robert robert 16384 2012-03-22 18:58 SONARData2
 
 
By the way, names such as 'OldVista' are names of a drive I had pulled from another machine - no more Vista on this... Just that with many drives, I was looking for a way to remember / identify which HDD was which.... :-) Lazy way I know...
 
Thanks again,

---

### Post by Morbius1 on 2012-03-25
You will notice that SONARData2, OLDWinVista, NetAccess_WD_MyBook, and Backup_WD_MyBook have Linux permissions such that "robert" is the only one who has access to the directory. You may have instructed Samba to allow guest access but "guest" is not "robert" and Samba cannot add permissions over Linux. The only one not affected by this is Big_One which has universal access in Linux.

The easiest way out of this problem is to add a line to the [global] section of smb.conf:
```
force user = robert
```Then restart samba:
```
sudo service smbd restart
```The way this will work is that the remote "guest", or the remote user who has to authenticate for those shares that require it , will be converted to "robert" after authentication and then have access to the share.

---

### Post by ButchMel on 2012-03-25
> **Morbius1 said:**
> The easiest way out of this problem is to add a line to the [global] section of smb.conf:
```
force user = robert
```Then restart samba:
```
sudo service smbd restart
```The way this will work is that the remote "guest", or the remote user who has to authenticate for those shares that require it , will be converted to "robert" after authentication and then have access to the share.
 
I just tried it, but unless I haven't wrote it atthe proper place, it unfortunately did not solve the problem... Is there a specific location within the 'global' section I should write the line?  And do I need to place a 'pound sign' in front of the line, as most other lines have in that section?
 
I placed it sort of at the end of that section (before 'network' I guess...)
 
Thanks again,

---

### Post by Morbius1 on 2012-03-25
Put it right under the workgroup line at the beginning of the section and remove the # sign. A pound sign tells the samba interpreter to ignore that line.

---

### Post by ButchMel on 2012-03-25
> **Morbius1 said:**
> Put it right under the workgroup line at the beginning of the section and remove the # sign. A pound sign tells the samba interpreter to ignore that line.

Just to make sure :


#======================= Global Settings =======================

[global]

## Browsing/Identification ###

# Change this to the workgroup/NT-domain name your Samba server will part of
	workgroup = wave11
force user = robert

# server string is the equivalent of the NT Description field
	server string = %h server (Samba, Ubuntu)

# Windows Internet Name Serving Support Section:
# WINS Support - Tells the NMBD component of Samba to enable its WINS Server
#   wins support = no

---

### Post by Morbius1 on 2012-03-25
That is correct. 

Just make sure you restart samba after you save the file:
```
sudo service smbd restart
```
Then wait a few minutes. The network has a conniption when samba is restarted and needs time to settle down.

---

### Post by ButchMel on 2012-03-25
> **Morbius1 said:**
> That is correct. 

Just make sure you restart samba after you save the file:
```
sudo service smbd restart
```
Then wait a few minutes. The network has a conniption when samba is restarted and needs time to settle down.

I did that, waited a few minutes, restarted the Windows machine to make sure, but unfortunately it did not correct the issue...  I thought to copy the entire samba config, if something can be pointed:

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
	workgroup = wave11
force user = robert

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
#   security = User

# You may wish to use password encryption.  See the section on
# 'encrypt passwords' in the smb.conf(5) manpage before enabling.
	encrypt passwords = Yes

# If you are using encrypted passwords, Samba will need to know what
# password database type you are using.  
;	passdb backend = tdbsam

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
;	usershare max shares = 100

# Allow users who've been granted usershare privileges to create
# public shares, not just authenticated ones
	usershare allow guests = yes
	security = share
;	guest ok = no
;	guest account = nobody

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

[Big_One]
	path = /media/Big_One
	writeable = yes
;	browseable = yes
	guest ok = yes
	comment = Hard drive IDE

[SONARData2]
	path = /media/SONARData2
	writeable = yes
;	browseable = yes
	comment = From il Colosseo Family
	guest ok = yes

[OLDWinVista]
	path = /media/OLDWinVista
	writeable = yes
;	browseable = yes
	comment = From Il Colosseo Family Itoo
	guest ok = yes

---

### Post by Morbius1 on 2012-03-25
BTW, You've still got security set to share:
> # Allow users who've been granted usershare privileges to create
# public shares, not just authenticated ones
usershare allow guests = yes
[COLOR=Blue]security = share[/COLOR]
; guest ok = no
; guest account = nobody

From Ubuntu run the following command and see if you can access the share:
```
nautilus smb://wave11/SONARData2
```

---

### Post by ButchMel on 2012-03-25
> **Morbius1 said:**
> BTW, You've still got security set to share:


From Ubuntu run the following command and see if you can access the share:
```
nautilus smb://wave11/SONARData2
```

I get this :

Could not display "smb://wave11/sonardata2/".
Error: Failed to mount Windows share
Please select another viewer and try again.

(Please note that the Windows machine is shut down...)

---

### Post by Morbius1 on 2012-03-25
That's a linux permissions error.

Let's go through the basics again and post the output of:
```
testparm -s
```Forget that. For some reason I thought your Ubuntu machine name was wave11. Redo the command with the correct host name please:
```
 nautilus smb://hostname/SONARData2
```
Change "hostname" to your machine name on ubuntu

---

### Post by ButchMel on 2012-03-25
[QUOTE=Morbius1;11793440]That's a linux permissions error.

Let's go through the basics again and post the output of:
```
testparm -s
```

When trying the second nautilus command, I get the message outlines in my previous message.

Btw, under Mac OS X I have similar results - can only enter and access Big_One drive. (Forgot to mention: same PC, Hackintosh dual-boot with Windows 7...)

Ubuntu machine name is: CrabConnect. Using in a termibal: nautilus smb://CrabConnect/SONARData2 

I still get:
Could not display "smb://crabconnect/sonardata2/".
Error: Failed to mount Windows share
Please select another viewer and try again.





With testparm, I get the following:

~$ testparm -s
Load smb config files from /etc/samba/smb.conf
rlimit_max: rlimit_max (1024) below minimum Windows limit (16384)
Processing section "[printers]"
Processing section "[print$]"
Processing section "[Big_One]"
Processing section "[SONARData2]"
Processing section "[OLDWinVista]"
Loaded services file OK.
Server role: ROLE_STANDALONE
[global]
	workgroup = WAVE11
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
	dns proxy = No
	usershare allow guests = Yes
	panic action = /usr/share/samba/panic-action %d
	force user = robert

[printers]
	comment = All Printers
	path = /var/spool/samba
	create mask = 0700
	printable = Yes
	browseable = No
	browsable = No

[print$]
	comment = Printer Drivers
	path = /var/lib/samba/printers

[Big_One]
	comment = Hard drive IDE
	path = /media/Big_One
	read only = No
	guest ok = Yes

[SONARData2]
	comment = From il Colosseo Family
	path = /media/SONARData2
	read only = No
	guest ok = Yes

[OLDWinVista]
	comment = From Il Colosseo Family Itoo
	path = /media/OLDWinVista
	read only = No
	guest ok = Yes

---

### Post by Morbius1 on 2012-03-26
Let's review the symptoms of this problem:

***** You have one share that is not a problem:**
> [Big_One]
    comment = Hard drive IDE
    path = /media/Big_One
    read only = No
    guest ok = YesIt has the following permissions:
>  drwxrwxrwx 1 root root 4096 2012-03-19 22:12 Big_One***** You have another share that is a problem and is shared multiple time using different methods. Once using Classic sharing:**
> [SONARData2]
    comment = From il Colosseo Family
    path = /media/SONARData2
    read only = No
    guest ok = Yes
And again through Nautilus:
> [armorial]
path=/media/SONARData2/armorial influencias musicais
comment=
usershare_acl=Everyone:F,
guest_ok=y

[cakewalk]
path=/media/SONARData2/Cakewalk Projects
comment=
usershare_acl=Everyone:F,
guest_ok=y It has these permissions:
>  drwx------ 1 robert robert 16384 2012-03-22 18:58 SONARData2You fixed the permissions problem by adding "force user = robert" in smb.conf but the bad share is not accessible by WIn7, OSX, and most disturbing cannot even be accessed by the samba client on the same box:
> Could not display "smb://crabconnect/sonardata2/".
Error: Failed to mount Windows share
Please select another viewer and try again.Since I'm at a loss as to the cause of this problem let me start asking some stupid questions:

(1) The SONARData2 partition is mounted when you do the "nautilus smb://..." command right?

If you run the following command:
```
mount
```Does it show the partition as currently being mounted? If not when you go to Nautilus and mount it can you now run the "nautilus smb://...." command successfully?

(2) Is the SONARData2 partition on an external USB HDD or an internal HDD?

---

### Post by ButchMel on 2012-03-26
1) Yes it is mounted (I guess...)

robert@CrabConnect:~$ mount
/dev/mapper/CrabConnect-root on / type ext4 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
none on /sys type sysfs (rw,noexec,nosuid,nodev)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
none on /dev type devtmpfs (rw,mode=0755)
none on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
none on /dev/shm type tmpfs (rw,nosuid,nodev)
none on /var/run type tmpfs (rw,nosuid,mode=0755)
none on /var/lock type tmpfs (rw,noexec,nosuid,nodev)
none on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
/dev/sdb1 on /boot type ext2 (rw)
/dev/sdc1 on /media/Big_One type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/robert/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=robert)
/dev/sdd2 on /media/NetAccess_WD_MyBook type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
/dev/sdd1 on /media/Backup_WD_MyBook type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
/dev/sda1 on /media/OLDWinVista type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
/dev/sda2 on /media/SONARData2 type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)

2) This drive is - well let's say internal: it is on a IDE cable, even though a SATA drive - I'm using a PATA/SATA adapter.

3) I will go again through samba config and post as I *think* I now have more drives/folders that are accessible (I sort of played a little - not sure of what I was doing, but simply trying to 'reproduce' things I saw with 'Big_One', and late, yesterday, from Mac OS X I was able to access some more: can access and browse and open folders in SONARDATA2 and OLDWIN_VISTA drives (both on same physical HDD, internal, SATA connected on IDE with a SATA/PATA adapter. But this was first time I tried that under OS X. Thus I retried under Win 7 (same machine, dual-boot - Hackintosh) and still cannot access those drives (see in following post).  



4) Btw : tonight:
nautilus smb://CRABCONNECT/SONARData2  now open the window showing content of the drive :-)  (Might be that I was using small caps instead of capital, or the few changes I tried....)

---

### Post by ButchMel on 2012-03-26
Unfortunately, nothing really changed under Windows.

Either I receive directly a prompt:
Windows cannot access \\CRABCONNECT\old d or h. You do not have permissions to access.....'

OR

I'm first prompted to : 'Enter Network Password. Enter your password to connect to: CRABCONNECT. Domain ILCOLOSSEO III'

*then* (once I enter robert and password: ... 'is not accessible. You might not have permission. The specified server cannot perform the requested operation'

1) testparm -s
Load smb config files from /etc/samba/smb.conf
rlimit_max: rlimit_max (1024) below minimum Windows limit (16384)
Processing section "[printers]"
Processing section "[print$]"
Processing section "[Big_One]"
Processing section "[SONARData2]"
Processing section "[OLDWinVista]"
Processing section "[Backup_WD_MyBook]"
Processing section "[Mes Documents]"
Loaded services file OK.
WARNING: You have some share names that are longer than 12 characters.
These may not be accessible to some older clients.
(Eg. Windows9x, WindowsMe, and smbclient prior to Samba 3.0.)
Server role: ROLE_STANDALONE
[global]
	workgroup = WAVE11
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
	dns proxy = No
	usershare allow guests = Yes
	panic action = /usr/share/samba/panic-action %d
	force user = robert

[printers]
	comment = All Printers
	path = /var/spool/samba
	create mask = 0700
	printable = Yes
	browseable = No
	browsable = No

[print$]
	comment = Printer Drivers
	path = /var/lib/samba/printers

[Big_One]
	comment = Hard drive IDE
	path = /media/Big_One
	read only = No
	guest ok = Yes

[SONARData2]
	comment = From il Colosseo Family
	path = /media/SONARData2
	read only = No
	guest ok = Yes

[OLDWinVista]
	comment = From Il Colosseo Family Itoo
	path = /media/OLDWinVista
	read only = No
	guest ok = Yes

[Backup_WD_MyBook]
	path = /media/Backup_WD_MyBook
	valid users = Robert
	read only = No

[Mes Documents]
	path = /media/Backup_WD_MyBook/Mes Documents
	valid users = Robert, avahi-autoipd, avahi
	browseable = No
	browsable = No


Now:
ls -al /media

robert@CrabConnect:~$ ls -al /media
total 128
drwxr-xr-x  8 root   root    4096 2012-03-26 21:13 .
drwxr-xr-x 22 root   root    4096 2012-03-22 19:31 ..
drwx------  1 robert robert 49152 2012-03-11 22:22 Backup_WD_MyBook
drwxrwxrwx  1 root   root    4096 2012-03-25 22:58 Big_One
-rw-r--r--  1 root   root      14 2012-03-19 21:17 .created_by_python-fstab
lrwxrwxrwx  1 root   root       7 2012-03-04 22:23 floppy -> floppy0
drwxr-xr-x  2 root   root    4096 2012-03-04 22:23 floppy0
drwx------  1 robert robert 28672 2012-03-11 22:22 NetAccess_WD_MyBook
drwx------  1 robert robert 16384 2012-03-25 22:49 OLDWinVista
drwx------  1 robert robert 16384 2012-03-25 22:57 SONARData2
robert@CrabConnect:~$

---

### Post by Morbius1 on 2012-03-27
[1] You are going to have to find a way to change your security setting to "User". Right now you have it set to "SHARE":
>      security = SHAREGo into smb.conf, find all references to "security = share" and change it to:
```
security = User
```Verify that it has changed by running testparm -s . If you did it correctly there should be no reference to "security =" in the output of testparm since "User" it's the default setting.

[2] There is no such user on your Linux box named Robert:
> [Backup_WD_MyBook]
    path = /media/Backup_WD_MyBook
[COLOR=Blue]**     valid users = Robert**[/COLOR]
    read only = NoIf that's the user on your Windows box and you want that "Robert" to be the same "robert" on your Linux box then you have to do something to make it so. But the easiest thing to do is change Robert to robert in smb.conf and have the client login as robert not Robert.

Just make sure you created a samba password for robert:
```
sudo smbpasswd -a robert
```And make sure you restart samba:
```
sudo service smbd restart
```

---

### Post by ButchMel on 2012-03-28
Thanks again for taking your time: this is much appreciated!

Made those changes indeed. Unfortunately still can't access (except Big_One)...

Just wondering if there is a (simple) way to just redo things from scratch for those drives.  Also: I am going to replace (soon) / or add a 2TB drive that will be the 'real thing' for this file server - so guess that's the one I'd like to clone settings from Big_One (but also I'd leave WD_Backup there, so this one also needs to work....). Not that concerned with SonarData2 and OldWinVista (although I can access those drives from the Mac !!...).  Btw for one or two shares, I now start to have a new message adding when I try to access from the Win7 machine - refering to something such as 'can't have more than one access' (sorry can't remember the exact wording but it really seamed that I'm trying to access with more than one user name and/or password).

Result for testparm -s after changes:

robert@CrabConnect:~$ gksu gedit /etc/samba/smb.conf
robert@CrabConnect:~$ testparm -s
Load smb config files from /etc/samba/smb.conf
rlimit_max: rlimit_max (1024) below minimum Windows limit (16384)
Processing section "[printers]"
Processing section "[print$]"
Processing section "[Big_One]"
Processing section "[SONARData2]"
Processing section "[OLDWinVista]"
Processing section "[Backup_WD_MyBook]"
Processing section "[Mes Documents]"
Loaded services file OK.
WARNING: You have some share names that are longer than 12 characters.
These may not be accessible to some older clients.
(Eg. Windows9x, WindowsMe, and smbclient prior to Samba 3.0.)
Server role: ROLE_STANDALONE
[global]
	workgroup = WAVE11
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
	force user = robert

[printers]
	comment = All Printers
	path = /var/spool/samba
	create mask = 0700
	printable = Yes
	browseable = No
	browsable = No

[print$]
	comment = Printer Drivers
	path = /var/lib/samba/printers

[Big_One]
	comment = Hard drive IDE
	path = /media/Big_One
	read only = No
	guest ok = Yes

[SONARData2]
	comment = From il Colosseo Family
	path = /media/SONARData2
	read only = No
	guest ok = Yes

[OLDWinVista]
	comment = From Il Colosseo Family Itoo
	path = /media/OLDWinVista
	read only = No
	guest ok = Yes

[Backup_WD_MyBook]
	path = /media/Backup_WD_MyBook
	valid users = robert
	read only = No

[Mes Documents]
	path = /media/Backup_WD_MyBook/Mes Documents
	valid users = robert, avahi-autoipd, avahi
	browseable = No
	browsable = No
robert@CrabConnect:~$

---

### Post by ButchMel on 2012-03-28
I'm attaching 2 screenshots of what I get under 'properties' / Permissions for a folder called ''Cakewalk Projects' which is on the 'SonarData2' drive. If this could give additional hints I'm not seeing/understanding.

---

### Post by Morbius1 on 2012-03-28
**First**, I have a WIn7 machine in this menagerie and I simply can't reproduce your symptoms. "force user" is the big "fixer" for problems like this - in fact one was fixed just yesterday: [http://ubuntuforums.org/showthread.php?t=1947150](http://ubuntuforums.org/showthread.php?t=1947150)

**Second**, there are 2 methods of creating Samba shares:
[COLOR=Blue]Classic Shares[/COLOR] - share definitions are in smb.conf
[COLOR=Blue]Usershares[/COLOR] - share definitions are in /var/lib/samba/usershares and are created within Nautilus.

For the sake of your own sanity decide on one method or the other. In your case there is no way you can create a Usershare specifying that only one valid user can have access ( at least not within Nautilus ) so I would remove all of your Usershares. Just go back into Nautilus and undo the share or go into /var/lib/samba/usershares and delete all the share definition files. Run the following command to make sure all usershares have been removed - it should come back empty:
```
net usershare info --long
```**Third**, Ironically it is now easier to create and access shared folders on Linux than it is on Windows thanks to what they've done to Win7. You're getting the "multiple users" error because Windows never forgets anything that it previously did. There's a way to fix that but this is a Linux forum not a Windows forum. The only thing I can think of is to have Linux map the Windows user ( Robert ) to the corresponding Linux samba user ( robert ) so that when the Windows user tries to access a share Robert will be converted to robert automatically:

[1] Create and edit a new file as root:
```
gksu gedit /etc/samba/smbusers
```[2] Add the following line to that file:
```
robert = Robert
```[3] Save the file and add the following line to smb.conf - in the [global] section - under the workgroup line:
```
username map = /etc/samba/smbusers
```[4] Save that file and restart samba:
```
sudo service smbd restart
```**Forth**, If all else fails the only other thing I can think of is to have all these NTFS partition automount with the exact same permissions as the "Big_One". That's easy enough to do but the Backup_WD_MyBook ( external USB drive ? ) will be a problem in that it will always have to be running before you boot your system. This shouldn't be necessary with the "force user" option but I'm at a loss as to why it's not working in this case. If you want to go this last step let us know - we'll need some information about your partitions and fstab to make the change.

---

### Post by ButchMel on 2012-03-28
I will go point by point with your suggestions.  Meanwhile, after some fooling around in permissions, at least I now get something consistent:

**UNDER WINDOWS 7**:
1) still can access only Big_One
 
2) For all others, now, rather than having different ways of refusal, I get the same thing everywhere:
 
Network Error

WINDOWS CANNOT ACCESS \\CRABCONNECT\mes documents
You do not have permission to access \\CRABCONNECT\ mes documents. Contact your network administrator to request access.

For more information about permissions see Windows Help and Support

------thus you get it: no more prompt from Windows then from CrabConnect for User names and passwords... Don't know if it't really any better, but... it's consistent. 

**UNDER Mac OS X**:

1) I now access all drives defined under Samba (5 out of the 12 shares, the other ones being specific folders defined as shares... Must find out how/where) + 1 folder defined as shared.  Basically, all drives on the 3 HDD are now accessible under Mac....

2) Still have 6 folders defined as shares - not seen under Samba, guess I did that by right-clicking on the folders and went to share and permissions (as per my two images uploaded in previous post).

I'm encouraged, and will slowly give a try to your suggestions 2-3- (4?) above, which I hope can solve things under Win7 - unless I need to solve this under Windows ??.... (My sense tells me problems may lies within Windows, since I have more succes with Mac).

One question meanwhile: **should I reactivate the Firewall in Ubuntu**? Or do I risk adding more trouble?

Will keep you posted on other results as I progress. Man you deserve it ! :-)  Your help is VERY appreciated.

---

### Post by ButchMel on 2012-03-28
> **Morbius1 said:**
> [B]
**Second**, there are 2 methods of creating Samba shares:
[COLOR=Blue]Classic Shares[/COLOR] - share definitions are in smb.conf
[COLOR=Blue]Usershares[/COLOR] - share definitions are in /var/lib/samba/usershares and are created within Nautilus.

For the sake of your own sanity decide on one method or the other. In your case there is no way you can create a Usershare specifying that only one valid user can have access ( at least not within Nautilus ) so I would remove all of your Usershares. Just go back into Nautilus and undo the share or go into /var/lib/samba/usershares and delete all the share definition files. Run the following command to make sure all usershares have been removed - it should come back empty:
```
net usershare info --long
```[B]

I'd like to start with this one, but am unsure on the process and/or option.  when you mentio code, is it the first share method or second you suggest? (In other words, from terminal, do I do /var/lib/samba/usershares, OR net usershare info --long ?

And when you need to delete, you mean *everything* that will appear there?

Oh, and funny, but what appear there are exactely the 6 folders (except first called 'armorials') that I cannot access from Mac OS X (see my other reply before):

net usershare info --long
[armorial]
path=/media/SONARData2/armorial influencias musicais
comment=
usershare_acl=Everyone:F,
guest_ok=y

[videos from web]
path=/media/NetAccess_WD_MyBook/VIDEOS FROM WEB
comment=
usershare_acl=Everyone:F,
guest_ok=n

[iphonepics_backup_12sept2010]
path=/media/NetAccess_WD_MyBook/iPhonePics_backup_12sept2010
comment=
usershare_acl=Everyone:F,
guest_ok=n

[mes documents]
path=/media/Backup_WD_MyBook/Mes Documents
comment=
usershare_acl=Everyone:F,
guest_ok=n

[itunes main folder]
path=/media/NetAccess_WD_MyBook/iTunes Main Folder
comment=
usershare_acl=Everyone:F,
guest_ok=n

[old d or h]
path=/media/Backup_WD_MyBook/old D or H
comment=
usershare_acl=Everyone:F,
guest_ok=n

[cakewalk]
path=/media/SONARData2/Cakewalk Projects
comment=
usershare_acl=Everyone:F,
guest_ok=n

robert@CrabConnect:~$ /var/lib/samba/usershares 
bash: /var/lib/samba/usershares: is a directory


Thanks

---

### Post by Morbius1 on 2012-03-29
> [Mes Documents]
    path = /media/Backup_WD_MyBook/Mes Documents
    valid users = robert, avahi-autoipd, avahi
    browseable = No
    browsable = No> [mes documents]
path=/media/Backup_WD_MyBook/Mes Documents
comment=
usershare_acl=Everyone:F,
guest_ok=n
The first share is in smb.conf, it is not even browseable, it does not allow write, and only allows 3 users access.

The second share is from Nautilus, it is browseable, it does allow write, and is accessible to anyone with credentials.

I have no idea which one Samba is listening to so make a decision which one you want to keep and discard the rest. If you want the flexibility of of specifying that only specific users have access to a share then use only smb.conf shares. If you don't then use only shares you create through Nautilus.

If you want to delete all shares you created from Nautilus:

Open a root instance of Nautilus and go to /var/lib/samba/usershares:
```
gksu nautilus /var/lib/samba/usershares
```And delete all the files that are in that directory.

---

### Post by ButchMel on 2012-03-31
> **Morbius1 said:**
> If you want to delete all shares you created from Nautilus:
 
Open a root instance of Nautilus and go to /var/lib/samba/usershares:
```
gksu nautilus /var/lib/samba/usershares
```And delete all the files that are in that directory.
 
1) Ok done that. At least all folders that were not working from both Win7 *and* Mac are no longer there.
 
2) I removed a small HDD (2 partitions : OldWinVista and Sonardata2) and replaced by one brand new large 1TB empty (which I simply formatted NTFS on a Win machine).  I *just* used Samba to create a share on the drive (not on any folder inside that drive that I created after).  And still : no access from Windows 7 !! 
 
3) So now I am with only 5 drives on which I still can *only* access Big_One from Win7. (And now I have tried on another Win 7 machine and get the same result). So problem.  However, I can access the 5 drives from Mac OS X (well almost... No issue with Big_One, but 4 others, if I try to copy from mac and paste in one of these 4 drives on Ubuntu, I'm prompted that I do not have enough permissions... although it *looks* like it still put it there... )
 
So I guess we're narrowing down the problem, probably some cleaning yet to do...
 
I'll keep going through all our conversation and see if I missed (or haven't tried) something... Meanwhile if you have another idea from what I just wrote...
 
Cheers,

---

### Post by Morbius1 on 2012-03-31
Post the output of the following commands:
```
sudo blkid -c /dev/null
```
```
cat /etc/fstab
```
```
mount
```

---

### Post by ButchMel on 2012-04-01
Hi again,
 
Some sorcellery operated today, as I launched NTFS Manager in Ubuntu : it sort of asked me ''something'' while pointing exactely the problematic drives (...)  which I okayed and... Tadam !  I can now access all the drives freely, no more prompt, instantaneously, browse, write, delete, and so on... At least from Win 7 ;-) 
 
Will try it tomorrow with Mac as well. 
 
I will keep testing and tweaking, and post the results on 3 commands you just suggested, especially if I encounter other problems.
 
Morbius1 I want to thank you very sincerely for your help, details and patience.  Of course, cleaning the mess (which you led me to) definitely brought me close to the solution. This last step (for some reason I had tried something similar earlier last week and iit did not solve...)  But one great lesson I must remember:
 
1) Samba permissions cannot override Linux
2) Filesystem permissions ( (which, if I get it correctly, is Nautilus, right ?) cannot override Samba permissions.
 
And : as you pointed out: I have to use just one of the two...
 
Thanks very very much !

---

### Post by HiImTye on 2012-04-01
to get file sharing working between my (girlfriends') Windows 7 machine and my Ubuntu machine, I had to do the following:
1. on the Windows machine, make sure that the network is set to a 'work' network, not a home network
2. on the Windows machine, make sure that file sharing is on and that it allows connections from less than 128-bit encrypted connections
3. set up the share in Samba's GUI; I made a single 'Shared' folder and then added symlinks to the other folders I wanted to share. to do so, I had to edit /etc/samba/smb.conf and add the following lines under the [global] section:
```
    unix extensions = no
    wide links = yes
```4. make sure that both are in the same work group. you could do it in other work groups but it saves time navigating to other work groups to find the computers
5. as I run UFW I had to set the following UFW rules:
```
135,139,445/tcp            ALLOW       192.168.0.0/16
137,138/udp                ALLOW       192.168.0.0/16
```I have other rules for my network-enabled printer and for my Ubuntu machine to accept network-related logs from my router, but those are my rules to enable SAMBA
6. as my machine is for some reason not discoverable by her Windows 7 machine I had to manually go to my machine by name and then once mounted, make a network drive (which I assigned as Z:)

there might be more but these are the steps I remember doing atm

---

### Post by ifrisbie on 2012-10-22
I resolved my problem connecting my Windows 7 box to my Ubuntu samba (11.10).  I Had the "Windows cannot access" error (0x80070035 - the network path was not found" when trying to access the server (or share).  I tried a lot of things, but when it came down to what actually solved it (all other items reversed) it was the "Microsoft Network client: Digitally sign communications (always)" setting that was causing my problem.  Once it was disabled, I could see the shares and map the drive.

---

