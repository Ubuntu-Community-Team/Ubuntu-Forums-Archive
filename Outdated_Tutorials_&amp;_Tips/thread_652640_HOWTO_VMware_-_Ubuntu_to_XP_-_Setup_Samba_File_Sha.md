---
title: "HOWTO: VMware - Ubuntu to XP - Setup Samba File Sharing (4 Steps, no fuss)"
date: 2007-12-28
forum: Outdated Tutorials &amp; Tips
---

### Post by SilverWave on 2007-12-28
_________________________________________

**HOWTO:**

Setup Samba to share a folder on a Ubuntu host so your VMware server's XP guest can use it.

Almost completely based on a fantastic post by Russ Hall here:
[http://2tap.com/2007/04/22/sharing-files-between-a-windows-guest-and-ubuntu-host-using-vmware-and-samba/](http://2tap.com/2007/04/22/sharing-files-between-a-windows-guest-and-ubuntu-host-using-vmware-and-samba/)
(I have pared his instructions down to the bone and any mistakes are mine).

OS: Ubuntu 7.10
Architecture: 64bit.
VMware Server using NAT networking.
_________________________________________

**1 -** Issue these commands:
sudo apt-get install samba

sudo groupadd sharer
sudo useradd --gid sharer --shell /bin/false sharer --home /nonexistent
sudo smbpasswd -a sharer

cd $HOME
mkdir sharer
sudo chown YourUserNameHere:sharer sharer
sudo chmod 775 sharer
sudo chmod g+s sharer

sudo gedit /etc/samba/smb.conf

**2 -** Update the smb.conf file to reflect your details (see below). 

**3 -** Issue the command:
sudo /etc/init.d/samba restart

**4 -** On your XP guest VM do the following:
My Computer >Tools>Map Network Drive
Drive: S
Folder: \\YourUbuntuHostIP\sharer
Choose: Connect using a different user name.
username: sharer
password: yoursharerpassword


Done :)

Cheers



Items that will need changed:

Delete the ; in front of security = user,
```

security = user,

```

Add the following to the end of the "Share Definitions" section.
(You will need to change: path = /home/YourUserNameHere/sharer).
```

[sharer]
path = /home/YourUserNameHere/sharer
valid users = sharer
read only = No
create mask = 0777
directory mask = 0777

```

Here is my file:
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
   workgroup = MSHOME

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
   security = user

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

[sharer]
path = /home/YourUserNameHere/sharer
valid users = sharer
read only = No
create mask = 0777
directory mask = 0777


```
You will need to change: path = /home/YourUserNameHere/sharer



_________________________________________

Notes:

Reading this great article by Fahmida Y. Rashid & Mario Morejon, at the CMP Channel started me looking into this.
[http://www.crn.com/software/204802209;jsessionid=15PWPET2SHZTKQSNDLRSKHSCJUNN2JVN?pgno=1](http://www.crn.com/software/204802209;jsessionid=15PWPET2SHZTKQSNDLRSKHSCJUNN2JVN?pgno=1)
In particular this quote:
> "Engineers mapped the share under Places, Connect, and then entering the machine's hostname (an IP address is also valid input), the name of the share, and a username for the server. After being prompted for a password, there was a shortcut to the mounted share on the desktop and a window automatically opened, displaying the contents. As long as the machine was on the server and the machine information was at hand, this was a snap."
And this worked to access a share on the windows box but I wanted to do it the other way around :)



_________________________________________

Extras:

For extra security this may be a good idea but I have not tried it yet:

sudo gedit /etc/samba/smb.conf

bind interfaces only = true
interfaces = vmnet0 vmnet1 vmnet8
; interfaces = vmnet0, vmnet1, vmnet8
sudo /etc/init.d/samba restart



_________________________________________

Acknowledgments:

This HOWTO is almost completely based on a fantastic post by Russ Hall here:
[http://2tap.com/2007/04/22/sharing-files-between-a-windows-guest-and-ubuntu-host-using-vmware-and-samba/](http://2tap.com/2007/04/22/sharing-files-between-a-windows-guest-and-ubuntu-host-using-vmware-and-samba/)
(I have pared his instructions down to the bone and any mistakes are mine).

I also reviewed these in my searching:
[http://youtube.com/watch?v=Ad17kma8rNM](http://youtube.com/watch?v=Ad17kma8rNM)
[http://ubuntuforums.org/showthread.php?t=202605&highlight=samba](http://ubuntuforums.org/showthread.php?t=202605&highlight=samba)
[http://ubuntuforums.org/showthread.php?t=296668](http://ubuntuforums.org/showthread.php?t=296668)



Best of Luck :)

---

### Post by doug-M on 2008-01-10
I did this:
bind interfaces only = true
interfaces = lo vmnet1 

To only allow samba on loopback and the host only network.
However I have found that samba fails to start on boot. Or rather smbd does but nmbd does not.
I think the problem is the the VMWare vmnet1 adapter is not up yet.

In /var/log/samba/log.nmbd I get

nmbd/nmbd_subnetdb.c:create_subnets(245) create_subnets: unable to create any subnet from given interfaces. nmbd is terminating
nmbd/nmbd.c:main(771)   ERROR: Failed when creating subnet lists. Exiting.

Restarting samba sorts it out but I suspect either VMWare needs to be earlier in the boot order or Samba later.

sudo /etc/init.d/samba restart

---

### Post by SilverWave on 2008-01-13
I think this may help :)

[http://ubuntuforums.org/showpost.php?p=2160523&postcount=19](http://ubuntuforums.org/showpost.php?p=2160523&postcount=19)

> **misha680 said:**
> One thing that is a problem is that samba starts before vmware does, so the vmnet1 and vmnet8 interfaces don't exist yet when samba starts and it doesn't recognize their creation later on. A quick solution for this is:
```
sudo /etc/init.d/samba restart
```
A more permanent fix:
```
sudo gedit /etc/rc.local
```
And add the following lines somewhere:
```
# Restart samba so it takes into consideration VMWare network interfaces
/etc/init.d/samba restart
```
This will just restart samba as the last thing that happens when your machine is booting, ensuring that the vmware networking devices are loaded.

Misha

I have not tried  adding "/etc/init.d/samba restart" to "/etc/rc.local" but it looks like it could resolve this issue for you.

Best of luck :)

---

### Post by frogotronic on 2008-01-14
hmmm

works well, BUT
now I can't see, or connect to see any Windows computers via Places>Network>Windows Network

Any ideas?

---

### Post by SilverWave on 2008-01-16
> **cement_head said:**
> hmmm

works well, BUT
now I can't see, or connect to see any Windows computers via Places>Network>Windows Network

Any ideas?

Can you give some details of your network?
Are all your windows machines set to the same workgroup?
Can you ping the machines?
Was samba setup and working prior to following this howto?
Can you undo your changes and if so does this issue then resolve itself?

Cheers!

---

### Post by frogotronic on 2008-01-19
Hi,

Okay - sorry for the delay.  Got my SAMBA figured out.

I followed your instructions and it completely worked.  Then I shut down the VMWare WindowsXP OS and rebooted Ubuntu.

Now When I try to connect from my VMWare/XP to my "sharer" folder, it asks me for a password.  I keep entering my username & password and get "The netwrok path could not be found".

I can ping the vmnet0 connection.

How do I fix this connection?

---

### Post by frogotronic on 2008-01-20
> **cement_head said:**
> Hi,

Okay - sorry for the delay.  Got my SAMBA figured out.

I followed your instructions and it completely worked.  Then I shut down the VMWare WindowsXP OS and rebooted Ubuntu.

Now When I try to connect from my VMWare/XP to my "sharer" folder, it asks me for a password.  I keep entering my username & password and get "The netwrok path could not be found".

I can ping the vmnet0 connection.

How do I fix this connection?

Is the problem that I am I trying to run TWO SMB servers?

Bottom of this post?

[http://www.vmware.com/support/gsx3/doc/network_samba_gsx.html](http://www.vmware.com/support/gsx3/doc/network_samba_gsx.html)

---

### Post by SilverWave on 2008-01-21
> **cement_head said:**
> Hi,

Okay - sorry for the delay.  Got my SAMBA figured out.

I followed your instructions and it completely worked.  Then I shut down the VMWare WindowsXP OS and rebooted Ubuntu.

Now When I try to connect from my VMWare/XP to my "sharer" folder, it asks me for a password.  I keep entering my username & password and get "The netwrok path could not be found".

I can ping the vmnet0 connection.

How do I fix this connection?

OK if I reboot my (VM Guest) WindowsXP OS and try to access the (Ubuntu VM Host) "sharer" folder I get prompted for User name & Password in the form:
\\server\sharer\
I needed to delete \\server\ so it now prompts with:
username: sharer
password: yoursharerpassword

If you still have problems I would delete the mapped drive then remap it and see if that works.

e.g 
4 - On your XP guest VM do the following:
My Computer >Tools>Map Network Drive
Drive: S
Folder: \\YourUbuntuHostIP\sharer
Choose: Connect using a different user name.
username: sharer
password: yoursharerpassword

TBH I snapshot my XP just after the latest critical updates and just power off > revert to snapshot :)

All I have to remember on resuming is to tick "connect to network" once its restored and wait till XP finds the network before using the mapped folder.

Hope that helps.

---

### Post by frogotronic on 2008-01-21
I'll try this and get back - Thanks!

- CH

---

### Post by eolatunde4 on 2008-01-22
I am attempting to setup my SAMBA following the instructions posted here.  I don't have any experience with linux so this is all new to me.  However, I'm stuck at the part where I am to perform the sudo egit command.  When I try to use this command I get a "Cannot open display:" message.  It says to run gedit --help for available command line options, but I don't know which one to use.  All help would be appreciated.

---

### Post by dcstar on 2008-01-22
> **eolatunde4 said:**
> I am attempting to setup my SAMBA following the instructions posted here.  I don't have any experience with linux so this is all new to me.  However, I'm stuck at the part where I am to perform the sudo egit command.  When I try to use this command I get a "Cannot open display:" message.  It says to run gedit --help for available command line options, but I don't know which one to use.  All help would be appreciated.

The command must be run in a terminal session opened inside your Gnome desktop, not an "ALT-Fn" terminal.

If you want to edit in that way, replace "gedit" with "nano".

---

### Post by frogotronic on 2008-01-23
If you still have problems I would delete the mapped drive then remap it and see if that works.

e.g 
4 - On your XP guest VM do the following:
My Computer >Tools>Map Network Drive
Drive: S
Folder: \\YourUbuntuHostIP\sharer
Choose: Connect using a different user name.
username: sharer
password: yoursharerpassword

TBH I snapshot my XP just after the latest critical updates and just power off > revert to snapshot :)

All I have to remember on resuming is to tick "connect to network" once its restored and wait till XP finds the network before using the mapped folder.

Hope that helps.[/QUOTE]

Okay, deleted the mapped drive.  Just to clarify...What is my "YourUbuntuHostIP"?

Is it the vmnet1 IP, or my eth0 IP?

Thanks,
CH

---

### Post by SilverWave on 2008-01-25
> 

Okay, deleted the mapped drive.  Just to clarify...What is my "YourUbuntuHostIP"?

Is it the vmnet1 IP, or my eth0 IP?

Thanks,
CH

> NAT networking

In this mode, your guest OS shares your host’s address (in terms of other machines on the LAN) and communicates with the host via a private network. In this case, the IP address you need to connect to is most likely the bottom one from the output of this command:

ifconfig | grep "inet addr:"

Connecting to the share from within Windows

If you are unsure as to your host’s IP address, try and ping it first from within the Windows guest to confirm you have the right one. from here:
[http://2tap.com/2007/04/22/sharing-files-between-a-windows-guest-and-ubuntu-host-using-vmware-and-samba/](http://2tap.com/2007/04/22/sharing-files-between-a-windows-guest-and-ubuntu-host-using-vmware-and-samba/)

Good Luck :)

---

### Post by frogotronic on 2008-01-26
it keeps (the Guest O/S) asking me for my password?

see screen shot.

How do I re-change my password?

---

### Post by frogotronic on 2008-01-26
> **cement_head said:**
> it keeps (the Guest O/S) asking me for my password?

see screen shot.

How do I re-change my password?

FIXED!!!

There was some stuff in my SMB.CONF file that was preventing contacts between my host and guest.  Working well now

Thanks!!

---

### Post by diablo75 on 2008-01-27
> **cement_head said:**
> FIXED!!!

There was some stuff in my SMB.CONF file that was preventing contacts between my host and guest.  Working well now

Thanks!!

Good to hear, but could you elaborate on the changes you made to your smb.conf file?

---

### Post by frogotronic on 2008-01-27
My Firestarter/IP tables added a blockage to "sharer" section.

I edited my smb.conf file and deleted  the extra parameters (which for some reason were appended to the [sharer] which stated:

```
access=no
writable=no
browseable=no

```

and then I added a policy rule to Firestarter that allowed incoming connections from my guest Host IP.

Seems to work well now.

---

### Post by diablo75 on 2008-01-27
I don't know much of anything about firestarter.  How do you use it?

---

### Post by frogotronic on 2008-01-27
> **diablo75 said:**
> I don't know much of anything about firestarter.  How do you use it?

[https://help.ubuntu.com/community/Firestarter](https://help.ubuntu.com/community/Firestarter)

---

### Post by sethtriggs on 2008-02-02
Worked great for me. Now I have a question...I have VMWare Server with Win2000 in it. (I had to reinstall my system due to a hard drive that burned out).

I've got my Internet running at normal speed and that's great. And I have my Samba running, yet it seems a bit slow. IS it possible to use that 1.0GBit card for just the local Samba connections but yet still be able to use the Internet? I have no idea really. Anyone out there know?

-Seth

---

### Post by frogotronic on 2008-02-03
> **sethtriggs said:**
> Worked great for me. Now I have a question...I have VMWare Server with Win2000 in it. (I had to reinstall my system due to a hard drive that burned out).

I've got my Internet running at normal speed and that's great. And I have my Samba running, yet it seems a bit slow. IS it possible to use that 1.0GBit card for just the local Samba connections but yet still be able to use the Internet? I have no idea really. Anyone out there know?

-Seth

Hi Seth,

  It shouldn't be a problem.  I can use the internet via my Ethernet card and communicate from my VMWare OS (WinXP) to my Ubuntu side *simultaneously*.

If you can't do that - there might be an iptables issue.  Can you start Firestarter and create a POLICY rule for "Inbound traffic policy" and add the IP address for your VMWare Ethernet.

- CH

---

### Post by sethtriggs on 2008-02-03
Oh my, I can't get it to work with Firestarter. Now I get no connection whatsoever to my local machine. I was able to connect via IP before (slowly), but now I cannot anymore to the main machine. Putting in the IP address for my vmnet1 and vmnet8 connections does no good.

My VMWare networking setup is Ethernet 1 as a specific virtual network, while Ethernet 2 is a Bridged connection. The Bridged connection seems to be the one connecting to the Internet since it's always flashing.

---

### Post by frogotronic on 2008-02-03
> **sethtriggs said:**
> Oh my, I can't get it to work with Firestarter. Now I get no connection whatsoever to my local machine. I was able to connect via IP before (slowly), but now I cannot anymore to the main machine. Putting in the IP address for my vmnet1 and vmnet8 connections does no good.

My VMWare networking setup is Ethernet 1 as a specific virtual network, while Ethernet 2 is a Bridged connection. The Bridged connection seems to be the one connecting to the Internet since it's always flashing.

Hi,

  You'll also need to set up SAMBA permissions on your ALLOW SERVICES.  See attached png of my policies.  The 172.xxx.xx.xxx addresses are the VMware IPs; The "LIFE" workgroup is the name of my MS WORKGROUP and my local SMB.conf WORKGROUP name.

- CH

---

### Post by sethtriggs on 2008-02-05
> **cement_head said:**
> Hi,

  You'll also need to set up SAMBA permissions on your ALLOW SERVICES.  See attached png of my policies.  The 172.xxx.xx.xxx addresses are the VMware IPs; The "LIFE" workgroup is the name of my MS WORKGROUP and my local SMB.conf WORKGROUP name.

- CH

I've done this, and it works now! Even though it's not fast (like 1.0GB fast), it's still good enough. Thank you! Oddly in Firestarter I had to do this from the Events window, and it was seeing my password as something totally different. I have it now I think.

-Seth

---

### Post by kerunt on 2008-02-07
Awesome!

Worked like a charm :)

Thanks!

---

### Post by SilverWave on 2008-03-04
Glad to be of help :)

---

### Post by Akkeresu on 2008-03-11
This is excellent.

Just got this working for my MGCCC Linux Admin class and this has helped us out considerably instead of trying it on FC4 or OpenSUSE 10.3

I would recommend this to anyone, and in fact, I would have the mods sticky this thread, as it is so useful!

Thanks!

~Akkeresu

---

### Post by fatagnus on 2008-03-29
followed the guide, see the shares, it asks me for password, but doesn't matter what I do, it keeps asking for the password anyway. The password is correct, I changed it multiple times to the same over and over, nothing changes.
I even have copied and pasted the sample config file (with the needed modifications), but no change.
The worst is that I can't know what is going wrong, since windows doesn't have a console for this, it only keeps asking me for the password no matter what.
How could I know what's wrong with it?

---

### Post by frogotronic on 2008-03-29
> **fatagnus said:**
> followed the guide, see the shares, it asks me for password, but doesn't matter what I do, it keeps asking for the password anyway. The password is correct, I changed it multiple times to the same over and over, nothing changes.
I even have copied and pasted the sample config file (with the needed modifications), but no change.
The worst is that I can't know what is going wrong, since windows doesn't have a console for this, it only keeps asking me for the password no matter what.
How could I know what's wrong with it?

Is windows asking for the password?

---

### Post by fatagnus on 2008-04-08
Thank you cement_head for answering, I solved it now, it was a matter of permissions, but not of the shared directory itself. My home directory didn't have execute permissions for everyone. Once i changed that It worked, although I don't really understand why.
I'll need a better understanding of permissions if I want to retain my sanity while using Linux  :)

---

### Post by frogotronic on 2008-07-12
Hello,

I got a weird problem.  Using Hardy Heron and had the samba share set up with no problem.

After a kernel update; I reran the the vmware config and it asked if I wanted to keep the vmnet settings, which I said yes to.  I then had a few issues with file permissions on my .dmrc file; which I fixed.

Now I cannot connect to my samba share and I think it has to do the file permissions that I might have changed.  I have re-applied the instructions at post one and it has not helped.

I can ping only one vmnet address (192.168.228.1) from my guest OS (XP), but I cannot connect to it anymore

the output of my ```
$ifconfig | grep "inet addr:"
```

is

 ```
inet addr:127.0.0.1  Mask:255.0.0.0
 inet addr:192.168.228.1  Bcast:192.168.228.255  Mask:255.255.255.0
 inet addr:172.16.130.1  Bcast:172.16.130.255  Mask:255.255.255.0
 inet addr:192.168.2.100  Bcast:192.168.2.255  Mask:255.255.255.0
```

Does anyone have suggestions?

---

### Post by frogotronic on 2008-07-12
Okay, so I can see my samba share (see screenshot)...BUT I cannot connect to my sharer folder.

I can't figure out why?

---

### Post by Existance0 on 2008-08-12
> 4 - On your XP guest VM do the following:
My Computer >Tools>Map Network Drive
Drive: S
Folder: \\YourUbuntuHostIP\sharer
Choose: Connect using a different user name.
username: sharer
password: yoursharerpassword

I'm stuck on this step I'm not sure what you're telling me to do.

---

### Post by kdebugx86 on 2008-10-25
good tutorial samba on ubuntu. :)

thank you.

---

### Post by SILLAT on 2008-12-08
i did this tutorial about a month ago after i did a fresh install of Ubuntu Ibex 8.10, but now i no longer can connect to my share folder, its says path cannot be found.
when i try mapping a new drive in XP an click browse i see Microsoft Network then Workgroup then Vmware Share Folder but it does not show my share folder in my /home on the Ubuntu side tht it use to.
wat cud cause my folder not to work no more..i havent touch my samba config file since . . only install updates tht comes in from ubuntu ... 
any one has any trick i can try ??

---

### Post by SilverWave on 2008-12-10
> **Existance0 said:**
> I'm stuck on this step I'm not sure what you're telling me to do.

4 - On your XP guest VM do the following:

Goto "My Computer"
Menu: "Tools"
Menu: "Map Network Drive"
Enter a drive letter:
e.g. 
"S"

Fill in the following information when asked

Folder:
"\\YourUbuntuHostIP\sharer"
(Change this to your ip for ubuntu).

Then Choose:
"Connect using a different user name."

Fill in the following information when asked:

username:
"sharer"

password:
"yoursharerpassword"

Hope this helps :)

---

### Post by SilverWave on 2008-12-10
> **SILLAT said:**
> i did this tutorial about a month ago after i did a fresh install of Ubuntu Ibex 8.10, but now i no longer can connect to my share folder...
any one has any trick i can try ??

All I can suggest is to start from the begining and work through the howto again... double checking everything as you go :(

Check your firewall first though!

---

### Post by SILLAT on 2008-12-13
i ran this tutorial from scratch again and it still did not work, i have Xp on NAT connection i also added the XP Ip address to my allowed list in firestarter jus to make it work, i've done this b4 an it worked an i didnt even touch firestarter. Another thing when i try map a network drive using the IP adress or machine name i get network path cannot be found, also when i click Browse i see Vmware share folder but when i click the + sign on the vmware share folders to extend it to see my share folder i created nothing comes down (its blank)
i've attached a clip of my Me Tryin to map the folder have a look see if u hav any trick i can try .. for the record i did create my share folder i already double check that

---

### Post by frogotronic on 2008-12-13
> **SILLAT said:**
> i ran this tutorial from scratch again and it still did not work, i have Xp on NAT connection i also added the XP Ip address to my allowed list in firestarter jus to make it work, i've done this b4 an it worked an i didnt even touch firestarter. Another thing when i try map a network drive using the IP adress or machine name i get network path cannot be found, also when i click Browse i see Vmware share folder but when i click the + sign on the vmware share folders to extend it to see my share folder i created nothing comes down (its blank)
i've attached a clip of my Me Tryin to map the folder have a look see if u hav any trick i can try .. for the record i did create my share folder i already double check that

Can you post your smb.conf file?

---

### Post by SILLAT on 2008-12-13
Here is a copy of my Samba config as u requested.
one thing to note is my samba group id is share and my samba user is also name share an my shared folder name is share, resides in my /home partition. dont get it twisted it always wrk 4me.

---

### Post by frogotronic on 2008-12-13
> **SILLAT said:**
> Here is a copy of my Samba config as u requested.
one thing to note is my samba group id is share and my samba user is also name share an my shared folder name is share, resides in my /home partition. dont get it twisted it always wrk 4me.

nothing jumps out at me, do you have firestarter working?  with correct permissions?

---

### Post by SILLAT on 2008-12-13
i'm not totally sure how to configure firestarter but i dont normally configure it cuz when i follow the tutorial it jus works ..
it worked in hardy it worked for a while in ibex i'm a bit confused now . .
Can u send a rundown of how to configure firestarter for Vmware Samba share on ibex ? ?
i'll try it an see what happens
thnx in advance . .

---

### Post by doug-M on 2010-08-12
Sorry to dredge up an old thread but this isn't working on my new 10.04 box.

In my smb.conf (copied from my 9.04 working system) I have:
	interfaces = vmnet1 lo

	bind interfaces only = true

vmnet1    Link encap:AMPR NET/ROM  HWaddr   
          inet addr:172.16.102.1  Mask:255.255.255.0

smbclient //127.0.0.1/shared
Domain=[WORKGROUP] OS=[Unix] Server=[Samba 3.4.7]
smb: \> 

smbclient //172.16.102.1/Documents
Connection to 172.16.102.1 failed (Error NT_STATUS_CONNECTION_REFUSED)

I had this before and found I needed to restart samba using this:
sudo /etc/init.d/samba restart

That command isn't valid anymore so I used this:
sudo service smbd restart
sudo service nmbd restart

It didn't help though.

---

### Post by doug-M on 2010-08-12
I found this in the /var/log/samba/log.nmbd

[2010/08/12 20:13:52,  0] nmbd/nmbd.c:854(main)
  nmbd version 3.4.7 started.
  Copyright Andrew Tridgell and the Samba Team 1992-2009
[2010/08/12 20:13:52,  0] nmbd/nmbd_subnetdb.c:206(create_subnets)
  create_subnets: No local IPv4 non-loopback interfaces !
[2010/08/12 20:13:52,  0] nmbd/nmbd_subnetdb.c:207(create_subnets)
  create_subnets: Waiting for an interface to appear ...

So it looks like Samba is failing to understand interface names on the interface line. (This is very bad)

I found that it would start working if I changed the interfaces line to use IP addresses and ranges, of course if you use DHCP on multiple networks then this won't work. So it sounds like a Samba bug.

So this seemed to work in the smb.conf:
#	interfaces = vmnet1 lo
	interfaces = 127.0.0.1 172.16.102.1/24

lo = 127.0.0.1
vmnet1 = 172.16.102.1/24 (in my case)

---

