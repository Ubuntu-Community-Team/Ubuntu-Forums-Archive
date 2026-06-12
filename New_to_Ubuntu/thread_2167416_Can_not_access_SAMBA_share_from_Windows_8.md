---
title: "Can not access SAMBA share from Windows 8"
date: 2013-08-13
forum: New to Ubuntu
---

### Post by Christian_W._Ombustvedt on 2013-08-13
Hi all,

I'm a noob trying to set up a home server for file sharing with Ubuntu 13.04 and Samba.
I have configured Samba (as good as I can with my limited knowledge) and added a share, but can not access this from Windows 8.
I have searched the net and read articles and forum posts for a total of about six hours, but it's just to many different cases and solutions, I'm just getting more confused the more I read.
That's why I'm posting this here, to try to get some help for my specific issue.

So here's the details:
I've downloaded and configured Samba and set up a share. Sometimes I can see this share in Windows (most often after a restart), but suddenly it disappears. I have never been able to access it or see its content (Windows says "Network path can not be found".)
When trying to ping the Ubuntu machine I sometimes can reach the machine and other times get "Destination host unreachable."
Pinging the Windows 8 machine from Ubuntu works every time.

Here is my smb.conf file: 
 
(I've edited out hashed text)

[global]


   workgroup = WORKGROUP
   server string = %h server (Samba, Ubuntu)
;   wins server = w.x.y.z
   dns proxy = no
;   name resolve order = lmhosts host wins bcast
;   interfaces = 127.0.0.0/8 eth0
;   bind interfaces only = yes
   log file = /var/log/samba/log.%m
   max log size = 1000
   syslog = 0
   panic action = /usr/share/samba/panic-action %d
   encrypt passwords = true   
   passdb backend = tdbsam
   obey pam restrictions = yes
   unix password sync = yes
   passwd program = /usr/bin/passwd %u
   passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .
   pam password change = yes
   map to guest = bad user
;   domain logons = yes
;   logon path = \\%N\profiles\%U
;   logon drive = H:
;   logon script = logon.cmd
; add user script = /usr/sbin/adduser --quiet --disabled-password --gecos "" %u
; add machine script  = /usr/sbin/useradd -g machines -c "%u machine account" -d /var/lib/samba -s /bin/false %u  
; add group script = /usr/sbin/addgroup --force-badname %g
;   printing = bsd
;   printcap name = /etc/printcap
;   printing = cups
;   printcap name = cups
;   include = /home/samba/etc/smb.conf.%m
;   message command = /bin/sh -c '/usr/bin/linpopup "%f" "%m" %s; rm %s' &
;   idmap uid = 10000-20000
;   idmap gid = 10000-20000
;   template shell = /bin/bash
;   winbind enum groups = yes
;   winbind enum users = yes
;   usershare max shares = 100
   usershare allow guests = yes
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
  realm = localdomain
  server role = domain controller
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
;[cdrom]
;   comment = Samba server's CD-ROM
;   read only = yes
;   locking = no
;   path = /cdrom
;   guest ok = yes
;   preexec = /bin/mount /cdrom
;   postexec = /bin/umount /cdrom
[Media]
path = /media/christian/17CFC1D9106CE4DD
available = yes
valid users = christian
read only = no
browsable = yes
public = yes
writable = yes


Any and all feedback very much appreciated!


- C

---

