---
title: "How to share files using Samba (the more secure way)"
date: 2005-04-12
forum: Outdated Tutorials &amp; Tips
---

### Post by vnbuddy2002 on 2005-04-12
Required tools:

- samba
- samba-common

To install:  sudo apt-get install samba

Once the server is install, issue the following command:

```
sudo gedit /etc/samba/smb.conf
```

Make the following changes:

  ```
 workgroup = WORKGROUP
```

underneath it, add
  
   netbios name = name_of_your_server (no spaces)

For example:

   ```
netbios name = kenny_smb_server 
```

Make sure "security" is set to "user".

Scroll down until you see "[homes]", set:
```

browseable = yes
writable = yes
```

Then save the changes.


Finally, create a SMB user, make sure this account exists on your Ubuntu Linux.

```
sudo smbpasswd -a `whoami`
```

and set your password

OKAY, you are finished configuring Samba on your Ubuntu Linux.

------------------------------------------------------------------------------------------------
Winblowz
------------------------------------------------------------------------------------------------

There are two ways to access it:

Method 1:
My network places > Entire Network > My Windows Network > Workgroup

Method 2:
in the address barm type in "\\[whatever you named the Samba server]". From my example above, I used "\\kenny_smb_server\".


You should see a folder call "homes", click on it, and it will ask you for your username and password, enter your Ubuntu Login Name and whatever you choose for the password when you used command "smbpasswd". You should be able to take it from here.

Keep in mind that you are sharing,   /home/[login name]/*

------------------------------------------------------------------------------------------------
Linux
------------------------------------------------------------------------------------------------

Install smbfs:

```
sudo apt-get install smbfs
mkdir Network
sudo mount -t smbfs -o username=[network user],password=[network pass],uid=`whoami`,gid=`whoami`,fmask=000,dmask=000  //[whatever you named the Samba server]/[network user] /home/`whoami`/Network

```

Example:
```
sudo mount -t smbfs -o username=kenny,password=test,uid=`whoami`,gid=`whoami`,fmask=000,dmask=000  //kenny_smb_server/kenny /home/`whoami`/Network
```

---- END

 ;-) Good luck!

---

### Post by crun on 2005-04-17
thanks vnbuddy, I've been trying to get Samba to let my Windows brethern see my shared dirs for some time, but failed up until now. This worked perfectly.

---

### Post by DoubleDangerClub on 2005-04-17
How do I delete an smb user?

DDC

---

### Post by mgor on 2005-04-17
```
$ smbpasswd -h | grep delete
  -x                   delete user
```

```
smbpasswd -x myuser
```

does the trick :)

---

### Post by DoubleDangerClub on 2005-04-17
Thanks mgor!  I was also wondering if it's usual to open up the share on windows and have 2 directories?  I have one called "homes" and one called "jake" (my username).  But they both aim at my jake directory, is this set up right?

DDC

---

### Post by mgor on 2005-04-17
hm, check to se if you've got double entries for your homedir in /etc/samba/smb.conf under the section "Share Definitions".

---

### Post by DoubleDangerClub on 2005-04-17
I don't even see where the homedir is set in my conf file.

Here's my smb.conf file.  Also, is there somewhere else that it lists what directories have access?  In other words, somewhere it lists my homes dir and my jake dir?

```
#
# Sample configuration file for the Samba suite for Debian GNU/Linux.
#`
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
# "testparm" to check that you have not many any basic syntactic 
# errors. 
#

#======================= Global Settings =======================

[global]

## Browsing/Identification ###

# Change this to the workgroup/NT-domain name your Samba server will part of
   workgroup = MSHOME
   netbios name = Ubuntu_Share

# server string is the equivalent of the NT Description field
   server string = %h server

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
# /usr/share/doc/samba-doc/htmldocs/ServerType.html in the samba-doc
# package for details.
;   security = user

# You may wish to use password encryption.  See the section on
# 'encrypt passwords' in the smb.conf(5) manpage before enabling.
   encrypt passwords = true

# If you are using encrypted passwords, Samba will need to know what
# password database type you are using.  
   passdb backend = tdbsam guest

   obey pam restrictions = yes

;   guest account = nobody
   invalid users = root

# This boolean parameter controls whether Samba attempts to sync the Unix
# password with the SMB password when the encrypted SMB password in the
# passdb is changed.
;   unix password sync = no

# For Unix password sync to work on a Debian GNU/Linux system, the following
# parameters must be set (thanks to Augustin Luton <aluton@hybrigenics.fr> for
# sending the correct chat script for the passwd program in Debian Potato).
   passwd program = /usr/bin/passwd %u
   passwd chat = *Enter\snew\sUNIX\spassword:* %n\n *Retype\snew\sUNIX\spassword:* %n\n .

# This boolean controls whether PAM will be used for password changes
# when requested by an SMB client instead of the program listed in
# 'passwd program'. The default is 'no'.
;   pam password change = no


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
;   printer admin = @ntadmin


######## File sharing ########

# Name mangling options
;   preserve case = yes
;   short preserve case = yes


############ Misc ############

# Using the following line enables you to customise your configuration
# on a per machine basis. The %m gets replaced with the netbios name
# of the machine that is connecting
;   include = /home/samba/etc/smb.conf.%m

# Most people will find that this option gives better performance.
# See smb.conf(5) and /usr/share/doc/samba-doc/htmldocs/speed.html
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

#======================= Share Definitions =======================

[homes]
   comment = Home Directories
   browseable = yes

# By default, the home directories are exported read-only. Change next
# parameter to 'yes' if you want to be able to write to them.
   writable = yes

# File creation mask is set to 0700 for security reasons. If you want to
# create files with group=rw permissions, set next parameter to 0775.
   create mask = 0700

# Directory creation mask is set to 0700 for security reasons. If you want to
# create dirs. with group=rw permissions, set next parameter to 0775.
   directory mask = 0700

# Un-comment the following and create the netlogon directory for Domain Logons
# (you need to configure Samba to act as a domain controller too.)
;[netlogon]
;   comment = Network Logon Service
;   path = /home/samba/netlogon
;   guest ok = yes
;   writable = no
;   share modes = no

[printers]
   comment = All Printers
   browseable = no
   path = /tmp
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
``` 

BTW, thanks for your help on this. :)

DDC

---

### Post by speedman on 2005-04-17
[QUOTE=DoubleDangerClub]I don't even see where the homedir is set in my conf file.[/QUOTE]

#======================= Share Definitions =======================

[homes]
   comment = Home Directories
   browseable = yes


Regards,

SM

---

### Post by mgor on 2005-04-17
not sure what or where the 'username' share is specified, but you could comment out the homes share in smb.conf.

---

### Post by riffic on 2005-04-17
[QUOTE=speedman]#======================= Share Definitions =======================

[homes]
   comment = Home Directories
   browseable = yes


Regards,

SM[/QUOTE]
looks like that section of default smb.conf is missing a "path =" statement.

just add a new line underneath browsable that states path = /home/<username>/ , and you should be good to go.

---

### Post by speedman on 2005-04-17
[QUOTE=riffic]looks like that section of default smb.conf is missing a "path =" statement.[/QUOTE]

Not quite.  :) 

For global home directory sharing no path statement is necessary.

> just add a new line underneath browsable that states path = /home/<username>/ , and you should be good to go.

No.  If the original poster does not like the share displays with all of the home directories being shared he/she can comment out everything under the [homes] section and add a new share just for their own home directory as such:

[jake]
    comment = jake's home directory
    path = /home/jake
    browsable = yes
    public = no
    read only = no
    valid users = jake


Regards,

SM


EDIT - fixed a typo

---

### Post by DoubleDangerClub on 2005-04-18
That really helped SM!  Thanks a ton for your help!

DDC

---

### Post by codejunkie on 2005-04-18
Thank you so much vnbuddy until now i had only been able to see my wifes winders box in ubuntu now i have full network support and again i thank you.

---

### Post by fire59 on 2005-04-18
Currently I have smb setup on my laptop and server.  This is what i use to mount it:
smbmount //intranet/web /mnt/server -o username=user,password=password
How do i add it to my fstab so it auto mount when i boot? I would also like it to mount the /mnt/server folder as none root.

---

### Post by speedman on 2005-04-18
[QUOTE=fire59]How do i add it to my fstab so it auto mount when i boot?[/QUOTE]

//intranet/web /mnt/server smbfs username=your_username,password=your_password,uid=your_uid,gid=your_gid,users 0 0

OR

//intranet/web /mnt/server smbfs credentials=/root/.smbcredentials,user 0 0

Where the contents of /root/.smbcredentials looks like this:

username = your_username
password = your_password


Regards,

SM

---

### Post by Ozitraveller on 2005-04-18
I now have my network working, and printing as well. Now I would like to install firestarter, the last time I did this it killed the network. It must have blocked a port that samba uses I suspect.

What do I need to set so that the network still works after I install firestarter?


Any help would be greatly appreciated!

---

### Post by Ozitraveller on 2005-04-19
Now I remember asking this question before. :roll: 

This might help someone...

It has the ports for Samba.


Samba Help
[http://ubuntuforums.org/showthread.php?p=91201#post91201](http://ubuntuforums.org/showthread.php?p=91201#post91201)

---

### Post by themoddingden on 2005-05-13
Hi;
I'm useing Kununtu.
Now when I go to Control panel networking then samba it opens the window that lets you see all the tabs to configure it but when I hit the admi mode button it just kicks me out to the comtrol panel .
How do I get access to samba to set it up I had it on a prior install set up ok with my network name etc but wanted to dual boot plus had problems with the install after a system hang then hard reset(kde was messed up along with all desktop features were bjorked) .
My pw is right cause I can get synaptic running etc that needs pw so what else could it be ???

---

### Post by wiljam on 2005-05-14
Because the thread was about file sharing _the most secure way_ I thought to give my share to it. Here's some parts of my smb.conf. feel free to try them.

[global]
   smb ports =  445
   interfaces = 192.168.1.2/24 127.0.0.1/24
   bind interfaces only = yes   
   workgroup = workgroup
; This option is important for security. It allows you to restrict
; connections to machines which are on your local network. The
; following example restricts access to two C class networks and
; the "loopback" interface. For more examples of the syntax see
: the smb.conf man page
   hosts allow = 127. 192.168.1.
   hosts deny = *
   passdb backend = smbpasswd
; Most people will find that this option gives better performance.
; See speed.txt and the manual pages for details
; You may want to add the following on a Linux system:
   socket options = IPTOS_LOWDELAY TCP_NODELAY SO_RCVBUF=8192 SO_SNDBUF=8192
; Cause this host to announce itself to local subnets here
   remote announce = 192.168.1.255

and the shares

[files]
  comment = files
  path = /var/files/
  valid users = wiljam,melina,rami
  public = yes
  writable = yes
  printable = no
  create mode = 0644
  create mask = 0644
  directory mask = 0744

---

### Post by themoddingden on 2005-05-17
Hi;
Anyone now why it will not let me edit my samba config via kontrol panel anymore did it the first time I can't change Workgroup name etc .
See my other post.
I click the admin tab put in pw and I go back to control panel screen.
Do  I need to do it via konsole?? If so how can i??

---

### Post by Eazy© on 2005-06-10
[QUOTE=themoddingden]Hi;
Anyone now why it will not let me edit my samba config via kontrol panel anymore did it the first time I can't change Workgroup name etc .
See my other post.
I click the admin tab put in pw and I go back to control panel screen.
Do  I need to do it via konsole?? If so how can i??[/QUOTE]

in a console: sudo kcontrol

edit: sorry, didnt see that is was an old thread, but perhaps it can be usefull info for someone else :)

this was my first post so maybe I'm excused ;)

---

### Post by Iuliux on 2005-06-11
I have followed thesteps shown in this post...I manage to install and start samba 
> iuliux@kubuntu:~$ ps ax |grep bd
 4214 ?        S      0:00 [khubd]
 6381 ?        Ss     0:00 /usr/sbin/nmbd -D
 6383 ?        Ss     0:00 /usr/sbin/smbd -D
 6404 ?        S      0:00 /usr/sbin/smbd -D
19463 ?        S      0:00 /usr/sbin/smbd -D
20960 pts/1    S+     0:00 grep bd
iuliux@kubuntu:~$   
but my problem is that I see only another compiuter on my network...and there should be at least 10

---

### Post by Iuliux on 2005-06-16
can someone (who got the samba up and running), post his smb.conf file here
???

---

### Post by manicka on 2005-06-19
I just want to say another thankyou to vnbuddy for the HowTo. Before coming to Ubuntu I never had much success with samba in SuSE. This was so easy and works faultlessly.

---

### Post by spockrock on 2005-06-19
thank you your guide works perfectly

---

### Post by Artanis on 2005-06-22
Good howto, had so much trouble with samba in the past that I gave up and I just used FTP to/from my windows box's, which made it a pain in the ass when I took my laptop (running gentoo) to school as no one else had a decent FTP client installed on their system.

---

### Post by wiseNoob on 2005-07-14
I know I must have missed this somewhere... I got samba working with really no issue, but I would like to run it on startup.  I am a fedora core user mostly, and chkconfig doesn't seem to work... :roll:

I am trying to teach myself to NOT use the gui, so I am looking for a command line command.

---

### Post by xbaez on 2005-08-01
I configured samba successfully
from what I understand, the USER security option means that everybody that wants to connect to this samba server needs a user and a pass right?
here are a few things about my smb.conf file

[global]
restrict anonymous = no
security = user
username map = /etc/samba/smbusers
encrypt passwords = yes
passdb backend = smbpasswd
guest account = nobody
invalid users = root

socket options = SO_KEEPALIVE TCP_NODELAY IPTOS_LOWDELAY SO_SNDBUF=8192 SO_RCVBUF=8192 

domain master = yes
max protocol = NT
ldap ssl = No
server signing = Auto
os level = 21
map to guest = Bad User
guest ok = yes



By checking at the logs, using a Linux (Suse 8.2) client, I was able to access my samba server (using Konqueror, smb://MYSERVER)

However, when I tried to access certain folders (restricted users), it asked me for a user and a password
when I entered them, I had full access

here is the log:

[B][2005/08/01 13:37:33, 1] smbd/service.c:make_connection_snum(642)
suse_linux connect to service SERVER_downloads initially as user nobody
[2005/08/01 13:40:55, 1] smbd/service.c:make_connection_snum(642)
suse_linux connect to service SERVER_sensitive_data initially as user server_master[/B]


Ok, so everything works ok
BUT, when I try to access from a Window$ machine, I get this


[B][2005/08/01 13:44:18, 1] smbd/service.c:make_connection_snum(642)
machine-01 signed connect to service SERVER_Downloads initially as user machine-01[/B]


This is the main problem.
I have a user named
machine-01, with pass machine-01

When I connect from it, I am able to see everything, and I only have access to what I should have
BUT
when I try to connect to 
SERVER_sensitive_data it prompts me for a user and password 
I enter my user and password, and I just get denied

The strange this is that it works on Linux

any help will be appreciated.

The main problem is
[B]using a linux client, I am able to browse my Samba server as nobody (guest), and then I type my user and pass when I need to access a sensitive data folder

In Window$, the system doesn't lets me browse my Samba server, unless I enter the user and password (machine-01, a user with read-only permission)

Then, I want to browse the sensitive data folder, it prompts me for a user and password, and then I get denied[/B]

---

### Post by xbaez on 2005-08-01
ok I found that by placing
[global]
guest ok = yes

The Window$ client loads all of my shared

However, when I try to load to the Sensitive_folder, I get this error in the logs:

[2005/08/01 14:18:34, 1] smbd/service.c:make_connection_snum(642)
machine-01 connect to service Server_Downloads initially as user nobody (uid=65534, gid=65534) (pid 4292)
[2005/08/01 14:18:37, 0] smbd/service.c:make_connection_snum(577)
 Can't become connected user! ( I was trying to become server_master)

Any ideas?

I am using the smbpasswd, I will now try with the deault options

The curious thing is that, if I enter from a machine that has
server-master  as the windows login (same password as the server-master has here in smbpasswd), I am able to see all the sensitive-data folders

And from the linux client, I am able to browse my shares as Guest, and when I try to load the sensitive data, it prompts me for a user and a password.

I type server-master and it's pass, and it works great

---

### Post by xbaez on 2005-08-01
I just tried with the deaults options

[global]
security = user
username map = /etc/samba/smbusers
encrypt passwords = yes
passdb backend = tdbsam guest
guest account = nobody
invalid users = root
passwd program = /usr/bin/passwd %u
passwd chat = *Enter\snew\sUNIX\spassword:* %n\n *Retype\snew\sUNIX\spassword:* %n\n .

Well now with the Window$ clients, I am able to see all my shares
BUT when I try to load a sensitive_folder share, it prompts me for a user and password

It just doesn't works

**Can't become connected user!**

I'd appreciate any suggestions

---

### Post by Boomerang on 2005-08-02
[QUOTE=xbaez]
Well now with the Window$ clients, I am able to see all my shares
BUT when I try to load a sensitive_folder share, it prompts me for a user and password

It just doesn't works

**Can't become connected user!**

I'd appreciate any suggestions[/QUOTE]

I've had the same problem. Try adding protocol = LANMAN2 to the global configuration section:

```

[global]
protocol = LANMAN2

```

It did the trick for me!

---

### Post by xbaez on 2005-08-02
ok I'll give it a try now, I really hope this works as I've been trying to have a Samba server for a lot of time now

(later...)
Installing Samba it's one of those things I've always wanted to do but since it's not in your top priorities you don't do it right away

I will like to know if you can tell me a page were I can read a basic intro about Samba (including the protocol = LANMAN2 thing you just mentioned here), since I didn't had a clue about what was wrong with my server.

I tested your protocol, and WOW, it works perfectly. Now I really have a "Window$ NT 4.x" server in my linux box

I really, really thing there are some things people just love. Your favorite soccer team, your career, your job... and of course, your favorite distro: Ubuntu  :grin: 

I've never had this amazing support anywere else

---

### Post by toadhall on 2005-08-02
I have Samba installed and visible from my XP box and viewable through OS X, but I cannot mount the file system.  I keep getting this error when I try to mount the smbfs:

5975: tree connect failed: ERRDOS - ERRnosuchshare (You specified an invalid share name).   
:confused: 

I have double checked all the directory trees, and they look correct.  I have users built in Samba and Linux, and I am able to get as far as the actual share file folders before the access fails from both Windows and OS X.  Samba is working fine the other way.

Any help?  I know this is an old thread but hopefully not abandoned.  

Thanks,
TH

---

### Post by xbaez on 2005-08-05
So from Window$ you go to 'My Network places', then see your WORKGROUP, then try to access  your SERVER's Shares, and you have problems?

$grep log /etc/samba/smb.conf

# This tells Samba to use a separate log file for each machine
**log file = /var/log/samba/log.%m**


Make sure to do that
in my server, I'll do this to check for problems:
(/var/log/samba/log.192.168.0.x(it can also be their bios name, like /var/log/samba/computer01)

**# tail -f /var/log/samba/log.192.168.0.x**

Try that and tell me the errors

---

### Post by toadhall on 2005-08-08
Thanks for the help Xavier... I got Samba working through downloading the GUI interface in the Ubuntu downloads... and several missing libs from the Samba suite.

From the download dialogue, I noticed that I was missing a couple of elements in the original Samba set-up.  I can't remember the name of the exact lib that I was missing in the installation.  I am still learning dependencies, and I might have skipped a lib that I didn't think was necessary.  The machine I am using only has a 6GB drive, and I am trying to conserve space.

I did set up the log files to dump from each machine trying to connect in.  Unfortunately, I already fixed the problem before your post... otherwise I would have more info for you, and could have been some help on this board.   :roll:

---

### Post by xbaez on 2005-08-09
Hey Boomerang now I have this problem:

[2005/08/09 15:14:28, 0] smbd/service.c:make_connection_snum(615)
  '/tmp' does not exist or is not a directory, when connecting to [IPC$]
[2005/08/09 15:14:28, 3] smbd/sec_ctx.c:set_sec_ctx(288)
  setting sec ctx (0, 0) - sec_ctx_stack_ndx = 0
[2005/08/09 15:14:28, 3] smbd/connection.c:yield_connection(69)
  Yielding connection to IPC$
[2005/08/09 15:14:28, 3] smbd/error.c:error_packet(105)
  error string = Permission denied
[2005/08/09 15:14:28, 3] smbd/error.c:error_packet(145)
  error packet at smbd/reply.c(415) cmd=117 (SMBtconX) eclass=1 ecode=67
[2005/08/09 15:14:28, 3] smbd/process.c:timeout_processing(1334)
  timeout_processing: End of file from client (client has disconnected).

I installed various programs with apt-get, now I boot my computer, and Samba just doesn't works anymore

I swear it's the excact smb.conf file I had working. When I have a daemon such as this working, I back it up. I'm using that file, newly created files... it just doesn't works

And if I don't put the 
protocol = LANMAN2
treak, I get an Invalid error
tree connect failed: NT_STATUS_BAD_NETWORK_NAME

Somebody please help me

I'd appreciate some help

---

### Post by xbaez on 2005-08-09
[QUOTE=xbaez]Hey Boomerang now I have this problem:

[2005/08/09 15:14:28, 0] smbd/service.c:make_connection_snum(615)
  '/tmp' does not exist or is not a directory, when connecting to [IPC$]
[2005/08/09 15:14:28, 3] smbd/sec_ctx.c:set_sec_ctx(288)
  setting sec ctx (0, 0) - sec_ctx_stack_ndx = 0
[2005/08/09 15:14:28, 3] smbd/connection.c:yield_connection(69)
  Yielding connection to IPC$
[2005/08/09 15:14:28, 3] smbd/error.c:error_packet(105)
  error string = Permission denied
[2005/08/09 15:14:28, 3] smbd/error.c:error_packet(145)
  error packet at smbd/reply.c(415) cmd=117 (SMBtconX) eclass=1 ecode=67
[2005/08/09 15:14:28, 3] smbd/process.c:timeout_processing(1334)
  timeout_processing: End of file from client (client has disconnected).

I installed various programs with apt-get, now I boot my computer, and Samba just doesn't works anymore

I swear it's the excact smb.conf file I had working. When I have a daemon such as this working, I back it up. I'm using that file, newly created files... it just doesn't works

And if I don't put the 
protocol = LANMAN2
treak, I get an Invalid error
tree connect failed: NT_STATUS_BAD_NETWORK_NAME

Somebody please help me

I'd appreciate some help[/QUOTE]
 **"tree connect failed: ERRDOS - ERRnosuchshare (You specified an invalid share name)" + Ubuntu**

I don't know what package I installed, but Samba has stopped working

I know the shares are right, samba is just not working

mount.smbfs is not working neither, it stays trying to connect to the samba share for hours.

Can anybody please help me?

---

### Post by Mastodront on 2005-08-14
> #
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
# "testparm" to check that you have not many any basic syntactic 
# errors. 
#

#======================= Global Settings =======================

[global]

## Browsing/Identification ###

# Change this to the workgroup/NT-domain name your Samba server will part of
   workgroup = WORKGROUP
   netbios name = mange_smb_server

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
# /usr/share/doc/samba-doc/htmldocs/ServerType.html in the samba-doc
# package for details.
;   security = user

# You may wish to use password encryption.  See the section on
# 'encrypt passwords' in the smb.conf(5) manpage before enabling.
   encrypt passwords = true

# If you are using encrypted passwords, Samba will need to know what
# password database type you are using.  
   passdb backend = tdbsam guest

   obey pam restrictions = yes

;   guest account = nobody
   invalid users = root

# This boolean parameter controls whether Samba attempts to sync the Unix
# password with the SMB password when the encrypted SMB password in the
# passdb is changed.
;   unix password sync = no

# For Unix password sync to work on a Debian GNU/Linux system, the following
# parameters must be set (thanks to Augustin Luton <aluton@hybrigenics.fr> for
# sending the correct chat script for the passwd program in Debian Potato).
   passwd program = /usr/bin/passwd %u
   passwd chat = *Enter\snew\sUNIX\spassword:* %n\n *Retype\snew\sUNIX\spassword:* %n\n .

# This boolean controls whether PAM will be used for password changes
# when requested by an SMB client instead of the program listed in
# 'passwd program'. The default is 'no'.
;   pam password change = no


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
;   printer admin = @ntadmin


######## File sharing ########

# Name mangling options
;   preserve case = yes
;   short preserve case = yes


############ Misc ############

# Using the following line enables you to customise your configuration
# on a per machine basis. The %m gets replaced with the netbios name
# of the machine that is connecting
;   include = /home/samba/etc/smb.conf.%m

# Most people will find that this option gives better performance.
# See smb.conf(5) and /usr/share/doc/samba-doc/htmldocs/speed.html
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

#======================= Share Definitions =======================

[homes]
   comment = Home Directories
   browseable = yes	

# By default, the home directories are exported read-only. Change next
# parameter to 'yes' if you want to be able to write to them.
   writable = yes

# File creation mask is set to 0700 for security reasons. If you want to
# create files with group=rw permissions, set next parameter to 0775.
   create mask = 0700

# Directory creation mask is set to 0700 for security reasons. If you want to
# create dirs. with group=rw permissions, set next parameter to 0775.
   directory mask = 0700

# Un-comment the following and create the netlogon directory for Domain Logons
# (you need to configure Samba to act as a domain controller too.)
;[netlogon]
;   comment = Network Logon Service
;   path = /home/samba/netlogon
;   guest ok = yes
;   writable = no
;   share modes = no

[printers]
   comment = All Printers
   browseable = no
   path = /tmp
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


Hmmm, doesn't work for me :(  I'm trying to share /home/share but my winxp computer won't find my Ubuntu system. I've opened the ports (137-139) in firestarter but that doesn't seem to do the trick. From my Ubuntu computer I can see the XP-system though :/

Any tips?

---

### Post by Slugger on 2005-08-14
[QUOTE=riffic]looks like that section of default smb.conf is missing a "path =" statement.

just add a new line underneath browsable that states path = /home/<username>/ , and you should be good to go.[/QUOTE]
 Thanks this is a lot of help thanks

---

### Post by Mastodront on 2005-08-14
> [2005/08/14 11:41:17, 0] libsmb/nmblib.c:send_udp(790)
  Packet send failed to 192.168.0.255(137) ERRNO=Operation not permitted
[2005/08/14 11:41:17, 0] nmbd/nmbd_packets.c:send_netbios_packet(163)
  send_netbios_packet: send_packet() to IP 192.168.0.255 port 137 failed
[2005/08/14 11:41:17, 0] nmbd/nmbd_namequery.c:query_name(237)
  query_name: Failed to send packet trying to query name WORKGROUP<1d>
[2005/08/14 11:42:19, 0] libsmb/nmblib.c:send_udp(790)
  Packet send failed to 192.168.0.255(138) ERRNO=Operation not permitted

<From /var/log/samba/log.nmdb>

Seems to be some kind of problem there :/

I have Allow SMB 137-139 for everyone enabled in Firestarters "Inbound traffic policy"...


Hmmm #2:  Odd, should it send packets to 192.168.0.255? The other computer in my network has 192.168.1.102 and the router has 192.168.1.254 :/

---

### Post by Mastodront on 2005-08-15
Am I really the only one who can't get the server to work? :(

Now I tried to comment the [homes]-part and added [mange]:

> #
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
# "testparm" to check that you have not many any basic syntactic 
# errors. 
#

#======================= Global Settings =======================

[global]

## Browsing/Identification ###

# Change this to the workgroup/NT-domain name your Samba server will part of
   workgroup = WORKGROUP
   netbios name = mange

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
# /usr/share/doc/samba-doc/htmldocs/ServerType.html in the samba-doc
# package for details.
;   security = user

# You may wish to use password encryption.  See the section on
# 'encrypt passwords' in the smb.conf(5) manpage before enabling.
   encrypt passwords = true

# If you are using encrypted passwords, Samba will need to know what
# password database type you are using.  
   passdb backend = tdbsam guest

   obey pam restrictions = yes

;   guest account = nobody
   invalid users = root

# This boolean parameter controls whether Samba attempts to sync the Unix
# password with the SMB password when the encrypted SMB password in the
# passdb is changed.
;   unix password sync = no

# For Unix password sync to work on a Debian GNU/Linux system, the following
# parameters must be set (thanks to Augustin Luton <aluton@hybrigenics.fr> for
# sending the correct chat script for the passwd program in Debian Potato).
   passwd program = /usr/bin/passwd %u
   passwd chat = *Enter\snew\sUNIX\spassword:* %n\n *Retype\snew\sUNIX\spassword:* %n\n .

# This boolean controls whether PAM will be used for password changes
# when requested by an SMB client instead of the program listed in
# 'passwd program'. The default is 'no'.
;   pam password change = no


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
;   printer admin = @ntadmin


######## File sharing ########

# Name mangling options
;   preserve case = yes
;   short preserve case = yes


############ Misc ############

# Using the following line enables you to customise your configuration
# on a per machine basis. The %m gets replaced with the netbios name
# of the machine that is connecting
;   include = /home/samba/etc/smb.conf.%m

# Most people will find that this option gives better performance.
# See smb.conf(5) and /usr/share/doc/samba-doc/htmldocs/speed.html
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

#======================= Share Definitions =======================

#[homes]
#   comment = Home Directories
#   browseable = yes
   	

# By default, the home directories are exported read-only. Change next
# parameter to 'yes' if you want to be able to write to them.
#   writable = yes

# File creation mask is set to 0700 for security reasons. If you want to
# create files with group=rw permissions, set next parameter to 0775.
#   create mask = 0700

# Directory creation mask is set to 0700 for security reasons. If you want to
# create dirs. with group=rw permissions, set next parameter to 0775.
#   directory mask = 0700

# Un-comment the following and create the netlogon directory for Domain Logons
# (you need to configure Samba to act as a domain controller too.)

##Egen
[mange]
comment = Manges share
path = /home/share
browsable = yes
public = no
read only = no
valid users = share


;[netlogon]
;   comment = Network Logon Service
;   path = /home/samba/netlogon
;   guest ok = yes
;   writable = no
;   share modes = no

[printers]
   comment = All Printers
   browseable = no
   path = /tmp
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

And now I can see the computer from my winxp-computer but I don't have the rights to browse it :(

This is my log.nmdb...





> [2005/08/15 21:34:55, 0] libsmb/nmblib.c:send_udp(790)
  Packet send failed to 192.168.0.255(137) ERRNO=Operationen inte tillåten
[2005/08/15 21:34:55, 0] nmbd/nmbd_packets.c:send_netbios_packet(163)
  send_netbios_packet: send_packet() to IP 192.168.0.255 port 137 failed
[2005/08/15 21:34:55, 0] nmbd/nmbd_namequery.c:query_name(237)
  query_name: Failed to send packet trying to query name WORKGROUP<1d>
[2005/08/15 21:39:55, 0] libsmb/nmblib.c:send_udp(790)
  Packet send failed to 192.168.0.255(137) ERRNO=Operationen inte tillåten
[2005/08/15 21:39:55, 0] nmbd/nmbd_packets.c:send_netbios_packet(163)
  send_netbios_packet: send_packet() to IP 192.168.0.255 port 137 failed
[2005/08/15 21:39:55, 0] nmbd/nmbd_namequery.c:query_name(237)
  query_name: Failed to send packet trying to query name WORKGROUP<1d>
[2005/08/15 21:40:55, 0] libsmb/nmblib.c:send_udp(790)
  Packet send failed to 192.168.0.255(138) ERRNO=Operationen inte tillåten



Edit: And of course I've created the user "share" and I've "sudo smbpasswd -a share" and created the folder /home/share which I've given the ownership to the user "share"

---

### Post by nedbenj on 2005-10-02
Hi,

I have followed the excellent how-to in order to set up samba and I can see my linux box from my windows computer and vice-versa. I can also, for example, view a picture in windows that is stored on the linux box. However, I cannot do this the other way around - i.e. all of my windows files are visible, but not accessible. The icons appear with a padlock in the top lefthand corner. Can anyone explain why please?

Thanks.

---

### Post by Quirky on 2005-10-15
Problems I have had, with the solutions. All the problems were on the Windows side (Windows 98). The Samba server Just Worked.

The server smb_server was not recognised from the client. This is because the IP address is not mapped. Edit c:\windows\lmhosts and add <ip address> <server name>. This seems a bit of a hack. Requires fixed IPs and currently I have DHCP activated, so needs tweaking.

Needed to add 'Client For Microsoft Networks' to the Network panel (Start>Settings>Control Panel>Network) In this, I only have 'Quick Logon' enabled. In the Network 'Identification' panel, add the workgroup defined in the srever's smb.conf.

From a DOS promt, the message "Error 5:" may be shown when trying to mount a Windows drive with the command "net use F: //server/homes". The solution is to check that the Windows logged in user name is the same as the Ubuntu user name. This may be over rideable from the Network 'Access Control' panel, but I haven't found any docs on how to do it.

One more thing: I had forgotten the old chestnut change virtually anything in Windows and it requires a reboot! Ubuntu has spoiled me :)

---

### Post by higgins on 2005-11-04
I am trying to get samba working. I have used the following:

sudo mount -t smbfs -o username=tim,password=*****,uid=`whoami`,gid=`whoami`,fmask=000,dmask=000  //ubuntu/tim /home/`whoami`/Network

however the shell returns the following:

mount: wrong fs type, bad option, bad superblock on //ubuntu/tim,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

What am I doing wrong?

---

### Post by skunkydog on 2005-11-12
i can't write to the directory when connecting from my other ubuntu 5.04 machine. i can when i connect to the share from the ubuntu  5.10 machine i'm sharing from.  here is the section from the config file

[me]
path = /home/me
available = yes
browseable = yes
public = yes
writable = yes
guest ok = yes

am i missing something?
thanks,
sd

---

### Post by lance bermudez on 2006-02-15
From my windows box I can see its share
C:\Documents and Settings\mother>net view 192.168.3.2
Shared resources at 192.168.3.2
Share name   Type         Used as  Comment
-------------------------------------------------------------------------------
wshare       Disk
The command completed successfully.

And still from my windows box I can see my Ubuntu shares
C:\Documents and Settings\mother>net view 192.168.3.3
Shared resources at 192.168.3.3
breezyBadger server (Samba, Ubuntu)
Share name   Type         Used as  Comment
-------------------------------------------------------------------------------
homes        Disk                  Home Directories
lshare       Disk
PSC-750      Print                 PSC-750
windows      Disk
The command completed successfully.

From the windows box I can ping both pc ip addresses and computer names.

From the Ubuntu box using the ip address of the computer name i get
 smbclient -L breezybadger
Password:
Domain=[LBERMUDEZ] OS=[Unix] Server=[Samba 3.0.14a-Ubuntu]
        Sharename       Type      Comment
        ---------       ----      -------
        homes           Disk      Home Directories
        lshare          Disk
        windows         Disk
        print$          Disk      Printer Drivers
        IPC$            IPC       IPC Service (breezyBadger server (Samba, Ubuntu))
        ADMIN$          IPC       IPC Service (breezyBadger server (Samba, Ubuntu))
        PSC-750         Printer   PSC-750
Domain=[LBERMUDEZ] OS=[Unix] Server=[Samba 3.0.14a-Ubuntu]
        Server               Comment
        ---------            -------
        BREEZYBADGER         breezyBadger server (Samba, Ubuntu)
        MOM

        Workgroup            Master
        ---------            -------
        LBERMUDEZ            MOM

and form the Ubuntu box for the window using the ip address and computer name i getting
root@breezyBadger:~# smbclient -L //192.168.3.2
Password:
Anonymous login successful
Domain=[LBERMUDEZ] OS=[Windows 5.0] Server=[Windows 2000 LAN Manager]
        Sharename       Type      Comment
        ---------       ----      -------
Error returning browse list: NT_STATUS_ACCESS_DENIED
session request to 192.168.3.2 failed (Called name not present)
session request to 192 failed (Called name not present)
Anonymous login successful
Domain=[LBERMUDEZ] OS=[Windows 5.0] Server=[Windows 2000 LAN Manager]
        Server               Comment
        ---------            -------
        BREEZYBADGER         breezyBadger server (Samba, Ubuntu)
        GRASSHOPPER
        MOM
        Workgroup            Master
        ---------            -------
        LBERMUDEZ            MOM

this is because i just changed from my window xp to my Ubuntu other wise grasshopper is the computer name for my win xp. if i restart then from my Ubuntu using the Ubuntu ip address or computer name i get

root@breezyBadger:~# smbclient -L \\192.168.3.3
Password:
Domain=[LBERMUDEZ] OS=[Unix] Server=[Samba 3.0.14a-Ubuntu]
        Sharename       Type      Comment
        ---------       ----      -------
        homes           Disk      Home Directories
        lshare          Disk
        windows         Disk
        print$          Disk      Printer Drivers
        IPC$            IPC       IPC Service (breezyBadger server (Samba, Ubunt u))
        ADMIN$          IPC       IPC Service (breezyBadger server (Samba, Ubunt u))
        PSC-750         Printer   PSC-750
Domain=[LBERMUDEZ] OS=[Unix] Server=[Samba 3.0.14a-Ubuntu]
        Server               Comment
        ---------            -------
        BREEZYBADGER         breezyBadger server (Samba, Ubuntu)
        MOM
        Workgroup            Master
        ---------            -------
        LBERMUDEZ            BREEZYBADGER

and for the windows from the Ubuntu i get 

root@breezyBadger:~# smbclient -L \\mom
Password:
Anonymous login successful
Domain=[LBERMUDEZ] OS=[Windows 5.0] Server=[Windows 2000 LAN Manager]
        Sharename       Type      Comment
        ---------       ----      -------
Error returning browse list: NT_STATUS_ACCESS_DENIED
Anonymous login successful
Domain=[LBERMUDEZ] OS=[Windows 5.0] Server=[Windows 2000 LAN Manager]
        Server               Comment
        ---------            -------
        Workgroup            Master
        ---------            -------

and working from the window after the restart i still get what i had from the top. the Ubuntu and Windows xp pc is a dual boot. i think the problem is on the Ubuntu because i can see both from the windows 2000 pc. but im not shure what the problem is or where it is. below is my smb.conf file and how i have it set up

First let that I’m printing from windows 2000 to Ubuntu breezy badger where my HP PSC 750 printer is attached. And the files can be shared from the Ubuntu breezy badger to the windows but not from the windows to the breezy badger. Make sure samba, samba-common, smbclient, smbfs, libsmbclient, and libsmbclient-dev are installed. Also make sure the printer is installed by using system administraton printing then click add printer. Now to get started the commands that need to be typed in are surrounded by “” and have to be typed in terminal using “sudo su –“ to use super user the password will be you login password. Terminal is open by clicking applications then accessories then terminal. To get this to work you have to have all to the three user mathch user names and password they are windows user, Linux user, and samba user. With the “smbpasswd –a username” hit enter and put in the password also you will have to add the root user to samba “smbpasswd –a root” this is for administration use. Then edit the smb.conf file of samba with “vi /etc/samba/smb.conf” to match what is below. To add the changes press the insert key on the key board and make it look like what is below

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
# "testparm" to check that you have not many any basic syntactic
# errors.
#

#======================= Global Settings =======================

[global]

## Browsing/Identification ###

# Change this to the workgroup/NT-domain name your Samba server will part of
workgroup = LBERMUDEZ

# server string is the equivalent of the NT Description field
server string = %h server (Samba, Ubuntu)

# Windows Internet Name Serving Support Section:
# WINS Support - Tells the NMBD component of Samba to enable its WINS Server
wins support = yes

#authentication
security = user


# CUPS printing. See also the cupsaddsmb( manpage in the
# cupsys-client package.
load printers = yes
printing = cups
printcap name = cups

show add printer wizard = No

[homes]
comment = Home Directories
path = /home/lance
browseable = yes
writable = yes
create mask = 0700
directory mask = 0700

[printers]
comment = All Printers
path = /tmp
printable = Yes
guest ok = Yes
public = yes
use client driver = No
browseable = Yes
printer admin = root

[print$]
comment = Printer Drivers
path = /var/lib/samba/printer
browseable = yes
read only = yes
guest ok = yes
write list = root

when you have typed what is above save it by pressing the esc key to exit the insert mode then press shift q then type exit. Restart samba by typing “/etc/init.d/samba restart” then type “cupsaddsmb –U root –v –a “ hit enter then enter the password that you used for the samba root account. This will add the driver to samba for the printer. If you need help understanding this part read this web page at [http://www.linuxdevcenter.com/pub/a/...kbk_samba.html](http://www.linuxdevcenter.com/pub/a/...kbk_samba.html)
after the drivers have been copied reedit the smb.conf file and change the “security = user” part to “security = share” under #authentication comment and save and restart samba. To get printing to work download the adobe program and adobe ppd toward the botton of page from the url to the windows 2000 box. on the Ubuntu box type “/etc/cups/ppd” hit enter then type “ls” find your printer and whrite down its name they type “cp printer name /home/shared folder name” then type “cd /usr/share/cups/model/hplip” hit enter type “ls” find your printer then type “cp printer /home/shared folder name” on the windows 2000 box connect to the Ubuntu share and copy the printer files to windows 2000. unzip the adobe ppd program and where ever you copy it to past the printer files you copied from Ubuntu into it the run the adobe program and install the printer.

---

### Post by paredown on 2006-02-15
well i'm a noob and thinking about *nix again--command line phobia and all. Sure 'nuff the results from the first instruction freaked me out:

'Suggested packages:
  samba-doc
The following NEW packages will be installed:
  samba
0 upgraded, 1 newly installed, 0 to remove and 21 not upgraded.
Need to get 0B/2389kB of archives.
After unpacking 6070kB of additional disk space will be used.

Preconfiguring packages ...
Selecting previously deselected package samba.
(Reading database ... 61213 files and directories currently installed.)
Unpacking samba (from .../samba_3.0.14a-6ubuntu1_i386.deb) ...
Setting up samba (3.0.14a-6ubuntu1) ...
Generating /etc/default/samba...
TDBSAM version too old (0), trying to convert it.
TDBSAM converted successfully.
account_policy_get: tdb_fetch_uint32 failed for field 1 (min password length), r eturning 0
account_policy_get: tdb_fetch_uint32 failed for field 2 (password history), retu rning 0
account_policy_get: tdb_fetch_uint32 failed for field 3 (user must logon to chan ge password), returning 0
account_policy_get: tdb_fetch_uint32 failed for field 4 (maximum password age), returning 0
account_policy_get: tdb_fetch_uint32 failed for field 5 (minimum password age), returning 0
account_policy_get: tdb_fetch_uint32 failed for field 6 (lockout duration), retu rning 0
account_policy_get: tdb_fetch_uint32 failed for field 7 (reset count minutes), r eturning 0
account_policy_get: tdb_fetch_uint32 failed for field 8 (bad lockout attempt), r eturning 0
account_policy_get: tdb_fetch_uint32 failed for field 9 (disconnect time), retur ning 0
account_policy_get: tdb_fetch_uint32 failed for field 10 (refuse machine passwor d change), returning 0
 * Starting Samba daemons..                                              [ ok ]'

What have I just witnessed?

---

### Post by lance bermudez on 2006-02-16
here is eveything working fine

First let that I’m printing from windows 2000 to Ubuntu breezy badger where my HP PSC 750 printer is attached. And the files can be shared from the Ubuntu breezy badger to the windows but not from the windows to the breezy badger. Make sure samba, samba-common, smbclient, smbfs, libsmbclient, and libsmbclient-dev are installed.  Also make sure the printer is installed by using system administraton printing then click add printer. Now to get started the commands that need to be typed in are surrounded by “” and have to be typed in terminal using “sudo su –“ to use super user the password will be you login password. Terminal is open by clicking applications then accessories then terminal. To get this to work you have to have all to the three user mathch user names and password they are windows user, Linux user, and samba user. With the “smbpasswd –a username” hit enter and put in the password also you will have to add the root user to samba “smbpasswd –a root” this is for administration use. Then edit the smb.conf file of samba with “vi /etc/samba/smb.conf” to match what is below. To add the changes press the insert key on the key board and make it look like what is below

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
# "testparm" to check that you have not many any basic syntactic 
# errors. 
#

#======================= Global Settings =======================

[global]

## Browsing/Identification ###

# Change this to the workgroup/NT-domain name your Samba server will part of
   workgroup = LBERMUDEZ

# server string is the equivalent of the NT Description field
   server string = %h server (Samba, Ubuntu)

# Windows Internet Name Serving Support Section:
# WINS Support - Tells the NMBD component of Samba to enable its WINS Server
   wins support = yes

#resole host names to ip addresses
name resolve order = lmhosts host wins bcast
bind interfaces only = yes
hosts deny = all
hosts allow =192.168.3.0/24 127.
interfaces = eth0 lo

#authentication
security = user

# encrpyt password in the smb.conf
encrypt passwords = yes
smb passwd file  = /etc/samba/smbpasswd
local master = no
dns proxy = no

# CUPS printing.  See also the cupsaddsmb(8) manpage in the
# cupsys-client package.
   load printers = yes
   printing = cups
   printcap name = cups
   show add printer wizard = No

[homes]
   comment = Home Directories
   path = /home/lance
   browseable = yes
   writable = yes
   create mask = 0700
   directory mask = 0700

[lshare]
  path = /home/lance/lshare
  available = yes
  browseable = yes
  public = yes
  writable = yes
  guest ok = yes

[windows]
  path = /media/windows
  available = yes
  browseable = yes
  writable = yes
  guest ok = yes

[printers]
   comment = All Printers
   path = /tmp
   printable = Yes
   guest ok = Yes
  public = yes 
  use client driver = No
   browseable = Yes
  printer admin = root

[print$]
  comment = Printer Drivers
  path = /var/lib/samba/printer
  browseable = yes
  read only = yes
  guest ok = yes
  write list = root

when you have typed what is above save it by pressing the esc key to exit the insert mode then press shift q then type exit. Restart samba by typing “/etc/init.d/samba restart” then type “cupsaddsmb –U root –v –a “ hit enter then enter the password that you used for the samba root account. This will add the driver to samba for the printer.  If you need help understanding this part read this web page at [http://www.linuxdevcenter.com/pub/a/linux/2005/01/13/lnxckbk_samba.html](http://www.linuxdevcenter.com/pub/a/linux/2005/01/13/lnxckbk_samba.html)
after the drivers have been copied reedit the smb.conf file and change the “security = user” part to “security = share” under #authentication comment and save and restart samba. To get printing to work download the adobe program and adobe ppd toward the botton of page from the url to the windows 2000 box. on the Ubuntu box type “/etc/cups/ppd”  hit enter then type “ls” find your printer and whrite down its name they type “cp printer name /home/shared folder name” then type “cd /usr/share/cups/model/hplip” hit enter type “ls” find your printer then type “cp printer /home/shared folder name” on the windows 2000 box connect to the Ubuntu share and copy the printer files to windows 2000. unzip the adobe ppd program and where ever you copy it to past the printer files you copied from Ubuntu into it the run the adobe program and install the printer.   The [window] is a fat32 part of my hard drive i use to share files with the dual boot and the network and the [lshare] is for network sharing they both allow access without needing user name and password but [home] needs user name and access. the #resole host names to ip addresses line is for security so that only my network pc can use my linux samba server and the # encrpyt password in the smb.conf line is for win 2000 and above because windows encrpyt passwords with these version but is not needed for version below. now the winows will talk to the linux but the linux will not talk to the windows tell you fix the window and linux some more. this part will not work with dhcp and may not be a problem but needs to be done on static network for computer names to be pinged in linux. on the window edit the lmhosts and hosts. for the windows hosts  should be ip space computer name
127.0.0.1       localhost
192.168.3.2	mom
192.168.3.3	breezyBadger
and for the lmhosts on the winows  should be ip address netbios name
192.168.3.3 breezybadger #PRE
192.168.3.2 mom #PRE
and for the linux hosts ip computer name
127.0.0.1 localhost.localdomain localhost breezyBadger
192.168.3.3 breezyBadger
192.168.3.2 MOM
to connect to the windows computer form linux the user must have the sharing permissions set and the windows user added to both the sharing permission and security tab. does not need a password unless your user has one for security use 
smbclient //ip address/folder share name -U username%password
example 
smbclient //192.168.3.2/wshare -U lance%bermudez
to browse the windows computer for shares use
smbclient -L //192.168.3.2 -N -U lance%bermudez

rembember to be in the command line directory you want to send files to the windows or save the files because it acts like an ftp. for a gui mount it with 
 mount //192.168.3.2/wshare /media/wshare -t smbfs -o username=lance,password=bermudez,dmask=777,fmask=777

also edit /etc/gnome-vfs-2.0/modules/smb-module.conf change the line
smb: [daemon] libsmb
to read
smb: libsmb.so
but i did
smb: libsmb
and it seems to work fine

---

### Post by prara on 2006-02-25
When you get this error when sharing folders, check for logs at /var/log/samba/
An error like:

```
'/path/to/folder' does not exist or is not a directory, when connecting to [share_name]
```

means that the folder permissions are not enough. Check the the user running samba server (usually root) has proper permissions to access the folder.

---

### Post by ZarathustraDK on 2006-07-11
Ah finally I got filesharing working.

I couldn't understand why I could only connect to my shares via "System->Network Servers" on my own computer. Turns out I had forgot to install the smbfs-package on the other machines, d'oh.

I never thought simple filesharing over network would be such a hassle, nonetheless I learned a thing or two about sambaserver ;-)

---

### Post by moore.bryan on 2006-10-15
*this might be a silly question, but i've setup samba as per this thread on my home ubuntu and want to access it on my work windows... how do i set up the windows machine?*

---

### Post by jingo811 on 2007-02-07
Creator of this how to tutorial could you please come in here and help me?!
[http://www.ubuntuforums.org/showthread.php?t=353271](http://www.ubuntuforums.org/showthread.php?t=353271)
I'm stuck.

---

### Post by bandoba on 2007-02-09
Thanks for the simple guide. 

I followed this guide and SAMBA server is working fine on Ubuntu. When I connect from Windows machine to my Ubuntu server, I see **Homes** folder as well as **<username-on-ubuntu>** folder. Both these folders show same content. Can somebody tell me why do I see Homes folder and can I get rid of it? I just want it to show home directory of <username-on-ubuntu>.

---

### Post by rcgreg on 2008-12-14
Example:
```
sudo mount -t smbfs -o username=kenny,password=test,uid=`whoami`,gid=`whoami`,fmask=000,dmask=000  //kenny_smb_server/kenny /home/`whoami`/Network
```


Using this line with the following substitutions
username = smb [the name of the created smb user]
password = **** [the password for the smb user]
kenny_smb_server = linux [the name of the server box]
/kenny = smb

I receive the error bad username 'whoami'

I'm pretty much clueless asbout this - any help is appreciated !!!

---

