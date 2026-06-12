---
title: "Guest write Samba"
date: 2013-01-29
forum: New to Ubuntu
---

### Post by burningfly on 2013-01-29
I can't seem to get my samba share able to be accessed for writing by a guest. Here are the settings

I can't seem to get my samba share able to be accessed for writing by a guest. Here are the settings. The /Terriblebyte has read, write and execute permissions set for the guest...
Any pointers?

[global]
	server string = 
	null passwords = Yes
	guest account = nobody
	username map = /etc/samba/smbusers
	syslog only = Yes
	announce version = 5.0
	name resolve order = hosts wins bcast
	socket options = TCP_NODELAY IPTOS_LOWDELAY SO_KEEPALIVE SO_RCVBUF=8192 SO_SNDBUF=8192
	wins support = Yes
	idmap config * : backend = tdb


[Terriblebyte]
	comment = The Terriblebyte
	path = /Terriblebyte
	read only = No
	create mask = 0777
	directory mask = 0777
	guest ok = Yes
	public = yes
	only guest = yes

---

### Post by furything on 2013-01-29
Your guest user account 'nobody'

Have you given it (nobody) write access to '/Terriblebyte'?

For guest account to write to folder the actual folder must have write access given to the actual machine folder.

[https://help.ubuntu.com/community/Samba/SambaServerGuide#File_Sharing_.28Advanced.29](https://help.ubuntu.com/community/Samba/SambaServerGuide#File_Sharing_.28Advanced.29)

---

### Post by burningfly on 2013-01-29
I have given /Terriblebyte 777 access, so nobody should have write access... Right?

---

### Post by furything on 2013-01-29
Your samba configuration does not match my format. I am running 12.04 LTS (mythbuntu) with the following configuration (I have edited this to show you the guest user nobody)

```
[global]
workgroup = Your group
server string = %h server (Samba, ubuntu)
log file = /var/log/samba/log.%m
max log size = 1000
syslog = 0
panic action = /usr/share/samba/panic-action %d
dns proxy = no
security = share

[video]
comment = Videos
path = /var/lib/mythtv/vidoes
public = yes
writable = no
create mask = 0777
directory mask = 0777
force user = nobody
force group = nogroup
```

If I run ```
cat /etc/passwd
```
I get my user nobody. Can you run the same command and confirm you have noboby in the user list?
The folder group you are trying to share should be 'nogroup' if matching the above configuration. Alternatively you could use the actual existing group and user account that belongs to that group.
For example the default group on my share is mythtv and the user is also mythtv so to make my folder writable I would use (and actually do)
```
[video]
comment = Videos
path = /var/lib/mythtv/vidoes
public = yes
writable = no
create mask = 0777
directory mask = 0777
force user = mythtv
force group = mythtv
```
I could just add nobody to the mythtv group - this is what I mean in the previous post
```
useradd -G {group-name} username
```
Also what version of Linux are you using e.g. xubuntu 11.10?

---

### Post by burningfly on 2013-01-29
I do indeed have nobody in the passwd file, 

nobody:x:65534:65534:nobody:/nonexistent:/bin/sh

the shared directory has 777 permissions set, so the group shouldn't matter, though I tried using forcing another user and their group...

I tried resetting the smb.conf file to defaults (sudo cp  /usr/share/samba/smb.conf /etc/samba/smb.conf) and then using the file browser to share the folder and it worked!
All shared and with read write permissions.

Originally I think it didn't as I hadn't mounted the folder with the correct permissions..

---

### Post by furything on 2013-01-29
Have you done this?
```
sudo smbpasswd -a USERNAME
```
Replace USERNAME with real user accounts.
In your case USERNAME should be 'nobody'

Not had much experience with mint and am surprised the samba config is so different.  My understanding is that mint is based on ubuntu (please correct me if I am wrong). 

In the process of upgrading of upgrading to 12.10 right now so will see what samba does when upgrade finishes. If it changes to the same format as yours I can play around with it to get write access.

Will search around this forum to see if I can find someone who maybe can help further.

---

