---
title: "Samba: &quot;Some Lines couldn't be understood while reading the configuration file&quot;"
date: 2014-04-19
forum: New to Ubuntu
---

### Post by the-paul-84 on 2014-04-19
I am attempting to set up a file server to share files between all of my computers. I installed Samba and a GUI to help in managing it, but it appears the smb.conf is broken, or at least will not load.

When I opened up Samba Server Configuration (the GUI I downloaded), I get an error sayoing "Some Lines coulden't be understood while reading the configuration file. When I try to open the file from the command line using vi, and it just keeps loading (I have attached screen shots of both to illistrate what I am talking about).

Any help is much appriciated. Thanks in advance.

[ATTACH=CONFIG]252261[/ATTACH][ATTACH=CONFIG]252262[/ATTACH]

---

### Post by bab1 on 2014-04-19
> **the-paul-84 said:**
> I am attempting to set up a file server to share files between all of my computers. I installed Samba and a GUI to help in managing it, but it appears the smb.conf is broken, or at least will not load.

When I opened up Samba Server Configuration (the GUI I downloaded), I get an error sayoing "Some Lines coulden't be understood while reading the configuration file. When I try to open the file from the command line using vi, and it just keeps loading (I have attached screen shots of both to illistrate what I am talking about).

Any help is much appriciated. Thanks in advance.

[ATTACH=CONFIG]252261[/ATTACH][ATTACH=CONFIG]252262[/ATTACH]

The samba configuration file is at ```
/etc/samba/smb.conf
```

The leading / is important and you left it off in your CLI command.

The default smb,conf file works just fine.  Your problem is most likely the GUI tool.  Post the output of ```
cat /etc/samba/smb.conf
```

When you post the contents be sure to place the text BETWEEN the [code] blocks by clicking on the [SIZE=5]# [/SIZE]icon first.  This formats the text so we can read it.

---

### Post by the-paul-84 on 2014-04-19
Thanks for responding. When I run cat /etc/samba/smb.conf These are my results:

```
jpk@deathstar:~$ cat /etc/samba/smb.conf

[global]
netbios name = deathstar
server string = Samba file and print server
workgroup = Workgroup
security = user
hosts allow = 127. 192.168.0.
interfaces = 127.0.0.1/8 192.168.0.0/24
bind interfaces only = yes
remote announce = 192.168.0.255
remote browse sync = 192.168.0.255
printcap name = cups
load printers = yes
cups options = raw
printing = cups
guest account = smbguest
log file = /var/log/samba/samba.log
max log size = 1000
null passwords = no
username level = 6
password level = 6
encrypt passwords = yes
unix password sync = yes
socket options = TCP_NODELAY SO_RCVBUF=8192 SO_SNDBUF=8192
local master = no
domain master = no
preferred master = no
domain logons = no
os level = 33
logon drive = m:
logon home = \\%L\homes\%u
logon path = \\%L\profiles\%u
logon script = %G.bat
time server = no
name resolve order = wins lmhosts bcast
wins support = no
wins proxy = no
dns proxy = no
preserve case = yes
short preserve case = yes
client use spnego = no
client signing = no
client schannel = no
server signing = no
server schannel = no
nt pipe support = yes
nt status support = yes
allow trusted domains = no
obey pam restrictions = yes
enable spoolss = yes
client plaintext auth = no
disable netbios = no
follow symlinks = no
update encrypted = yes
pam password change = no
passwd chat timeout = 120
hostname lookups = no
username map = /etc/samba/smbusers
passdb backend = tdbsam
passwd program = /usr/bin/passwd '%u'
passwd chat = *New*password* %n\n *ReType*new*password* %n\n *passwd*changed*\n
add user script = /usr/sbin/useradd -d /dev/null -c 'Samba User Account' -s /dev/null '%u'
add user to group script = /usr/sbin/useradd -d /dev/null -c 'Samba User Account' -s /dev/null -g '%g' '%u'
add group script = /usr/sbin/groupadd '%g'
delete user script = /usr/sbin/userdel '%u'
delete user from group script = /usr/sbin/userdel '%u' '%g'
delete group script = /usr/sbin/groupdel '%g'
add machine script = /usr/sbin/useradd -d /dev/null -g sambamachines -c 'Samba Machine Account' -s /dev/null -M '%u'
machine password timeout = 120
idmap uid = 16777216-33554431
idmap gid = 16777216-33554431
template shell = /dev/null
winbind use default domain = yes
winbind separator = @
winbind cache time = 360
winbind trusted domains only = yes
winbind nested groups = no
winbind nss info = no
winbind refresh tickets = no
winbind offline logon = no

[homes]
comment = Home Directories
path = /home
valid users = %U
read only = no
available = yes
browseable = yes
writable = yes
guest ok = no
public = no
printable = no
locking = no
strict locking = no

[netlogon]
comment = Network Logon Service
path = /var/lib/samba/netlogon
read only = no
available = yes
browseable = yes
writable = no
guest ok = no
public = no
printable = no
locking = no
strict locking = no

[profiles]
comment = User Profiles
path = /var/lib/samba/profiles
read only = no
available = yes
browseable = yes
writable = yes
guest ok = no
public = no
printable = no
create mode = 0600
directory mask = 0700
locking = no
strict locking = no

[printers]
comment = All Printers
path = /var/spool/samba
browseable = yes
writable = no
guest ok = no
public = no
printable = yes
locking = no
strict locking = no

[pdf-documents]
path = /var/lib/samba/pdf-documents
comment = Converted PDF Documents
admin users = %U
available = yes
browseable = yes
writeable = yes
guest ok = yes
locking = no
strict locking = no

[pdf-printer]
path = /tmp
comment = PDF Printer Service
printable = yes
guest ok = yes
use client driver = yes
printing = bsd
print command = /usr/bin/gadmin-samba-pdf %s %u
lpq command =
lprm command =

jpk@deathstar:~$ 


```

---

### Post by bab1 on 2014-04-19
What version of Samba are you running?  What version of Ubuntu are you running?  How is this Samba server to be used?  As a file server or DC on a AD domain?

How did you install Samba?  What helper apps for Samba did you also install?

---

### Post by the-paul-84 on 2014-04-19
The version of Samba I am running is 3.6.3. This is to use as a file server.

The Operating System I am using isUbuntu 12.04 LTS

I had installed Samba from the Ubuntu Software. I have also installed gadmin-samba and system-config-samba.

---

### Post by bab1 on 2014-04-19
> **the-paul-84 said:**
> The version of Samba I am running is 3.6.3. This is to use as a file server.

The Operating System I am using isUbuntu 12.04 LTS

I had installed Samba from the Ubuntu Software. I have also installed gadmin-samba and system-config-samba.

The problem is the gadmin-samba.  The system-config doesn't understand the weird settings that gadmin-samba uses.  Quite frankly these settings are obscure and incorrect.

The easiest way to configure Samba is to un-install gadmin-samba like this```
sudo apt-get purge gadmin-samba
```

Unfortunately the /etc/samba/smb.conf file needs to be replaced with the default copy.  maybe you have one.  Post the output of this in the ```
 blocks[CODE]ls -l /etc/samba
```... That's an ell (l) not a one (1).

---

### Post by the-paul-84 on 2014-04-19
Thanks. I purged the gadmin. Should I remove that all together?

Here is the ls results

```
jpk@deathstar:~$ ls -l /etc/samba
total 28
-rw-r--r-- 1 root root     8 Jun  8  2012 gdbcommands
-rw-r--r-- 1 root root  3590 Apr 18 16:20 smb.conf
-rw-r--r-- 1 root root 12464 Apr 18 15:54 smb.conf.old.gadmin-samba-0.3.2
-rw-r--r-- 1 root root    91 Apr 18 15:53 smbusers
jpk@deathstar:~$ 


```

---

### Post by bab1 on 2014-04-19
> **the-paul-84 said:**
> Thanks. I purged the gadmin. Should I remove that all together?


If you have purged gadmin-samba then it's gone.  That is the only thing we need to purge.
> 

Here is the ls results

```
jpk@deathstar:~$ ls -l /etc/samba
total 28
-rw-r--r-- 1 root root     8 Jun  8  2012 gdbcommands
-rw-r--r-- 1 root root  3590 Apr 18 16:20 smb.conf
-rw-r--r-- 1 root root 12464 Apr 18 15:54 smb.conf.old.gadmin-samba-0.3.2
-rw-r--r-- 1 root root    91 Apr 18 15:53 smbusers
jpk@deathstar:~$ 


```

Post the output of this```
cat mb.conf.old.gadmin-samba-0.3.2
```
I'll bet that is the default smb.conf.  I want to see it first.

---

### Post by the-paul-84 on 2014-04-19
I tried running that, but the results were not what I had hoped for-
```
jpk@deathstar:~$ cat mb.conf.old.gadmin-samba-0.3.2
cat: mb.conf.old.gadmin-samba-0.3.2: No such file or directory


```

---

### Post by bab1 on 2014-04-19
> **the-paul-84 said:**
> I tried running that, but the results were not what I had hoped for-
```
jpk@deathstar:~$ cat mb.conf.old.gadmin-samba-0.3.2
cat: mb.conf.old.gadmin-samba-0.3.2: No such file or directory


```Oops!  i left off the leading s.  It should be ```

cat smb.conf.old.gadmin-samba-0.3.2

```

---

### Post by the-paul-84 on 2014-04-19
Pretty much the same results that time

```
jpk@deathstar:~$ cat smb.conf.old.gadmin-samba-0.3.2
cat: smb.conf.old.gadmin-samba-0.3.2: No such file or directory
jpk@deathstar:~$ 


```

---

### Post by bab1 on 2014-04-19
> **the-paul-84 said:**
> Pretty much the same results that time

```
jpk@deathstar:~$ cat smb.conf.old.gadmin-samba-0.3.2
cat: smb.conf.old.gadmin-samba-0.3.2: No such file or directory
jpk@deathstar:~$ 


```I'm being distracted here.  The cat command doesn't need the :  Use the absolute path like this```

cat /etc/samba/smb.conf.old.gadmin-samba-0.3.2

```

---

### Post by the-paul-84 on 2014-04-19
I think that di it! Thank you so much. Here are the results I got-
```
server signing = no
server schannel = no
nt pipe support = yes
nt status support = yes
allow trusted domains = no
obey pam restrictions = yes
enable spoolss = yes
client plaintext auth = no
disable netbios = no
follow symlinks = no
update encrypted = yes
pam password change = no
passwd chat timeout = 120
hostname lookups = no
username map = /etc/samba/smbusers
passdb backend = tdbsam
passwd program = /usr/bin/passwd '%u'
passwd chat = *New*password* %n\n *ReType*new*password* %n\n *passwd*changed*\n
add user script = /usr/sbin/useradd -d /dev/null -c 'Samba User Account' -s /dev/null '%u'
add user to group script = /usr/sbin/useradd -d /dev/null -c 'Samba User Account' -s /dev/null -g '%g' '%u'
add group script = /usr/sbin/groupadd '%g'
delete user script = /usr/sbin/userdel '%u'
delete user from group script = /usr/sbin/userdel '%u' '%g'
delete group script = /usr/sbin/groupdel '%g'
add machine script = /usr/sbin/useradd -d /dev/null -g sambamachines -c 'Samba Machine Account' -s /dev/null -M '%u'
machine password timeout = 120
idmap uid = 16777216-33554431
idmap gid = 16777216-33554431
template shell = /dev/null
winbind use default domain = yes
winbind separator = @
winbind cache time = 360
winbind trusted domains only = yes
winbind nested groups = no
winbind nss info = no
winbind refresh tickets = no
winbind offline logon = no

[homes]
comment = Home Directories
path = /home
valid users = %U
read only = no
available = yes
browseable = yes
writable = yes
guest ok = no
public = no
printable = no
locking = no
strict locking = no

[netlogon]
comment = Network Logon Service
path = /var/lib/samba/netlogon
read only = no
available = yes
browseable = yes
writable = no
guest ok = no
public = no
printable = no
locking = no
strict locking = no

[profiles]
comment = User Profiles
path = /var/lib/samba/profiles
read only = no
available = yes
browseable = yes
writable = yes
guest ok = no
public = no
printable = no
create mode = 0600
directory mask = 0700
locking = no
strict locking = no

[printers]
comment = All Printers
path = /var/spool/samba
browseable = yes
writable = no
guest ok = no
public = no
printable = yes
locking = no
strict locking = no

[pdf-documents]
path = /var/lib/samba/pdf-documents
comment = Converted PDF Documents
admin users = %U
available = yes
browseable = yes
writeable = yes
guest ok = yes
locking = no
strict locking = no

[pdf-printer]
path = /tmp
comment = PDF Printer Service
printable = yes
guest ok = yes
use client driver = yes
printing = bsd
print command = /usr/bin/gadmin-samba-pdf %s %u
lpq command =
lprm command =

jpk@deathstar:~$ smbstatus
Ignoring unknown parameter "update encrypted"
Ignoring unknown parameter "update encrypted"

Samba version 3.6.3
PID     Username      Group         Machine                        
-------------------------------------------------------------------

Service      pid     machine       Connected at
-------------------------------------------------------

No locked files

jpk@deathstar:~$ sudo apt-get purge gadmin-samba
[sudo] password for jpk: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  menu libwpg-0.2-2 libreoffice-emailmerge guile-1.8-libs
  libreoffice-base-core python-uno gnome-games-data libwps-0.2-2 libwpd-0.9-9
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
  gadmin-samba*
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
After this operation, 444 kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 199325 files and directories currently installed.)
Removing gadmin-samba ...
Purging configuration files for gadmin-samba ...
dpkg: warning: while removing gadmin-samba, directory '/etc/gadmin-samba' not empty so not removed.
dpkg: warning: while removing gadmin-samba, directory '/var/lib/samba/profiles' not empty so not removed.
Processing triggers for man-db ...
Processing triggers for menu ...
Processing triggers for desktop-file-utils ...
Processing triggers for bamfdaemon ...
Rebuilding /usr/share/applications/bamf.index...
Processing triggers for gnome-menus ...
jpk@deathstar:~$ ls -l /etc/samba
total 28
-rw-r--r-- 1 root root     8 Jun  8  2012 gdbcommands
-rw-r--r-- 1 root root  3590 Apr 18 16:20 smb.conf
-rw-r--r-- 1 root root 12464 Apr 18 15:54 smb.conf.old.gadmin-samba-0.3.2
-rw-r--r-- 1 root root    91 Apr 18 15:53 smbusers
jpk@deathstar:~$ clear

jpk@deathstar:~$ cat mb.conf.old.gadmin-samba-0.3.2
cat: mb.conf.old.gadmin-samba-0.3.2: No such file or directory
jpk@deathstar:~$ cat smb.conf.old.gadmin-samba-0.3.2
cat: smb.conf.old.gadmin-samba-0.3.2: No such file or directory
jpk@deathstar:~$ cat smb.conf.old.gadmin-samba-0.3.2
cat: smb.conf.old.gadmin-samba-0.3.2: No such file or directory
jpk@deathstar:~$ cat /etc/samba/smb.conf.old.gadmin-samba-0.3.2
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

Now that I have the set up correctly (I hope), can I use system-config-samba to set everythin up? Or do I need to use the commandline?

---

### Post by bab1 on 2014-04-19
Wait a minute here.  It's not set up yet!  :-)

---

### Post by the-paul-84 on 2014-04-19
Dang. I thought that was all I needed. And seriosely, I can not thank you enought for all of your help.

---

### Post by bab1 on 2014-04-19
The step needed to give you a default install is to copy the original file back to the original in name.  Then we have to configure a share.

We may have other items that need taking care of also.  We shall see.

For the first step let's make a copy of the original file.  We can to that with this command```

sudo cp /etc/samba/smb.conf.old.gadmin-samba-0.3.2  /etc/samba/smb.conf.original

```
To check your work you do this```
ls -l /etc/samba
```
Post the output of JUST that.

---

### Post by the-paul-84 on 2014-04-19
Here are the ls results-

```
total 44
-rw-r--r-- 1 root root     8 Jun  8  2012 gdbcommands
-rw-r--r-- 1 root root  3590 Apr 18 16:20 smb.conf
-rw-r--r-- 1 root root 12464 Apr 18 15:54 smb.conf.old.gadmin-samba-0.3.2
-rw-r--r-- 1 root root 12464 Apr 19 20:17 smb.conf.original
-rw-r--r-- 1 root root    91 Apr 18 15:53 smbusers


```

---

### Post by bab1 on 2014-04-19
> **the-paul-84 said:**
> Here are the ls results-

```
total 44
-rw-r--r-- 1 root root     8 Jun  8  2012 gdbcommands
-rw-r--r-- 1 root root  3590 Apr 18 16:20 smb.conf
-rw-r--r-- 1 root root 12464 Apr 18 15:54 smb.conf.old.gadmin-samba-0.3.2
-rw-r--r-- 1 root root 12464 Apr 19 20:17 smb.conf.original
-rw-r--r-- 1 root root    91 Apr 18 15:53 smbusers


```
Now we will make a backup copy of the gadmin created smb.conf with this command```

sudo cp /etc/samba/smb.conf /etc/samba/smb.conf.gadmin

```

Post he results of this again```
ls -l /etc/samba
```

If all is well we can overwrite the current smb.conf file with the default smb.conf file next.

---

### Post by the-paul-84 on 2014-04-19
I think it is looking good (but I'm not sure). Here is what I got-
```
-rw-r--r-- 1 root root     8 Jun  8  2012 gdbcommands
-rw-r--r-- 1 root root  3590 Apr 18 16:20 smb.conf
-rw-r--r-- 1 root root  3590 Apr 19 20:28 smb.conf.gadmin
-rw-r--r-- 1 root root 12464 Apr 18 15:54 smb.conf.old.gadmin-samba-0.3.2
-rw-r--r-- 1 root root 12464 Apr 19 20:17 smb.conf.original
-rw-r--r-- 1 root root    91 Apr 18 15:53 smbusers
```

---

### Post by bab1 on 2014-04-19
> **the-paul-84 said:**
> I think it is looking good (but I'm not sure). Here is what I got-
```
-rw-r--r-- 1 root root     8 Jun  8  2012 gdbcommands
-rw-r--r-- 1 root root  3590 Apr 18 16:20 smb.conf
-rw-r--r-- 1 root root  3590 Apr 19 20:28 smb.conf.gadmin
-rw-r--r-- 1 root root 12464 Apr 18 15:54 smb.conf.old.gadmin-samba-0.3.2
-rw-r--r-- 1 root root 12464 Apr 19 20:17 smb.conf.original
-rw-r--r-- 1 root root    91 Apr 18 15:53 smbusers
```
So far we're doing great.  Now we want to overwrite the smb.conf file with the default text.  We do that like this```

sudo cp /etc/samba/smb.conf.original /etc/samba/smb.conf


```

Post the output of this```

cat /etc/samba/smb.conf

```
The smb.conf file should now have the default text.

We have several steps to go before you have a working share, but we should be back to the default install now.

---

### Post by the-paul-84 on 2014-04-19
This is so cool! Here is what the file looks like now-
```
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

jpk@deathstar:~$ sudo cp /etc/samba/smb.conf.old.gadmin-samba-0.3.2  /etc/samba/smb.conf.original
[sudo] password for jpk: 
jpk@deathstar:~$ ls -l /etc/samba
total 44
-rw-r--r-- 1 root root     8 Jun  8  2012 gdbcommands
-rw-r--r-- 1 root root  3590 Apr 18 16:20 smb.conf
-rw-r--r-- 1 root root 12464 Apr 18 15:54 smb.conf.old.gadmin-samba-0.3.2
-rw-r--r-- 1 root root 12464 Apr 19 20:17 smb.conf.original
-rw-r--r-- 1 root root    91 Apr 18 15:53 smbusers
jpk@deathstar:~$ sudo cp /etc/samba/smb.conf /etc/samba/smb.conf.gadmin
jpk@deathstar:~$ clear

jpk@deathstar:~$ ls -l /etc/samba
total 48
-rw-r--r-- 1 root root     8 Jun  8  2012 gdbcommands
-rw-r--r-- 1 root root  3590 Apr 18 16:20 smb.conf
-rw-r--r-- 1 root root  3590 Apr 19 20:28 smb.conf.gadmin
-rw-r--r-- 1 root root 12464 Apr 18 15:54 smb.conf.old.gadmin-samba-0.3.2
-rw-r--r-- 1 root root 12464 Apr 19 20:17 smb.conf.original
-rw-r--r-- 1 root root    91 Apr 18 15:53 smbusers
jpk@deathstar:~$ sudo cp /etc/samba/smb.conf.original /etc/samba/smb.conf
jpk@deathstar:~$ cat /etc/samba/smb.conf
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

jpk@deathstar:~$ 


```

---

### Post by bab1 on 2014-04-19
Try and only post the last command's output.  It makes for hard reading when I have to go through all those lines.  To clear the screen all you need to do is use this command```
clear
```

The file looks great!

What type of share are you trying to make?  Public (everyone can read and write to the share) or private (only you can read and write to the share)?  In a typical Samba server setup I usually put all the data at [FONT=Courier New][SIZE=2]/srv/samba/<some_directory>[/SIZE][/FONT].  That is the Linux File System standard.

---

### Post by the-paul-84 on 2014-04-19
I was planning on havng it open fpr everyone on my network to read and write. Ideally, this would be for keeping medis (movies, music, and images) on a central location and being able to be accessed from all the laptops around the house.

---

### Post by bab1 on 2014-04-20
> **the-paul-84 said:**
> I was planning on havng it open fpr everyone on my network to read and write. Ideally, this would be for keeping medis (movies, music, and images) on a central location and being able to be accessed from all the laptops around the house.

This means we need to put all users in the user group named *users *. public **does not mean** you have to have the share available to autonomous users also.  You can limit the share to only those users that are authenticated to the network (e.g. users that login -- no guests).  Or you can have anybody that happens to be on you network (guests).  Which are you after?

---

### Post by the-paul-84 on 2014-04-20
I hate to be so needy, but could you help me out setting this up? If not, point me in the right direction?

---

### Post by bab1 on 2014-04-20
> **the-paul-84 said:**
> I hate to be so needy, but could you help me out setting this up? If not, point me in the right direction?

What do you think I'm doing here?

---

### Post by the-paul-84 on 2014-04-20
Lol, sorry.

---

### Post by bab1 on 2014-04-20
> **the-paul-84 said:**
> Lol, sorry.
How about answering my last questions.  Did you read the entire post?

---

### Post by the-paul-84 on 2014-04-20
I'd prefer to have only a set person on the network be able to access it. So logged in users, not guests

---

### Post by bab1 on 2014-04-20
Let's set up the share directory that will hold all the data.  make the directory with this command```

sudo mkdir -p /srv/samba

```

Then you need to change the group owner to the group *users* with this command```

sudo chgrp users /srv/samba

```

Now we set the proper permissions and inheritance with this command```
sudo chmod 2775 /srv/samba
```

Post the output of ```
ls -l /srv
```

---

### Post by the-paul-84 on 2014-04-20
This was the output-
```
total 4
drwxrwsr-x 2 root users 4096 Apr 19 21:21 samba


```
The word Samba was blue

---

### Post by bab1 on 2014-04-20
> **the-paul-84 said:**
> This was the output-
```
total 4
drwxrwsr-x 2 root users 4096 Apr 19 21:21 samba


```
The word Samba was blue

That's the directory that we are going to share.

Now we need to check on the user set up.

Post the output of this```
sudo pdbedit -L
```

This is the listing of all the Samba users on your machine.

---

### Post by the-paul-84 on 2014-04-20
My Samba users are-
```
nobody:65534:nobody
smbguest:1001:Samba guest account
root:0:root
jpk:1000:John Paul Keenan


```

---

### Post by bab1 on 2014-04-20
> **the-paul-84 said:**
> My Samba users are-
```
nobody:65534:nobody
smbguest:1001:Samba guest account
root:0:root
jpk:1000:John Paul Keenan


```
I assume that gadmin created the accounts.  Your account is okay but we should remove the smbguest account from samba and Ubuntu if it is there too.

Post the output of this```

getent passwd | grep 1001

```

This will tell me whether you have an Ubuntu user smbguest that we have to also remove.

---

### Post by the-paul-84 on 2014-04-20
My output from that is-
```
smbguest:x:1001:1001:Samba guest account:/dev/null:/dev/null
```

---

### Post by the-paul-84 on 2014-04-20
I forgot to add that the 1001s were both red

---

### Post by bab1 on 2014-04-20
> **the-paul-84 said:**
> My output from that is-
```
smbguest:x:1001:1001:Samba guest account:/dev/null:/dev/null
```
Lets start by removing this user from Ubuntu.  Use this command to remove the user```

sudo deluser smbguest

```

Then run this to remove the Samba user of the same name ```


sudo pdbedit  -u smbguest -x 
```

Post the output of these 2 commands```

getent passwd | grep 100

```... and 
```

sudo pdbedit -L

```

---

### Post by bab1 on 2014-04-20
> **the-paul-84 said:**
> I forgot to add that the 1001s were both red
That's because grep is looking for the number

---

### Post by the-paul-84 on 2014-04-20
Going correctly so far. Here are the outputs of the 2 commands-
```
jpk@deathstar:~$ getent passwd | grep 100
libuuid:x:100:101::/var/lib/libuuid:/bin/sh
jpk:x:1000:1000:John Paul Keenan,,,:/home/jpk:/bin/bash
jpk@deathstar:~$ sudo pdbedit -L
nobody:65534:nobody
smbguest:4294967295:Samba guest account
root:0:root
jpk:1000:John Paul Keenan


```

---

### Post by bab1 on 2014-04-20
> **the-paul-84 said:**
> Going correctly so far. Here are the outputs of the 2 commands-
```

jpk@deathstar:~$ sudo pdbedit -L
nobody:65534:nobody
smbguest:4294967295:Samba guest account
root:0:root
jpk:1000:John Paul Keenan


```
The smbguest changed but it didn't go away.  Lets use this command to remove it```
sudo smbpasswd -x smbguest
```

Output of this again```
sudo pdbedit -L
```

Were in the world are you?  What timezone?  I am GMT -8 (Pacific Coast of USA).

---

### Post by the-paul-84 on 2014-04-20
I do not think that worked. The 
sudo smbpasswd -x smbguest gave me-
```
Failed to delete entry for user smbguest.
```

The sudo pdbedit -L brought-
```
nobody:65534:nobody
smbguest:4294967295:Samba guest account
root:0:root
jpk:1000:John Paul Keenan

```

---

### Post by bab1 on 2014-04-20
> **the-paul-84 said:**
> I do not think that worked. The 
sudo smbpasswd -x smbguest gave me-
```
Failed to delete entry for user smbguest.
```

The sudo pdbedit -L brought-
```
nobody:65534:nobody
smbguest:4294967295:Samba guest account
root:0:root
jpk:1000:John Paul Keenan

```
it's not the end of the world.  Lets see if we can disable the account with this```
sudo smbpasswd -d smbguest
```

We need to add a user so you can see how to do that.  Give me a user name on one of the Windows machines that you want to have access.

---

### Post by the-paul-84 on 2014-04-20
I ran that and smbguest is now diabled. 

If the username can be the same as my Ubuntu username, I'd like to use jpk. ZIf that causes an issue, I'll use the username of subt

---

### Post by bab1 on 2014-04-20
> **the-paul-84 said:**
> I ran that and smbguest is now diabled. 

If the username can be the same as my Ubuntu username, I'd like to use jpk. ZIf that causes an issue, I'll use the username of subt
The user name jpk is already in both the Ubuntu and Samba user databases.  Is subt already used on either a Windows or an Ubuntu client.

I can add that user to the Ubuntu machine but it should match up to the user that is on the client machine.

I'll post the generic commands.  You substitute the actual user name when you have one.

To add the user to Ubuntu ```


sudo adduser <user_name>

## follow the prompts 
```

To add the user to the Samba ```
sudo smbpasswd -a <user_name>
```

Now you need to add the user to the *users* group.  Since we need to do this for your user we will use your username```

sudo adduser jpk users

```

To check that you were added to the group you use```
getent group users
```

Post the output of that.

---

### Post by the-paul-84 on 2014-04-20
I added the user account for user subt Here are the results-
```
users:x:100:jpk
```

---

### Post by bab1 on 2014-04-20
> **the-paul-84 said:**
> I added the user account for user subt Here are the results-
```
users:x:100:jpk
```

Let's add subt to the users group then```
sudo adduser subt users 
```

Then we will check the users one more time with this commands```


sudo pdbedit -L
## Samba users

getent passwd |grep 100
## User accounts

getent group users
## The users in the group users
```

Next we need to add the share definition.  Yeah!  ;-)

Have you used the text editor nano?  Is it installed on your machine? 

If it is not installed you can install it with this```
sudo apt-get install nano
```

---

### Post by the-paul-84 on 2014-04-20
Everythng is all set up and nano is installedd. This is awesome!

---

### Post by bab1 on 2014-04-20
> **the-paul-84 said:**
> Everythng is all set up and nano is installedd. This is awesome!

Open the smb.conf file like this```
sudo nano /etc/samba/smb.conf
```

Add this to the bottom of the file```

[public]
        comment = Shared Data
        path = /srv/samba
        browseable = yes

        force group = users
        writeable = yes

        create mask = 0664
        force directory mode = 2775

```
Save and exit the file.

Then reboot the Samba daemon (server) with this```
sudo seervice smbd restart
```

You should see the share in a few minutes.  Add a file and a directory and check the permissions.

---

### Post by the-paul-84 on 2014-04-20
I was able to find the folder in the UI, but when I tried to drag and drop a text file into it, I got the following error-
```
Error opening file '/srv/samba/test': Permission denied
```

---

### Post by bab1 on 2014-04-20
> **the-paul-84 said:**
> I was able to find the folder in the UI, but when I tried to drag and drop a text file into it, I got the following error-
```
Error opening file '/srv/samba/test': Permission denied
```

See if you can cut and paste it.  Also see if you can ***create*** a file on the share.  I assume you are logged into Samba as jpk.  Cut and Paste is different from Drag and Drop.  When you drag a file that is owned by some other user you will have problems.  Just one of those Samba things.

---

### Post by the-paul-84 on 2014-04-20
I tried to cut and paste, but was unable to paste. I tried opening file and doing a save as n that folder while using text editor and got the following error-
```
You do not have the permissions necessary to save the file. Please check that you typed the location correctly and try again.
```

I do not know how else to create the file in the folder

---

### Post by bab1 on 2014-04-20
> **the-paul-84 said:**
> I tried to cut and paste, but was unable to paste. I tried opening file and doing a save as n that folder while using text editor and got the following error-
```
You do not have the permissions necessary to save the file. Please check that you typed the location correctly and try again.
```

I do not know how else to create the file in the folder
Lets look at the share definition again.  Post the output ```
cat /etc/samba/smb.conf
```

From the Ubuntu CLI see if you can make a file this way```
touch /srv/samba/test.txt
```..and see if you can make a directory like this```
mkdir /srv/samba/testdir
```

Post the output of```
ls -l /srv/samba
```

---

### Post by the-paul-84 on 2014-04-20
When I tried to make a text file or a directory I got an error saying permission denied. When running the ls command, I get this output-
```
total 0
```

---

### Post by bab1 on 2014-04-20
> **the-paul-84 said:**
> When I tried to make a text file or a directory I got an error saying permission denied. When running the ls command, I get this output-
```
total 0
```
Let's backup one level.  Post the output of ```
ls -l /srv
```...and let's see the /srv permissions also with this```
ls -ld /srv
```

These are 2 different commands so they will look slightly different.

What time is it where you are?

---

### Post by the-paul-84 on 2014-04-20
It's just about midnight here. I actually need to go to bed as I have familt plans dor Easter tomorrow.

But, Running  ls -l /srv gives me
```
drwxrwsr-x 2 root users 4096 Apr 19 21:21 samba
```

and running ls -ld /srv gives me
```
drwxr-xr-x 3 root root 4096 Apr 19 21:21 /srv

```

I'll be back on tomorrow. Thank you for all of your amazing help so far today

---

### Post by bab1 on 2014-04-20
> **the-paul-84 said:**
> It's just about midnight here. I actually need to go to bed as I have familt plans dor Easter tomorrow.

But, Running  ls -l /srv gives me
```
drwxrwsr-x 2 root users 4096 Apr 19 21:21 samba
```

and running ls -ld /srv gives me
```
drwxr-xr-x 3 root root 4096 Apr 19 21:21 /srv

```

I'll be back on tomorrow. Thank you for all of your amazing help so far today

I know the problem.  Your account doesn't know that you have added jpk to the *users* group.  When you shut down and reboot tomorrow the problem will most likely be gone.

Post here tomorrow evening or Monday and I will continue with you.

---

### Post by Ubi_one_2014 on 2014-04-20
> **bab1 said:**
> Open the smb.conf file like this```
sudo nano /etc/samba/smb.conf
```

Add this to the bottom of the file```

[public]
        comment = Shared Data
        path = /srv/samba
        browseable = yes

        force group = users
        writeable = yes

        create mask = 0664
        force directory mode = 2775

```
Save and exit the file.

Then reboot the Samba daemon (server) with this```
sudo seervice smbd restart
```

You should see the share in a few minutes.  Add a file and a directory and check the permissions.

otherwise, open /etc/samba/smb.conf with kate

```
sudo kate /etc/samba/smb.conf
```

---

### Post by bab1 on 2014-04-20
> **Ubi_one_2014 said:**
> otherwise, open /etc/samba/smb.conf with kate

```
sudo kate /etc/samba/smb.conf
```
The disadvantage is that kate requires all the KDE dependencies, just as gedit requires all the Gnome dependancies.  Nano on the other hand requires none of these.  Nano is a terminal based test editor rather than a GUI based text editor.

---

### Post by the-paul-84 on 2014-04-20
I restarted the comuter and have downloaded kate and opened smb.conf with it. Once you get back, let me know the next steps to take.

---

### Post by bab1 on 2014-04-20
> **the-paul-84 said:**
> I restarted the comuter and have downloaded kate and opened smb.conf with it. Once you get back, let me know the next steps to take.
Why did you do that?  You shouldn't need to edit anything more at this point.  Have you tried adding files after booting up the machine?

---

### Post by the-paul-84 on 2014-04-21
I didn't vchange anything in that file, I had misunderstood your previous steps.

I was able to add a text file into the srv/samba folder without issue. If I add a folder with a bunch of sub folders in it, will that work?

---

### Post by bab1 on 2014-04-21
> **the-paul-84 said:**
> I didn't vchange anything in that file, I had misunderstood your previous steps.

I was able to add a text file into the [COLOR="#0000FF"]srv/samba[/COLOR] folder without issue. If I add a folder with a bunch of sub folders in it, will that work?

I was surprised.  I didn't tell you to install *kate*.  In fact I lobbied against you doing that.

I think you almost have it set up correctly now.  Add the folders and then post me the output of ```
ls -l /srv/samba
```

[COLOR="#0000FF"]Edit:  When you user the full path to a file you need to start with the leading /.  This means you need to have /srv/samba. The / is the absolute root of the entire file system.  The path srv/samba is "from whatever working directory I'm in /srv/samba.  A big difference[/COLOR]

---

### Post by the-paul-84 on 2014-04-23
Sorry for the delayed response, work kind of got in the way. But here are the results-
```
total 24
drwx------  4 jpk users 12288 Sep 29  2008 movies
drwx------  3 jpk users  4096 Apr 12 14:12 Music
drwx------ 52 jpk users  4096 Jun 10  2010 television
-rw-rw-r--  1 jpk users     9 Apr 19 23:21 test


```

---

### Post by bab1 on 2014-04-23
> **the-paul-84 said:**
> Sorry for the delayed response, work kind of got in the way. But here are the results-
```
total 24
drwx------  4 jpk users 12288 [COLOR="#FF0000"]Sep 29[/COLOR]  2008 movies
drwx------  3 jpk users  4096 [COLOR="#FF0000"]Apr 12 [/COLOR]14:12 Music
drwx------ 52 jpk users  4096 [COLOR="#FF0000"]Jun 10  2010 [/COLOR]television
-rw-rw-r--  1 jpk users     9 [COLOR="#0000FF"]**Apr 19 23:21**[/COLOR] test


```
The test file is okay.  The directories are **not** okay.  My guess is that you did create the directories.  Rather, you copied existing directories.  If you look at the dates (in red) you will see they are earlier in time.  If you create them today they should be like the file (in blue).

Create a directory named testdir1 from the Ubuntu command line ```
mkdir /srv/samba/testdir1
```

Then create a second directory at that same directory using the GUI on a Windows machine.

From the Ubuntu machine post the output of this ```
ls -l /srv/samba
```

---

### Post by the-paul-84 on 2014-04-23
I made the directory on the ubuntu machine, however I do not have a windpows computer. My pother machine is a mac, should I create it on there? 

Also, I can't see the server on my mac at all, did I do something wrong?

---

### Post by bab1 on 2014-04-23
> **the-paul-84 said:**
> I made the directory on the ubuntu machine, however I do not have a windpows computer. My pother machine is a mac, should I create it on there? 

Also, I can't see the server on my mac at all, did I do something wrong?
If you can see the share by browsing on the ubuntu machine then Samba is working correctly.  I can't tell you what to do on you Mac.  I can tell you that later versions of OSX have screwed up CIFS (SMB) sharing.  You will have to visit an OSX forum to fix that.

What is the output of what you have now?

---

### Post by the-paul-84 on 2014-04-23
So I guess to connect to smb on a mac, I need to enter in the servername/sharenameon of the smb computer. Do you know how to find that?

---

### Post by bab1 on 2014-04-23
> **the-paul-84 said:**
> So I guess to connect to smb on a mac, I need to enter in the servername/sharenameon of the smb computer. Do you know how to find that?
To connect with ***ANY *** CIFS/SMB share you use //server_name/share_name or  /IP_Address/share_name.  It doesn't mater if it's Windows, Linux or OSX.

[COLOR="#0000FF"]Edit:  If you are asking me how to connect using a MAC.  The answer is:  I don't know.  I've never used OSX for anything.[/COLOR]

---

### Post by the-paul-84 on 2014-04-23
That makes sense. I am not asking how to connect with a mac, just how to find the server_name/share_name or  /IP_Address/share_name so

---

### Post by bab1 on 2014-04-23
> **the-paul-84 said:**
> That makes sense. I am not asking how to connect with a mac, just how to find the server_name/share_name or  /IP_Address/share_name so

From the Ubuntu command line you should be able to  see all shares on the network with this command```
smbtree
```

---

### Post by the-paul-84 on 2014-04-23
I was able to make a folder in the UI using my mac called testdir2

---

### Post by the-paul-84 on 2014-04-23
I was able to make a folder in the UI using my mac called testdir2

---

### Post by bab1 on 2014-04-23
From the Ubuntu machine post the output of this
```
ls -l /srv/samba

```

---

### Post by the-paul-84 on 2014-04-24
```
jpk@deathstar:~$ ls -l /srv/samba
total 32
drwx------  4 jpk users 12288 Sep 29  2008 movies
drwx------  3 jpk users  4096 Apr 12 14:12 Music
drwx------ 52 jpk users  4096 Jun 10  2010 television
-rw-rw-r--  1 jpk users     9 Apr 19 23:21 test
drwxrwsr-x  2 jpk users  4096 Apr 23 16:44 testdir1
drwxrwsr-x  2 jpk users  4096 Apr 23 19:16 testdir2


```

Everything other than test (which is  text file) is the color blue

---

### Post by bab1 on 2014-04-24
> **the-paul-84 said:**
> ```
jpk@deathstar:~$ ls -l /srv/samba
total 32
[COLOR="#008000"]**drwx------ **[/COLOR] 4 jpk users 12288 [COLOR="#800080"]Sep 29  2008[/COLOR] movies
[COLOR="#008000"]**drwx------ **[/COLOR]   3 jpk users  4096 [COLOR="#800080"]Apr 12 14:12 [/COLOR]Music
[COLOR="#008000"]**drwx------ **[/COLOR]  52 jpk users  4096 [COLOR="#800080"]Jun 10  2010[/COLOR] television
-rw-rw-r--  1 jpk users     9 Apr 19 23:21 test
[COLOR="#008000"]**drwxrwsr-x  **[/COLOR]2 jpk users  4096 Apr 23 16:44 testdir1
[COLOR="#008000"]**drwxrwsr-x**[/COLOR]  2 jpk users  4096 Apr 23 19:16 testdir2


```

Everything other than test (which is  text file) is the color blue
If you look at it from a permissions standpoint (the green part) you will see that the directories have different permissions.  The reason for this is that the legacy directories were created before the share was made (the purple part).

Lets just change all the files and folders permissions on the entire tree with this command```

sudo chmod -R u=rwX,g=rwXs,o=rX /srv/samba

```
This should allow you access to the share from the MAC or Ubuntu (Samba sharing) and also directly from Ubuntu.

---

### Post by the-paul-84 on 2014-04-24
That worked! I can pull and view the files pon my mac without issue. Jere are the results of the ls when I did it again
```
jpk@deathstar:~$ ls -l /srv/samba
total 32
drwxrwsr-x  4 jpk users 12288 Sep 29  2008 movies
drwxrwsr-x  3 jpk users  4096 Apr 12 14:12 Music
drwxrwsr-x 52 jpk users  4096 Jun 10  2010 television
-rw-rwSr--  1 jpk users     9 Apr 19 23:21 test
drwxrwsr-x  2 jpk users  4096 Apr 23 16:44 testdir1
drwxrwsr-x  2 jpk users  4096 Apr 23 19:16 testdir2


```

---

### Post by bab1 on 2014-04-24
> **the-paul-84 said:**
> That worked! I can pull and view the files pon my mac without issue. Jere are the results of the ls when I did it again
```
jpk@deathstar:~$ ls -l /srv/samba
total 32
drwxrwsr-x  4 jpk users 12288 Sep 29  2008 movies
drwxrwsr-x  3 jpk users  4096 Apr 12 14:12 Music
drwxrwsr-x 52 jpk users  4096 Jun 10  2010 television
-rw-rwSr--  1 jpk users     9 Apr 19 23:21 test
drwxrwsr-x  2 jpk users  4096 Apr 23 16:44 testdir1
drwxrwsr-x  2 jpk users  4096 Apr 23 19:16 testdir2


```
I'm glad it all works now and the problems have been solved.  Please the mark this thread ***solved***!!!

---

### Post by the-paul-84 on 2014-04-24
Thank you so much for all of your help! I have marked it as solved and since this is my first time on this board, is there a way I can give you a kudos or thumbs up? Your helpfulness and kindness are more than I could have imagined.

---

### Post by bab1 on 2014-04-24
> **the-paul-84 said:**
> Thank you so much for all of your help! I have marked it as solved and since this is my first time on this board, is there a way I can give you a kudos or thumbs up? Your helpfulness and kindness are more than I could have imagined.
I'm glad it worked out,  Thanks for the appreciation expressed.  That's all that I need,  :-)

---

### Post by the-paul-84 on 2014-04-27
I'm sorry to bother you again on this topic, but I had one more questions.

Oneof my laptops uses Ubuntu 12.04. How do I access the Samba server from that one?  This is not the server computer itself, but another laptop. Thanks.

---

### Post by bab1 on 2014-04-27
> **the-paul-84 said:**
> I'm sorry to bother you again on this topic, but I had one more questions.

Oneof my laptops uses Ubuntu 12.04. How do I access the Samba server from that one?  This is not the server computer itself, but another laptop. Thanks.

Either use Places >> Network and click on the server or Places >> Connect to server.  

You can also use the Nautilus file manager click on Go >>Network or Alt+L and type in smb://server/share like I showed you before

All 4 of these methods ultimately connect with //SERVER/share.

---

