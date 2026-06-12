---
title: "Windows can't access Samba shares (code 0x80070035)"
date: 2012-03-28
forum: New to Ubuntu
---

### Post by peeweejd on 2012-03-28
I'm trying to set up a computer to act as a fileserver for a bunch of Windows computers.  I have Ubuntu Desktop edition 11.10 installed.  The OS is on one disk.  I  have a RAID 1 array set up to share with the network.

I can browse the network on the windows machines and see the server.  I can even open the server up to see some shared folders.  When I try to open the folder in Windows, I get the error 0x80070035 (The network path was not found).  Funny because I  obviously found it ;-)

I've googled around and found lots of people have asked for help solving this problem.  Can someone help me with this?

**testparm -s**
```

Load smb config files from /etc/samba/smb.conf
rlimit_max: increasing rlimit_max (1024) to minimum Windows limit (16384)
Processing section "[printers]"
Processing section "[shared]"
Loaded services file OK.
Server role: ROLE_STANDALONE
[global]
	server string = %h server (Samba, Ubuntu)
	security = SHARE
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
	usershare owner only = No
	panic action = /usr/share/samba/panic-action %d

[printers]
	comment = All Printers
	path = /var/spool/samba
	create mask = 0700
	printable = Yes
	browseable = No

[shared]
	comment = Shared Files
	path = /media/raid_/shared
	read only = No
	guest ok = Yes


```


**net usershare info --long**
```

[raid10]
path=/media/raid10
comment=
usershare_acl=Everyone:R,MCSERVER\yoda:F,
guest_ok=n

[shared]
path=/media/raid_/shared
comment=
usershare_acl=Everyone:F,
guest_ok=y

```

---

### Post by peeweejd on 2012-03-29
Can anyone help me with this?

Do I need to have users on Ubuntu with the same username as windows?

---

### Post by ifrisbie on 2012-10-22
I resolved my problem connecting my Windows 7 box to my Ubuntu samba (11.10).  I Had the "Windows cannot access" error (0x80070035 - the network path was not found" when trying to access the server (or share).  I tried a lot of things, but when it came down to what actually solved it (all other items reversed) it was the "Microsoft Network client: Digitally sign communications (always)" setting that was causing my problem.  Once it was disabled, I could see the shares and map the drive.

---

