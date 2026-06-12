---
title: "do i need an antivirus?"
date: 2010-05-30
forum: Recurring Discussions
---

### Post by abhot on 2010-05-30
I have a dual boot of windows 7 & ubuntu 10.04......
i was wandering do i need an antivirus in ubutntu.......
if yes,please suggest some.........
by the way i don't use wine........:guitar:

---

### Post by TeoBigusGeekus on 2010-05-30
No.

---

### Post by etdsbastar on 2010-05-30
Hey friend,

Dont mind but still you are in confusion, Ubuntu is not affected with viruses, if you again want to install one and please install clamav from synaptic.

You can also protect your pc from external access by firewall. Try using these commands:

$ sudo ufw allow from 192.168.0.0/16

Type you password (asked only once) and press enter then type:

$ sudo ufw default DENY

$ sudo ufw enable

if you want firewall logs to be enabled then please type.

$ sudo ufw logging enable

hope this helps to you...

---

### Post by geirha on 2010-05-30
Some information on the «No.»:
[http://librenix.com/?inode=21](http://librenix.com/?inode=21)
[https://help.ubuntu.com/community/Antivirus](https://help.ubuntu.com/community/Antivirus)

---

### Post by etdsbastar on 2010-05-30
[QUOTE=geirha;9384649]Some information on the «No.»:
[]("http://librenix.com/?inode=21")
have you checked for the solution i gave you friend.

---

### Post by Rasa1111 on 2010-05-30
No you dont need antivirus in Ubuntu. 

But if you also use windows, or share files with other windows users~

You might want to install **clamTK**,
it is a simple virus scanner with a nice GUI (graphical user interface).

 Find it in software center or in synaptic package manager. 

 It can scan files you already have, or it can scan files before you download them. 

  but make sure you get clam**TK**.

 Also~ an easier way to use your firewall is to install UFW firewall. 

 Its just an easy way to config. and turn on and off your firewall that comes with Ubuntu~
without using the terminal.

---

### Post by abhot on 2010-05-30
ok thanks for all your replies........
those links were really helpful
i will try clamtk since i share my files with windows

---

### Post by cariboo on 2010-05-30
This question has been asked and answered many times over. Moved to Recurring

---

### Post by jerenept on 2010-05-30
> **cariboo907 said:**
> This question has been asked and answered many times over. Moved to Recurring
Yay!!!!

KlamAV ia also an excellent option, if you want an antivirus to protect the unfortunate Windows users from viruses.

---

### Post by CharlesA on 2010-05-30
> **etdsbastar said:**
> Hey friend,

Dont mind but still you are in confusion, Ubuntu is not affected with viruses, if you again want to install one and please install clamav from synaptic.

You can also protect your pc from external access by firewall. Try using these commands:

$ sudo ufw allow from **192.168.0.0/16**

Type you password (asked only once) and press enter then type:

$ sudo ufw default DENY

$ sudo ufw enable

if you want firewall logs to be enabled then please type.

$ sudo ufw logging enable

hope this helps to you...

Wrong CIDR notation, it should be /24 if you want to allow access from 192.168.x.x networks. Unless you want one subnet to be from 192.168.0.1 to 192.168.255.254.

---

### Post by etdsbastar on 2010-06-01
> **CharlesA said:**
> Wrong CIDR notation, it should be /24 if you want to allow access from 192.168.x.x networks. Unless you want one subnet to be from 192.168.0.1 to 192.168.255.254.

Thanks for telling me the mistake i have done.

---

### Post by KegHead on 2010-06-01
Hi!

I use Clam out of a bad habit from using dos and windows.

KegHead

---

### Post by etdsbastar on 2010-06-17
> **KegHead said:**
> Hi!

I use Clam out of a bad habit from using dos and windows.

KegHead

have you ever searched for other AVs for linux/ubuntu.

---

