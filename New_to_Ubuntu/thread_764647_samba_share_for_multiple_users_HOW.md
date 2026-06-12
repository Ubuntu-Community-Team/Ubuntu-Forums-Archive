---
title: "samba share for multiple users HOW?"
date: 2008-04-24
forum: New to Ubuntu
---

### Post by djules26 on 2008-04-24
just shared a folder name program thru samba. I already made this folder accessible to anyone without any password whatsoever, its enabled for read/write/create but when other users from our network access this samba shared folder they got an "access denied error".

help anyone please.

---

### Post by SpaceTeddy on 2008-04-24
How does autheification work on the samba side ? is the share set to public ? is the anonymous login set for a public share ?

also, if you have multile - different users connecting to a fully public share, you might want to set the force user to make sure that every file belongs to the same user... 

can you please paste your smb.conf file to make sure that all options are set ?

---

### Post by vpjr on 2008-04-24
Hi, you can either:

1. download the Samba Server Configuration GUI from the repositories to make configuring easier. There is a security tab in the GUI so you can set who logins.

2. Or add "valid user = #no user list, anyone can login" to the section where you define the directory to be shared.

best regards,

ven

---

### Post by djules26 on 2008-04-24
HERE's MY SMB.CONF

#======================= Global Settings =======================
[global]
   workgroup = Workgroup
   server string = Server
;  wins support = no
;  wins server = w.x.y.z
   dns proxy = no
;  name resolve order = lmhosts host wins bcast

#### Networking ####
;   interfaces = 127.0.0.0/8 eth0
;   bind interfaces only = true

#### Debugging/Accounting ####

   log file = /var/log/samba/log.%m
   max log size = 1000
;  syslog only = no
   syslog = 0
   panic action = /usr/share/samba/panic-action %d

####### Authentication #######

   security = share
;  encrypt passwords = true
   passdb backend = tdbsam
;  obey pam restrictions = yes
   guest account = nobody
   invalid users = root
;  unix password sync = no
   passwd program = /usr/bin/passwd %u
   passwd chat = *Enter\snew\sUNIX\spassword:* %n\n *Retype\snew\sUNIX\spassword:* %n\n *passwd:*password\supdated\ssuccessfully* .
;  pam password change = no

########## Domains ###########

;   domain logons = yes
;   logon path = \\%N\profiles\%U
;   logon path = \\%N\%U\profile
;   logon drive = H:
;   logon home = \\%N\%U
;   logon script = logon.cmd
;   add user script = /usr/sbin/adduser --quiet --disabled-password --gecos "" %u


############ Misc ############

;   include = /home/samba/etc/smb.conf.%m
    socket options = TCP_NODELAY
;   message command = /bin/sh -c '/usr/bin/linpopup "%f" "%m" %s; rm %s' &
;   domain master = auto
;   idmap uid = 10000-20000
;   idmap gid = 10000-20000
;   template shell = /bin/bash
;   winbind enum groups = yes
;   winbind enum users = yes

#======================= Share Definitions =======================

wins support = no

[pcbr2]    <--------------- this is shared for everyone(rwx)
path = /program/pcbr2
available = yes
browsable = yes
public = yes
writable = yes
create mask = 0777
directory mask = 0777 
force user = nobody
force group = nogroup 
guest ok = yes

[backup]
path = /backup
available = yes
browsable = yes
public = yes
writable = yes

---

### Post by SpaceTeddy on 2008-04-25
your definition looks fine - there is just one line missing - you have the
> guest account = nobody
which means that there is a guest account anybody can use - but you did not specify when to use that guest account.

add the line
> map to guest = Bad User
to the smb.conf, restart samba and check if it works then :)

---

