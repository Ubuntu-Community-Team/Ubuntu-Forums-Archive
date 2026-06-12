---
title: "How to Network UBUNTU to Windwos XP.."
date: 2008-05-23
forum: Philippine Team
---

### Post by elord on 2008-05-23
Any one here sa mga ka tropa ko sa Pinas..Paano ba e network ang dalawang OS UBUNTU and XP..COz i have some files sa XP na ilipat ko sa UBUNTU... wats the method? I'm trying to install SAMBA but maraming version..I'm using 7.10 version of Ubuntu... anyone here can teach me to network the two OS..

---

### Post by Nhatz on 2008-05-23
Yeah samba nga... yun gamit ko
just type sa terminal mo...
```
sudo apt-get install samba
```

then pag installed na sya edit mo yung "smb.conf" mo. 

stop mo muna samba daemon
```
sudo /etc/init.d/samba stop
```

```
sudo gedit /etc/samba/smb.conf
```

then scrolldown mo at hanapin yung line na WORKGROUP=MSHOME
palitan mo sya kung anong workgroup kasama yung ibang pc mo..
ex.
WORKGROUP=OFFICE
(take note: dapat all caps din yung pagka type mo)

save mo na then exit

then restart mo yung samba daemon

```
sudo /etc/init.d/samba restart
```

yun.... makikita mo na yung ubuntu box mo sa network at pwede ka na mag file transfer.

Astig! :guitar:

---

### Post by elord on 2008-05-23
walang laman sir yong samba.smb.conf ko... paano ba? actually i install samba 
sa System>synaptic Package Manager..

---

### Post by Nhatz on 2008-05-23
> **elord]walang laman sir yong samba.smb.conf ko... paano ba? actually i install samba
sa System>synaptic Package Manager.. [/QUOTE]

Hala ka lagot...!!! bakit walang laman smb.conf mo? saan napunta? hehehehe.
sure ka na installed ang samba at /etc/samba/smb.conf yun ha.....

BTW here's a sample smb.conf

[QUOTE]
#
# Sample configuration file for the Samba suite for Debian GNU/Linux.
#
#
# This is the main Samba configuration file. You should read the
# smb.conf(5) manual page in order to understand the options listed
# here. Samba has a huge number of configurable options most of which 
# are not shown in this example
#
# Any line which starts with a  said:**
> 

## Browsing/Identification ###

# Change this to the workgroup/NT-domain name your Samba server will part of
   workgroup = ENGKWANG

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


copy and paste mo nalang yan at palitan yung WORKGROUP. hehehehe:)
ASTIG! :guitar:

---

### Post by elord on 2008-05-23
elord@elord-desktop:~$ sudo apt-get install samba
sudo: unable to resolve host elord-desktop
Reading package lists... Done
Building dependency tree       
Reading state information... Done
samba is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 229 not upgraded.
elord@elord-desktop:~$ 

ito nang yari after i install samba.. hehehehhe..and im using DHCP.. so for sure thru Host Name lang mag communicate..

---

### Post by kenweill on 2008-05-23
there's no need to install if you're transfering files from XP to Ubuntu.
but if you're transfering from Ubuntu to XP, then you need Samba so that you can share files from Ubuntu fro XP.

---

### Post by elord on 2008-05-23
> **kenweill said:**
> there's no need to install if you're transfering files from XP to Ubuntu.
but if you're transfering from Ubuntu to XP, then you need Samba so that you can share files from Ubuntu fro XP.


i need both transferring from Ubuntu to XP and XP to UBUNTU.. actually i already installed the samba but when i go to Places>Network to see the Workgroup it will disappear in few seconds.. so what's the problems.. do i need to upgrade my OS to UBUNTU 8.04 coz ryt now im using the 7.10..

---

### Post by kenweill on 2008-05-23
> **elord said:**
> i need both transferring from Ubuntu to XP and XP to UBUNTU.. actually i already installed the samba but when i go to Places>Network to see the Workgroup it will disappear in few seconds.. so what's the problems.. do i need to upgrade my OS to UBUNTU 8.04 coz ryt now im using the 7.10..

what disappeared? did you see the workgroup in XP? was there an object/icon? then disappeared? 

btw, i haven't tried samba in 8.04 yet. i have used samba from 5.10-7.10.

---

### Post by elord on 2008-05-23
when im trying to connect my UBUNTU to XP by clicking Places>Network the windows will disappear in few seconds.. But My UBUntu  will be seen in my XP.. now My problem is i want to connect My Ubuntu to XP..

---

### Post by Nhatz on 2008-05-23
[QUOTE=elord]i need both transferring from Ubuntu to XP and XP to UBUNTU.. actually i already installed the samba but when i go to Places>Network to see the Workgroup it will disappear in few seconds.. so what's the problems.. do i need to upgrade my OS to UBUNTU 8.04 coz ryt now im using the 7.10..[/QUOTE]

Suggestion lang ulit... try mo remove/uninstall muna yung samba then install mo ulit....

ASTIG! :guitar:

---

### Post by elord on 2008-05-23
sorry mga bro.. its my fault now.. i never restart my PC.. ok na lahat both party mag kita na sila..tnxs a lot..

---

### Post by Nhatz on 2008-05-23
Ngek...!!! hehehehe :)
ASTIG! :guitar:

---

### Post by I_have_seen_the_light on 2008-05-23
baka makatulong din sa inyo tong thread na to.  This is what I use eh.  I found no problems with it.  pero bka matulungan nyo ko kung paano i enable yung printer sharing.


[http://ubuntuforums.org/showthread.php?t=202605&highlight=stormbringer](http://ubuntuforums.org/showthread.php?t=202605&highlight=stormbringer)

---

### Post by elord on 2008-05-24
Nautilius.. yan naman ang probs ko ngayon ... ahay kailan maging stable ang linux...

---

### Post by goatkeep on 2008-05-28
Bakit pag nag save yung Windows PC sa shared folder ng Ubuntu, pag tinignan mo ito sa Ubuntu ay may kandado na lagi [read only]? Ano ba't dapat gawin para hindi mag karoon ng kandado pag nag se save nang files sa shared folder?

---

### Post by Nhatz on 2008-05-28
[QUOTE=goatkeep]Bakit pag nag save yung Windows PC sa shared folder ng Ubuntu, pag tinignan mo ito sa Ubuntu ay may kandado na lagi [read only]? Ano ba't dapat gawin para hindi mag karoon ng kandado pag nag se save nang files sa shared folder?[/QUOTE]

view mo muna yung permission nung file

```
ls -l
```

heto lalabas

gaijin@zion:~$ ls -l
total 80
-rw-r--r--  1 gaijin gaijin 24879 2008-05-16 22:19 compiz-check
drwxr-xr-x  2 gaijin gaijin  4096 2008-05-20 13:04 dccrecv
drwxr-xr-x 12 gaijin gaijin  4096 2008-05-28 15:14 Desktop
drwxr-xr-x  2 gaijin gaijin  4096 2008-05-21 18:35 Documents
drwx------  3 gaijin gaijin  4096 2008-05-27 11:28 Downloads
drwx------  7 gaijin gaijin  4096 2008-05-16 14:46 Gnome Looks
drwxr-xr-x  6 gaijin gaijin  4096 2008-05-19 18:39 LimeWire
drwxr-xr-x  2 gaijin gaijin  4096 2008-05-28 11:10 logs
drwxr-xr-x  2 gaijin gaijin  4096 2008-05-16 14:00 Music
drwxr-xr-x  2 gaijin gaijin  4096 2008-05-16 14:00 Pictures
drwxr-xr-x  5 gaijin gaijin  4096 2008-05-16 15:05 pSX
drwxr-xr-x  2 gaijin gaijin  4096 2008-05-16 14:00 Public
drwxr-xr-x  2 gaijin gaijin  4096 2008-05-16 14:00 Templates
drwxr-xr-x  6 gaijin gaijin  4096 2008-05-16 14:41 Videos

for example yung Downloads folder ko gusto ko lagyan ng read,write,execute permission ang group at other users..

drwx------  3 gaijin gaijin  4096 2008-05-27 11:28 Downloads

chmod mo nalang sya sa ubuntu box mo....

```
sudo chmod a+rwx /home/gaijin/Documents
```

a = all
u = user
g = group
o = other

The chmod command (abbreviated from change mode) is a shell command in Unix and Unix-like environments. When executed, the command can change file system modes of files and directories. The modes include permissions and special modes.

ASTIG! :guitar:

---

### Post by perbiu on 2008-05-28
Actually, para sa akin ay bug yung pag share ng folder sa Hardy kung gagamitin mo yung Share Options GUI doon sa Nautilus. Nilagay pa nila doon kung hindi rin magagamit ng baguhan.

[IMG]http://img88.imageshack.us/img88/1598/screenshotfilemanager29hq0.png[/IMG]

Ayan may lumalabas na error 255

I. Para gumana yung Share Options doon sa Nautilus kailangan mo mag Root para gumana, kaso mag kakaproblema ka sa permissions, yun yung mag kakaroon ng kandado na icon kada may naglagay na ibang user doon sa naka Shared Folder.

:guitar:Pero ito ang solusyon diyan para gumana ng maayos yung Share Options:

Edit mo yung smb.conf pagkatapos mo mainstall yung samba
```
sudo gedit /etc/samba/smb.conf
```

Copy & Paste mo ito sa Global na nakasulat o kaya hanapin yung may usershare din na line at paste doon sa ibaba noon.
```
usershare owner only = false
```

Restart yung samba
```
sudo /etc/init.d/samba restart
```

Ayan gagana na yan.

Source [http://blog.myfenris.net/?p=429](http://blog.myfenris.net/?p=429)



II. Kung nanghihingi ng password o log in pag ina access sa ibang computer yung Shared Folder

Edit mo ulit yung smb.conf
```
sudo gedit /etc/samba/smb.conf
```

Hanapin mo ito
```
security = user
```

At Palitan mo nito:
```
security = share
```

Hanapin mo ito
```
; guest account = nobody
```

At tanggalin yung semi colon ; sa harapan
```
 guest account = nobody
```



III. At kung gusto rin I Share yung Printer mo para magamit ng iba o makagawa ng Print Server, hanapin mo ang mga linyang ito at tanggalin mo lang yun mga semi colon ; ng mga ito.

```
;   load printers = yes
```

```
;   printing = cups
;   printcap name = cups
```

---

### Post by goatkeep on 2008-05-28
Gan yan pa rin may kandado pa rin.

---

### Post by Nhatz on 2008-05-28
[QUOTE=goatkeep]Gan yan pa rin may kandado pa rin. [/QUOTE]

kung ayaw parin try mo change ng owner nung file... 

gaijin@zion:~$ ls -l
total 80
-rw-r--r-- 1 gaijin gaijin 24879 2008-05-16 22:19 compiz-check
drwxr-xr-x 2 gaijin gaijin 4096 2008-05-20 13:04 dccrecv
drwxr--r-x 12 [COLOR="Red"]gaijin[/COLOR] [COLOR="Blue"]gaijin[/COLOR] 4096 2008-05-28 15:14 Desktop
drwxr-xr-x 2 gaijin gaijin 4096 2008-05-21 18:35 Documents
drwx------ 3 gaijin gaijin 4096 2008-05-27 11:28 Downloads
drwx------ 7 gaijin gaijin 4096 2008-05-16 14:46 Gnome Looks

sa example ko sa taas yung first "[COLOR="Red"]gaijin[/COLOR]" na nakalagay ay yung owner mismo ng file then yung second "[COLOR="RoyalBlue"]gaijin[/COLOR]" ay yung group. so ibig sabihin yung folder ko na Desktop yung owner lang ang may permission na mag-read,write,execute then yung group read lang..... gets?

so para mapalitan yung owner ng file "chown" command ang gagamitin mo.

```
sudo chown <username mo> <file or directory>
```

yan sana gumana na yan... hehehehe:)
ASTIG! :guitar:

---

### Post by perbiu on 2008-05-29
> **goatkeep said:**
> Gan yan pa rin may kandado pa rin.

Yung mga may padlock na icons sundan nalang yung instruction ni Nhatz

Pero para hindi na ulit mag karoon ng padlock icons yung ilalagay mo doon ay edit mo ulit yung smb.conf mo.

Hanapin ulit ito
```
guest account = nobody
```

At palitan nito
```
guest account = perbiu
```

Yung guest account = yung username na ginamit mo.

:guitar:Solve yan.

---

### Post by goatkeep on 2008-05-29
Na ayos na. TY

---

### Post by benhur99ph on 2008-06-06
I have successfully done this. What I did is I right - clicked on a folder and selected "sharing.." then Ubuntu prompted me to install Samba. After that, I did a "logout - login". Then I went to System>Users and groups. I chose Manage groups and at the bottom of the list, selected the group Samba and added my username to it. Then after that I tried to share my folder again by doing a right - click and choosing "sharing.." and it worked!!

---

