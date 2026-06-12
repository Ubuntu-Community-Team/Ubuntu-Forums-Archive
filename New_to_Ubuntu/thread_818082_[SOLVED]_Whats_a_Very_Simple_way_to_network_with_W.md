---
title: "[SOLVED] Whats a *Very* *Simple* way to network with Windows XP?"
date: 2008-06-04
forum: New to Ubuntu
---

### Post by Nchalada on 2008-06-04
The computer that I installed Gutsy on suddenly decided last Wednesday to refuse to run Windows XP. I have no idea why this is so, but it is...


Anywho, I have a large drive with movies and tv eps and so forth that the rest of the xp puters on my network would access on a regular basis.

Now, not one of them can browse my drives...

I've been using Windows XP for about ... 6 years, and have come to know most of the quirks and so forth of said OS. 

So, as a convert (forced tho it is), I need a very simple way to get these xp computers to access my drives again.


HELP!! :o :D


Tony

---

### Post by kamaji792 on 2008-06-04
The quick answer is you need to install **samba**.

Search for info on setting samba up.

The configuaration file is: /etc/samba/smb.conf
make a copy before you modify it.

To get the samba server to re-read the configuation file:
sudo /etc/init.d/samba restart

all the best

---

### Post by ZabiGG on 2008-06-04
To avoid networking, and since you have a large disk, you could also install XP as a virtual machine inside your Ubuntu install using VirtualBox or VMWare. The big advantage of this is that you can actually clone your XP comp with files and all and use it straight away from your more secure Ubuntu system.

---

### Post by quinnten83 on 2008-06-04
There is no simple way to use your Ubuntu box as a windows share.
but try with these tutorials:
[http://www.youtube.com/watch?v=Ad17kma8rNM]("http://www.youtube.com/watch?v=Ad17kma8rNM")
[http://maddhat.com/?p=13]("http://maddhat.com/?p=13")
[http://us1.samba.org/samba/docs/SambaIntro.html]("http://us1.samba.org/samba/docs/SambaIntro.html")

---

### Post by Inxsible on 2008-06-04
You could also simply ssh into your Ubuntu box from XP. and file transfers can be done with WinSCP. I do it all the time.

Yes....i ssh within my own network as well...but even when I am away from my network..i can still access those files since i have a dydns address

---

### Post by hyper_ch on 2008-06-04
SSH is the simplest... however for large transfers it will be slower than samba...

For SSH:

(1) In your linux box
```

sudo apt-get install openssh-server

```

(2) download winscp on XP: [http://www.winscp.com](http://www.winscp.com)

(3) Run WinSCP, enter the IP of the linux box, your username on the linux box and your password on the linux box and hit "connect"

---

### Post by Nchalada on 2008-06-04
SSH is all well and good (btw, i have used winscp on my windows install to play with my SME box (running as a hardware firewall)), but as far as i know, you cannot stream with it, hence the samba working properly.

{MAJOR EDIT}

It works now :D That Maddhat.com link worked a treat.

samba.conf as of now:

```

# Samba config file created using SWAT
# from 127.0.0.1 (127.0.0.1)
# Date: 2008/06/04 23:43:53

[global]
	workgroup = OURS
	server string = %h server (Samba, Ubuntu)
	security = SHARE
	obey pam restrictions = Yes
	passdb backend = tdbsam
	passwd program = /usr/bin/passwd %u
	passwd chat = *Enter\snew\sUNIX\spassword:* %n\n *Retype\snew\sUNIX\spassword:* %n\n *passwd:*password\supdated\ssuccessfully* .
	syslog = 0
	log file = /var/log/samba/log.%m
	max log size = 1000
	dns proxy = No
	panic action = /usr/share/samba/panic-action %d
	invalid users = root
	valid users = 
	hosts allow = 
	hosts deny = 

wins support = no
[printers]
	comment = All Printers
	path = /var/spool/samba
	create mask = 0700
	printable = Yes
	browseable = No

[print$]
	comment = Printer Drivers
	path = /var/lib/samba/printers


[d]
path = /media/Archive
available = yes
browsable = yes
public = yes
writable = yes

[e]
path = /media/BugScreenz
available = yes
browsable = yes
public = yes
writable = yes

```

Finally was able to get Swat working, 
> **dberetta said:**
> 
sudo update-inetd --enable 'swat'

TY to dberetta :D
however... it seems to be a bit long winded, for a "basic" tool.

anywho...

Thanky for the helps.

Tony

---

