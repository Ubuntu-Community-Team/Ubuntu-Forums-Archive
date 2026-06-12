---
title: "Can't get samba shares to work"
date: 2008-07-26
forum: New to Ubuntu
---

### Post by DonBucknall on 2008-07-26
Hello,

I've installed ubuntu server today with samba. I want the users home folders to be shared and that only the users can access it with their username and password.
There are a few other folders I want to be shared and just be open.
It keeps asking me for a username and password on my ubuntu laptop and I can't see the users home folders.
On winXP I can see them but can't access them, it comes up with 'access denied'.
Here's my smb.conf:

> #======================= Global Settings =======================



[global]



   workgroup = bucknall

   os level = 2



   security = user

   encrypt passwords = true

   browseable = yes

   guest account = nobody

   map to guest = bad user

   server string = UbuntuServer

   hosts allow = 192.168.





   username map = /etc/samba/smbusers



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

   comment = Home Directories

   browseable = no

   read only = no

   create mask = 0640

   directory mask = 0750

   hide dot files = yes

   hide unreadable = yes



# By default, \\server\username shares can be connected to by anyone

# with access to the samba server.  Un-comment the following parameter

# to make sure that only "username" can connect to \\server\username

# This might need tweaking when using external authentication schemes

;   valid users = %S



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

#       cdrom share is accesed. For this to work /etc/fstab must contain

#       an entry like this:

#

#       /dev/scd0   /cdrom  iso9660 defaults,noauto,ro,user   0 0

#

# The CD-ROM gets unmounted automatically after the connection to the

#

# If you don't want to use auto-mounting/unmounting make sure the CD

#       is mounted on /cdrom

#

;   preexec = /bin/mount /cdrom

;   postexec = /bin/umount /cdrom



[share]

   comment = share

   path = /share

   writable = yes

   create mask = 0777

   directory mask = 0777



[transfer]

   path = /home/transfer

   create mask = 0660

   public = yes

   writeable = yes

   browseable = yes



[music]

   path = /home/music

   create mask = 0660

   public = yes

   writeable = yes

   browseable = yes



[pictures]

   path = /home/pictures

   create mask = 0660

   public = yes

   writeable = yes

   browseable = yes



Does anyone have an idea?
Thanks alot!!

Don Bucknall

---

### Post by arkara on 2008-07-26
You should add the users by yourself..
from the command line giving the following command
```
smbpasswd -a username
```

---

### Post by ibuclaw on 2008-07-26
1) Have you restarted samba?
```
sudo /etc/init.d/samba restart
```
2) What does this command output?
```
ls -l /home/music
```
3) Try putting in the following
```
directory mask = 0660
```
Under each mapped samba share.

Regards
Iain

---

### Post by DonBucknall on 2008-07-26
@arkara: I did add the users that way so that won't be it.

@tinivole: 1) I did a restart a few times, doesn't make any difference.
           2) It comes up with permission denied.
           3) This didn't help either.

I really don't understand cause it works for my uncle.
Could it have anything to do with owners?

Thanks for quick reply!

---

### Post by ibuclaw on 2008-07-26
Yes, it definitely sounds like a permssions problem then.

When you say permission denied do you mean
```
ls: cannot open directory foo: Permission denied
```
?

If so, paste the output of this:
```
ls -ld /home/music
```

And can you state the username you use to connect the Windows PCs to the samba share?

Regards
Iain

---

### Post by DonBucknall on 2008-07-26
@tinivole: the output is: drw-rw---- 2 root root 4096 2008-07-26 18:55 /home/music

the username for accessing the samba shares is donbucknall, do you mean the username on windows or set in samba? well it is donbucknall eitherway.
but even the shared folder who don't need a login aren't accesable?

I appreciate your help!!

---

### Post by badrunner on 2008-07-26
> **DonBucknall said:**
> @tinivole: the output is: drw-rw---- 2 root root 4096 2008-07-26 18:55 /home/music

the username for accessing the samba shares is donbucknall, do you mean the username on windows or set in samba? well it is donbucknall eitherway.
but even the shared folder who don't need a login aren't accesable?

I appreciate your help!!

Looks like /home/music is only readable by root. Either make it readable by all: "chmod a+r -R /home/music", or set it to be owned by which ever user the samba daemon runs us (presumably the user is samba, but i dont have it installed on this box so cant immediately check).

---

### Post by badrunner on 2008-07-26
> **badrunner said:**
> Looks like /home/music is only readable by root. Either make it readable by all: "chmod a+r -R /home/music", or set it to be owned by which ever user the samba daemon runs us (presumably the user is samba, but i dont have it installed on this box so cant immediately check).

Oh and directories should have the execute permission to be browseable. You can do chmod a+x /home/music to fix that, and you'll probably need to do it for any subdirectories too.

---

### Post by DonBucknall on 2008-07-26
ok I changed owners and did the +x thing... I can access them now create a new folder inside put a file in music but not in the newly created folder.

And I still can't see or access the home directories?

thanks alot guys!

---

### Post by ibuclaw on 2008-07-26
Hi, sorry for the delay, got held up.

I would personally make you the owner and the samba account name the group.

If there isn't a login/group for the samba login name on your machine, then create one :)
```
sudo groupadd sandbox
sudo useradd --gid sandbox --shell /bin/false sandbox
```
Replace "sandbox" with the name of the account you use to login to.

Then run
```
sudo chown **username**:**sambaname** /home/music -R
```
Change "username" with your ubuntu username and "sambaname" with the name of the login access for windows.

And the last thing I can think of:
```
ifconfig | grep "inet addr:"
```
Use the first IP address on the bottom line for the other PCs in your local network to connect to you.

ie: Mine is 192.168.1.2

[EDIT]
If you can get this working for your /home/music folder, then repeat the same process for your other folders too.

Regards
Iain

---

### Post by DonBucknall on 2008-07-27
I changed owners and groups yesterday and permissions like badrunner said.

output of ls -ld /home/music is:
drwxrwx--x 2 donbucknall users 4096 2008-07-26 18:55 /home/music

yesterday evening I could access from my laptop xp the music transfer and picture shares but not the home folders, I couldn't even see them.

This morning my laptop couldn't find the network(little strange) so I tried on laptop and pc of my cousin and on the desktop pc I can see the folders but I get access denied when trying to access them.
On the laptop when I dubble click the UbuntuServer in the network it asks me for username and password.

It's all kind of messed up seems to me.. 

I've got a fresh install of ubuntu server on a other machine aswell could you tell me what to do on the fresh install to achieve what I discribed in my first post? Just to see if that works, cause if that would work something else is wrong on my main machine.

Thanks yet again!!

---

### Post by DonBucknall on 2008-07-27
Well, I haven't been sitting around waiting so I copied the working smb.conf of my uncle wich is this:

```
#

# /etc/samba/smb.conf ist the main samba configuration file. Cf. the

# manual page of smb.conf and the included documantation in

# /usr/share/doc/packages/samba in order to understand the options

# listed here and many more features.

#

# Lines in this example which starts with ; and # are ignored comment

# ones. # indicates a comment and ; a deactivated example line.

#

# We suggest to use the command 'testparm' after any changes you made.

#

# Copyright (c) 1999 - 2001 SuSE GmbH Nuernberg, Germany.

#

# Please send bugfixes or comments to feedback@suse.de.

#

[global]

    workgroup = bucknall

    os level = 2



    security = user

    encrypt passwords = yes

    browseable = yes

#   guest account = guest

    map to guest = Bad User

    server string  = Mercury

;   hosts allow = 192.168.



# This tells samba to use the file smbusers for user mapping.

;   username map = /etc/samba/smbusers



# This tells samba to write log files per machine.

;   log file = /var/log/samba/%m

# This sets an alternate log level. Default is 2.

;   log level = 3





# Uncomment the following, if you want to use an existing NT-Server to

# authenticate users, but don't forget that you also have to create them

# locally!

;   security = server

;   password server = 192.168.1.10



    printing = LPRNG

    printcap name = /etc/printcap

    load printers = no



# These settings are a suggestion for a local network. Cf. section

# 'socket options' in the man page of smb.conf and socket(7).

    socket options = SO_KEEPALIVE IPTOS_LOWDELAY TCP_NODELAY



# Uncomment this, if you want to integrate your server

# into an existing net e.g. with NT-WS to prevent nettraffic

;   local master = No



# Please uncomment the following entry and replace the ip number and

# netmask with the values of your network interface configuration.

    interfaces = 192.168.0.3/255.255.255.0



# If you want Samba to act as a wins server, please set

# 'wins support' to yes.

    wins support = No



# If you want Samba to use an existing wins server, please uncomment the

# following line and replace the dummy with the wins server's ip number.

;   wins server = 192.168.1.1



# Set these two parameters to your DOS code page and appropriate UNIX

# character set. These values are for west European languages (Latin-9)

# UNIX character and MS-DOS Latin 1 code page.

    character set = ISO8859-15


    client code page = 850



# This is a simple measure against Nimba Worm. Cf. README.Win32-Viruses

    veto files = /*.eml/*.nws/riched20.dll/*.{*}/



# Do you wan't samba to act as a logon-server for your windows 95/98

# clients, so uncomment the following:

    domain logons = Yes

    domain master = Yes

# For a specific logon script per user

;   logon script = %U.bat

# For a specific logon script per machine

;   logon script = %m.bat



# Where to store the logon scripts.

;[netlogon]

;   comment = Network Logon Service

;   path = /var/lib/samba/netlogon



# Where profiles of Windows 9x systems are stored.

# First example for a centralized place.

;   logon home = \\%L\profiles\%U

# Second example for a subdirectory of the users home.

;   logon home = \\%L\%U\profile

# Where profiles of Windows NT systems are stored.

;   logon path = \\%L\profiles\%U



# Extra share for profiles. Default is the home of the user.

;[profiles]

;   comment = Network Profiles Service

;   path = /var/lib/samba/profiles

;   browseable = No



[homes]

    comment = Home Directories

    read only = No

    create mask = 0640

    directory mask = 0750

    browseable = no

    hide dot files = yes

    hide unreadable = yes



# The following share gives all users access to the Server's CD drive,

# assuming it is mounted under /media/cdrom. To enable this share,

# please remove the semicolons before the lines

[cdrom]

    comment = Linux CD-ROM

    path = /mnt/cdrom

    locking = No

    browseable = yes

    guest ok = yes



[guest]

    comment = Linux Download

    path = /home/guest

    locking = No

    read only = no

    browseable = yes

    guest ok = yes

    public = yes



[transfer]

    path = /home/transfer

    create mask = 0660

    public = yes

    writeable = yes

    browseable = yes



[music]

    path = /home/music

    create mask = 0660

    public = yes

    writeable = yes

    browseable =yes





[PLC]

    path = /home/PLC

    create mask = 0660

    public = yes

    writeable = yes

    browseable = yes



[books]

    path = /home/books

    create mask = 0660

    public = yes

    writeable = yes

    browseable = yes



[info]

    path = /home/info

    create mask = 0660

    public = yes

    writeable = yes

    browseable = yes



[manuals]

    path = /home/manuals

    create mask = 0660

    public = yes

    browseable = yes



[pictures]

    path = /home/pictures

    create mask = 0660

    public = yes

    browseable = yes



[appnotes]

    path = /home/appnotes

    create mask = 0660

    public = yes

    browseable = yes



[datasheets]

    path = /home/datasheets

    create mask = 0660

    public = yes

    browseable = yes


```

Deleted the folders I didn't need and set the folder permissions to 0777.
So music, pictures and transfer work now!

I've got 3 users on my machine, donbucknall, callum and billy now I want it so they can be seen on the network but can only be accessed with username and password. I haven't added them to samba yet, so what do I do from here?

Thanks!!

[EDIT] I don't know how this thank you system works, but I really appreciate all help!! And where I can I try to help others!!

---

