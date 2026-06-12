---
title: "Android and Samba Share"
date: 2012-12-20
forum: New to Ubuntu
---

### Post by strickja on 2012-12-20
I am new, trying to do something with lubuntu I can do with windows; simply browse my shares on lubuntu 12.10 install with ES File Exp or Astro File Manager on my tablet

Fresh install of lubuntu 12.10, can browse windows shares, but windows doesn't see my lubuntu share.  Same with tablet, can browse windows 7 shares, but scan and manual config don't see linux share. 

have been through dozen samba troubleshooting guides, no progress. 

Ping visibility is there for all devices, all on same network, windows and android devices see each other, linux box sees windows boxes with smb:///ipaddress.  Windows //ipaddress returns message that device won't accept connection.  Android devices list several errors, but the are meaningless (wifi on, same network, etc.)

two linux boxes on same network, from same install disc, don't see each other's shares;   thus, its gotta be something with my linux install of samba;   I don't know what info to give to help other than ping level confirmation 

any fresh ideas / directions appreciated.

---

### Post by strickja on 2012-12-20
if this helps 

strickja@strickja-TOSHIBA-NB305:~$ testparm -s
Load smb config files from /etc/samba/smb.conf
rlimit_max: increasing rlimit_max (1024) to minimum Windows limit (16384)
WARNING: The "null passwords" option is deprecated
WARNING: The "password level" option is deprecated
Unknown parameter encountered: "update encrypted"
Ignoring unknown parameter "update encrypted"
WARNING: The "idmap uid" option is deprecated
WARNING: The "idmap gid" option is deprecated
Unknown parameter encountered: "winbind offclient lanman auth"
Ignoring unknown parameter "winbind offclient lanman auth"
Unknown parameter encountered: "line logon"
Ignoring unknown parameter "line logon"
Unknown parameter encountered: "server role"
Ignoring unknown parameter "server role"
Processing section "[homes]"
Processing section "[netlogon]"
Processing section "[profiles]"
Processing section "[printers]"
Processing section "[pdf-documents]"
Processing section "[pdf-printer]"
Processing section "[sysvol]"
Loaded services file OK.
WARNING: You have some share names that are longer than 12 characters.
These may not be accessible to some older clients.
(Eg. Windows9x, WindowsMe, and smbclient prior to Samba 3.0.)
Server role: ROLE_STANDALONE
[global]
	realm = LOCALDOMAIN
	netbios name = STRICKJA-NB305
	server string = Samba file and print server
	interfaces = 127.0.0.1/8, 192.168.0.0/24
	bind interfaces only = Yes
	client schannel = No
	server schannel = No
	allow trusted domains = No
	obey pam restrictions = Yes
	guest account = smbguest
	passwd program = /usr/bin/passwd '%u'
	passwd chat = *New*password* %n\n *ReType*new*password* %n\n *passwd*changed*\n
	passwd chat timeout = 120
	username map = /etc/samba/smbusers
	password level = 6
	username level = 6
	unix password sync = Yes
	client NTLMv2 auth = No
	log file = /var/log/samba/samba.log
	max log size = 1000
	name resolve order = wins lmhosts bcast
	client signing = No
	client use spnego = No
	socket options = TCP_NODELAY SO_RCVBUF=8192 SO_SNDBUF=8192
	printcap name = cups
	machine password timeout = 120
	add user script = /usr/sbin/useradd -d /dev/null -c 'Samba User Account' -s /dev/null '%u'
	delete user script = /usr/sbin/userdel '%u'
	add group script = /usr/sbin/groupadd '%g'
	delete group script = /usr/sbin/groupdel '%g'
	add user to group script = /usr/sbin/useradd -d /dev/null -c 'Samba User Account' -s /dev/null -g '%g' '%u'
	delete user from group script = /usr/sbin/userdel '%u' '%g'
	add machine script = /usr/sbin/useradd -d /dev/null -g sambamachines -c 'Samba Machine Account' -s /dev/null -M '%u'
	logon script = %G.bat
	logon path = \\%L\profiles\%u
	logon drive = m:
	logon home = \\%L\homes\%u
	os level = 33
	local master = No
	domain master = No
	dns proxy = No
	wins support = Yes
	remote announce = 192.168.0.255
	remote browse sync = 192.168.0.255
	template shell = /dev/null
	winbind separator = @
	winbind cache time = 360
	winbind use default domain = Yes
	winbind trusted domains only = Yes
	winbind nested groups = No
	winbind nss info = no
	idmap config * : range = 16777216-33554431
	idmap config * : backend = tdb
	hosts allow = 127., 192.168.0.
	cups options = raw
	follow symlinks = No

[homes]
	comment = Home Directories
	path = /home
	valid users = %U
	read only = No
	locking = No
	strict locking = No

[netlogon]
	comment = Network Logon Service
	path = /var/lib/samba/netlogon
	locking = No
	strict locking = No

[profiles]
	comment = User Profiles
	path = /var/lib/samba/profiles
	read only = No
	create mask = 0600
	directory mask = 0700
	locking = No
	strict locking = No

[printers]
	comment = All Printers
	path = /var/spool/samba
	printable = Yes
	print ok = Yes
	browseable = No
	locking = No
	strict locking = No

[pdf-documents]
	comment = Converted PDF Documents
	path = /var/lib/samba/pdf-documents
	admin users = %U
	read only = No
	guest ok = Yes
	locking = No
	strict locking = No

[pdf-printer]
	comment = PDF Printer Service
	path = /tmp
	guest ok = Yes
	printable = Yes
	print ok = Yes
	printing = bsd
	print command = /usr/bin/gadmin-samba-pdf %s %u
	lpq command = 
	use client driver = Yes

[sysvol]
	path = /var/lib/samba/sysvol
	read only = No
strickja@strickja-TOSHIBA-NB305:~$ 
strickja@strickja-TOSHIBA-NB305:~$ sudo service smbd restart
[sudo] password for strickja: 
smbd stop/waiting
smbd start/running, process 4803

---

### Post by dannyboy79 on 2012-12-20
shorten up your netbios name and share names to less then 12 character and also try changing this line
```
name resolve order = wins lmhosts bcast
```
to this
```
name resolve order = lmhosts bcast wins host
```

also, your /etc/nsswitch.conf file, have it read like this
```
hosts: files dns wins
```

---

### Post by strickja on 2012-12-20
thank you will try;  just fyi - i did an install an another box, with amd64 distro, and all the sudden its showing up on my tablet, and i haven't even configured a share;  would copying that smb.conf file from one machine to another be a viable troubleshooting step ?  am going to try edits now will post  thanks

---

### Post by strickja on 2012-12-20
made changes, restarted services, no change in behavior - it feels like the samba service isn't visible to the network , is there a way to check that other than connecting from another computer ?  sorry for simple questions, is frustrating to be so versed in networking windows computers and struggle with something simple like this in a new OS

---

### Post by dannyboy79 on 2012-12-20
yes, you could copy smb.conf between computers just change the netbios name. and obviously the correct share names.

---

### Post by strickja on 2012-12-20
copying the .conf file worked, it now shows up on my tablet; odd thing is, I didn't edit anything (yet) ; just the straight example samba file from a current 12.10 lubuntu amd64 dist.  Anyway, progress , not solved, and thanks for the assistance

---

