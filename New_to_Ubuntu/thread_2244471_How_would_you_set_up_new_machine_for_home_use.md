---
title: "How would you set up new machine for home use"
date: 2014-09-16
forum: New to Ubuntu
---

### Post by watson524 on 2014-09-16
As some of you know, I recently lost my boot harddrive and am working through that issue (still have to try testdisk) but for right now, I need to focus on getting a machine up and running.

I have a variety of internal and external harddrives with very poor data management to date (my own fault) and things scattered all over. I have a 250GB internal drive that I plan to make the OS drive in the machine. Should I partition that knowing that I have no plans to put data there (other than things like the profile, and my email - which I need to get better about backing up) and if so what size do you recommend? Also, would you format it as ext2, ext4 or ntfs or something else?

I have several other drives that I plan to use for data and backup (not all of them, don't need this much, just what I have)
320GB, 750GB and 1.5TB internals
2TB external

I actually plan to put any internal drives in an external bay reader (2 slots) so my thought was use the 750GB and 1.5TB there and then the 2TB External

What I'd like to do is have all data/media on one drive that can be read by machines over the network running Win 7 (so I'm thinking NTFS formats) and then I want to figure out a way to do a weekly full backup to another drive and daily incrementals (I've been looking at Bacula but open to suggestions).

What do you think the best way to set this up is? Being as I'm a newbie, I don't want to just throw a bunch of drives there and have things copying randomly so I figured I'd look here for some advice.

thanks!

---

### Post by SeijiSensei on 2014-09-16
1) If you are starting with an empty 250 G drive, I'd just let Ubuntu handle the partitioning during installation.  Just tell it to use the whole disk, and let the installer do its thing.

2) I'm not sure what you mean by an "external bay reader."  Are you talking about an external enclosure with a USB connection, or something like a [hot-swap]("http://www.newegg.com/Product/ProductList.aspx?Submit=ENE&Depa=0&Order=BESTMATCH&Description=hot%20swap%20bay&IsRelated=1&cm_sp=KeywordRelated-_-hot-swap-_-hot%20swap%20bay") enclosure?  If you are using the drives more for backup than for daily use, then a USB connection is fine.  I'd still put one of the drives in the machine with a SATA cable for better performance.

3)  You should format anything that Linux will use natively as ext4.  To export your data over the network to Windows machines requires the use of a server program called [Samba]("https://help.ubuntu.com/14.04/serverguide/samba-fileserver.html"), and it expects the data to reside on an ext filesystem.  The only time you would want to format a drive in a Linux machine with NTFS is if you intend to dual-boot Linux and Windows on the same machine.  On a Linux-only box, use ext4 everywhere.

---

### Post by watson524 on 2014-09-16
1.) Ok thanks, I'll use all 250GB and be done with that
2.) External bay drive holder that'll hold 2 drives and yes, USB connect ([http://www.newegg.com/Product/Product.aspx?Item=N82E16817153146](http://www.newegg.com/Product/Product.aspx?Item=N82E16817153146)). I figure at least one in there would be daily use but your point is well taken about making the daily use drive inside the case on a SATA cable. So it seems like the 1.5TB would be best in there so I can ensure everything fits on it sans some media which I don't need daily/fast access to. 
3.) When you say "export your data over the network", I just want to be clear. I'll actually be accessing the data from a windows machine but living on the linux box like a server. So not that I'll copy it to windows and use it there. I want to map a drive windows to point to \\mylinuxbox\driveshare_name No plans to dual boot from the drive. So is ext4 still the way to go and use samba (which I'll have to read up on) to get to it from windows machines?

Is there a good backup software available to do full/incremental to another mounted partition on a schedule?

Thanks for helping me out!

---

### Post by SeijiSensei on 2014-09-16
Yes, ext4+Samba is the correct combination if you want to share files with Windows machines.

I don't use backup packages so I'm afraid I can't help with that.  I run custom bash scripts nightly from [cron]("https://help.ubuntu.com/community/CronHowto") that use **[rsync]("http://linux.die.net/man/1/rsync")** to ship data to the backup device.

---

### Post by watson524 on 2014-09-17
ok I have the machine set up with an 80gb drive I found from an old windows vista install. I just let the installer erase that and start over. I also have a blank 1.5TB drive in there for storage and I put the entry in fstab so it mounts on startup which seems to be working ok after doing a mkdir /media/15tbint and then adding /dev/sdb1 /media/15tbint ext4 user,rw 0 2 to the fstab 

but I can't see to get the samba thing to work. I installed it and edited smb.conf properly (i thought) and restarted the service but i can't see it in my network from a windows machine. I also installed the gui of samba thinking that would be easier to work with but it doesn't seem to help. I'm reading the documentation but not getting anywhere. Are there anythings I can look at?

---

### Post by sotiris2 on 2014-09-17
Make sure the workgroup is the same for both machines?

---

### Post by watson524 on 2014-09-17
i didn't think that had to be the case? especially since one is a work laptop that's not in a workgroup but a domain

---

### Post by Paulgirardin on 2014-09-17
Look at Back in Time for backup software

---

### Post by Michael_McKenney on 2014-09-17
I make it a practice to buy a new hard drive for each OS.  I don't like installing on an old hard drive.

---

### Post by mastablasta on 2014-09-18
> **watson524 said:**
> i didn't think that had to be the case? especially since one is a work laptop that's not in a workgroup but a domain

it is probably the case.

as soon as computers are in same workgroup all you need to do to share is right click a folder in Ubuntu and select propperties and then enable sharing on it. 

you can also connect to the computer manually by typing the ip address smb://yourubuntuIP address

to see which computers (& printers & other devices) are in samba network and their addresses you can use smbtree command:
[http://www.samba.org/samba/docs/man/manpages/smbtree.1.html](http://www.samba.org/samba/docs/man/manpages/smbtree.1.html)

for backup - back in time or lucky backup if you do not want to deal with commands. otherwise rsync should do the job well as suggested.

---

### Post by watson524 on 2014-09-18
Ok I'm going to look into this a bit more. I need a way to connect to the ubuntu machine from my work machine that's not in a workgroup and can't be. I thought back in time I might have done it once. Going to try the IP address method (which reminds me I have to set that as static, forgot to change that in my setup) and will report back. It seems rsync might be the way to go based on what I was reading tho I might look into some of the GUI front ends for it given my limited knowledge.

---

### Post by watson524 on 2014-09-18
Looks like I have something goofed up somewhere. Connecting from a windows machine to smb://10.233.38.224 doesn't work. Any suggestions? Also, eliminating the work laptop for now, I have both the linux box and my home windows machine in a workgroup called "workgroup" and still no love.

---

### Post by SeijiSensei on 2014-09-18
Did you run the command "testparm" to check your Samba configuration?  

Are you running a firewall on this machine?  If so, make sure ports 137-139 and 445 are open for both TCP and UDP.

Perhaps you can post your smb.conf file here?  Surround it in [noparse]```

```[/noparse] tags for legibility.

---

### Post by watson524 on 2014-09-18
Hadn't heard of testparm. Just from a terminal window? No firewall involved.

Below is smb.conf

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

#======================= Global Settings =======================

[global]

## Browsing/Identification ###

# Change this to the workgroup/NT-domain name your Samba server will part of
	workgroup = workgroup

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

# Server role. Defines in which mode Samba will operate. Possible
# values are "standalone server", "member server", "classic primary
# domain controller", "classic backup domain controller", "active
# directory domain controller". 
#
# Most people will want "standalone sever" or "member server".
# Running as "active directory domain controller" will require first
# running "samba-tool domain provision" to wipe databases and create a
# new domain.
	server role = standalone server

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

#
# The following settings only takes effect if 'server role = primary
# classic domain controller', 'server role = backup domain controller'
# or 'domain logons' is set 
#

# It specifies the location of the user's
# profile directory from the client point of view) The following
# required a [profiles] share to be setup on the samba server (see
# below)
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

############ Misc ############

# Using the following line enables you to customise your configuration
# on a per machine basis. The %m gets replaced with the netbios name
# of the machine that is connecting
;   include = /home/samba/etc/smb.conf.%m

# Some defaults for winbind (make sure you're not using the ranges
# for something else.)
;   idmap uid = 10000-20000
;   idmap gid = 10000-20000
;   template shell = /bin/bash

# Setup usershare options to enable non-root users to share folders
# with the net usershare command.

# Maximum number of usershare. 0 (default) means that usershare is disabled.
;	usershare max shares = 100

# Allow users who've been granted usershare privileges to create
# public shares, not just authenticated ones
	usershare allow guests = yes
	username map = /etc/samba/smbusers
	security = user
;	encrypt passwords = yes
;	guest ok = no
;	guest account = nobody

#======================= Share Definitions =======================

# Un-comment the following (and tweak the other settings below to suit)
# to enable the default home directory shares. This will share each
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
# with access to the samba server.
# Un-comment the following parameter to make sure that only "username"
# can connect to \\server\username
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

[share]
	comment = Share 1.5tb int
	path = /media/15tbint
	browseable = yes
	guest ok = yes
	writeable = yes
	create mask = 0755

```

---

### Post by SeijiSensei on 2014-09-18
I don't see any obvious problems in that file.

Yes, testparm is a command-line program that will parse smb.conf and identify possible problems.

Reviewing the logs in /var/log/samba should also be helpful.

---

### Post by watson524 on 2014-09-18
Doesn't look like testparm is having a fit about anything
```

michele@craftlinux:/var/log/samba$ testparm
Load smb config files from /etc/samba/smb.conf
rlimit_max: increasing rlimit_max (1024) to minimum Windows limit (16384)
Processing section "[printers]"
Processing section "[print$]"
Processing section "[share]"
Loaded services file OK.
Server role: ROLE_STANDALONE
Press enter to see a dump of your service definitions

[global]
	server string = %h server (Samba, Ubuntu)
	server role = standalone server
	map to guest = Bad User
	obey pam restrictions = Yes
	pam password change = Yes
	passwd program = /usr/bin/passwd %u
	passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .
	username map = /etc/samba/smbusers
	unix password sync = Yes
	syslog = 0
	log file = /var/log/samba/log.%m
	max log size = 1000
	dns proxy = No
	usershare allow guests = Yes
	panic action = /usr/share/samba/panic-action %d
	idmap config * : backend = tdb

[printers]
	comment = All Printers
	path = /var/spool/samba
	create mask = 0700
	printable = Yes
	print ok = Yes
	browseable = No

[print$]
	comment = Printer Drivers
	path = /var/lib/samba/printers

[share]
	comment = Share 1.5tb int
	path = /media/15tbint
	read only = No
	create mask = 0755
	guest ok = Yes
michele@craftlinux:/var/log/samba$

```

And I looked in /var/log/samba and nothing looks too alarming but what do I know

/var/log/samba/log.smbd
```

michele@craftlinux:/var/log/samba$ cat log.smbd
[2014/09/17 13:29:33,  0] ../source3/smbd/server.c:1198(main)
  smbd version 4.1.6-Ubuntu started.
  Copyright Andrew Tridgell and the Samba Team 1992-2013
[2014/09/17 13:29:33.426212,  0] ../source3/smbd/server.c:1278(main)
  standard input is not a socket, assuming -D option
[2014/09/17 13:40:48.689966,  0] ../lib/util/pidfile.c:153(pidfile_unlink)
  Failed to delete pidfile /var/run/samba/smbd.pid. Error was No such file or directory
[2014/09/17 13:40:48,  0] ../source3/smbd/server.c:1198(main)
  smbd version 4.1.6-Ubuntu started.
  Copyright Andrew Tridgell and the Samba Team 1992-2013
[2014/09/17 13:40:48.714524,  0] ../source3/smbd/server.c:1278(main)
  standard input is not a socket, assuming -D option
[2014/09/18 08:53:34.249740,  0] ../lib/util/pidfile.c:153(pidfile_unlink)
  Failed to delete pidfile /var/run/samba/smbd.pid. Error was No such file or directory
[2014/09/18 08:54:43,  0] ../source3/smbd/server.c:1198(main)
  smbd version 4.1.6-Ubuntu started.
  Copyright Andrew Tridgell and the Samba Team 1992-2013
[2014/09/18 08:54:44.395617,  0] ../source3/smbd/server.c:1278(main)
  standard input is not a socket, assuming -D option
[2014/09/18 09:09:45.778066,  0] ../lib/util/pidfile.c:153(pidfile_unlink)
  Failed to delete pidfile /var/run/samba/smbd.pid. Error was No such file or directory
[2014/09/18 09:10:45,  0] ../source3/smbd/server.c:1198(main)
  smbd version 4.1.6-Ubuntu started.
  Copyright Andrew Tridgell and the Samba Team 1992-2013
[2014/09/18 09:10:45.291679,  0] ../source3/smbd/server.c:1278(main)
  standard input is not a socket, assuming -D option
[2014/09/18 09:10:45.813435,  0] ../source3/printing/print_cups.c:151(cups_connect)
  Unable to connect to CUPS server localhost:631 - Bad file descriptor
[2014/09/18 09:10:45.813661,  0] ../source3/printing/print_cups.c:528(cups_async_callback)
  failed to retrieve printer list: NT_STATUS_UNSUCCESSFUL
[2014/09/18 11:00:07.683954,  0] ../lib/util/pidfile.c:153(pidfile_unlink)
  Failed to delete pidfile /var/run/samba/smbd.pid. Error was No such file or directory
[2014/09/18 11:01:53,  0] ../source3/smbd/server.c:1198(main)
  smbd version 4.1.6-Ubuntu started.
  Copyright Andrew Tridgell and the Samba Team 1992-2013
[2014/09/18 11:01:53.088366,  0] ../source3/smbd/server.c:1278(main)
  standard input is not a socket, assuming -D option
[2014/09/18 11:01:53.560257,  0] ../source3/printing/print_cups.c:151(cups_connect)
  Unable to connect to CUPS server localhost:631 - Bad file descriptor
[2014/09/18 11:01:53.560482,  0] ../source3/printing/print_cups.c:528(cups_async_callback)
  failed to retrieve printer list: NT_STATUS_UNSUCCESSFUL
[2014/09/18 11:23:51.301529,  0] ../lib/util/pidfile.c:153(pidfile_unlink)
[2014/09/18 11:25:04,  0] ../source3/smbd/server.c:1198(main)
  smbd version 4.1.6-Ubuntu started.
  Copyright Andrew Tridgell and the Samba Team 1992-2013
[2014/09/18 11:25:04.223523,  0] ../source3/smbd/server.c:1278(main)
  standard input is not a socket, assuming -D option
[2014/09/18 11:25:04.587115,  0] ../source3/printing/print_cups.c:151(cups_connect)
  Unable to connect to CUPS server localhost:631 - Bad file descriptor
[2014/09/18 11:25:04.587340,  0] ../source3/printing/print_cups.c:528(cups_async_callback)
  failed to retrieve printer list: NT_STATUS_UNSUCCESSFUL
[2014/09/18 11:33:14.290639,  0] ../lib/util/pidfile.c:153(pidfile_unlink)
  Failed to delete pidfile /var/run/samba/smbd.pid. Error was No such file or directory
[2014/09/18 11:34:21,  0] ../source3/smbd/server.c:1198(main)
  smbd version 4.1.6-Ubuntu started.
  Copyright Andrew Tridgell and the Samba Team 1992-2013
[2014/09/18 11:34:21.941256,  0] ../source3/smbd/server.c:1278(main)
  standard input is not a socket, assuming -D option
[2014/09/18 11:34:22.338252,  0] ../source3/printing/print_cups.c:151(cups_connect)
  Unable to connect to CUPS server localhost:631 - Bad file descriptor
[2014/09/18 11:34:22.338468,  0] ../source3/printing/print_cups.c:528(cups_async_callback)
  failed to retrieve printer list: NT_STATUS_UNSUCCESSFUL

```

this looks suspect maybe /var/log/samba/log.%m
```

[2014/09/18 11:34:22.555631,  0] ../source4/smbd/server.c:478(binary_smbd_main)
  At this time the 'samba' binary should only be used for either:
  'server role = active directory domain controller' or to access the ntvfs file server with 'server services = +smb' or the rpc proxy with 'dcerpc endpoint servers = remote'
  You should start smbd/nmbd/winbindd instead for domain member and standalone file server tasks

```

and /var/log/samba/log.nmbd
```

  *****
[2014/09/18 11:33:14,  0] ../source3/nmbd/nmbd.c:57(terminate)
  Got SIGTERM: going down...
[2014/09/18 11:34:25,  0] ../source3/nmbd/nmbd.c:902(main)
  nmbd version 4.1.6-Ubuntu started.
  Copyright Andrew Tridgell and the Samba Team 1992-2013
[2014/09/18 11:34:48,  0] ../source3/nmbd/nmbd_become_lmb.c:397(become_local_master_stage2)
  *****
  
  Samba name server CRAFTLINUX is now a local master browser for workgroup WORKGROUP on subnet 10.233.38.224
  

```

---

### Post by SeijiSensei on 2014-09-20
How are you connecting to the share from Windows?  Are you using a hostname like \\craftlinux or its IP address?  Try using \\ip.of.the.server and see if that works.  If so, your Windows client cannot resolve the name "craftlinux".  

My smb.conf has fewer options than yours.  Maybe you can start with a more stripped-down version and see if that works.  
```

[global]
        workgroup = WORKGROUP
        server string = Samba Server
        log file = /var/log/samba/%m.log
        max log size = 50
        dns proxy = No
        wins support = Yes
        cups options = raw

[homes]
        comment = Home Directories
        read only = No
        browseable = No

[Music]
        path = /home/seiji/Music
        read only = No
        guest ok = Yes

```

Adding "wins support = yes" might solve your name-resolution problem.  And, as others have said, make sure both the server and clients are in the same Windows workgroup.

---

### Post by redrumrogue on 2014-09-20
I use samba on my ubuntu box to share folder over my home network with my windows 7 laptop.  I used system-config-samba (GUI) to set it up and it was very easy.  Have you not tried system-config-samba? You can start it in command line with
```
sudo -i system-config-samba
```
I can't remember if this is included in ubuntu or not so you may have to install it first.

Once it's open you'll see this ...
[ATTACH=CONFIG]256559[/ATTACH]

You can add your folder shares in this window.

If you click on Preferences -> Server Settings ...

[ATTACH=CONFIG]256560[/ATTACH]and security settings ... [ATTACH=CONFIG]256561[/ATTACH]

Then under Preferences -> Samba Users ... setup a samba user which you can use to log in with from your windows machine.

[ATTACH=CONFIG]256562[/ATTACH]

Once it's configured just restart your samba server with 
```
sudo service smbd restart
```

Then try and access the share from your windows machine using the sambe user log in credentials.

Hope this helps!

---

### Post by redrumrogue on 2014-09-20
Regarding your backup requirements - you could use deja-dup (included with ubuntu) or CrashPlan ([http://www.code42.com/crashplan/](http://www.code42.com/crashplan/)).  There are probably loads of alternatives but these two work very well for me.  I use Deja-Dup to back the data on my ubuntu machines to an external USB HDD (pictures, music, docs, videos)  and I use CrashPlan to backup data from 3 remote machines onto my ubuntu machine.

---

### Post by redrumrogue on 2014-09-20
may I also suggest that if you have several HDDs that you want to use for data storage then you should consider using LVM to group them together into one large volume.  You can create striped logical volumes with great read / write performance.  You could also do this with mdadm (software RAID) but I find LVM (Logical Volume Management) easier and more flexible.  If you want more info just ask!

---

### Post by watson524 on 2014-09-20
> **SeijiSensei said:**
> How are you connecting to the share from Windows?  Are you using a hostname like \\craftlinux or its IP address?  Try using \\ip.of.the.server and see if that works.  If so, your Windows client cannot resolve the name "craftlinux". 

Adding "wins support = yes" might solve your name-resolution problem.  And, as others have said, make sure both the server and clients are in the same Windows workgroup.

Trying to get to \\craftlinux\15tbint

just tried it with \\10.233.38.224 and it seems to work fine. Haven't full tested RW privleges since I'm having some issues with that but I copied a file from my windows machine to the server with no issues. Added the wins support = yes and it doesn't change things so somewhere it's not resolving something. Just not sure where or why.

Also, from my work machine (not in the WORKGROUP workgroup) I was able to get to it too via \\10.233.38.224 so that sort of helps that issue, but I don't see craftlinux at all in either windows machine's network directory listing...

---

### Post by watson524 on 2014-09-20
Related to back ups, I think I'm going to stick with the -a option on rsync since that's about my level of understanding at this point tho I need to play with the cron jobs as I'm not sure they're running. I'll post that under separate thread because I think it may relate to some overall permissions/ownership. My id "michele" seems to be an admin but not root and I'm not sure if that's throwing things off or not.

---

### Post by SeijiSensei on 2014-09-21
The simplest way to resolve name resolution problems is to add entries to the clients' "hosts" files.  On *nix boxes, that file is /etc/hosts.  In [Windows]("http://en.wikipedia.org/wiki/Hosts_(file)#Location_in_the_file_system") it is usually located at C:\windows\system32\drivers\etc\hosts.  I suggest reading this section from the Samba manual about network browsing: [https://www.samba.org/samba/docs/man/Samba-HOWTO-Collection/NetworkBrowsing.html](https://www.samba.org/samba/docs/man/Samba-HOWTO-Collection/NetworkBrowsing.html).  Warning: your eyes may glaze over.

---

### Post by Bill Tetzeli on 2014-09-21
> **SeijiSensei said:**
> You should format anything that Linux will use natively as ext4.  To export your data over the network to Windows machines requires the use of a server program called [Samba]("https://help.ubuntu.com/14.04/serverguide/samba-fileserver.html"), and it expects the data to reside on an ext filesystem.  The only time you would want to format a drive in a Linux machine with NTFS is if you intend to dual-boot Linux and Windows on the same machine.  On a Linux-only box, use ext4 everywhere.


I have to strongly disagree with that.  Remember, this is a forum for newbies.  A la Staples, I like to push the "Easy Button" whenever possible.  Easy in this case is NTFS because it can be read by Linux and Windows with no extra work.  I have rarely had trouble with NTFS drives in Linux (certainly no more than in Windows), usually due to disconnecting during an unmounting operation that I thought was done but wasn't, making the drive unreadable.  In those instances, it was simple enough to use testdisc to locate and copy the files onto my computer or another drive, reformat the drive, then copy the files back on there.  A pain, but not nearly as much as setting up a samba share would be.  Like I said, consider that this is the noob corner of the forum, and what's the easiest solution?  No point in creating more work than necessary.

P.S. All my large externals are NTFS except for the RAID I put all my music on, and that's because Linux seems to have trouble mounting a RAID array formatted in NTFS.  So for that I use ext4.  Everything else though is NTFS, no muss, no fuss, no perfect becoming the enemy of the good.

---

### Post by mastablasta on 2014-09-22
> **Bill Tetzeli said:**
> I have to strongly disagree with that.  Remember, this is a forum for newbies.  A la Staples, I like to push the "Easy Button" whenever possible.  Easy in this case is NTFS because it can be read by Linux and Windows with no extra work.  I have rarely had trouble with NTFS drives in Linux (certainly no more than in Windows), usually due to disconnecting during an unmounting operation that I thought was done but wasn't, making the drive unreadable.  In those instances, it was simple enough to use testdisc to locate and copy the files onto my computer or another drive, reformat the drive, then copy the files back on there.  A pain, but not nearly as much as setting up a samba share would be.  Like I said, consider that this is the noob corner of the forum, and what's the easiest solution?  No point in creating more work than necessary.


really? how do you defragment the drive? ntfs get's fragmented.
How do you run check disk (chkdsk) from Linux? it has to be run occasionally.

if the user will be using Linux exclusively then ext4 (at least) is the way to go.


though for external data drives  it doesn't matter as much if you are using Linux only in house you might have trouble repairing those without windows tools.

I use NTFS on RaspberyPi "media server", but I have no issue with NTFS since I have plenty of windows PC available where I can plug the external drive and do any possible repairs.

also what is complicated about samba? you need to be in the same workgroup and then you just mark folder as shared and that's it.

---

### Post by SeijiSensei on 2014-09-22
Having drives formatted with NTFS on a Linux box doesn't make them available to other Windows machines on the local network.  For that you need Samba.

---

### Post by Bill Tetzeli on 2014-09-22
> **SeijiSensei said:**
> Having drives formatted with NTFS on a Linux box doesn't make them available to other Windows machines on the local network.  For that you need Samba.

I think this might be an option when you're trying to access ext4 drives from Windows (preferably in read-only mode, though):

[http://www.howtogeek.com/112888/3-ways-to-access-your-linux-partitions-from-windows/](http://www.howtogeek.com/112888/3-ways-to-access-your-linux-partitions-from-windows/)

As far as defragging or chkdsk, I mainly use NTFS external drives for large music or video files.  A lot goes on but only rarely is anything deleted.  Not much of a fragging problem there.  And like I said, in two and a half years of using Linux, I haven't had any real problems to speak of.

---

### Post by mastablasta on 2014-09-23
yeah well for static data it is not such an issue. chkdsk could still be needed in case of power failure etc. while disk is being written/read. of course one could do that with a rescue disk as well. or if external drive just plug it  into windows PC...

I am still not sure what would be gained in Linux only environment by using NTFS. since ext4 and let's not even start with other file system are a lot more efficient or offer more features than NTFS. then again NTFS support is good lately and I haven't had data issue as well. but I've been running it for only about 10 months now.

---

