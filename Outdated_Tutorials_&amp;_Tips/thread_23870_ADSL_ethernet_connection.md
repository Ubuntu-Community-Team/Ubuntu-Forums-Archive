---
title: "ADSL ethernet connection"
date: 2005-04-04
forum: Outdated Tutorials &amp; Tips
---

### Post by mila80 on 2005-04-04
Hi,
   I have a DSL-302T modem and an ADSL connection.
I can surf well if a make my connection starting up at the boot.
I have not a flat contract so I'd like to starting up my connection when I want and the same for stopping it.
How can I do it?

MArco

---

### Post by wfx on 2005-04-04
im not realy know the debian way but this must work:
take a look in "/etc/network/interfaces" there mustbe a line similary
"auto ppp0" so if you remove it the connection only start by doing on a terminal
"ifup ppp0" to start and
"ifdown ppp0" to close the conection.

Ps:
Attachment is a extremly simple script
rename it to adsl.py and make it executable "chmod +x adsl.py".
Add a starter to youre panel and call it.
Hope it work for you.

PPs: how can i use the "gnome ask pass window" (or whatever it is named"

---

### Post by mila80 on 2005-04-05
Hi wfx,
   many thanks for your help, but i havn't solve my problem: with command ifup pppO and ifdown pppO my internet connection doesn't start and stop.
How can I do now???
Marco

---

### Post by hashimoto on 2005-04-05
In terminal, to stop:
sudo ifdown eth0

to start:
sudo ifup eth0

---

### Post by mila80 on 2005-04-05
This is the error that ifdown command return

marco@ubuntu:~ $ sudo ifdown eth0
Password:
ifdown: interface eth0 not configured

what can I do???

---

### Post by wfx on 2005-04-05
it is ppp0 (not O maybe this is the mistake)
and if you dont want it at start take a look on my previous post(or does it not work?).

---

### Post by mila80 on 2005-04-05
[QUOTE=wfx]it is ppp0 (not O maybe this is the mistake)
and if you dont want it at start take a look on my previous post(or does it not work?).[/QUOTE]
I tried with ppp0 but notthing, It return the same error (ifdown: interface pppO not configured).

---

### Post by m4ng0 on 2005-04-05
To start the connection:
sudo pon dsl-provider
and to stop it:
sudo poff dsl-provider

Hope this helps.

---

### Post by kadissie on 2005-04-06
[QUOTE=mila80]I tried with ppp0 but notthing, It return the same error (ifdown: interface pppO not configured).[/QUOTE]
 You can always find out what interfaces *are* configured by issuing the command "ifconfig", which describes the interfaces which are up, or "ifconfig -a" to see what's available.  I'm not entirely sure about the pppconfig and pon/poff arrangements for setting up interfaces (which strikes me as being inelegant and not Sys-V compliant), but there's also the "plog" command to tell you what's up with Point-to-Point connections.

---

### Post by mila80 on 2005-04-07
[QUOTE=m4ng0]To start the connection:
sudo pon dsl-provider
and to stop it:
sudo poff dsl-provider

Hope this helps.[/QUOTE]


Hi,
   I tryed with pon and poff, they works only if I switch on my modem before the booting of the system. So The connection starts automatically and I can stop it with poff dsl-provider and restart it with pon dsl-provider.
What can I do to make my modem works if I switch it on after the system's boot???
Marco

---

### Post by m4ng0 on 2005-04-07
[QUOTE=mila80]I tryed with pon and poff, they works only if I switch on my modem before the booting of the system. So The connection starts automatically and I can stop it with poff dsl-provider and restart it with pon dsl-provider.
What can I do to make my modem works if I switch it on after the system's boot???
[/QUOTE]

Probably you chose to start the connection at boot time (pppoeconf asks if you want this or not). If you don't want the connection to start at boot time automatically, you can just remove /etc/ppp/ppp_on_boot. After removing this file you can connect whenever you want with pon dsl-provider and stop the connection with poff dsl-provider.

---

### Post by mila80 on 2005-04-08
Hi,
   many thanks for your help, NOW it works very well!!!
Have a Good day, 
MArco

---

