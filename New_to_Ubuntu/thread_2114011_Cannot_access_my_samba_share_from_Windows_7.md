---
title: "Cannot access my samba share from Windows 7"
date: 2013-02-08
forum: New to Ubuntu
---

### Post by apalexander on 2013-02-08
I'm pulling my hair out over this one! I am new to this forum, and ubuntu.

I have set up a server with Ubuntu Server 11.04, and I'm trying to share out my Raid1 array to my Windows 7 machine. I have installed samba, and am using Webmin to set up the share. I'm able to get as far as seeing the server in Windows explorer, and I can see the share, and open it. However, when I try to open a sub-directory, or create any file, I get an error that says I do no have permission to access the directory. I've gone through the share set up many times and I don't know what I'm doing wrong.

Here's the text from my smb.conf file (minus a bunch of comments):

#======================= Global Settings =======================

[global]
	log file = /var/log/samba/log.%m
	name resolve order = wins lmhosts host bcast
	passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .
	obey pam restrictions = yes
	map to guest = bad user
	encrypt passwords = true
	passwd program = /usr/bin/passwd %u
	passdb backend = tdbsam
	wins support = yes
	dns proxy = no
	server string = %h server (Samba, Ubuntu)
	path = /var/data
	unix password sync = yes
	workgroup = WORKGROUP
        force user = andrew
	security = users
	syslog = 0
	usershare allow guests = yes
	panic action = /usr/share/samba/panic-action %d
	max log size = 1000
	pam password change = yes

## Browsing/Identification ###

;   wins server = w.x.y.z

#### Networking ####

;   interfaces = 127.0.0.0/8 eth0

;   bind interfaces only = yes

########## Domains ###########

;   domain logons = yes

;   logon path = \\%N\profiles\%U

#   logon path = \\%N\%U\profile

;   logon drive = H:
#   logon home = \\%N\%U

;   logon script = logon.cmd

; add user script = /usr/sbin/adduser --quiet --disabled-password --gecos "" %u

; add machine script  = /usr/sbin/useradd -g machines -c "%u machine account" -d /var/lib/samba -s /bin/false %u
  
; add group script = /usr/sbin/addgroup --force-badname %g

########## Printing ##########

;   printing = bsd
;   printcap name = /etc/printcap

;   printing = cups
;   printcap name = cups

############ Misc ############

;   include = /home/samba/etc/smb.conf.%m

;   message command = /bin/sh -c '/usr/bin/linpopup "%f" "%m" %s; rm %s' &

;   idmap uid = 10000-20000
;   idmap gid = 10000-20000
;   template shell = /bin/bash

;   winbind enum groups = yes
;   winbind enum users = yes

;   usershare max shares = 100

#======================= Share Definitions =======================

;[homes]
;   comment = Home Directories
;   browseable = no

;   read only = yes

;   create mask = 0700

;   directory mask = 0700

;   valid users = %S

;[netlogon]
;   comment = Network Logon Service
;   path = /home/samba/netlogon
;   guest ok = yes
;   read only = yes

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

[print$]
   comment = Printer Drivers
   path = /var/lib/samba/printers
   browseable = yes
   read only = yes
   guest ok = no

;   write list = root, @lpadmin

# A sample share for sharing your CD-ROM with others.
;[cdrom]
;   comment = Samba server's CD-ROM
;   read only = yes
;   locking = no
;   path = /cdrom
;   guest ok = yes

;   preexec = /bin/mount /cdrom
;   postexec = /bin/umount /cdrom

[Data]
delete readonly = yes
writeable = yes
force directory mode = 775
force group = admin
force create mode = 775
force user = andrew
browsable = yes
public = yes
create mode = 775
directory mode = 775

---

### Post by prodigy_ on 2013-02-09
First, it's **security = user**, not **users**. Second, **force user** is not recommended in most cases and I'd especially avoid using it in the **[global]** section.

And an example Win7 accessible share:
```
[global] # add the following lines
local master = yes
preferred master = yes
ntlm auth = no
lanman auth = no

[System] # share itself
comment = Windows C: drive
browsable = yes
read only = no
path = /media/System
guest ok = no
sec = ntlmv2
create mask = 0755
```

---

### Post by brent1975 on 2013-02-09
I never really had good luck using webmin with samba. not to say it doesn't work just didn't for me. 

have you tried doing it manually?

I am assuming this is for a home server or non production thus the 11.xx version.

Here is how I set up samba every time I go to redo my server for pure practice. and this works for me. Just change your share name, path, and user(s) and should work for you.

First you have to create the users that are going to have access to the samba share.

To create the users you will need to run these two comands:

```
sudo smbpasswd -a your-user-name
```

and
```
sudo smbpasswd -e your-user-name
```


Then make a backup of smb.conf

```
sudo mv /etc/samba/smb.conf  /etc/samba/smb.conf.bak
```

Verify that it is in the directory as smb.conf.bak

Now create another smb.conf file.
```
sudo nano /etc/samba/smb.conf
```

Here is my smb.conf file

```
 #======================= Share Definitions =======================

    # Un-comment the following (and tweak the other settings below to suit)
    # to enable the default home directory shares. This will share each
    # user's home directory as \\server\username
    [homes]
    comment = Home Directories
    browseable = yes

    # By default, \\server\username shares can be connected to by anyone
    # with access to the samba server. Un-comment the following parameter
    # to make sure that only "username" can connect to \\server\username
    valid users = %S

    # By default, the home directories are exported read-only. Change next
    # parameter to 'yes' if you want to be able to write to them.
    writable = yes
        [global]
        server string = %h server (Samba, Ubuntu)
        map to guest = Bad User
        obey pam restrictions = Yes
        pam password change = Yes
        passwd program = /usr/bin/passwd %u
        passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .
        unix password sync = Yes
        syslog = 0
        log file = /var/log/samba/log.%m
        max log size = 1000
        dns proxy = No
        usershare allow guests = Yes
        panic action = /usr/share/samba/panic-action %d
        valid users = brent, brian, jessica
        admin users = brent, brian, jessica
        write list = brent, brian, jessica

[printers]
        comment = All Printers
        path = /var/spool/samba
        create mask = 0700
        printable = Yes
        browseable = No

[print$]
        comment = Printer Drivers
        path = /var/lib/samba/printers

[www]
        path = /var/www
        username = brent,root
        write list = brent, root

[Brent]
        path = /home/brent
        valid users = brent
        write list = brent

[Jessica]
        path = /home/jessica
        valid users = brent, jessica
        write list = brent, jessica
[movies]
        path = /home/movies
        valid users = brent, jessica
        write list = brent, jessica

[music]
        path = /home/music
        valid users = brent, jessica
        write list = brent, brian

```

make your changes save and close the file

You will need to restart samba
```
sudo restart smbd 
```

From Windows 7 you should be able to access your share.

```
\\ubuntuserver\username
```


I hope this helps... :)

---

### Post by Morbius1 on 2013-02-09
There is a lot of things that samba will automatically correct because it just assumes you were high when you edited smb.conf - or used webmin :).

"security = users" is one of them. It will ignore it so the default "security = user" will be in force.

You also have the path to your shared folder in the [global] section which won't harm anything for the moment.
> path = /var/dataNothing wrong with a "force user" and nothing wrong with it being in the [global] section as long as you realize that if you have it in the [global] section it will affect all shares.

Anywho, what are the ownership / permissions of the target folder:
```
ls -dl /var/data
```The way you have this share set up:
force user = andrew
force group = admin

Either the owner has to be andrew, or the group has to be admin and permissions need to be 775, or the permissions have to be 777 for the client to write.

---

