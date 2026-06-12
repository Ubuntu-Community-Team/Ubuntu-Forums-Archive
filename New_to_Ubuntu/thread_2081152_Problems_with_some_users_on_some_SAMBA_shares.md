---
title: "Problems with some users on some SAMBA shares"
date: 2012-11-06
forum: New to Ubuntu
---

### Post by LedFoot74 on 2012-11-06
Hi All,

Am building the 3rd generation of my home media server  and making the big step from the point and shoot freenas, to the more  capable Ubuntu server.

Please keep in mind that I'm also trying  to learn/do everything via the command line so I can get a deeper  understanding of the Linux.

So far I've successfully installed ubuntu 12.04 server (no GUI), can ssh in and have SAMBA running with some shares.

My  problem is that I've got SAMBA running and I can access the shares from  my windows machine. But some shares cannot be accessed by some users  when they should.

[SIZE=3]**Background:**[/SIZE]
**I've got three users:**

[LIST=1]
[*]risto - admin made during setup
[*]leanne - user added afterwards
[*]xbmc - user added afterwards
[/LIST]
**I've got 2 groups:**

[LIST=1]
[*]mediagp - contains users risto, leanne and xbmc
[*]leannegp - contains users risto, leanne
[/LIST]
**Shares with permissions**

risto@server:/zfs2$ ls -l
total 10
drwxrwx--- 2 risto leannegp 3 Nov  6 14:17 leanne
drwxrwx--- 2 risto mediagp  5 Nov  5 23:43 media
drwxr----- 2 risto mediagp  2 Nov  5 21:19 photos
drwxr-xr-x 2 risto root     3 Nov  6 14:16 risto


**Samba config file**
risto@server:/etc/samba$ sudo nano /etc/samba/samba.config
risto@server:/etc/samba$ ls -l
total 24
-rw-r--r-- 1 root root     0 Nov  6 17:08 dhcp.conf
-rw-r--r-- 1 root root     8 Jun  8 23:14 gdbcommands
-rw-r--r-- 1 root root     0 Nov  5 19:45 samba.conf
-rw-rw-r-- 1 root adm    854 Nov  6 17:39 smb.conf
-rw-r--r-- 1 root root 12464 Nov  5 19:44 smb.conf.bak
risto@server:/etc/samba$ sudo nano smb.conf
  GNU nano 2.2.6          File: smb.conf

#============ Global Settings ====================
[global]
workgroup = WORKGROUP
server string = Samba Server %v on %l
netbios name = server
security = user
map to guest = bad user
dns proxy = no
encrypt passwords = yes

#============ Share Definitions ==================
[Media]
path = /zfs2/media
comment = Tv shows and Movies
browsable = yes
writable = yes
guest ok = no
read only = no
valid users = leanne, xbmc, risto

[Photos]
path = /zfs2/photos
comment = Risto and Lea's photos
browsable = yes
writable = yes
guest ok = no
read only = no
valid users = leanne, xbmc, risto

[Risto]
path = /zfs2/risto
comment = Risto's share
browsable = yes
writable = yes
guest ok = no
read only = no
valid users = risto

[Leanne]
path = /zfs2/leanne
comment = Lea's share
browsable = yes
writable = yes
guest ok = no
read only = no
valid users = leanne, risto


**[SIZE=3]What I wan[SIZE=3]t to do[/SIZE][/SIZE]**
So I've got 4 shares and I want the following users to be able to access them and all files/directories under them:

[LIST=1]
[*]Leanne - rw by users leanne, risto and group leanegp
[*]risto - rw by user risto
[*]media - rw by users risto, xbmc and group mediagp. r by user leanne
[*]photos - rw by user risto. r by users leanne, xbmc and group mediagp
[/LIST]

**[SIZE=3]What [SIZE=3]the problem is[/SIZE][/SIZE]**
Now  all users can see the server and the list the shares from a windows  machine, but the problem I have is the following (this is all from a  windows machine):[INDENT]**User Leanne**

[LIST=1]
[*]can access \\server\leanne (rw as expected)
[*]gets "windows cannot access \\server\media" (should have r)
[*]gets "windows cannot access \\server\photos" (should have r)
[*]requires user/password for \\server\risto" (as expected)
[/LIST]
[B]User risto
[/B]
[LIST=1]
[*]Can access everything (rw as expected)
[/LIST]
[B]User xbmc
[/B]
[LIST=1]
[*]Can access \\server\media
[*]gets "windows cannot access \\server\photos" (should have rw)
[*]requires user/password for \\server\risto & \\server\leanne (as expected)
[/LIST]
[/INDENT]Any ideas on what to check?

---

### Post by LedFoot74 on 2012-11-08
Hi All,

I finally managed to work it out, there seemed to be an issue with the password set for the two users leanne and xbmc. I reset that and everything started to come together. I've now been able to figure out how to force create modes etc and the shares are coming together nicely.

I just wanted to also say a big thank you to everyone who replied to this thread. I was really struggling and you were an incredible help. I could not have resolved this without your incredible guidance, thoughts, tips, suggestions and quick replies!

---

