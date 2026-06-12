---
title: "Access to Windows Shares over wireless network lost after automatic updates"
date: 2015-03-06
forum: New to Ubuntu
---

### Post by brhengineers on 2015-03-06
Fistly I am still finding my way around the Ubuntu forums so excuse me if this is not the right place to ask my question.  I originally posted it on [https://answers.launchpad.net/ubuntu/+question/263122](https://answers.launchpad.net/ubuntu/+question/263122) about 3 days ago but have had no response.  

I have been running Ubuntu 14.04 on a HP Probook 4710s for about four months. The initial set up took a little time but with help from the available online documentation I soon had everything I needed working well.  I have a wireless network setup with a Netgear router and it provides internet access to which my laptop still connects without problems.  I also have a desktop machine in my study running Window 7 and my wife has an Acer laptop also running Windows.  Until about 10 days ago I could access shared files on both Windows machines using Nautilus or applications such as LibreOffice and Gimp running on the laptop.  

I am using the automatic software updater to check for and recommend Ubuntu updates and accept its recommendated updates when it notifies me of them.  A few days ago I allowed this software  updater to install the latest updates and now have the following  problems: 

1.  I can no longer print to a Canon printer connected to the desktop machine over my wireless network.  Before the update this was working  perfectly

 2.  I can no longer access shared files and folders on the desktop machine or the Acer laptop.

 3.  When I use Nautilus and select "Browse Network" it shows the  desktop machine by its name “STUDY” and lists  Type “Unknown”, Modified  “Unknown” and Location “network:///” .  When I double click it I see two  sub-folders named “print$” with the location “smb://study/” and  “Ubuntu_Documents” also with the location “smb://study/”.  Double  clicking the Ubuntu_Documents folder mounts this folder under  “Network” but looking at what is in the folder it is actually the  Home  Documents folder of my Ubuntu user account on the HP Laptop.  I no longer have access to the shared files on the desktop machine STUDY.  The two Windows machines still access shared files over the network as before.

 This is a serious enough problem that unless I can find out how to fix it I may have to go back to using Windows on my laptop, which I would hate to do as I am otherwise enjoying Ubuntu's responsiveness and functionality.  I have to be able to print documents and to access and edit documents store on the study desktop machine that my wife and I share.

I can find nothing accessible through the GUI that helps and I don't know enough to use the Linux terminal to try and solve these problems.  Any help would  be appreciated.

 Bryan.

---

### Post by bab1 on 2015-03-06
> **brhengineers said:**
> Fistly I am still finding my way around the Ubuntu forums so excuse me if this is not the right place to ask my question.  I originally posted it on [https://answers.launchpad.net/ubuntu/+question/263122](https://answers.launchpad.net/ubuntu/+question/263122) about 3 days ago but have had no response.  

I have been running Ubuntu 14.04 on a HP Probook 4710s for about four months. The initial set up took a little time but with help from the available online documentation I soon had everything I needed working well.  I have a wireless network setup with a Netgear router and it provides internet access to which my laptop still connects without problems.  I also have a desktop machine in my study running Window 7 and my wife has an Acer laptop also running Windows.  Until about 10 days ago I could access shared files on both Windows machines using Nautilus or applications such as LibreOffice and Gimp running on the laptop.  

I am using the automatic software updater to check for and recommend Ubuntu updates and accept its recommendated updates when it notifies me of them.  A few days ago I allowed this software  updater to install the latest updates and now have the following  problems: 

1.  I can no longer print to a Canon printer connected to the desktop machine over my wireless network.  Before the update this was working  perfectly

 2.  I can no longer access shared files and folders on the desktop machine or the Acer laptop.

 3.  When I use Nautilus and select "Browse Network" it shows the  desktop machine by its name &#8220;STUDY&#8221; and lists  Type &#8220;Unknown&#8221;, Modified  &#8220;Unknown&#8221; and Location &#8220;network:///&#8221; .  When I double click it I see two  sub-folders named &#8220;print$&#8221; with the location &#8220;smb://study/&#8221; and  &#8220;Ubuntu_Documents&#8221; also with the location &#8220;smb://study/&#8221;.  Double  clicking the Ubuntu_Documents folder mounts this folder under  &#8220;Network&#8221; but looking at what is in the folder it is actually the  Home  Documents folder of my Ubuntu user account on the HP Laptop.  I no longer have access to the shared files on the desktop machine STUDY.  The two Windows machines still access shared files over the network as before.

 This is a serious enough problem that unless I can find out how to fix it I may have to go back to using Windows on my laptop, which I would hate to do as I am otherwise enjoying Ubuntu's responsiveness and functionality.  I have to be able to print documents and to access and edit documents store on the study desktop machine that my wife and I share.

I can find nothing accessible through the GUI that helps and I don't know enough to use the Linux terminal to try and solve these problems.  Any help would  be appreciated.

 Bryan.
It's going to be easier to diagnose your problems from the command line.  Post the output of these commands```
cat /etc/samba/smb.conf

smbtree -d3
```

Both of these commands will produce lots of data so you will have to scroll back to highlight and copy the text.  Do each one separately.  

Post the data back her by placing the output between the [noparse]```

```[/noparse] code blocks.  To do this you can click on the **[SIZE=5]#[/SIZE]** icon at the top of the Advanced Reply Editor.  You can then paste the text in between the [noparse]```

```[/noparse] code blocks.

---

### Post by brhengineers on 2015-03-07
Thanks BAB1.  Here is the output from the first command:

```

bryan@bryan-HP-ProBook-4710s:~$ cat /etc/samba/smb.conf
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
;   usershare max shares = 100

# Allow users who've been granted usershare privileges to create
# public shares, not just authenticated ones
   usershare allow guests = yes

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

bryan@bryan-HP-ProBook-4710s:~$ 

```


And here is the output from the second command:

```

bryan@bryan-HP-ProBook-4710s:~$ smbtree -d3
lp_load_ex: refreshing parameters
Initialising global parameters
rlimit_max: increasing rlimit_max (1024) to minimum Windows limit (16384)
params.c:pm_process() - Processing configuration file "/etc/samba/smb.conf"
Processing section "[global]"
added interface wlan0 ip=192.168.0.7 bcast=192.168.0.255 netmask=255.255.255.0
Enter bryan's password: 
tdb(/var/cache/samba/gencache.tdb): tdb_open_ex: could not open file /var/cache/samba/gencache.tdb: Permission denied
resolve_lmhosts: Attempting lmhosts lookup for name WORKGROUP<0x1d>
resolve_lmhosts: Attempting lmhosts lookup for name WORKGROUP<0x1d>
name_resolve_bcast: Attempting broadcast lookup for name WORKGROUP<0x1d>
Got a positive name query response from 192.168.0.2 ( 192.168.0.2 )
Connecting to 192.168.0.2 at port 445
E2BIG: convert_string(UTF-8,CP850): srclen=23 destlen=16 - 'BRYAN-HP-PROBOOK-4710S'
Connecting to 192.168.0.2 at port 139
samba_tevent: EPOLL_CTL_DEL EBADF for fde[0xb7eb6398] mpx_fde[(nil)] fd[8] - disabling
Doing spnego session setup (blob length=42)
got OID=1.3.6.1.4.1.311.2.2.30
got OID=1.3.6.1.4.1.311.2.2.10
got principal=<null>
Got challenge flags:
Got NTLMSSP neg_flags=0x628a8215
NTLMSSP: Set final flags:
Got NTLMSSP neg_flags=0x60088215
NTLMSSP Sign/Seal - Initialising with flags:
Got NTLMSSP neg_flags=0x60088215
WORKGROUP
resolve_lmhosts: Attempting lmhosts lookup for name WORKGROUP<0x1d>
resolve_lmhosts: Attempting lmhosts lookup for name WORKGROUP<0x1d>
name_resolve_bcast: Attempting broadcast lookup for name WORKGROUP<0x1d>
Got a positive name query response from 192.168.0.2 ( 192.168.0.2 )
Connecting to 192.168.0.2 at port 445
Doing spnego session setup (blob length=42)
got OID=1.3.6.1.4.1.311.2.2.30
got OID=1.3.6.1.4.1.311.2.2.10
got principal=<null>
Got challenge flags:
Got NTLMSSP neg_flags=0x628a8215
NTLMSSP: Set final flags:
Got NTLMSSP neg_flags=0x60088215
NTLMSSP Sign/Seal - Initialising with flags:
Got NTLMSSP neg_flags=0x60088215
    \\STUDY                  
resolve_lmhosts: Attempting lmhosts lookup for name STUDY<0x20>
resolve_lmhosts: Attempting lmhosts lookup for name STUDY<0x20>
resolve_wins: WINS server resolution selected and no WINS servers listed.
resolve_hosts: Attempting host lookup for name STUDY<0x20>
Connecting to 127.0.53.53 at port 445
Doing spnego session setup (blob length=74)
got OID=1.3.6.1.4.1.311.2.2.10
got principal=not_defined_in_RFC4178@please_ignore
Got challenge flags:
Got NTLMSSP neg_flags=0x608a8215
NTLMSSP: Set final flags:
Got NTLMSSP neg_flags=0x60088215
NTLMSSP Sign/Seal - Initialising with flags:
Got NTLMSSP neg_flags=0x60088215
        \\STUDY\Ubuntu_Documents    
        \\STUDY\Canon-LBP6020      Canon LBP6020 CAPT
        \\STUDY\print$             Printer Drivers
        \\STUDY\IPC$               IPC Service (bryan-HP-ProBook-4710s server (Samba, Ubuntu))
    \\                       bryan-HP-ProBook-4710s server (Samba, Ubuntu)
resolve_lmhosts: Attempting lmhosts lookup for name <0x20>
resolve_lmhosts: Attempting lmhosts lookup for name <0x20>
resolve_wins: WINS server resolution selected and no WINS servers listed.
resolve_hosts: Attempting host lookup for name <0x20>
Connecting to 192.168.0.5 at port 445
E2BIG: convert_string(UTF-8,CP850): srclen=23 destlen=16 - 'BRYAN-HP-PROBOOK-4710S'
Connecting to 192.168.0.5 at port 139
samba_tevent: EPOLL_CTL_DEL EBADF for fde[0xb7eca760] mpx_fde[(nil)] fd[13] - disabling
samba_tevent: EPOLL_CTL_DEL EBADF for fde[0xb7eca828] mpx_fde[(nil)] fd[14] - disabling
bryan@bryan-HP-ProBook-4710s:~$ 

```

thanks,
Bryan

---

### Post by brhengineers on 2015-03-07
Hi BAB1,

I may be importand that during output from the second command I was asked to enter my password.  I did so but the cursor did not move showing any input characters but pressing "Enter" continued the output.

Bryan.

---

### Post by bab1 on 2015-03-07
Bryan,

It looks like your problem is with your machine: **bryan-HP-ProBook-4710s**.  The SMB protocol specifies that the COMPUTER NAME (NETBIOS) must be no longer than 15 characters.  Samba has trouble converting the 21 character long hostname of your laptop to a 15 character NETBIOS NAME.

It is pretty easy to provide a proper NETBIOS name while leaving the hostname as it is.  I think it's also helpful to explicitly state the Samba name resolution method.  Here is what I think you should do:
Make a backup copy of the smb.conf file 
```
sudo cp /etc/samba/smb.conf /etc/samba/smb.conf.original
```

Then edit the smb.conf file.  You can edit the file with gedit with this command```
gksudo gedit /etc/samba/smb.conf
```

You will need to add this to the [global] section```

netbios name = HP-LAPTOP
name resolve order = bcast

```...you can use a different netbios name if you like.  Just remember that it can't be longer than 15 characters.

Now you need to restart Samba.  To do that you use this command```
sudo service smbd restart
```

Wait 5 minutes or so and then try smbtree.  Again, post the output of ```
smbtree -d3
```

---

### Post by bab1 on 2015-03-07
> **brhengineers said:**
> Hi BAB1,

I may be importand that during output from the second command I was asked to enter my password.  I did so but the cursor did not move showing any input characters but pressing "Enter" continued the output.

Bryan.
It's the normal reaction.  The login is not shown to the screen in this instance.

---

### Post by brhengineers on 2015-03-08
Hi BAB1,

Gksudo was not installed but I did this without a problem.  I have included the output from the terminal below in case there is an issue later so that you know exactly what I did.


```

bryan@bryan-HP-ProBook-4710s:~$ sudo cp /etc/samba/smb.conf /etc/samba/smb.conf.original
[sudo] password for bryan: 
bryan@bryan-HP-ProBook-4710s:~$ gksudo gedit /etc/samba/smb.conf
The program 'gksudo' is currently not installed. You can install it by typing:
sudo apt-get install gksu
bryan@bryan-HP-ProBook-4710s:~$ sudo apt-get install gksu
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following package was automatically installed and is no longer required:
  kde-l10n-engb
Use 'apt-get autoremove' to remove it.
The following extra packages will be installed:
  libgksu2-0
The following NEW packages will be installed:
  gksu libgksu2-0
0 upgraded, 2 newly installed, 0 to remove and 10 not upgraded.
Need to get 98,9 kB of archives.
After this operation, 728 kB of additional disk space will be used.
Do you want to continue? [Y/n] Y
Get:1 http://za.archive.ubuntu.com/ubuntu/ trusty/universe libgksu2-0 i386 2.0.13~pre1-6ubuntu4 [71,4 kB]
Get:2 http://za.archive.ubuntu.com/ubuntu/ trusty/universe gksu i386 2.0.2-6ubuntu2 [27,5 kB]
Fetched 98,9 kB in 1s (83,9 kB/s)
Selecting previously unselected package libgksu2-0.
(Reading database ... 657873 files and directories currently installed.)
Preparing to unpack .../libgksu2-0_2.0.13~pre1-6ubuntu4_i386.deb ...
Unpacking libgksu2-0 (2.0.13~pre1-6ubuntu4) ...
Selecting previously unselected package gksu.
Preparing to unpack .../gksu_2.0.2-6ubuntu2_i386.deb ...
Unpacking gksu (2.0.2-6ubuntu2) ...
Processing triggers for man-db (2.6.7.1-1ubuntu1) ...
Processing triggers for gconf2 (3.2.6-0ubuntu2) ...
Processing triggers for mime-support (3.54ubuntu1.1) ...
Processing triggers for gnome-menus (3.10.1-0ubuntu2) ...
Processing triggers for desktop-file-utils (0.22-1ubuntu1) ...
Processing triggers for bamfdaemon (0.5.1+14.04.20140409-0ubuntu1) ...
Rebuilding /usr/share/applications/bamf-2.index...
Setting up libgksu2-0 (2.0.13~pre1-6ubuntu4) ...
update-alternatives: using  /usr/share/libgksu/debian/gconf-defaults.libgksu-sudo to provide  /usr/share/gconf/defaults/10_libgksu (libgksu-gconf-defaults) in auto  mode
Processing triggers for gconf2 (3.2.6-0ubuntu2) ...
Setting up gksu (2.0.2-6ubuntu2) ...
Processing triggers for libc-bin (2.19-0ubuntu6.6) ...
bryan@bryan-HP-ProBook-4710s:~$ gksudo gedit /etc/samba/smb.conf

(gksudo:3167): GConf-CRITICAL **: gconf_value_free: assertion 'value != NULL' failed

(gedit:3176): Gtk-WARNING **: Calling Inhibit failed: GDBus.Error:eek:rg.freedesktop.DBus.Error.ServiceUnknown: The name org.gnome.SessionManager was not provided by any .service files
bryan@bryan-HP-ProBook-4710s:~$ sudo service smbd restart
smbd stop/waiting
smbd start/running, process 3280
bryan@bryan-HP-ProBook-4710s:~$

```

After the above running smbtree -d3 produced the following output:

```

bryan@bryan-HP-ProBook-4710s:~$ smbtree -d3
lp_load_ex: refreshing parameters
Initialising global parameters
rlimit_max: increasing rlimit_max (1024) to minimum Windows limit (16384)
params.c:pm_process() - Processing configuration file "/etc/samba/smb.conf"
Processing section "[global]"
added interface wlan0 ip=192.168.0.7 bcast=192.168.0.255 netmask=255.255.255.0
Enter bryan's password: 
tdb(/var/cache/samba/gencache.tdb): tdb_open_ex: could not open file /var/cache/samba/gencache.tdb: Permission denied
name_resolve_bcast: Attempting broadcast lookup for name WORKGROUP<0x1d>
Got a positive name query response from 192.168.0.2 ( 192.168.0.2 )
Connecting to 192.168.0.2 at port 445
Connecting to 192.168.0.2 at port 139
samba_tevent: EPOLL_CTL_DEL EBADF for fde[0xb9325210] mpx_fde[(nil)] fd[8] - disabling
Doing spnego session setup (blob length=42)
got OID=1.3.6.1.4.1.311.2.2.30
got OID=1.3.6.1.4.1.311.2.2.10
got principal=<null>
Got challenge flags:
Got NTLMSSP neg_flags=0x628a8215
NTLMSSP: Set final flags:
Got NTLMSSP neg_flags=0x60088215
NTLMSSP Sign/Seal - Initialising with flags:
Got NTLMSSP neg_flags=0x60088215
WORKGROUP
name_resolve_bcast: Attempting broadcast lookup for name WORKGROUP<0x1d>
Got a positive name query response from 192.168.0.2 ( 192.168.0.2 )
Connecting to 192.168.0.2 at port 445
Connecting to 192.168.0.2 at port 139
samba_tevent: EPOLL_CTL_DEL EBADF for fde[0xb9336c48] mpx_fde[(nil)] fd[10] - disabling
Doing spnego session setup (blob length=42)
got OID=1.3.6.1.4.1.311.2.2.30
got OID=1.3.6.1.4.1.311.2.2.10
got principal=<null>
Got challenge flags:
Got NTLMSSP neg_flags=0x628a8215
NTLMSSP: Set final flags:
Got NTLMSSP neg_flags=0x60088215
NTLMSSP Sign/Seal - Initialising with flags:
Got NTLMSSP neg_flags=0x60088215
    \\STUDY                  
name_resolve_bcast: Attempting broadcast lookup for name STUDY<0x20>
Got a positive name query response from 192.168.0.2 ( 192.168.0.2 )
Connecting to 192.168.0.2 at port 445
Doing spnego session setup (blob length=42)
got OID=1.3.6.1.4.1.311.2.2.30
got OID=1.3.6.1.4.1.311.2.2.10
got principal=<null>
Got challenge flags:
Got NTLMSSP neg_flags=0x628a8215
NTLMSSP: Set final flags:
Got NTLMSSP neg_flags=0x60088215
NTLMSSP Sign/Seal - Initialising with flags:
Got NTLMSSP neg_flags=0x60088215
        \\STUDY\VERBATIM2TB        
        \\STUDY\Users              
        \\STUDY\TEMP STUFF         
        \\STUDY\print$             Printer Drivers
        \\STUDY\PortableApps       
        \\STUDY\Photographs        
        \\STUDY\My Pictures        
        \\STUDY\My Documents       
        \\STUDY\Music              
        \\STUDY\IPC$               Remote IPC
        \\STUDY\hp psc 1200 series    hp psc 1200 series
        \\STUDY\E$                 Default share
        \\STUDY\Dropbox            
        \\STUDY\D Unknown          
        \\STUDY\D                  
        \\STUDY\Canon LBP6020      Canon LBP6020
        \\STUDY\C$                 Default share
        \\STUDY\Bryans Pictures    
        \\STUDY\Bryan              
        \\STUDY\Andrews Pictures    
        \\STUDY\ADMIN$             Remote Admin
    \\                       bryan-HP-ProBook-4710s server (Samba, Ubuntu)
name_resolve_bcast: Attempting broadcast lookup for name <0x20>
samba_tevent: EPOLL_CTL_DEL EBADF for fde[0xb93390c0] mpx_fde[(nil)] fd[14] - disabling
bryan@bryan-HP-ProBook-4710s:~$ 


```

I have now checked and access to the windows shares is working as is printing to the shared printers.  Thanks!

If I can ask two questions please.  Why did the Ubuntu update have this effect?  Did it change the 
/etc/samba/smb.conf file content?
Is this likely to happen again?

Secondly in the output from installing gedit there is code saying
```

The following package was automatically installed and is no longer required:
  kde-l10n-engb
Use 'apt-get autoremove' to remove it.

```

Do I need to run apt-get autoremove?

Your help is much appreciated.

Bryan.

---

### Post by bab1 on 2015-03-08
> **brhengineers said:**
> Hi BAB1,
...

I have now checked and access to the windows shares is working as is printing to the shared printers.  Thanks!

If I can ask two questions please.  Why did the Ubuntu update have this effect?  Did it change the 
/etc/samba/smb.conf file content?
Is this likely to happen again?

1. I usually find that this happens because the configuration was not correct in the first place.  I've often wondered how did it work originally?
2. Not in the sense that it changed anything in the smb.conf file.
3. No.  it's configured correctly now.
> 

Secondly in the output from installing gedit there is code saying
```

The following package was automatically installed and is no longer required:
  kde-l10n-engb
Use 'apt-get autoremove' to remove it.

```

Do I need to run apt-get autoremove?

I think you mean gksudo rather than gedit here.  The  package *kde-l10n-engb *has to do with **British English (engb) localization for KDE**.  It doesn't have anything to do with with you installing *gksudo*.  My bet is it has been available for removal for some time.  Autoremove is used to remove abandoned packages that did not get removed when other packages were removed.

> 
Your help is much appreciated.

Bryan.
Let's mark this solved.  You can do that using the **Thread Tools ** menu at the top right of the editor.

---

### Post by brhengineers on 2015-03-08
Thanks!

---

