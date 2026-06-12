---
title: "SAMBA will not stop asking for authentication"
date: 2012-06-29
forum: New to Ubuntu
---

### Post by j0eh4x on 2012-06-29
i've tried everything, i've tried multiple guides on the internet, ive even downgraded to 11.10 and samba will still not stop asking for authentication... 
im currently using this guide [http://www.howtoforge.com/creating-a-home-media-and-file-server-with-ubuntu](http://www.howtoforge.com/creating-a-home-media-and-file-server-with-ubuntu)

my smb.conf is 
> 
[global]
workgroup = WORKGROUP #(Set this to your Windows workgroup)
netbios name = WORKGROUP  #(Set this to your Windows workgroup)
security = share
[Server] #(Set this to the name you want the shared folder to have)
comment = entire shared drive #(Comments about the shared folder)
path = /srv/files/ #(Path to the shared folder or mount-point of harddrive)
read only = no
guest ok = yes
writable = yes

first off though... I do not care where i need to put my share... I'll put it anywhere. I also dont care if it requires authentication or doesnt. I just want it to work. Even with authentication it wont take my user and password. So please someone help me, also im using server edition so i only have command line

---

### Post by Morbius1 on 2012-06-29
Well, I'll tell you I'm not going to go through the steps necessary to rebuild that smb.conf so that it looks like the default but there are some things straight off that you can check:
>  netbios name = WORKGROUP  #(Set this to your Windows workgroup)If that's what the HowTo states then stop reading the HowTo. The netbios name by default in Debian based systems is your hostname. You don't need the line at all if your host name is 15 characters or less in length but if you want to add one anyway WORKGRROUP seems an odd choice since that is the name of your ... well ... workgroup.

But the one thing you should do is check the permissions of the shared directory. Your share allows write access to guests so if you do a:
```
ls -al /srv/files/
```The entire path has to allow for "others" to gain access. So, for example:
/srv should be something like: drwxr-xr-x
/srv/files has to be drwxrwxrwx

Hopefully, you copied the default. If not there is a copy of it with one mistake in /usr/share/samba/smb.conf.

---

### Post by j0eh4x on 2012-06-29
> **Morbius1 said:**
> Well, I'll tell you I'm not going to go through the steps necessary to rebuild that smb.conf so that it looks like the default but there are some things straight off that you can check:
If that's what the HowTo states then stop reading the HowTo. The netbios name by default in Debian based systems is your hostname. You don't need the line at all if your host name is 15 characters or less in length but if you want to add one anyway WORKGRROUP seems an odd choice since that is the name of your ... well ... workgroup.

But the one thing you should do is check the permissions of the shared directory. Your share allows write access to guests so if you do a:
```
ls -al /srv/files/
```The entire path has to allow for "others" to gain access. So, for example:
/srv should be something like: drwxr-xr-x
/srv/files has to be drwxrwxrwx

Hopefully, you copied the default. If not there is a copy of it with one mistake in /usr/share/samba/smb.conf.



ive restored the default smb.conf and the output was

> drwxrwxrwx 3 root root 4096 2012-06-29 13:51 .
drwxr-xr-x 3 root root 4096 2012-06-29 12:44 ..
drwxrwxrwx 3 root root 4096 2012-06-29 13:53 unsorted


---

### Post by Morbius1 on 2012-06-29
Post the output of the following command so people can see how this is all set up:
```
testparm -s
```

---

### Post by Skydiel on 2012-06-29
@Morbius1
Correct me if I am wrong. Another way to solve this is:
[LIST=1]
[*]Map this share on windows using a different credential. Use a valid user on Linux and the authentication will stop showing up.
[*]Use a username and password that is identical in both systems. You are already authenticated on windows, so no need to do it again.
[/LIST]

---

### Post by j0eh4x on 2012-06-29
testparm -s output
> 
[global]
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

[print$]
        comment = Printer Drivers
        path = /var/lib/samba/printers

[Share]
        path = /srv/files
        read only = No
        guest only = Yes
        guest ok = Yes


smb.conf

> #
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
   security = share

# You may wish to use password encryption.  See the section on
# 'encrypt passwords' in the smb.conf(5) manpage before enabling.
   encrypt passwords = no

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

[Share]
writable = yes
path = /srv/files
public = yes
guest ok = yes
guest only = yes
guest account = nobody
browsable = yes



---

### Post by j0eh4x on 2012-06-29
> **Skydiel said:**
> @Morbius1
Correct me if I am wrong. Another way to solve this is:
[LIST=1]
[*]Map this share on windows using a different credential. Use a valid user on Linux and the authentication will stop showing up.
[*]Use a username and password that is identical in both systems. You are already authenticated on windows, so no need to do it again.
[/LIST]

i've tried using my linux login credentials and it doesn't go through, and they are also the same as my windows machine

---

### Post by Morbius1 on 2012-06-29
Edit smb.conf and change these 2 lines:
> security = SHARE
        encrypt passwords = NoTO this:
> security = user
encrypt passwords = YesThen restart samba:
```
sudo service smbd restart
```
[COLOR=Blue]**EDIT**[/COLOR]: Sorry, I went for the most obvious first:

You might want to remove this:
>          guest only = Yes
From the share definition as well.

---

### Post by j0eh4x on 2012-06-29
tried all the above and still isn't working, when it asks my for password i chose to user another account and tried joe then password, when that didnt work i tried joe@servername then password... it took longer to say no but it still says no

---

### Post by Morbius1 on 2012-06-29
Here's the thing. You have created a guest share that doesn't require authentication. 

The only way you would get an authentication prompt in Windows ( and I'm assuming the client is Windows here ) is if you have the same username on both systems but your samba password on the server for that user is different from the Window joe's login password. 

So if the Windows user is named joe and you have a joe account of the server you have 2 choices:

Make the samba password for joe match the Windows user's login password. [COLOR=Blue]*This is where the samba myth about having all user names and passwords match started. *[/COLOR]

Or, Remove the samba password for joe entirely since this is after all a guest share:
```
sudo smbpasswd -x joe
```

---

### Post by j0eh4x on 2012-06-29
all usernames and passwords matched. So since that wasn't working i tried \

> sudo smbpasswd -x joe

still asking for authentication 
:(

---

### Post by Morbius1 on 2012-06-29
I'll be honest with you. At this point I don't know what the problem is now.

I don't suppose there's some kind of encryption thing going on on the server is there?

Can the samba client on the server access the samba server's share?

Run the following command on the server itself:
```
smbclient //servername/Share
```When it asks you for a password don't give it one just hit enter. You should get a prompt that looks like this:
> smb:\>
To escape from this just enter:
```
quit
```

---

### Post by j0eh4x on 2012-06-29
yah that worked. When I first installed windows i accidentally put jor in for my user account but changed it to joe later. my windows file system however still uses jor, that wouldnt have anything to do with it would it ?

---

### Post by Morbius1 on 2012-06-29
That's interesting. You might want to see if there's a "jor" in the samba password database :
```
sudo pdbedit -w -L
```
If he's in there get rid of it:
```
sudo smbpasswd -x jor
```

---

### Post by j0eh4x on 2012-06-29
nope theres a nobody account...

> nobody:65534:XXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX:XXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX:[U          ]:LCT-00000000:


---

### Post by Morbius1 on 2012-06-29
I've got to shut down for the day, sorry.

I don't have a ready idea what the issue is at the moment anyway. Since a samba client can access the server's share without a password which is what you'd expect for a guest share I don't know why it's not doing the same thing for a Windows client.

A Windows client does something a Linux client does not do. It automatically passes the Windows user's actual login user name and password when it tries to access a share. In this case there is no match in the samba password database for that user so it's tagged a "Bad User" and then mapped to the Linux guest account - "nobody". You are allowing guest access so this should work at that point just like a Linux client.

Something is either being passed by Windows or getting distorted by Linux but I just don't see it yet.

---

### Post by koanhead on 2012-10-01
If you have ever used the GUI to set up shares, editing smb.conf will cause trouble. The GUI stores configuration information elsewhere than smb.conf (in /var/lib/samba/usershares/, see [https://help.ubuntu.com/community/Samba/SambaServerGuide](https://help.ubuntu.com/community/Samba/SambaServerGuide) for details). In my experience this leads to all sorts of bizarre behavior, including disappearing shares and permissions changing apparently at random.

My advice is to check /var/lib/samba/usershares (or run 'net usershare info') to see if there's anything recorded there, and if there is, see if there are any conflicts with your smb.conf (IOW nothing in 'testparm' should conflict with 'net usershare info'). If both of these agree and you still have trouble then consider removing the config data from /var/lib/samba/usershares/ (leaving smb.conf intact) and restart samba. If you still have problems after that it might be time to file a bug. If you do file a bug consider marking it related to [https://bugs.launchpad.net/bugs/1048119](https://bugs.launchpad.net/bugs/1048119) (which I filed earlier, but was rightly marked 'invalid' because I didn't read the docs correctly- don't be like me...)

Good luck!

---

### Post by Orez96 on 2012-10-05
I encountered the same problem.
So on the Windows machine I created a user with the name Optiplex owner
The Ubuntu machine is an Optiplex desktop and has but one user, owner.

It worked.
Try that.

Ubuntu user = abc
Windows user = Ubuntu computer name owner

---

