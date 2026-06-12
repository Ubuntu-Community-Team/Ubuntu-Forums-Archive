---
title: "I could switch to Ubuntu for work if I ever figure out how to network with Windows"
date: 2008-09-12
forum: New to Ubuntu
---

### Post by Nermi on 2008-09-12
I am a new Ubuntu user, and I must say in all aspects I love it.  

As a professional Web Developer, I was looking for programs and interfaces that I could use in my work and switch away from Windows, and I discovered Quanta, installed Xampp with MySql, and am perfectly comfortable using Gimp for graphics. Open office is for me fantastic and I love it for office work. And, I used Firefox for browsing anyway. 

At this point I could say I might switch to Ubuntu for 95% of my needs, but because my co-workers are on Windows machines (and must test my work on Windows too), I MUST figure out how to properly network with my Windows network first. 

There are three windows XP computers in windows workgroup called MAIN. I've done serious research on this and other forums, attempting to find out why I can not see my windows share from Ubuntu and found out that I needed to install samba. I did, but that didn't change much of anything, except now when I go to Places -> Network I see "Windows Network" icon. After clicking on that I get two icons: MAIN (name of my wind. workgroup) and WORKGROUP. Clicking on MAIN shows me computers in my Windows network, but when I click on them I get empty page. If I go back and click on WORKGROUP, I get an empty page. 

One way I could connect was to enter IP address of each machine, and that will connect me. I bookmarked them, but that's not real solution. Sometimes, our internet connection is interrupted and when it gets restored, IP addresses get all changed, then I have to go back in and enter all IP's share info in and bookmark them again. 

Another thing, Quanta (that I would be using for web development) does not let me open documents from computers on Windows network, even if I bookmark the shares. 

The printer connected to one Windows machine will work from Ubuntu ONLY if I enter IP... I tried connecting it to Ubuntu and it works out of box, but that is not a solution; there are other reasons why it has to be connected to windows pc. 

Now, interestingly enough; I managed to map the network drive from Windows to Ubuntu and I can see my Ubuntu share from Windows without problems. Ain't that weird? I've read so many posts from people who couldn't resolve that problem... 

Now, if anyone really knows how to do this, I would really appreciate some help. THIS IS THE ONLY THING THAT IS PREVENTING ME FROM SWITCHING AWAY FROM WINDOWS... 

Thanks. 

Nermi

---

### Post by limasierra on 2008-09-12
Read these tutorials:```
http://ubuntuforums.org/showthread.php?t=202605
``````
https://help.ubuntu.com/community/SettingUpSamba
```
Hope that it helps

---

### Post by Nermi on 2008-09-12
Thank you, but I have already done all that. Have these tutorials saved in my bookmarks. 



Nermi

---

### Post by gregphil on 2008-09-12
Ubuntu 8.04.1 is currently broken as far as authenticated file shares from windows boxes is concerned.  In spite of the mis-leading bug title see:

[https://bugs.launchpad.net/ubuntu/+source/gvfs/+bug/207072](https://bugs.launchpad.net/ubuntu/+source/gvfs/+bug/207072)
[http://bugzilla.gnome.org/show_bug.cgi?id=524485#c26](http://bugzilla.gnome.org/show_bug.cgi?id=524485#c26)

The 8.04.1 release switched to a new gnome library (gvfs) and the authentication routines in there (that GUI applications like nautilus network file browser call) fail to correctly handle authentication with windows boxes.  I hear you can use un-authenticated shares from the windows box (allow anonymous guest access) but that would be a huge security risk.

In any event there is a work-around for using authenticated shares, while we wait for it to get fixed.  If you know the full name of the share you can just enter it in the GUI application target box (in nautilus click on the pencil to change the target icon to a text box) and press enter.

If you don't know the full share names you can drop to the command line (open a terminal window) and enter 
"smbtree"  and the password  (the user & password must be in the Shares allowed user list on the windows box)

If that takes too long you can try it against one computer, from command line:
"smbclient -L COMPUTERNAME"
supply the password when prompted, and note the shares available.

It is actually not that bad, but it is hard to believe they didn't notice this bug when it was introduced, in the upgrade from ubuntu 7.10 to 8.04

On another up note, this bug only effects the gnome applications, so if you use KDE (kubuntu) there is not a problem accessing Windows authenticated shares.

Cheers!

---

### Post by Nermi on 2008-09-13
After reading your reply to my post, I first tried the obvious: installing and switching to KDE. And I really loved the look and functionality of KDE Desktop; however, my Windows network is still inaccessible. 

I need to read KDE Manual first, and especially the networking part; I see there are some differences as KDE doesn't require SAMBA to be installed... but, in the meantime I wanted to thank you for your helpful reply to my post. 

I have also tried to do "smbtree" command in the Terminal, but I would rather not share the results of that attempt here. I hope you don't mind if I PM it to you. 

Thank you for your help. 


Nermi

---

### Post by Nermi on 2008-09-14
Ok, I have tried everything and am still unable to access my windows network. Maybe something is wrong with my smbf.conf file? 
Here it is (my windows workgroup name is MAIN):
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
   workgroup = MAIN

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


```

Nermi

---

### Post by tangibleorange on 2008-09-14
you don't need samba to access windows machines - only to share files from the ubuntu box to the windows machines.

anyway, i also have the problem of being able to "see" the network computers but clicking on them doesn't give me anything. the solution is to use the IP address of the windows machine you want to access. So, if I am accessing my Windows PC at IP 192.168.1.3, I do this in nautilus (GNOME file browser):

[LIST]
[*]Open file browser
[*]Press Ctrl+L
[*]in the box that appears, type: smb://192.168.1.3
[*]you should now see the shared folders
[/LIST]

unfortunately this seems to be the only way it works for me. if you don't know the IP of the windows machine, you can go to a command prompt at it and type:

```
ipconfig
```

which should tell you. hope it helps and good luck!

---

### Post by gregphil on 2008-09-14
Try the basic command line tools before the fancy (and sometimes broken) GUI tools.  For example, from the kubuntu box (with Samba installed) try to browse the shares visable from your windows box. 

smbtree

If that gives too much output try browsing just one remote computer:

smbclient -L COMPUTERNAME

Note both of those asked for a password to use to browse, if the server end (the Windows box) is setup for anonymous (guest) browsing you could try

smbclient -L COMPUTERNAME -N

The -N means no password (anonymous)

Tell us what these return with, if the result (after a few seconds pause) is blank then your Samba workgroup is probably no set the same as you Windows workgroup (they need to be identical) OR you have some firewall enabled and getting in the way.

---

### Post by Nermi on 2008-09-14
No, there's no firewall. But, I get this:
```
nermi@nermi-linux:~$ smbclient -L BRUMLEY
timeout connecting to 24.28.193.9:445
timeout connecting to 24.28.193.9:139
Error connecting to 24.28.193.9 (Operation already in progress)
Connection to BRUMLEY failed (Error NT_STATUS_ACCESS_DENIED)

```

In my smbf.conf file I have wins support = no; should I change that to yes, and comment it out?

Nermi

---

### Post by gregphil on 2008-09-14
Making samba a WINS server is not required for true peer-to-peer browsing, and if you turn it on remember that only ONE machine on the sub-net can be a WINS server.

The timeout error really looks like a firewall issue, are you SURE you don't have the Windows firewall (or anyother 'helpful' programs) blocking the connection?

Another obvious question: are the machines you are trying to browse on the SAME sub-net (like all machines on 192.168.0.xxx)?  If you are on separate sub-nets (opposite sides of a router) then you will need to use a browsing protocol that can bridge sub-nets (like WINS).

Do you have a good grasp of your network configuratuon?  try

ifconfig -a

On a linux box to list it's current settings

Try ipconfig /all on the windows box.  Do they both have the same address in the first three sections of the IP address?

How are your IP addresses assigned?  DHCP or did you pix fixed addresses?  If there is no DHCP server you need to have a way to resolve NAMES to ip addresses (like entries in the lmhosts files).  A domain server or a WINS server can do this as well.

---

### Post by gregphil on 2008-09-14
BTW

To deal with the smb.conf file, and it's ~340 possible options, I find it is best to backup the starting file and then ERASE all the COMMENTS so you can see what is actually being used.  Any line that begins with # or ; is a comment and is being ignored by samba anyway.  It only takes about one page of actual smb.conf configuration entries, not the 10 pages of the default file.

You MAY have to actually resort to reading the manual (man smb.conf) but it is HUGE and is not installed by default (use the package manager to get samba-doc) Then "man smb.conf" might be helpful.

---

### Post by Nermi on 2008-09-14
Yes, all computers are on the same sub-net:

NERMIXP 192.168.0.3
BRUMLEY 192.168.0.4
EDJO 192.168.0.5
NERMI-LINUX 192.168.0.6

which I found out by checking my router admin page. There is no firewall on any of Windows machines, but I discovered that there's an option on my (Netgear) router to "disable SPI firewall". So, some sort of firewall is running on the router; I am just not sure if it affects this issue and what will happen if I disable it... ?
Maybe I should try and see what happens. 

Yes, I have DHCP. 

Nermi

---

### Post by gregphil on 2008-09-14
You could try an anonymous browse (maybe the Windows boxes won't accept an authenticated browse)

smbclient -L BRUMLEY -N

and to see if it is a nameserver issue try

smbclient -L 192.168.0.4 -N

or

smbclient -L 192.168.0.4

Do any of those work?

BTW, is there a username/password account on the Windows box with the exact same name and password as the kubuntu box?  This is normally what is needed for an authenticated sharing (but you say you are using anonymous sharing so this should not be the issue),  Also the error message would be different for failed to authenticate, it would not be timeout)

---

### Post by gregphil on 2008-09-14
I was just looking back over your earlier post of smb.conf.

I suggest you try changing the "obey pam restrictions" line to

     obey pam restrictions = no

save the file, and restart samba  
as root do 
   /etc/init.d/samba restart 

wait a few minutes (for browse discovery to happen) and then try

smbclient -L COMPUTERNAME -N

---

### Post by Nermi on 2008-09-15
I have change that line in smb.conf and unfortunately it didn't fix the problem. 

nermi@nermi-linux:~$ smbclient -L BRUMLEY -N
timeout connecting to 24.28.193.9:445
timeout connecting to 24.28.193.9:139
Error connecting to 24.28.193.9 (Operation already in progress)
Connection to BRUMLEY failed (Error NT_STATUS_ACCESS_DENIED)


Nermi

---

### Post by Nermi on 2008-09-15
But here is what I get when try

```
nermi@nermi-linux:~$  smbclient -L 192.168.0.4 -N
Domain=[EDJO] OS=[Windows 5.1] Server=[Windows 2000 LAN Manager]

	Sharename       Type      Comment
	---------       ----      -------
	IPC$            IPC       Remote IPC
	C on Ed         Disk      
	A_Lidija        Disk      
session request to 192.168.0.4 failed (Called name not present)
session request to 192 failed (Called name not present)
Domain=[EDJO] OS=[Windows 5.1] Server=[Windows 2000 LAN Manager]

	Server               Comment
	---------            -------

	Workgroup            Master
	---------            -------

```

EDJO is the name of one of computers in windows network. A_Lidija is the name of shared folder. 

Nermi

---

### Post by gregphil on 2008-09-15
So you now know you have a network name resolution issue.
 
Something on your network needs to convert computer NAMES to IP addresses.  Many different protocols exist for this.  Normally the DHCP router will perform this function if no other server is doing it.  
 
You could try enabling WINS on one (and only one) of your linux machines because a WINS server will provide name resolution.  Of course then that one machine would need to be on for the others to share.
 
If you have a small network with fixed IP adresses, you could just add a line for each computer to the lmhosts files (on each computer) to do name resolutiuon.  However these days most people use DHCP to get automatic (and variable) IP assignment.
 
At least you can focus on the name resolution issue now.

---

### Post by sudo_chop on 2008-09-15
You could use DHCP reservations, your router probably supports it. The computer IPs will always be the same, but can stay set to DHCP. That way you could add them to your lmhosts and be done. Keep it simple.

---

### Post by Nermi on 2008-09-15
Things are getting even worse. After I made that change in smb.conf, I turned of my Linux computer and left. When I turned it on again, and tried to go to network  folder, now I don't even see my Linux computer. And I get this error:

```
Unable to find any workgroups in your local network. This might be caused by an enabled firewall.
```

There's no firewall. And this is all happening before I even tried that thing with name resolution. 

But, how do I enable wins on my linux computer? In smb.conf file?
And the other thing about static IP addresses. Almost every time when we lose internet connection, which is often these days, all computers get assigned IP addresses different than before. I don't know how to make them static, and if I can anyway? 

Nermi

---

### Post by sudo_chop on 2008-09-15
Do you see anything in your router, around DHCP config, about DHCP reservations?

---

### Post by Nermi on 2008-09-15
Ok the above error about not being able to detect any workgroups has somehow fixed itself. 

Did you mean IP address reservation? I remember I've seen that feature somewhere in my router configuration, and am trying to find it now. This is supposed to make IP addresses fixed, right?


Nermi

---

### Post by sudo_chop on 2008-09-15
Right, it sets it so that every time a computer asks the DHCP server for an IP address, the DHCP server will give it the same one.

If you can't find it or your router doesn't have it, then you can do "hard coded" IPs in each computer.

---

### Post by Nermi on 2008-09-15
I have found it, and set up static IP's. 
But, no change. 

:(

Nermi

---

### Post by sudo_chop on 2008-09-15
> **Nermi said:**
> I have found it, and set up static IP's. 
But, no change. 

:(

Nermi

I thought we had it working already with

```
smbclient -L 192.168.0.4 -N
```

Sorry, but I don't know enough about samba or windows shares to help you past this point...

---

### Post by Nermi on 2008-09-15
You and Gregphill have helped me a lot. Thank you. 

However, there's an interesting progress. 

I think when I assigned IP addresses, it took some time for changes to take effect. 

Now, I see all three network computers from Ubuntu. However, when I click on them, I get only empty page. I don't see shared folders. 

But this result is interesting:

```
nermi@nermi-linux:~$ smbclient -L 192.168.0.6
Password: 
Domain=[BRUMLEY] OS=[Windows 5.1] Server=[Windows 2000 LAN Manager]

	Sharename       Type      Comment
	---------       ----      -------
	PMAIL           Disk      
	E$              Disk      Default share
	Quotes          Disk      
	My Documents    Disk      
	Prntr           Printer   Samsung ML-1200 Series (Copy 1)
	IPC$            IPC       Remote IPC
	print$          Disk      Printer Drivers
	My Music        Disk      
	ML-1200         Printer   Samsung ML-1210/ML-1220M
	css             Disk      
	C               Disk      
	SamsungM.3      Printer   Samsung ML-1200 Series (Copy 2)
	ADMIN$          Disk      Remote Admin
	C$              Disk      Default share
	Vongo           Disk      
session request to 192.168.0.6 failed (Called name not present)
session request to 192 failed (Called name not present)
Domain=[BRUMLEY] OS=[Windows 5.1] Server=[Windows 2000 LAN Manager]

	Server               Comment
	---------            -------

	Workgroup            Master
	---------            -------

```

especially this line:
```
session request to 192.168.0.6 failed (Called name not present)
```

What does that mean? Computer name IS BRUMLEY. 
:confused:

Nermi

---

### Post by sudo_chop on 2008-09-15
Try

```
smbclient -L BRUMLEY
```

*fingers crossed*

---

### Post by forger on 2008-09-15
I had this problem just a few days ago. I thought it was my dns server being the ones from [www.opendns.com](www.opendns.com)

Anyway, I'm not sure if you need all these, but this is what I did:
```
sudo apt-get install smbldap-tools smbget smbclient smbfs samba-tools
```

In the meantime, on the laptop with the windows vista, I assigned and let everyone (or guest account) view the shared points without to require a password to access them. (and rebooted it)

Then I used smbclient and assigned a guest user with no password (-N)
```
smbclient //aleksandra/music -I 192.168.1.3 -U guest -N
```
aleksandra is the pc name I wanted to access
music was the shared folder name
192.168.1.3 was the IP of the computer it was on.

I could access the folder, and started transferring files:
```

help
ls
prompt off
recurse on
mget *

```

Edit: not sure again, but try not to name your share name folders with a space, it's easier to access them this way

---

### Post by sudo_chop on 2008-09-15
> **sudo_chop said:**
> Try

```
smbclient -L BRUMLEY
```

*fingers crossed*

Actually no, wait, if you never made a lmhosts entry it probably wont resolve BRUMLEY.

---

### Post by Nermi on 2008-09-15
```
smbclient -L BRUMLEY
```

didn't work. Sorry. But, thank you for trying. 

Forger, hvala. :)

I will explore these options too. 

> In the meantime, on the laptop with the windows vista, I assigned and let everyone (or guest account) view the shared points without to require a password to access them. (and rebooted it)

How can I do that on XP?

Thanks. 

Nermi

---

### Post by Nermi on 2008-09-15
In the meantime, I edited smb.conf file (actually only to get rid of comments and have a clean file). If anyone notices anything weird in the file, please let me know. I don't know the first thing about this (yet). 

```
[global]

workgroup = MAIN
server string = %h server (Samba, Ubuntu)
;   wins support = no
;   wins server = w.x.y.z
   dns proxy = no
;   name resolve order = lmhosts host wins bcast

#### Networking ####
;   interfaces = 127.0.0.0/8 eth0
;   bind interfaces only = true


#### Debugging/Accounting ####

   log file = /var/log/samba/log.%m
   max log size = 1000
;   syslog only = no
   syslog = 0
   panic action = /usr/share/samba/panic-action %d


####### Authentication #######

;   security = user
   encrypt passwords = true
   passdb backend = tdbsam
   obey pam restrictions = no
;   guest account = nobody
   invalid users = root
   unix password sync = yes
   passwd program = /usr/bin/passwd %u
   passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .
   pam password change = yes
   map to guest = bad user

########## Domains ###########

;   domain logons = yes
;   logon path = \\%N\profiles\%U
;   logon path = \\%N\%U\profile
;   logon drive = H:
;   logon home = \\%N\%U
;   logon script = logon.cmd
;   add user script = /usr/sbin/adduser --quiet --disabled-password --gecos "" %u

########## Printing ##########

;   load printers = yes
;   printing = bsd
;   printcap name = /etc/printcap
;   printing = cups
;   printcap name = cups

############ Misc ############

;   include = /home/samba/etc/smb.conf.%m
    socket options = TCP_NODELAY
;   message command = /bin/sh -c '/usr/bin/linpopup "%f" "%m" %s; rm %s' &
;   domain master = auto
;   idmap uid = 10000-20000
;   idmap gid = 10000-20000
;   template shell = /bin/bash
;   winbind enum groups = yes
;   winbind enum users = yes
    usershare allow guests = yes

#======================= Share Definitions =======================

;[homes]
;   comment = Home Directories
;   browseable = no
;   read only = yes
;   create mask = 0700
;   directory mask = 0700
;   valid users = %S
;   [netlogon]
;   comment = Network Logon Service
;   path = /home/samba/netlogon
;   guest ok = yes
;   read only = yes
;   share modes = no
;  [profiles]
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
[print$]
   comment = Printer Drivers
   path = /var/lib/samba/printers
   browseable = yes
   read only = yes
   guest ok = no
;   write list = root, @ntadmin
;[cdrom]
;   comment = Samba server's CD-ROM
;   read only = yes
;   locking = no
;   path = /cdrom
;   guest ok = yes
;   preexec = /bin/mount /cdrom
;   postexec = /bin/umount /cdrom

```

thanks. 

Nermi

---

### Post by gregphil on 2008-09-15
I just got home from work.

You probably "had it working" five hours ago when you said you could "see" the computers but when you clicked on them "nothing happened".  If you remember a while back (yesterday?) I mentioned there is a severe bug in the gnone gvfs library and any of the gnome GUI applications that use this library (like Nuatilus Network File Browser") will fail when browsing authenticated shares.  When you could "see" the other computers you could have entered the full share name (like smb://BRUNBLY/TEMP) into the GUI target box and connected.  (see the links below)

[https://bugs.launchpad.net/ubuntu/+source/gvfs/+bug/207072](https://bugs.launchpad.net/ubuntu/+source/gvfs/+bug/207072)
[http://bugzilla.gnome.org/show_bug.cgi?id=524485#c26](http://bugzilla.gnome.org/show_bug.cgi?id=524485#c26)

Further you must not have been paying attention when I explained that is takes 12 minutes for peer-to-peer "discovery" to take place and share browsing probably won't be fully working before that.  This is because each machine 'broadcasts' on the sub-net the shares they have availabe, and all the other computers need to be listening.  To avoid clashing into each other the boradcasting is limited to no more than once every 12 minutes.  Peer-to-peer networking is not as efficient as a server based system (where the server answers all "share's available" queries, and authenticates all connections) but peer-to-peer networking does not require setting up or configuring dedicated servers.

I don't think you want a LADP server enabled (you are not on a domain ! !)

Did you intend to share something besides printers?  
I don't see any share defined in your ubuntu /etc/samba/smb.conf file.
Remember lines beginning with ; are comments   (they are ignored)

"security = USER" (authenticated sharing) is the DEFAULT. 
If you want guest sharing you need to use "security = SHARE"

You were close when you realized name resolution was not happening on your sub-net.  I think you have been back-tracking since then.

A short primer on DHCP:
   If a computer on the sub-net already has a fixed IP (it was configured that way)     then the DHCP server will leave that IP alone and assign a differnt one to the next computer that needs an IP.
   If DHCP assigns an IP to a computer it will allow it to keep that IP for at least the "lease time", AND will attempt to give the computer the same IP on the next boot.
   Since the DHCP server has "remembered" the IP it assigned to each computer, it is normally willing to act as a name server and offer up this information when asked.
   Other types of name servers exist (various "servers"), so to avoid conflict it is normally possible to turn off the DHCP server feature that does name resolution serving (as a DHCP configuration setting)

*************************

You need to get back to making 
"smbclinet -L BRUMLEY" 
work, or if you decide to use "security = SHARE" to make
"smbclient -L BRUMLEY -N
work (the -N means "no password" = anonymous)

Assumming BRUMLEY=192.168.0.6, if "smbclient -L 192.168.06" works, but "smbclient -L BRUMLEY" fails you still have a name resolution problem.  Something on you sub-net needs to provide name resolution.  Read up on "name resolution"

---

### Post by TJCIB on 2008-09-15
I don't mean to be the guy to throw everything off.  And I don't recall you mentioning specifics on the type of file sharing you are doing...but...

Given the "bug" mentioned and samba being ridiculous, and if you don't need printer sharing...would NFS work?  I have found it very easy to share between my ubuntu boxes and XP stations.

Just a thought...

*edit for clarification*
NFS doesn't need name recognition, it actually works better using IP addresses.
It's easy to give the permissions you want, and block everyone else.
seems to be faster for me also.

---

### Post by gregphil on 2008-09-15
I agree the gnome gvfs authentication bug is 'rediculous'  

But it is NOT a Samba bug, and Samba can work if it is setup correctly.  With the new default /etc/samba/smb.conf file, sharing does not 'just work' out of the box. I think this is what is throwing people.  They never had to understand any of these issues for simple peer-to-peer file browsing to work on a Windows network.  So terms like "name resolution" and "authentication" are new to them.  However, once one does *a little* research, the issues become clear and it is not that hard to get full BROWSING (not just bookmarked connections) working.

Note that the exact same Samba setup under KDE has no trouble browsing shared files with the KDE GUI applications.

The Samba package should come with a few 'example' smb.conf files.  The default file should be setup to enable legacy peer-to-peer file sharing with Windows machines.  There probably should be one with security=SHARE and another example with security=USER.  Since security=USER seems so hard for most users to understand maybe the security=SHARE version should be the default (but setup to only share a global share directory like /tmp/shared).  One working example can go a long way to answering questions.

Another thing that is really needed is some optional feedback in the GUI applications that allow the user to optionally see the error messages so the user can understand what might be causing the failures.  Either a "show recent errors" dialog, or an "enable connection monitoring" dialog.

Thank You

---

### Post by pbotros1234 on 2008-09-15
This is how I set my SAMBA up, and it worked perfectly. I just go to the Network Folders tab and it shows up under Windows Network and everything.

[Here]("http://www.linux.com/articles/58593")

---

### Post by Nermi on 2008-09-16
> Note that the exact same Samba setup under KDE has no trouble browsing shared files with the KDE GUI applications.

But, all this time I am using KDE. You must have overlooked in one of my replies to you I mentioned that I tried KDE and liked it a lot, and was hoping would be easier to establish file sharing with KDE. However, I still can't. 

Yes, I am fully aware of the "12 minute rule", but this whole thing is getting little silly. Last night, I finally managed to return to the point when I was able to see my windows network and windows computers connected to it. Could not see the actual shares. I turned of computers, and this morning - even after waiting for 12 minutes - I am back to the square 1... No computers visible on my network. 

I think I am giving up. Thank you for your time, and your help. 

Nermi

---

### Post by trestamanos on 2008-09-23
DISCLAIMER: I am n00b.......

Just a suggestion.  Probably like many Linux users (especially new ones like me)...still depend on certain applications because of many reasons (i know this is highly debatable from hardcore linux users).....

nevertheless, in my case i still need our accounting software......which i use through VirtualBox by running a copy of Windows.

I also use it to tap into the network folders at the office (via windows XP through Vbox)-which uses Win 2003.  I believe in time i will be able to migrate 100%.......but till then i am 95% there.:)

I've heard Ubuntu has many issue yet communicating with Win 2003 server?

I will do research see if i can use ubuntu for accesing network folders...then ill be 98% there....:)

---

### Post by stargeizer on 2008-12-23
Maybe i'm a little late in this forums... anyway...

By default, most distributions doesn't compile winbind support into the Samba package or worse, separates it. why is done this way is beyond me, since if you need to use samba is pretty obvious that you need to do so because there are windows machines in your net.

If you want name resolution of windows machines a la SMB way, you need to install the winbind package and make some changes to a file as root:

Open your favorite editor with root privieges (e.g. sudo nano) and open the file /etc/nsswitch.conf

look for the hosts: line... should have something like:

```
hosts:          files dns mdns4
```

just add the word "wins" (without "") like this:

```
hosts:          files dns mdns4 wins
```

then save the file,reboot your machine and you are set.

Best Regards.

J.

---

