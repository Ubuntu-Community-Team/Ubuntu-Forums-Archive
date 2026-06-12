---
title: "Cannot create a link to a samba share on Windows 10 desktop"
date: 2018-10-17
forum: New to Ubuntu
---

### Post by mwoosley on 2018-10-17
Good morning everyone.  I have a problem that I cannot find an answer to.  I have a couple servers, both running inside VirtualBox, and on different machines.  16.04 is being hosted by a Windows10 desktop machine and the 18.04 version is hosted by a laptop with Windows10.  On the 16.04 version I created a couple Samba shares and linked to them from my Windows desktop.  On the 18.04 version, I am trying the same, although unsucessful.  To the best of knowledge, Samba is setup correctly... when I enter the command 'smbclient -L localhost', I get the response that the sharename of what I created in the /etc/samba/smb.conf file is configured (maybe not correctly, but the same as the one on 16.04 and working). 

I also installed Apache, mySQL and PHP, and phpMyAdmin on both machines, not to mention Samba.

When I attempt to create my shortcut, \\192.168.1.204\fileshare, on the desktop, I get the error 'the file \\192.168.1.204\fileshare cannot be found'

Could I get one of you to suggest what I might be doing wrong with this newer version?  Like I said previously, I have a Windows desktop link to the 16.04 working on the desktop PC.  I got a feeling the problem lies somewhere with the smb.conf file, but from what I have seen posted, I cannot see the problem, if it is in fact THE problem.

My share as found in /etc/samba/smb.conf

[fileshare]
	comment = home share
	path = /home/mike
	hide dot files = no
	delete readonly = no
	available = yes
	valid users = mike,@mike
	writeable = yes
	create mode = 777
	directory mode = 777
	force create mode = 777
	create mode = 777

Thanks a million for any potential help you can throw my way.

Best,
Mike

---

### Post by TheFu on 2018-10-17
NAT or bridged networking on both virtualbox setups?

BTW, 18.04 samba has different defaults than all prior versions.  There are many threads here about the global settings necessary to make them work.  Also, Win10 changed the required CIFS protocol necessary, so check that too.

---

### Post by sp40140 on 2018-10-17
You can run "testparm" command (its part of samba). It checks for the potential config issues.
Can you access shares from any other computers? win10, win7, linux?
Have you tried to just browse for the samba share from file explorer (nautilus in ubuntu)?

---

