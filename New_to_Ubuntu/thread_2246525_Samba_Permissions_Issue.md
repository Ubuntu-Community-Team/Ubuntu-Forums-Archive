---
title: "Samba Permissions Issue"
date: 2014-10-01
forum: New to Ubuntu
---

### Post by josh97 on 2014-10-01
Hello all,

I have been scouring the internet in search of some valid information regarding samba share permissions and have a few questions. 

Some background info: I was not the one to setup the server or samba, that person is now gone and I have to take over.    My setup is Ubuntu 14.04 LTS with samba 4.1.6.  I have some experience with terminal as well as the Ubuntu GUI dating back to v8.10. It's running on an Intel Conroe system with 3 - 120GB SSD's in Raid 5.  

The issue I've encountered is: everytime a user, from their windows 7 PC, saves a document into their server directory the permissions that are attached to the document is 755, where the owner can do rwx, the group and other can do rx.  All I'm trying to setup is a 775 scenario where both the owner and the group have rwx permissions.

I've already enabled each persons individual account on the server to use the 775 permissions as well as modified the smb.conf file for create mask and directory mask yet the problem persists.  I've made sure that all users are included in the same primary group by doing a usermod -g "group" "user" for each account.  I also performed the 775 permissions update by doing: 

          chmod g+s <directory>
                                                                                 setfacl -d -m g::rwx /<directory>  /*set group*/
                                                                                 setfacl -d -m o::rw /<directory> /*set other*/
and checked it with:        getfacl /<directory>
The settings were enabled.

My questions are:

1. I've seen that many people have uploaded examples of their smb.conf files and they all include certain aspects that mine currently doesn't encompass.  These aspects are: force create mode, force directory mode, force directory security mode, directory security mask, directory security mode.  How is it that my smb.conf doesn't include these or are they actually listed as something else but referred to as the terms stated above?

2. Why is it that after modifying the permissions for each account and in the smb.conf (at least the ones I've located) that new files still are unwritable to group users?

Any additional suggestions are fully welcomed and thank you all for taking the time to look over this.

---

### Post by bab1 on 2014-10-01
> **josh97 said:**
> The issue I've encountered is: everytime a user, from their windows 7 PC, saves a document into their server directory the permissions that are attached to the document is 755, where the owner can do rwx, the group and other can do rx.  All I'm trying to setup is a 775 scenario where both the owner and the group have rwx permissions.

The basic permissions are set at 0777 for directory objects and 0666 for file objects.  The umask settings provide the actual permissions when a file or directory is created.  The umask should be 0002 and you subtract that from the 0777 or 0666 setting depending upon which object you are creating.  This means the default creation settings are directory = 775 and file = 664 (unless you are acting as root then the umask is 0022 providing 0755 and 0644 permissions.  The last umask setting declared is the umask that is used so some of the settings you are seeing are really just providing a umask for that shares operation.  Post the output of this command```
umask
```
> 
I've already enabled each persons individual account on the server to use the 775 permissions 

What did you do to achieve this?
> 
as well as modified the smb.conf file for create mask and directory mask yet the problem persists.  

These have always worked for me.  Post the complete smb.conf file so we may review it.  Use the ```
 blocks to preserve the formatting of the file.  The can be done by clicking on the [SIZE=5]**#**[/SIZE] icon at the top of the "advanced" editor that you use for reply.
> 
I've made sure that all users are included in the same primary group by doing a usermod -g "group" "user" for each account.  

This will work but it is not the common way (the Linux way) of doing this.  In fact it defeats the Debian "User Private Directory" scheme.  You can get the same inheritance scheme set by the particular file system branch using the sgid bit.  In fact that is what the ***chmod g+s*** used for below.  Why did you do that also? 
> 

I also performed the 775 permissions update by doing:[CODE] chmod g+s <directory>
setfacl -d -m g::rwx /<directory>  /*set group*/
setfacl -d -m o::rw /<directory> /*set other*/
```
and checked it with:        getfacl /<directory>
The settings were enabled.

But possibly misused in this instance.
> 

My questions are:

1. I've seen that many people have uploaded examples of their smb.conf files and they all include certain aspects that mine currently doesn't encompass.  These aspects are: force create mode, force directory mode, force directory security mode, directory security mask, directory security mode.  How is it that my smb.conf doesn't include these or are they actually listed as something else but referred to as the terms stated above?

Post the entire smb.conf file and then we may be able to answer your question.
> 

2. Why is it that after modifying the permissions for each account and in the smb.conf (at least the ones I've located) that new files still are unwritable to group users?

What is that output you have returned with this command```
umask
```> 

Any additional suggestions are fully welcomed and thank you all for taking the time to look over this.
Post the output I asked for and maybe some links to the examples you referred to and we can go from there.

---

### Post by josh97 on 2014-10-03
Hello BAB1,

Thank you for your reply and information.  Below is the smb.conf file that I modified using gedit within the server GUI environment.  

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

# What naming service and in what order should we use to resolve host names
# to IP addresses
;   name resolve order = lmhosts host wins bcast

#### Networking ####

# The specific set of interfaces / networks to bind to
# This can be either the interface name or an IP address/netmask;
# interface names are normally preferred
;   interfaces = [127.0.0.0/8]("http://127.0.0.0/8") eth0

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
;    encrypt passwords = yes

# If you are using encrypted passwords, Samba will need to know what
# password database type you are using.  
;    passdb backend = tdbsam

    obey pam restrictions = yes

# This boolean parameter controls whether Samba attempts to sync the Unix
# password with the SMB password when the encrypted SMB password in the
# passdb is changed.
    unix password sync = yes

# For Unix password sync to work on a Debian GNU/Linux system, the following
# parameters must be set (thanks to Ian Kahan <<[EMAIL="kahan@informatik.tu-muenchen.de"]kahan@informatik.tu-muenchen.de[/EMAIL]> for
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
;    printing = cups
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
;    usershare max shares = 100

# Allow users who've been granted usershare privileges to create
# public shares, not just authenticated ones
    usershare allow guests = yes
    username map = /etc/samba/smbusers
    security = user
;    guest ok = no
;    guest account = nobody

#======================= Share Definitions =======================

# Un-comment the following (and tweak the other settings below to suit)
# to enable the default home directory shares. This will share each 
# user's home director as \\server\username
;[homes]
;   comment = Home Directories
;   browseable = no

# By default, the home directories are exported read-only. Change the
# next parameter to 'no' if you want to be able to write to them.
;   read only = no

# File creation mask is set to 0700 for security reasons. If you want to
# create files with group=rw permissions, set next parameter to 0775.
;   create mask = 0775

# Directory creation mask is set to 0700 for security reasons. If you want to
# create dirs. with group=rw permissions, set next parameter to 0775.
;   directory mask = 0775

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

/* All user accounts are writable but not browseable */ 


The output from umask is 0022.

Here are a few of the links to the examples I used.  Some are directly related yet others are variations of similar issues.

[https://wiki.samba.org/index.php/Setup_and_configure_file_shares_with_Windows_ACLs](https://wiki.samba.org/index.php/Setup_and_configure_file_shares_with_Windows_ACLs)

[http://askubuntu.com/questions/403252/samba-file-share-permissions-issue](http://askubuntu.com/questions/403252/samba-file-share-permissions-issue)

[http://ubuntuforums.org/showthread.php?t=2198667](http://ubuntuforums.org/showthread.php?t=2198667)

[http://linuxcommand.org/lts0070.php](http://linuxcommand.org/lts0070.php)

[http://www.linux.com/learn/tutorials/760276-how-to-manage-file-and-folder-permissions-in-linux](http://www.linux.com/learn/tutorials/760276-how-to-manage-file-and-folder-permissions-in-linux)

[http://www.linuxquestions.org/questions/linux-newbie-8/what-is-the-use-of-chmod-g-s-245762/](http://www.linuxquestions.org/questions/linux-newbie-8/what-is-the-use-of-chmod-g-s-245762/)

I am specifically not writing a script that would run every few seconds and update permissions on files and folders because that's not fixing the real issue.  I know there has to be something I'm overlooking or do not currently comprehend about the permissions setup that will make this work properly and that's the outcome I'm looking for.  Thank you for going through this with me and helping me deduce what the true issue is.

---

### Post by Michael_McKenney on 2014-10-03
[FONT=Courier New]smbpasswd -a joe[/FONT]

Did you add the user to Samba.  I setup Samba last night.  I did the SMB.Conf file for the Homes.   I had to add the user and restart the services smbd and nmbd to get the changes to be active.

[http://www.cyberciti.biz/faq/adding-a-user-to-a-samba-smb-share/](http://www.cyberciti.biz/faq/adding-a-user-to-a-samba-smb-share/)

---

### Post by josh97 on 2014-10-03
Yes, all users were added to samba about 3 months ago and everything works except the permissions for newly created files.

---

### Post by Michael_McKenney on 2014-10-03
ls -la will show your folder rights.  Did you give both directory and folder 775 rights?

---

### Post by bab1 on 2014-10-03
> **josh97 said:**
> Hello BAB1,

Thank you for your reply and information.  Below is the smb.conf file that I modified using gedit within the server GUI environment. 

What did you modify.  It appears to be very close to the default.  I don't see any shares added.  But then again I may have missed something.  In the future used the Advanced Reply to respond if you are going to add terminal output.  This way you can use the **[SIZE=3]```
[/SIZE]** blocks option to preserver the text formatting.  See the [SIZE=5]**# **[/SIZE] icon at the top of the editor?  If not then you are not in advanced mode.

This 
> 

[CODE]/* All user accounts are writable but not browseable */ 
```
What does the above mean?> 

The output from umask is 0022.

More and more this doesn't look much like a Ubuntu 14.04 installation.  The smb.conf file looks to be from a Samba v3 package and the umask is not what the current versions of Ubuntu uses.  I believe that the umask has been 0002 since at least Ubuntu 10.04.  Here is the output from one of my servers that is Ubuntu 10.04 LTS.```
lsb_release -a
No LSB modules are available.
Distributor ID:	Ubuntu
Description:	Ubuntu 10.04.4 LTS
Release:	10.04
Codename:	lucid

``` ... Clearly not a current version of Ubuntu```
umask
0002

```...but with the correct umask 
> 

I am specifically not writing a script that would run every few seconds and update permissions on files and folders because that's not fixing the real issue.  I know there has to be something I'm overlooking or do not currently comprehend about the permissions setup that will make this work properly and that's the outcome I'm looking for.  Thank you for going through this with me and helping me deduce what the true issue is.
All permissions for new objects that are created (directories or files) use umask to determine the initial permissions.  Are we really talking about new files and directories?  Data that has been moved or copied is not considered as new creations by Samba so the original permissions and ownership is persevered on a best effort basis. 

What distro and what version of that distro are you using?  Umask is a configurable parameter.   It also appears you are using Samba usershares (configured via a GUI interface).  Normally you do not use this type of share configuration if you want specialized configuration parameters.

---

### Post by josh97 on 2014-10-06
Hello,

/* All user accounts are writable but not browseable */

This was meant to act as a comment.  Peoples full names are their usernames on this server so I cannot upload that information therefore I placed a comment within the document to specify the permissions for specific user accounts.  I am used to Java and C programming syntax so that is why I chose to represent it as such.

I modified the share definitions only: read only, create mask, and directory mask.  Are they correct in octal value for what I'm trying to achieve and should I modify anything else?

When I performed the lsb_release -a command I got this:

[FONT=Verdana]lsb_release -a
No LSB modules are available.
Distributor ID: Ubuntu
Description:  Ubuntu 14.04 LTS[/FONT]
[FONT=Verdana]Release:  14.04[/FONT]
[FONT=Verdana]Codename: trusty
[/FONT]
and Samba is:
#smbstatus
Samba version 4.1.6

I am using samba through a GUI, is there a big difference between terminal and GUI for samba operation and setup?

Each account is password protected so only certain people have access to it.  Those same accounts are not visible.  Is there any settings within my smb.conf file that could be conflicting with what I'm trying to do?

Thanks again for you help!

---

### Post by bab1 on 2014-10-07
> **josh97 said:**
> Hello,

/* All user accounts are writable but not browseable */

This was meant to act as a comment.  Peoples full names are their usernames on this server so I cannot upload that information therefore I placed a comment within the document to specify the permissions for specific user accounts.  I am used to Java and C programming syntax so that is why I chose to represent it as such.

Comments in the smb.conf file can be either # or ;  If you have that style comment in the smb.conf file you should change them.  I'm not sure what the other thought you have really means.  Are you saying that you have configured shares for each of your users based on there user name and that the user names are their First Name and Last Name (i.e user name = Joe Doaks).  If so, why?  That sure is the hard way of doing that.
> 

I modified the share definitions only: read only, create mask, and directory mask.  Are they correct in octal value for what I'm trying to achieve and should I modify anything else?

If I can't see the share then I can't comment.  I don't need to see the real [share name] or path so user place markers.
> 

When I performed the lsb_release -a command I got this:

[FONT=Verdana]lsb_release -a
No LSB modules are available.
Distributor ID: Ubuntu
Description:  Ubuntu 14.04 LTS[/FONT]
[FONT=Verdana]Release:  14.04[/FONT]
[FONT=Verdana]Codename: trusty
[/FONT]
and Samba is:
#smbstatus
Samba version 4.1.6

I am using samba through a GUI, is there a big difference between terminal and GUI for samba operation and setup?

Yes there can be.  I don't understand how your version of Ubuntu could have a default umask different for all the other Ubuntu installations without someone changing it.  The default umask is 0002.  I just checked a default install that is hours old and it is as stated: 0002.  The rule of thumb is the umask is always the last umask stated.  Any script can declare a different umask and GUI interfaces can change the umask.  One last thought:  The umask for root is different than that for mortal users (humans).  Root's umask is 0022 while it is 0002 for mortal users.  I'm not sure what the setting is for system users.  Are you checking all of this as the root user?

There are quite a few places you can change it if needed.  The traditional system side location is /etc/profile.  The file now lists this```
# The default umask is now handled by pam_umask.
# See pam_umask(8) and /etc/login.defs.

```... what is different from all of the Ubuntu 14.04 hosts that I have seen?  I wouldn't have a clue.  You will just have to dig some.
> 

Each account is password protected so only certain people have access to it.  Those same accounts are not visible.  Is there any settings within my smb.conf file that could be conflicting with what I'm trying to do?

Thanks again for you help!
It definitely sounds like you are going about this the hard way.  I'll ask again.  Are you attempting to make private directories for each of your mortal users?

FYI -- my scheme for users is this.  Their human name is just that (Joe Doaks).  Their user name is: local (to the host) users = first name (joe) or domain wide users = first initial and last name (jdoaks).  I can look at a log and tell whether I'm dealing with a local or domain user problem.  In a domain situation, local users are also sudoers so they administrate the systems on the domain.  Most of the time this local user is only for failsafe use.

---

### Post by josh97 on 2014-10-07
```

```Hello,

Yes, the person who setup the server created everyone's usernames to be their full name.

Here's the code for each user with their 'adjusted' usernames:
```
[FONT=Arial][joshb][/FONT][FONT=Arial]
    comment = Josh B
    path = /srv/samba/joshb
    writeable = yes
    browseable = no
    valid users = administrator,heatherb, jeremyb, joshb,, rdevelopment

[joshc]
    comment = Josh C
    path = /srv/samba/joshc
    writeable = yes
    browseable = no
    guest ok = yes

[heatherb]
    comment = Heather B
    path = /srv/samba/heatherb
    writeable = yes
    browseable = no
    valid users = administrator,heatherb, jeremyb

[jeremyb]
    comment = Jeremy B
    path = /srv/samba/jeremyb
    writeable = yes
    browseable = no
    valid users = heatherb,jeremyb

[management]
    comment = Management
    path = /srv/samba/management
    writeable = yes
    browseable = no
    valid users = heatherb,jeremyb, joshc, management

[production]
    comment = Production
    path = /srv/samba/production
    writeable = yes
;    browseable = yes
    guest ok = yes

[research_development]
    comment = Research &Develpment
    path =/media/administrator/f4249b3d-a69f-40fd-89d0-2126df9495ec/research_development
    writeable = yes
    browseable = no
    valid users = heatherb,jeremyb, joshb, joshc, rdevelopment

[shipping]
    comment = Shipping
    path = /srv/samba/shipping
    writeable = yes
;    browseable = yes
    guest ok = yes

[software]
    comment = Software
    path = /media/administrator/f4249b3d-a69f-40fd-89d0-2126df9495ec/software
    writeable = yes
    browseable = no
    valid users = administrator,heatherb, jeremyb, joshb, joshc, software[/FONT]
```

I am logged in as root when checking all these settings.  I apologize, I didn't know that would skew the results.

The private directories were already made prior to my involvement though I am wondering if it would be easier to reformat the partition and start over.  I have backups of all the data currently residing on that partition.  Otherwise I could remove the current users, implement a simpler system, and apply it within samba shares.  Either way it sounds like this was initially done improperly and I'd like to know it's going to be easily expandable when our company hires more people.  I don't mind taking the time right now to get this correct.  Do you have any opinion on the best route to take?

Are there any walkthroughs for setting up ubuntu with samba that would prove beneficial with either route?

In doing this I'm gaining a little bit of experience with ubuntu and so far I'm enjoying it.  I don't mind expanding into other OS's than windows I just haven't done much of it and I appreciate your patience with me.

---

### Post by josh97 on 2014-10-07
I just realized that the user accounts section of the smb.conf file needed to have the create mask and all included where it originally wasn't so now it looks like this:

```
[COLOR=#000000][FONT=Arial][joshb][/FONT][/COLOR][FONT=Arial]    comment = Josh B
    path = /srv/samba/joshb
    writeable = yes
    browseable = no
    create mask = 775
    directory mask = 775
    force user = joshb
    force group = companygroup
    valid users = administrator,heatherb, jeremyb, joshb,, rdevelopment

[joshc]
    comment = Josh C
    path = /srv/samba/joshc
    writeable = yes
    browseable = no
    guest ok = yes

[heatherb]
    comment = Heather B
    path = /srv/samba/heatherb
    writeable = yes
    browseable = no
    create mask = 775
    directory mask = 775
    force user = heatherb
    force group = companygroup
    valid users = administrator,heatherb, jeremyb

[jeremyb]
    comment = Jeremy B
    path = /srv/samba/jeremyb
    writeable = yes
    browseable = no
    create mask = 775
    directory mask = 775
    force user = jeremyb
    force group = companygroup
    valid users = heatherb,jeremyb

[management]
    comment = Management
    path = /srv/samba/management
    writeable = yes
    browseable = no
    create mask = 775
    directory mask = 775
    force user = management
    force group = companygroup
    valid users = heatherb,jeremyb, joshc, management

[production]
    comment = Production
    path = /srv/samba/production
    writeable = yes
;    browseable = yes
    guest ok = yes

[research_development]
    comment = Research &Develpment
    path =/media/administrator/f4249b3d-a69f-40fd-89d0-2126df9495ec/research_development
    writeable = yes
    browseable = no
    create mask = 775
    directory mask = 775
    force user = rdevelopment
    force group = companygroup
    valid users = heatherb,jeremyb, joshb, joshc, rdevelopment

[shipping]
    comment = Shipping
    path = /srv/samba/shipping
    writeable = yes
;    browseable = yes
    guest ok = yes

[software]
    comment = Software
    path = /media/administrator/f4249b3d-a69f-40fd-89d0-2126df9495ec/software
    writeable = yes
    browseable = no 
    create mask = 775
    directory mask = 775
    force user = software
    force group = companygroup[/FONT][COLOR=#000000][FONT=Arial]    valid users = administrator,heatherb, jeremyb, joshb, joshc, software[/FONT][/COLOR]
```


But now I cannot access any directory that requires a password and the directories I can access I cannot write two more than one folder deep.

---

### Post by bab1 on 2014-10-08
> **josh97 said:**
> Hello,

Yes, the person who setup the server created everyone's usernames to be their full name.

Here's the code for each user with their 'adjusted' usernames:
```

[joshb]
    comment = Josh B
    path = /srv/samba/joshb
    writeable = yes
    browseable = no
    valid users = administrator,heatherb, jeremyb, joshb,, rdevelopment

[joshc]
    comment = Josh C
    path = /srv/samba/joshc
    writeable = yes
    browseable = no
    guest ok = yes

[heatherb]
    comment = Heather B
    path = /srv/samba/heatherb
    writeable = yes
    browseable = no
    valid users = administrator,heatherb, jeremyb

[jeremyb]
    comment = Jeremy B
    path = /srv/samba/jeremyb
    writeable = yes
    browseable = no
    valid users = heatherb,jeremyb

[management]
    comment = Management
    path = /srv/samba/management
    writeable = yes
    browseable = no
    valid users = heatherb,jeremyb, joshc, management

[production]
    comment = Production
    path = /srv/samba/production
    writeable = yes
;    browseable = yes
    guest ok = yes

[research_development]
    comment = Research &Develpment
    path =/media/administrator/f4249b3d-a69f-40fd-89d0-2126df9495ec/research_development
    writeable = yes
    browseable = no
    valid users = heatherb,jeremyb, joshb, joshc, rdevelopment

[shipping]
    comment = Shipping
    path = /srv/samba/shipping
    writeable = yes
;    browseable = yes
    guest ok = yes

[software]
    comment = Software
    path = /media/administrator/f4249b3d-a69f-40fd-89d0-2126df9495ec/software
    writeable = yes
    browseable = no
    valid users = administrator,heatherb, jeremyb, joshb, joshc, software

```

Are you saying that the username is like this: joed (for Joe Doaks).  To me the full name is: "First Last".  On a Linux machine the username should not have any spaces in it. 
> 

I am logged in as root when checking all these settings. I apologize, I didn't know that would skew the results.

Yes indeed.  you should always test "as the user" and configure with root powers.
> 
The private directories were already made prior to my involvement though I am wondering if it would be easier to reformat the partition and start over. I have backups of all the data currently residing on that partition. Otherwise I could remove the current users, implement a simpler system, and apply it within samba shares. Either way it sounds like this was initially done improperly and I'd like to know it's going to be easily expandable when our company hires more people. I don't mind taking the time right now to get this correct. Do you have any opinion on the best route to take?

There is no reason to delete any directories or reformat the partition.  There is no reason to re-install Samba either.  The users have specific UID/GID numbering.  This numbering is more important than the names per se.  I don't need  to see the exact user names but I do need to understand the username formant (jdoaks or joed or ???) for a user who's first and last name is Joe Doaks.

I can help you set this up once it is clear in my mind.  To provide specific commands I need to know the specific parameters.
> 

Are there any walkthroughs for setting up ubuntu with samba that would prove beneficial with either route?
None that deal specifically with what we need to do.  Some of this Linux infrastructure and some is Samba configuration. > 
In doing this I'm gaining a little bit of experience with ubuntu and so far I'm enjoying it. I don't mind expanding into other OS's than windows I just haven't done much of it and I appreciate your patience with me. I just realized that the user accounts section of the smb.conf file needed to have the create mask and all included where it originally wasn't so now it looks like this:

```
[COLOR=#000000][FONT=Arial][joshb][/FONT][/COLOR][FONT=Arial]    comment = Josh B
    path = /srv/samba/joshb
    writeable = yes
    browseable = no
    create mask = 775
    directory mask = 775
    force user = joshb
    force group = companygroup
    valid users = administrator,heatherb, jeremyb, joshb,, rdevelopment

[joshc]
    comment = Josh C
    path = /srv/samba/joshc
    writeable = yes
    browseable = no
    guest ok = yes

[heatherb]
    comment = Heather B
    path = /srv/samba/heatherb
    writeable = yes
    browseable = no
    create mask = 775
    directory mask = 775
    force user = heatherb
    force group = companygroup
    valid users = administrator,heatherb, jeremyb

[jeremyb]
    comment = Jeremy B
    path = /srv/samba/jeremyb
    writeable = yes
    browseable = no
    create mask = 775
    directory mask = 775
    force user = jeremyb
    force group = companygroup
    valid users = heatherb,jeremyb

[management]
    comment = Management
    path = /srv/samba/management
    writeable = yes
    browseable = no
    create mask = 775
    directory mask = 775
    force user = management
    force group = companygroup
    valid users = heatherb,jeremyb, joshc, management

[production]
    comment = Production
    path = /srv/samba/production
    writeable = yes
;    browseable = yes
    guest ok = yes

[research_development]
    comment = Research &Develpment
    path =/media/administrator/f4249b3d-a69f-40fd-89d0-2126df9495ec/research_development
    writeable = yes
    browseable = no
    create mask = 775
    directory mask = 775
    force user = rdevelopment
    force group = companygroup
    valid users = heatherb,jeremyb, joshb, joshc, rdevelopment

[shipping]
    comment = Shipping
    path = /srv/samba/shipping
    writeable = yes
;    browseable = yes
    guest ok = yes

[software]
    comment = Software
    path = /media/administrator/f4249b3d-a69f-40fd-89d0-2126df9495ec/software
    writeable = yes
    browseable = no 
    create mask = 775
    directory mask = 775
    force user = software
    force group = companygroup[/FONT][COLOR=#000000][FONT=Arial]    valid users = administrator,heatherb, jeremyb, joshb, joshc, software[/FONT][/COLOR]
```


But now I cannot access any directory that requires a password and the directories I can access I cannot write two more than one folder deep.

This is most likely due to the lack of group user inheritance.  I see that some of the shares are external HDD directories.  Are the partitions formatted ext4 or NTFS?  NTFS can be a problem.  NTFS does not use the same user/groups or security model.

Post the output of this (obscure the names but not the format of them)```
getent passwd|grep ^100?| getent passwd|grep 100|tail -n4
```...this will show me a few of the user name formatting.

Post the output of this command```
sudo blkid -c /dev/null -o list
```...this will show the partitions and their file systems and mount point.

Post the output of these commands```
ls -l /srv/samba

ls -l /media
```...this will show me the permissions you have set on the file system tree that we are using.

With this information I will provide you with a strategy to simplify the user name scheme and the this system structure and Samba shares.  If you would prefer, you can PM me with this information.  I will post the reply here so that all can learn without referring to any of the information you provide specifically.

---

### Post by josh97 on 2014-10-08
I'll post the data you requested asap.  I wanted to let you know that the names are setup as "first Last" with no space between, ex: "johnsmith" for the user account then the samba directory name is set as the users last name, ex: "smith" and if there is more than one person with that last name then all people with that last name have their samba directory setup as "jsmith" with the first character of their first name then the whole last name.

---

### Post by josh97 on 2014-10-13
Hello,

This is what I got for [COLOR=#000000][FONT=Ubuntu Mono]getent passwd|grep ^100?| getent passwd|grep 100|tail -n4:
```
[/FONT][/COLOR]get[Ktent passwd |grep 100|[1P[C[C[C[C[C[C[C[C[C[Ctail.[K -n4shipping:x:1007:1007:Shipping,,,:/home/shipping:/bin/bash
production:x:1008:1008:Production,,,:/home/production:/bin/bash
rdevelopment:x:1009:1009:Research & Development,,,:/home/rdevelopment:/bin/bash
companyname:x:1012:1001::/home/companyname:[COLOR=#000000][FONT=Ubuntu Mono]
```


The code [/FONT][/COLOR][COLOR=#000000][FONT=Ubuntu Mono]sudo blkid -c /dev/null -o list got me:
```
[/FONT][/COLOR]]0;root@CompanyServer: ~root@CompanyServer:~# blkid -c /dev/m[Knull -o list



device                    fs_type    label       mount point                   UUID
-------------------------------------------------------------------------------------------------------------------
/dev/sda1                 linux_raid_member CompanyServer:2 (in use)              13660aa1-69ff-764c-3ac2-418981d958b8
/dev/sdb1                 linux_raid_member CompanyServer:2 (in use)              13660aa1-69ff-764c-3ac2-418981d958b8
/dev/sdc1                 linux_raid_member CompanyServer:0 (in use)              25c7926c-2254-b02e-2f1d-5536bb2b91f6
/dev/sdc2                 linux_raid_member CompanyServer:1 (in use)              499f293b-8022-e900-65a1-a23d6a13607e
/dev/sdd1                 linux_raid_member CompanyServer:0 (in use)              25c7926c-2254-b02e-2f1d-5536bb2b91f6
/dev/sdd2                 linux_raid_member CompanyServer:1 (in use)              499f293b-8022-e900-65a1-a23d6a13607e
/dev/sde1                 linux_raid_member CompanyServer:0 (in use)              25c7926c-2254-b02e-2f1d-5536bb2b91f6
/dev/sde2                 linux_raid_member CompanyServer:1 (in use)              499f293b-8022-e900-65a1-a23d6a13607e
/dev/md1                  ext4                   /                             c830a383-cbd6-408d-af26-d2430ee1d47b
/dev/md127                ext2                   (not mounted)                 f4249b3d-a69f-40fd-89d0-2126df9495ec

/dev/mapper/cryptswap1    swap                   <swap>                        fdece4ad-5328-46eb-b223-6a348ec3c79a[COLOR=#000000][FONT=Ubuntu Mono]
```

[/FONT][/COLOR][COLOR=#000000][FONT=Ubuntu Mono]

Then I did [/FONT][/COLOR][COLOR=#000000][FONT=Ubuntu Mono]ls -l /srv/samba and got:
[/FONT][/COLOR][COLOR=#000000][FONT=Ubuntu Mono]```
[/FONT][/COLOR]

]0;root@CompanyServer: ~root@CompanyServer:~# 
[K]0;root@CompanyServer: ~root@CompanyServer:~# ls -l /srv/samba
total 32


drwsrwsr-x+ 18 joshuab company 4096 Oct  8 16:09 [0m[01;34mjoshb[0m
drwxrwsr-x   2 joshuac     company 4096 Oct  2 10:18 [01;34mjoshc[0m
drwxrwsr-x   3 heather   company 4096 Apr  6  2014 [01;34mheatherb[0m
drwxrwsr-x   2 jeremyb    company 4096 Apr  5  2014 [01;34mjeremyb[0m
drwxrwsr-x   4 management        company 4096 Apr 30 15:29 [01;34mmanagement[0m
drwxrwsr-x  19 production        company 4096 Oct  9 14:39 [01;34mproduction[0m
drwxrwsr-x   3 shipping          company 4096 Oct 10 08:49 [01;34mshipping[0m[COLOR=#000000][FONT=Ubuntu Mono]
```

[/FONT][/COLOR][COLOR=#000000][FONT=Ubuntu Mono]and lastly I did [/FONT][/COLOR][COLOR=#000000][FONT=Ubuntu Mono]ls -l /media and it's output was:
```
[/FONT][/COLOR]

drwxrwxrwx+ 2 root          root          4096 Oct  8 16:34 [0m[34;42madministrator[0m
drwx------  2 administrator administrator 4096 Apr 30 12:01 [01;34mf4249b3d-a69f-40fd-89d0-2126df9495ec[0m
drwxr-x---+ 2 root          root          4096 Oct  8 16:28 [01;34mjoshuab[0m
drwxr-xr-x  2 root          root          4096 Apr 30 11:55 [01;34mmds127[0m[COLOR=#000000][FONT=Ubuntu Mono]
```[/FONT][/COLOR][COLOR=#000000][FONT=Ubuntu Mono]
[/FONT][/COLOR][COLOR=#000000][FONT=Ubuntu Mono]

The usernames were modified so you cannot see the last name but the full last names are part of the usernames.  I hope this helps!  Thanks again!
[/FONT][/COLOR][COLOR=#000000][FONT=Ubuntu Mono]

[/FONT][/COLOR][COLOR=#000000][FONT=Ubuntu Mono]
[/FONT][/COLOR][COLOR=#000000][FONT=Ubuntu Mono]
[/FONT][/COLOR]

---

