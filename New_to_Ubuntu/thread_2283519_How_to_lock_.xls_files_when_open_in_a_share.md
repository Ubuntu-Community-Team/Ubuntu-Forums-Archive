---
title: "How to lock .xls files when open in a share?"
date: 2015-06-22
forum: New to Ubuntu
---

### Post by hermeti-k on 2015-06-22
Hi guys!

Im trying to set up my smb.conf, and cannot find the solution of the problem

When user1 (ubunutu machine) opens a xls placed in a share, then user2 opens the same file, it opens whithout any warning that user1 is editing the file.


i tried to disable oplocks, kernel oplocks, without any success. I want that when user1 opens an xls file in that share, the srver locks the until the useres closes it.

is it posible???
here is my smb.conf file


```
&#8203;#======================= Global Settings =======================
[global]
workgroup = WORKGROUP
server string = %h server
dns proxy = no
log level = 0
syslog = 0
log file = /var/log/samba/log.%m
max log size = 1000
syslog only = yes
panic action = /usr/share/samba/panic-action %d
encrypt passwords = true
passdb backend = tdbsam
obey pam restrictions = yes
unix password sync = no
passwd program = /usr/bin/passwd %u
passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .
pam password change = yes
socket options = TCP_NODELAY IPTOS_LOWDELAY
guest account = nobody
load printers = no
disable spoolss = yes
printing = bsd
printcap name = /dev/null
unix extensions = yes
wide links = no
create mask = 0777
directory mask = 0777
use sendfile = no
null passwords = no
local master = yes
time server = no
wins support = no
kernel oplocks = yes
#======================= Share Definitions =======================
[share]
path = /media/3dcb9e47-f9a2-41fa-9e6a-b20a44674a6a/share/
guest ok = no
read only = no
browseable = yes
inherit acls = yes
inherit permissions = no
ea support = yes
store dos attributes = yes
printable = no
create mask = 0755
force create mode = 0644
directory mask = 0755
force directory mode = 0755
hide dot files = yes
valid users = "esteban"
invalid users =
read list =
write list = "esteban"
```

---

### Post by steveo314 on 2015-06-25
If your opening it in LibreOffice, is there a temp copy of the file made while the file is open?

---

