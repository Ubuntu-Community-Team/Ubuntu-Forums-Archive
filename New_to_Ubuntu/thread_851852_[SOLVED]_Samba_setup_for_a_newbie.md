---
title: "[SOLVED] Samba setup for a newbie"
date: 2008-07-07
forum: New to Ubuntu
---

### Post by rossco on 2008-07-07
Hi all,

I just built my first pc from scratch (Yay) and installed Ubuntu server 8.04.  I want to setup up samba file sharing to serve a network share for my windows clients.  I think I have the networking up and running because I can ping and SSH the server from my windows machine.  I can also see the server in my network list on my windows machine.  I have tried to configure the smb.conf file but now I can't open the server in Windows Explorer.  My current file is:

> [global]
   workgroup = WORKGROUP
   server string = %h server (Samba, Ubuntu)
   wins support = yes
   dns proxy = no
;   name resolve order = lmhosts host wins bcast

   interfaces = localhost eth0
   bind interfaces only = true

   log file = /var/log/samba/log.%m
   max log size = 1000
;   syslog only = no
   syslog = 0
   panic action = /usr/share/samba/panic-action %d

   security = user
   encrypt passwords = no
   passdb backend = tdbsam
   obey pam restrictions = yes
;   guest account = nobody
   invalid users = root
   unix password sync = yes
   passwd program = /usr/bin/passwd %u
   passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .
   pam password change = yes
   map to guest = bad user
   socket options = TCP_NODELAY
;   idmap uid = 10000-20000
;   idmap gid = 10000-20000
;   template shell = /bin/bash
;   winbind enum groups = yes
;   winbind enum users = yes
;   usershare max shares = 100
   usershare allow guests = no



[homes]
   comment = Home Directories
   browseable = yes
   read only = no
   create mask = 0700
   directory mask = 0700
   valid users = %S



;[printers]
;   comment = All Printers
;   browseable = no
;   path = /var/spool/samba
;   printable = yes
;   guest ok = no
;   read only = yes
;   create mask = 0700



;[print$]
;   comment = Printer Drivers
;   path = /var/lib/samba/printers
;   browseable = yes
;   read only = yes
;   guest ok = no
;   write list = root, @ntadmin



[cdrom]
   comment = Samba server's CD-ROM
   read only = yes
   locking = no
   path = /cdrom
   guest ok = yes
   preexec = /bin/mount /cdrom
   postexec = /bin/umount /cdrom


I want to have home directories for each windows user so I will create users on Ubuntu for each Windows user.  Currently I just have the one test user loaded.  I also want a common shared folder accessible to any user.  Can anyone help me with this?

---

### Post by cmnorton on 2008-07-08
> **rossco said:**
> Hi all,

I just built my first pc from scratch (Yay) and installed Ubuntu server 8.04.  I want to setup up samba file sharing to serve a network share for my windows clients.  I think I have the networking up and running because I can ping and SSH the server from my windows machine.  I can also see the server in my network list on my windows machine.  I have tried to configure the smb.conf file but now I can't open the server in Windows Explorer.  My current file is:



I want to have home directories for each windows user so I will create users on Ubuntu for each Windows user.  Currently I just have the one test user loaded.  I also want a common shared folder accessible to any user.  Can anyone help me with this?

There are a couple of ways to do this. You can create a generic user and then map samba users to that user. I prefer creating one account for each user, putting them into something like a "samba_share1_group", and giving that folder/folders group rwx privs. The biggest problem I have had with samba is making sure that you run sudo smbpasswd for each user.

If you do this the multiple user way, then start by creating a group; creating, sharing out, protections the folder(s) in question; create an actual user; run smbpasswd; and seeing if you can log in.

---

### Post by arloth on 2008-07-08
I like to use Swat to help me configure Samba.  It makes the more complicated setups especially easy.  Although I've found you need to have the root user enabled for it to work best, and allow local connections to it only, it's still a very handy tool. 
[https://help.ubuntu.com/community/Swat](https://help.ubuntu.com/community/Swat)

---

### Post by rossco on 2008-07-08
Hi guys,

Thanks very much for your help.  Funnily enough I had come to the same conclusions as you have and managed to get it to work!  I installed SWAT and got it configured correctly as just using apt-get doesn't install all the packages and set the settings required.  Its a great way to manage SAMBA.

I also came across the need to add each Windows User using smbpasswd and that was the main issue surrounding why I wasn't seeing the shares come up.  It was working correctly just SAMBA couldn't authenticate my Windows client!  Now I just need to configure it all the way I want it.

Cheers

---

