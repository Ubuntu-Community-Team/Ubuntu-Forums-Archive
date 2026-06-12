---
title: "[SOLVED] Samba Error Message"
date: 2008-08-22
forum: New to Ubuntu
---

### Post by getitright on 2008-08-22
After entering password in order to access Samba Settings the error message:-

"Some lines  couldn't be understood while reading the configuration file /etc/samba/smb.conf. These maybe unknown configuration directives for Samba plugins but could also be configuration errors." 

Not very helpful.

Clicking on details I get the message:-

"49: enable spoolss=yes"

After clicking OK I get the settings box.

I have Samba on two other machines and do not get these sequence of events.

Can anyone help me please?

---

### Post by tuxulin on 2008-08-22
maybe the samba "smb.conf" file was incorrectly edited
can you post the file here or recheck that file.

Tuxulin

edit
comment out the line "49: enable spoolss=yes" if its in the smb.conf file

---

### Post by getitright on 2008-08-22
Thanks Tuxulin. How do I do this?

---

### Post by Gannon8 on 2008-08-22
In a terminal (Accessories > Terminal) do:
```
gksudo gedit /etc/samba/smb.conf
```
This will allow you to edit the file.

---

### Post by dentaku65 on 2008-08-22
You can see this HowTo posted by me :-)
[http://ubuntuforums.org/showthread.php?t=890867&highlight=samba](http://ubuntuforums.org/showthread.php?t=890867&highlight=samba)
Plese post your questions there if any.

---

### Post by linux6994 on 2008-08-22
Samba made easy:

install system-config-samba via Synaptic
then go to System > Admin > Samba

---

### Post by getitright on 2008-08-22
This is the file printout. "49: enable spoolss=yes" does not appear to be there.



[global]
	netbios name = Samba24
	server string = 
	workgroup = ray
	security = user
	hosts allow = 127. 192.168.0.
	interfaces = 127.0.0.1/8 192.168.0.0/24
	remote announce = 192.168.0.255
	remote browse sync = 192.168.0.255
	printcap name = /etc/printcap
;	load printers = yes
	cups options = raw
;	printing = cups
;	guest account = nobody
	log file = /var/log/samba/samba.log
	max log size = 1000
;	null passwords = no
	username level = 8
	password level = 8
;	encrypt passwords = yes
	unix password sync = yes
	socket options = TCP_NODELAY SO_RCVBUF=8192 SO_SNDBUF=8192
	local master = no
	domain master = no
	preferred master = no
;	domain logons = no
	os level = 33
	logon drive = m:
	logon home = \\%L\homes\%u
	logon path = \\%L\profiles\%u
	logon script = %G.bat
;	time server = no
	name resolve order = wins lmhosts bcast
;	wins support = no
	wins server = 
;	wins proxy = no
	dns proxy = no
;	preserve case = yes
;	short preserve case = yes
	client use spnego = no
	client signing = no
	client schannel = no
;	server signing = no
	server schannel = no
;	nt pipe support = yes
;	nt status support = yes
	allow trusted domains = no
	obey pam restrictions = yes
	enable spoolss = yes
;	client plaintext auth = no
;	disable netbios = no
	follow symlinks = no
	update encrypted = yes
;	pam password change = no
	passwd chat timeout = 120
;	hostname lookups = no
;	smb passwd file = /etc/samba/smbpasswd
	passwd program = /usr/bin/passwd '%u'
	passwd chat = *New*password* %n\n *ReType*new*password* %n\n *passwd*changed*\n
	add user script = /usr/sbin/useradd -d /dev/null -c 'Samba User Account' -s /dev/null '%u'
	add user to group script = /usr/sbin/useradd -d /dev/null -c 'Samba User Account' -s /dev/null -g '%g' '%u'
	add group script = /usr/sbin/groupadd '%g'
	delete user script = /usr/sbin/userdel '%u'
	delete user from group script = /usr/sbin/userdel '%u' '%g'
	delete group script = /usr/sbin/groupdel '%g'
	add machine script = /usr/sbin/useradd -d /dev/null -g sambamachines -c 'Samba Machine Account' -s /dev/null -M '%u'
	machine password timeout = 120
	idmap uid = 16777216-33554431
	idmap gid = 16777216-33554431
	template shell = /dev/null
	winbind use default domain = yes
	winbind separator = @
	winbind cache time = 360
	winbind trusted domains only = yes
	winbind nested groups = no
	winbind nss info = no
;	winbind refresh tickets = no
;	winbind offline logon = no
;	guest ok = no
	username map = /etc/samba/smbusers

[homes]
	comment = Home Directories
	path = /home
	read only = no
;	available = yes
;	browseable = yes
;	guest ok = no
;	printable = no
	share modes = no
	locking = no

[netlogon]
	comment = Network Logon Service
	path = /home/netlogon
	read only = no
;	available = yes
;	browseable = yes
;	guest ok = no
;	printable = no
	share modes = no
	locking = no

[profiles]
	comment = User Profiles
	path = /var/samba/profiles
	read only = no
;	available = yes
	browseable = no
;	guest ok = no
;	printable = no
	locking = no
	create mode = 0600
	directory mask = 0700

[printers]
	comment = All Printers
	path = /var/spool/samba
;	browseable = yes
;	writable = No
;	guest ok = no
	printable = yes
	share modes = no
	locking = no

[pdf-documents]
	path = /home/pdf-documents
	comment = Converted PDF Documents
;	available = yes
;	browseable = yes
	writeable = yes
	guest ok = yes

[pdf-printer]
	path = /tmp
	comment = PDF Printer Service
	printable = yes
	guest ok = yes
	use client driver = yes
	printing = bsd
	print command = /usr/bin/gsambadpdf %s %u
	lpq command = 
	lprm command = 

[Shared Files]
	path = /home/ray/Shared Files
	writeable = yes
;	browseable = yes
	valid users = ray

[My Temporay Documents]
	path = /home/ray/My Temporay Documents
	writeable = yes
;	browseable = yes
	valid users = ray

[Documents]
	path = /home/ray/Documents
	writeable = yes
;	browseable = yes
	valid users = ray

---

### Post by aloshbennett on 2008-08-22
49 I believe is the line number. Look for spoolss=yes

---

### Post by cariboo on 2008-08-22
You can enable line numbering in Gedit by going to Edit-->Preferences and putting a check in the line numbering box. This will help you find line 49 a lot easier.

After you have finished edit /etc/samba/smb.conf, open a terminal and run **testparm** this will check your smb.conf file for errors.

Jim

---

### Post by getitright on 2008-08-22
linux6994, did what you suggested, still get warning message, however access to Samba Config no longer needs password.
aloshbennett,the file printout does not contain the file.
a

---

### Post by aloshbennett on 2008-08-22
> ; nt pipe support = yes
; nt status support = yes
allow trusted domains = no
obey pam restrictions = yes
**enable spoolss = yes**
; client plaintext auth = no
; disable netbios = no
follow symlinks = no
update encrypted = yes


This could be the line in question

---

### Post by getitright on 2008-08-22
Found"enable spoolss=yes",it is on line 49. Warning still appears.

---

### Post by aloshbennett on 2008-08-22
Well, if you haven't shared anything yet, you could try replacing the smb.conf with a vanilla version.

Here's my smb.conf.Its still the default one.

---

