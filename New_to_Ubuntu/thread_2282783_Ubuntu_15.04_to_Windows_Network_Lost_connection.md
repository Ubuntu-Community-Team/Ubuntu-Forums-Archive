---
title: "Ubuntu 15.04 to Windows Network Lost connection"
date: 2015-06-16
forum: New to Ubuntu
---

### Post by john413 on 2015-06-16
[COLOR=#000000]Hi,[/COLOR]
[COLOR=#000000]I am another new user with a connectivity problem. I have a basic home network with 2 wireless Windows 7 machines, 1 wireless Windows 8.1 machine, an HP laser that is networked and now a Lenovo tower running Ubuntu 15.04. When I first installed from CD I could not connect the Ubuntu machine to the Windows network. After reading a lot of the posts and things I found online I gave up trying to figure it out (until I had a few hours to dedicate to figuring it out).[/COLOR]
[COLOR=#000000]After restarting over the weekend, all of the windows pc's showed up like the picture posted earlier in this thread:[/COLOR]
[http://ubuntuforums.org/attachment.php?attachmentid=262088&d=1432097473](http://ubuntuforums.org/attachment.php?attachmentid=262088&d=1432097473)

[COLOR=#000000]Last night they all disappeared [/COLOR]:sad:
[COLOR=#000000]I got a prompt yesterday telling me that there was an update needed and I let it install. After said update, the machine rebooted and now no connections to windows machines.[/COLOR]
[COLOR=#000000]The whole time I DO have internet access on this machine and I can successfully ping it from other machines on the network. I can also print to the networked printer which has a dedicated IP (192.168.1.11).[/COLOR]
[COLOR=#000000]I don't know if a service got turned off or what the problem is.[/COLOR]
[COLOR=#000000]Thank you in advance.[/COLOR]
[COLOR=#000000]PS When the Ubuntu machine could "see" the Windows machines, they could not see the Ubuntu machine.[/COLOR]

---

### Post by bab1 on 2015-06-16
> **john413 said:**
> [COLOR=#000000]Hi,[/COLOR]
[COLOR=#000000]I am another new user with a connectivity problem. I have a basic home network with 2 wireless Windows 7 machines, 1 wireless Windows 8.1 machine, an HP laser that is networked and now a Lenovo tower running Ubuntu 15.04. When I first installed from CD I could not connect the Ubuntu machine to the Windows network. After reading a lot of the posts and things I found online I gave up trying to figure it out (until I had a few hours to dedicate to figuring it out).[/COLOR]...

[COLOR=#000000]Last night they all disappeared [/COLOR]:sad:
[COLOR=#000000]I got a prompt yesterday telling me that there was an update needed and I let it install. After said update, the machine rebooted and now no connections to windows machines.[/COLOR]
[COLOR=#000000]The whole time I DO have internet access on this machine and I can successfully ping it from other machines on the network. I can also print to the networked printer which has a dedicated IP (192.168.1.11).[/COLOR]
[COLOR=#000000]I don't know if a service got turned off or what the problem is.[/COLOR]
[COLOR=#000000]Thank you in advance.[/COLOR]
[COLOR=#000000]PS When the Ubuntu machine could "see" the Windows machines, they could not see the Ubuntu machine.[/COLOR]
Let's start by seeing what you really have done...

How did you install and configure Samba?  Is Samba running right now?

From the terminal (ctrl+alt+t) post the output of this command```
pgrep -l  mbd
```..that's a lower case ell.

Also post the output of these commands```
smbtree -d3

cat /etc/samba/smb.conf
```
The last commands have lots of data.  Please post text output using the [noparse]```
  
```[/noparse] blocks.  The easiest way to do this is to click on the [SIZE=6]**# **[/SIZE]icon at the top of the advanced editor that you use to reply with.  This will add the code blocks and you just have to paste the data inside of them.

---

### Post by wildmanne39 on 2015-06-16
Please use thumbnails or url's when posting images because many people have a slow connection or a limit on bandwidth.
Thanks

---

### Post by john413 on 2015-06-16
```
john@john-ThinkCentre-M58p:~$ pgrep -l mbd
 956 nmbd
 972 smbd
 973 smbd
 2025 smbd
```
 
 
 ```
john@john-ThinkCentre-M58p:~$ smbtree -d3
 lp_load_ex: refreshing parameters
 Initialising global parameters
 rlimit_max: increasing rlimit_max (1024) to minimum Windows limit (16384)
 params.c:pm_process() - Processing configuration file "/etc/samba/smb.conf"
 Processing section "[global]"
 added interface eth0 ip=192.168.1.4 bcast=192.168.1.255 netmask=255.255.255.0
 Enter john's password:  
 tdb(/var/cache/samba/gencache.tdb): tdb_open_ex: could not open file /var/cache/samba/gencache.tdb: Permission denied
 resolve_lmhosts: Attempting lmhosts lookup for name WORKGROUP<0x1d>
 resolve_lmhosts: Attempting lmhosts lookup for name WORKGROUP<0x1d>
 name_resolve_bcast: Attempting broadcast lookup for name WORKGROUP<0x1d>
 Got a positive name query response from 192.168.1.4 ( 192.168.1.4 )
 Connecting to 192.168.1.4 at port 445
 Doing spnego session setup (blob length=74)
 got OID=1.3.6.1.4.1.311.2.2.10
 got principal=not_defined_in_RFC4178@please_ignore
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
 Got a positive name query response from 192.168.1.4 ( 192.168.1.4 )
 Connecting to 192.168.1.4 at port 445
 Doing spnego session setup (blob length=74)
 got OID=1.3.6.1.4.1.311.2.2.10
 got principal=not_defined_in_RFC4178@please_ignore
 Got challenge flags:
 Got NTLMSSP neg_flags=0x608a8215
 NTLMSSP: Set final flags:
 Got NTLMSSP neg_flags=0x60088215
 NTLMSSP Sign/Seal - Initialising with flags:
 Got NTLMSSP neg_flags=0x60088215
 	\\TP6            		
 resolve_lmhosts: Attempting lmhosts lookup for name TP6<0x20>
 resolve_lmhosts: Attempting lmhosts lookup for name TP6<0x20>
 resolve_wins: WINS server resolution selected and no WINS servers listed.
 resolve_hosts: Attempting host lookup for name TP6<0x20>
 Connecting to 192.168.1.3 at port 445
 E2BIG: convert_string(UTF-8,CP850): srclen=22 destlen=16 - 'JOHN-THINKCENTRE-M58P'
 Connecting to 192.168.1.3 at port 139
 samba_tevent: EPOLL_CTL_DEL EBADF for fde[0xb92d9850] mpx_fde[(nil)] fd[12] - disabling
 Doing spnego session setup (blob length=320)
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
 	\\TP5            		TP5
 resolve_lmhosts: Attempting lmhosts lookup for name TP5<0x20>
 resolve_lmhosts: Attempting lmhosts lookup for name TP5<0x20>
 resolve_wins: WINS server resolution selected and no WINS servers listed.
 resolve_hosts: Attempting host lookup for name TP5<0x20>
 Connecting to 192.168.1.12 at port 445
 E2BIG: convert_string(UTF-8,CP850): srclen=22 destlen=16 - 'JOHN-THINKCENTRE-M58P'
 Connecting to 192.168.1.12 at port 139
 samba_tevent: EPOLL_CTL_DEL EBADF for fde[0xb92da9d8] mpx_fde[(nil)] fd[14] - disabling
 	\\               		john-ThinkCentre-M58p server (Samba, Ubuntu)
 resolve_lmhosts: Attempting lmhosts lookup for name <0x20>
 resolve_lmhosts: Attempting lmhosts lookup for name <0x20>
 resolve_wins: WINS server resolution selected and no WINS servers listed.
 resolve_hosts: Attempting host lookup for name <0x20>
 resolve_hosts: getaddrinfo failed for name  [Name or service not known]
 name_resolve_bcast: Attempting broadcast lookup for name <0x20>
 samba_tevent: EPOLL_CTL_DEL EBADF for fde[0xb92dc3f0] mpx_fde[(nil)] fd[15] - disabling
 	\\JAMIE-PC2      		
 resolve_lmhosts: Attempting lmhosts lookup for name JAMIE-PC2<0x20>
 resolve_lmhosts: Attempting lmhosts lookup for name JAMIE-PC2<0x20>
 resolve_wins: WINS server resolution selected and no WINS servers listed.
 resolve_hosts: Attempting host lookup for name JAMIE-PC2<0x20>
 Connecting to 192.168.1.8 at port 445
 E2BIG: convert_string(UTF-8,CP850): srclen=22 destlen=16 - 'JOHN-THINKCENTRE-M58P'
 Connecting to 192.168.1.8 at port 139
 samba_tevent: EPOLL_CTL_DEL EBADF for fde[0xb92dac10] mpx_fde[(nil)] fd[14] - disabling
 samba_tevent: EPOLL_CTL_DEL EBADF for fde[0xb92dbb80] mpx_fde[(nil)] fd[15] - disabling
 
```
 


 
```
 john@john-ThinkCentre-M58p:~$ cat /etc/samba/smb.conf
 
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

``` 
 
 john@john-ThinkCentre-M58p:~$

---

### Post by cariboo on 2015-06-17
The image you linked to is a bit deceiving, it is a screenshot I uploaded, both alexis and willy are running Ubuntu and BRN_89A329 is a Brother networked Laser printer. Both the computers have one shared directory using the built-in directory sharing utility, available when right-clicking on the folder in nautilus. The Windows Workgroup directory contains the shared directories on my Ubuntu powered server. I have two systems running Windows, neither were booted up at the time of the screenshot.

---

### Post by bab1 on 2015-06-17
> **john413 said:**
> ```
john@john-ThinkCentre-M58p:~$ pgrep -l mbd
 956 nmbd
 972 smbd
 973 smbd
 2025 smbd
```


This shows that the Samba server (smbd is running.  It forks from the original whenever someone is using it. The NetBios name server (nmbd) is also running. 
> 
 
 
 ```
john@john-ThinkCentre-M58p:~$ smbtree -d3
 lp_load_ex: refreshing parameters
 Initialising global parameters
 rlimit_max: increasing rlimit_max (1024) to minimum Windows limit (16384)
 params.c:pm_process() - Processing configuration file "/etc/samba/smb.conf"
 Processing section "[global]"
 added interface eth0 ip=192.168.1.4 bcast=192.168.1.255 netmask=255.255.255.0
 Enter john's password:  
 tdb(/var/cache/samba/gencache.tdb): tdb_open_ex: could not open file /var/cache/samba/gencache.tdb: Permission denied
 resolve_lmhosts: Attempting lmhosts lookup for name WORKGROUP<0x1d>
 resolve_lmhosts: Attempting lmhosts lookup for name WORKGROUP<0x1d>
 name_resolve_bcast: Attempting broadcast lookup for name WORKGROUP<0x1d>
 Got a positive name query response from 192.168.1.4 ( 192.168.1.4 )
 Connecting to 192.168.1.4 at port 445
 ...
**[COLOR="#FF0000"] E2BIG: convert_string(UTF-8,CP850): srclen=22 destlen=16 - 'JOHN-THINKCENTRE-M58P'[/COLOR]**
 Connecting to 192.168.1.3 at port 139
 samba_tevent: EPOLL_CTL_DEL EBADF for fde[0xb92d9850] mpx_fde[(nil)] fd[12] - disabling
 ...
[COLOR="#FF0000"] E2BIG: convert_string(UTF-8,CP850): srclen=22 destlen=16 - 'JOHN-THINKCENTRE-M58P'
 Connecting to 192.168.1.8 at port 139
 samba_tevent: EPOLL_CTL_DEL EBADF for fde[0xb92dac10] mpx_fde[(nil)] fd[14] - disabling
 samba_tevent: EPOLL_CTL_DEL EBADF for fde[0xb92dbb80] mpx_fde[(nil)] fd[15] - disabling[/COLOR]
 
```

Without going further, the first problem we need to fix is the hostname length (noted in red).  This is converted to the netbios name by Samba.  Unfortunately the name is limited to 15 characters or less.  The hostname of you Ubuntu machine exceeds that (e.g. john-ThinkCentre-M58p).  We can explicitly declare a NetBios name however. *_ Do you have a name you would like to call this server?_*  Not longer than 15 characters and no spaces. Case (UPPER/loser is not important).
>  

```
 john@john-ThinkCentre-M58p:~$ cat /etc/samba/smb.conf
 
 #
 # Sample configuration file for the Samba suite for Debian GNU/Linux.
 #
...

``` 
 
 john@john-ThinkCentre-M58p:~$
The smb.conf file looks untouched from the default.  Have you created shares yet?  Have you created usershares by sharing a directory with the GUI interface.  Post the output of this command```
 net usershare info --long
```

---

### Post by bab1 on 2015-06-17
> **cariboo said:**
> The image you linked to is a bit deceiving, it is a screenshot I uploaded, both alexis and willy are running Ubuntu and BRN_89A329 is a Brother networked Laser printer. Both the computers have one shared directory using the built-in directory sharing utility, available when right-clicking on the folder in nautilus. The Windows Workgroup directory contains the shared directories on my Ubuntu powered server. I have two systems running Windows, neither were booted up at the time of the screenshot.
This post makes no sense to me.  Are you speaking for the OP?

---

### Post by john413 on 2015-06-17
Progress! Thank you BAB1!
The original name was picked by the software during the initial install. I shortened it and now I can see the Win 8.1 machine and 1 of the Win 7 machines from the Ubuntu machine
I made a shared folder on the Ubuntu machine, and the Win 8.1 and one of the Win 7 machines can see it.
Since those 3 are playing nice with each other, I need to figure out why the 2nd Win 7 machine won't connect with the Ubuntu machine. It will connect to the other Win machines so me thinks it is a Win problem.
Thank you again for your assistance!
John

---

### Post by bab1 on 2015-06-17
> **john413 said:**
> Progress! Thank you BAB1!
The original name was picked by the software during the initial install. I shortened it and now I can see the Win 8.1 machine and 1 of the Win 7 machines from the Ubuntu machine
I made a shared folder on the Ubuntu machine, and the Win 8.1 and one of the Win 7 machines can see it.
Since those 3 are playing nice with each other, I need to figure out why the 2nd Win 7 machine won't connect with the Ubuntu machine. It will connect to the other Win machines so me thinks it is a Win problem.
Thank you again for your assistance!
John

Most likely you are correct. I would check to see if the Windows machine has NetBios over TCP (NBT) working.  That is usually the problem.

---

### Post by cariboo on 2015-06-18
> **bab1 said:**
> This post makes no sense to me.  Are you speaking for the OP?

Check the link in the op's first post.

[http://ubuntuforums.org/attachment.php?attachmentid=262088&d=1432097473](http://ubuntuforums.org/attachment.php?attachmentid=262088&d=1432097473)

---

