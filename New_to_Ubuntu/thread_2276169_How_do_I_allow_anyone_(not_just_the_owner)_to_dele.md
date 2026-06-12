---
title: "How do I allow anyone (not just the owner) to delete files/folders"
date: 2015-04-30
forum: New to Ubuntu
---

### Post by kkc on 2015-04-30
Thanks to you guys I got my drives on my Ubuntu 14.04 machine sharing with Win 7 machines on a local network. When another computer adds a folder to a shared partition, somebody on a different computer can't delete that folder. I thought I had all the permission set at 777 but I must be missing something. Is there  a way to give everybody total access to create/delete any folders/directories/files? We don't have any security issues since all our computers are on a local network in one location.

---

### Post by TheFu on 2015-04-30
Can you post the samba settings, please?
Would also be helpful to see the **ls -al **to the share directory.

Just because computers are on the same network, that doesn't stop ANY security issues - actually, it makes for more of them.

---

### Post by kkc on 2015-04-30
Samba settings: Allow access to everyone, Guest Account: No Guest Account,  Read/Write on the shares


Here is the listing:

kevin@coolermaster:~$ ls -al /media/Data1
total 24
drwxr-xr-x 6 root  root  4096 Apr 30 08:37 .
drwxr-xr-x 4 root  root  4096 Apr 30 06:59 ..
drwxrwxrwx 5 kevin kevin 4096 Apr 30 11:05 2tb1
drwxrwxrwx 5 kevin kevin 4096 Apr 30 11:05 2tb2
drwxrwxrwx 4 root  root  4096 Apr 30 12:19 4tb1
drwxrwxrwx 3 root  root  4096 Apr 27 16:20 4tb2
kevin@coolermaster:~$ 

Testing a little further it's just on the Ubuntu computer that I can't delete a folder placed in the shared partition by a Windows7 computer, unless 
I use gksudo nautilus. The other Window7 computers can delete a folder they didn't place in the shared partition.

---

### Post by sandyd on 2015-04-30
Which files are created by other people?

---

### Post by kkc on 2015-04-30
> **sandyd said:**
> Which files are created by other people?

We have three people working at our office and we have 12 windows computers and 2 Ubuntu computers. We just want everyone to have complete access at any computer they happen to be on. We develop Windows software but find that a Ubuntu file server in much more reliable than the old Windows server we used to have. We have a 10.04 Ubuntu file server running and will replace it with the 14.04 version.

---

### Post by TheFu on 2015-04-30
> **kkc said:**
> Samba settings: Allow access to everyone, Guest Account: No Guest Account,  Read/Write on the shares

You are trying to do this without editing the /etc/samba/smb.conf file?  Sorry - can't help. Don't know anything about the GUI control of settings.  I really expected you to post the smb.conf file.

> **kkc said:**
> 
Here is the listing:

kevin@coolermaster:~$ ls -al /media/Data1
total 24
drwxr-xr-x 6 root  root  4096 Apr 30 08:37 .
drwxr-xr-x 4 root  root  4096 Apr 30 06:59 ..
drwxrwxrwx 5 kevin kevin 4096 Apr 30 11:05 2tb1
drwxrwxrwx 5 kevin kevin 4096 Apr 30 11:05 2tb2
drwxrwxrwx 4 root  root  4096 Apr 30 12:19 4tb1
drwxrwxrwx 3 root  root  4096 Apr 27 16:20 4tb2
kevin@coolermaster:~$ 

Testing a little further it's just on the Ubuntu computer that I can't delete a folder placed in the shared partition by a Windows7 computer, unless 
I use gksudo nautilus. The other Window7 computers can delete a folder they didn't place in the shared partition.

Thanks for the ls -al. That helps slightly. Is there a reason kevin doesn't own the other directories too?
Be very careful running **any** GUI program with sudo. There are likely unwanted side effects.
Are those directories mount points?  Are they all Linux file systems or something else? 

Sorry for all the questions - I'd like to not make assumptions.

---

### Post by kkc on 2015-04-30
There are 4 drives one at each mount point 2tb1,2tb2,4tb1,4tb2. I don't know why doesn't own the 4tb1 and 4tb2, they are 4 TB drives the other are 2TB drives. All ext4 formats.

Sorry about not sending the smb.config file the first time.

Here is the listing:

```
#======================= Global Settings =======================

[global]

## Browsing/Identification ###

# Change this to the workgroup/NT-domain name your Samba server will part of
    workgroup = cmh

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
;    passdb backend = tdbsam

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
;    usershare max shares = 100

# Allow users who've been granted usershare privileges to create
# public shares, not just authenticated ones
    usershare allow guests = yes
    username map = /etc/samba/smbusers
    security = user
;    encrypt passwords = yes
;    guest ok = no
;    guest account = nobody

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
;    guest ok = no
;    read only = yes
    create mask = 0700

# Windows clients look for this share name as a source of downloadable
# printer drivers
[print$]
    comment = Printer Drivers
    path = /var/lib/samba/printers
;    browseable = yes
;    read only = yes
;    guest ok = no
# Uncomment to allow remote administration of Windows print drivers.
# You may need to replace 'lpadmin' with the name of the group your
# admin users are members of.
# Please note that you also need to set appropriate Unix permissions
# to the drivers directory for these users to have write rights in it
;   write list = root, @lpadmin

[4tb1]
    comment = 4tb1
    path = /media/Data1/4tb1
    writeable = yes
;    browseable = yes
    guest ok = yes

[4tb2]
    comment = 4tb2
    path = /media/Data1/4tb2
    writeable = yes
;    browseable = yes
    guest ok = yes

[2tb1]
    comment = 2tb1
    path = /media/Data1/2tb1
    writeable = yes
;    browseable = yes
    guest ok = yes

[2tb2]
    comment = 2tb2
    path = /media/Data1/2tb2
    writeable = yes
;    browseable = yes
    guest ok = yes
```

---

### Post by bab1 on 2015-04-30
> **kkc said:**
> Samba settings: Allow access to everyone, Guest Account: No Guest Account,  Read/Write on the shares


Here is the listing:

kevin@coolermaster:~$ ls -al /media/Data1
total 24
drwxr-xr-x 6 root  root  4096 Apr 30 08:37 .
drwxr-xr-x 4 root  root  4096 Apr 30 06:59 ..
drwxrwxrwx 5 kevin kevin 4096 Apr 30 11:05 2tb1
drwxrwxrwx 5 kevin kevin 4096 Apr 30 11:05 2tb2
drwxrwxrwx 4 root  root  4096 Apr 30 12:19 4tb1
drwxrwxrwx 3 root  root  4096 Apr 27 16:20 4tb2
kevin@coolermaster:~$ 

Testing a little further it's just on the Ubuntu computer that I can't delete a folder placed in the shared partition by a Windows7 computer, unless 
I use gksudo nautilus. The other Window7 computers can delete a folder they didn't place in the shared partition.

That's because you don't get to control the permissions that are provided on the later CREATED files and sub-directories.  Without configuring Linux users and Samba users with  a common user group, you will always find the you will lose access to other users work.  You need to configure the file system structure a little better than you have described in previous posts.  If you hack away at all of this and create workarounds so you can do this via a GUI interface you will be doomed to frustration.

Multiple users and machines means you need to manage the system by adding and managing those users and their data, not by abdicating the responsibility with "access for everyone".  All users, including the user nobody create files with the permissions of 664.  This is set by umask.  It is fairly easy to live within those bounds.  However, you can't set the the proper environment up unless you use the terminal to configure the system.

The basic CLI steps are:
[LIST]
[*]Set up the file system with the permissions set to include group inheritance
[*]Create Linux users and corresponding Samba users for all of your employees 
[*]Set the Samba shares to correctly share the data via the common user group(s) of your choice.
[*]
[/LIST]

---

### Post by kkc on 2015-04-30
BAB1

Thanks for the insight, guess I better learn to use the terminal commands.

---

### Post by Morbius1 on 2015-05-01
Is this a continuation of this post: [http://ubuntuforums.org/showthread.php?t=2275793](http://ubuntuforums.org/showthread.php?t=2275793)

Based on these requirements where everyone ( including the server user "kevin ) has total access and you don't want or need to pass credentials to gain access:
> When another computer adds a folder to a shared partition, somebody on a different computer can't delete that folder. I thought I had all the permission set at 777 but I must be missing something. [COLOR=#0000cd]**Is there a way to give everybody total access to create/delete any folders/directories/files? We don't have any security issues since all our computers are on a local network in one location.**[/COLOR] 
> **[COLOR=#0000cd]Testing a little further it's just on the Ubuntu computer that I can't delete a folder placed in the shared partition by a Windows7 computer[/COLOR]**, unless
I use gksudo nautilus. The other Window7 computers can delete a folder they didn't place in the shared partition. 

I would suggest something like this:

Take this one as an example:
> [4tb1]
    comment = 4tb1
    path = /media/Data1/4tb1
    writeable = yes
;    browseable = yes
    guest ok = yes
Add a line to the share definition so that it looks like this:
> [4tb1]
    comment = 4tb1
    path = /media/Data1/4tb1
    writeable = yes
;    browseable = yes
    guest ok = yes
    [COLOR=#0000cd]**force user = kevin**[/COLOR]
Then restart samba:
```
sudo service smbd restart
```

What will happen is samba will allow the remote guest user access to that particular share and then convert his identity ( from "nobody" ) to "kevin". Every file added by that user will be owned by "kevin". Every file added by "kevin" on the server itself will be owned by "kevin". All kevin all the time.

You will have to clean up the files and folders already there so that it's all owned by kevin but any future files added are kevin's.

[COLOR=#0000cd]**Important Note**[/COLOR]: Just remember that if another user - if there is one - or another process other than kevin adds anything to this folder on the server side or if there is a process adding things to this folder outside of samba it may not be owned by "kevin". If that happens with great regularity this is not the best option. If it happens rarely just remember to change ownership to kevin.

---

### Post by SeijiSensei on 2015-05-01
I use both Samba and NFS on my fileservers.  I use NFS to export shares to Linux machines and Samba for Windows clients.  As long as the username to user ID mappings are identical in the Ubuntu client's /etc/passwd and /etc/group files and the server's copies of those files, [NFS is pretty simple to set up]("https://help.ubuntu.com/community/SettingUpNFSHowTo").  In my experience it also has better performance than Samba for Unix-to-Unix filesharing.

Entries in /etc/passwd and/etc/group:
```

seiji:x:1000:1000:SeijiSensei:/home/seiji:/bin/bash

seiji:x:1000:

```
The first user in Ubuntu is assigned UID 1000 with later users getting IDs of 1001, 1002, etc.

You can assign new users to unused UIDs with the command:
```
sudo adduser --uid 1234 --gid 1234 username
```
You can modify existing users with the [usermod](http://manpages.ubuntu.com/manpages/trusty/man8/usermod.8.html) command.

---

### Post by TheFu on 2015-05-01
Plus with NFS, normal group membership we all know and love are valid, so sharing access to files and directories is straight forward.

Of course, if the clients are Windows, then Samba is almost always the best answer. There are security implications with using **force user**. These are probably not too important, but only you can decide and take any needed mitigation steps. Using a different userid might be better than one with any controls/login on the box, for example.

---

### Post by bab1 on 2015-05-01
> **Morbius1 said:**
> 

What will happen is samba will allow the remote guest user access to that particular share and then convert his identity ( from "nobody" ) to "kevin". 

Sort of but not really.  I works more like suid bit in that it assigns the "forced user" ownership to all files created.  I find that a hack (although a useful one).  I can lead to problems down the road. As you point out below.  It is the potential security risk that @TheFu mentioned.  
> 
Every file added by that user will be owned by "kevin". Every file added by "kevin" on the server itself will be owned by "kevin". All kevin all the time.

You will have to clean up the files and folders already there so that it's all owned by kevin but any future files added are kevin's.

[COLOR=#0000cd]**Important Note**[/COLOR]: Just remember that if another user - if there is one - or another process other than kevin adds anything to this folder on the server side or if there is a process adding things to this folder outside of samba it may not be owned by "kevin". If that happens with great regularity this is not the best option. If it happens rarely just remember to change ownership to kevin.
It's much faster to just bite the bullet and set the system up correctly.  In a group environment people come and go.  As you point out the user **kevin** may not be the only user in future.  Even worse, the user kevin may be gone from the team.

---

### Post by SeijiSensei on 2015-05-01
I've used "force user" in smb.conf when I had a small group of clients sharing a Windows accounting application.  I created a user "accounts" on the Linux server and exported a subdirectory under /home/accounts with "force user|group = accounts".  That worked fine in this case because the user management and auditing took place within the application itself.  If you need to track who creates files in a shared directory, this is not an acceptable solution.  If you're okay with users deleting files created by other users, then the "force user" approach would probably work for your application.

---

