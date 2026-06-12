---
title: "Remote accessing a Windows XP box from Ubuntu"
date: 2008-05-05
forum: New to Ubuntu
---

### Post by Igniteflow on 2008-05-05
My parents often have trouble with their Windows XP PC desktop and as I'm living abroad I often end up telling them how to fix their problems over the phone.  Does anyone know of a free/open source program I can use to remotely operate their computer with their consent?  I used to have one through XP on my computer, but I've got a Linux only setup now.  
Any suggestions would be hugely appreciated.

---

### Post by hyper_ch on 2008-05-05
Realvnc on the xp machine... lots of stuff for Linux... I normally use krdc/krfb

however realvnc does not, in the free version, support encrypted transmission and you will also have to set according port-forwarding.

---

### Post by Dani Filth on 2008-05-05
I think this may work :
1. Ask your parents to install some dynamic IP stuffs like dyndns.org and have it updated & running on Windows.
2. They should have an account at dyndns, for example : family.dyndns.org
3. Try : "rdesktop -0 family.dyndns.org"

In fact, I use this many times in LAN with the LAN IP replace the part "family.dyndns.org". I have never tried outside the LAN, though. I just heard that my colleague is able to access his working PC from home by using this way.

Hope this help.:popcorn:

---

### Post by mlentink on 2008-05-05
I use [Hamachi]("https://secure.logmein.com/products/hamachi/list.asp") and vnc to do exactly what you want to do. You don't have to install VNC on your Ubuntu box, it's already there. On the Windows side, I use [UltraVNC]("http://www.uvnc.com/download/index.html")

---

### Post by Maybe_Factor on 2008-05-05
I use Tight VNC on all my windows boxes and use ubuntu's remote desktop viewer to access them.....not sure about running over the internet though

---

### Post by lazyart on 2008-05-05
I use logmein.com.  It will require you to install an app on their machine, and an account.  But thereafter you can go to logmein.com, select their machine, enter the account password and view/take over their desktop.

---

### Post by MockY on 2008-05-06
VNC is (mark my words) HORRIBLE in terms of performance. It pales in comparison to RDP (something I wish wasn't true) and since you are trying to connect to a XP machine, there is absolutely no reason why you should use VNC. Like Dani Filth mentioned, use rdesktop when connecting to the machine.

I usually create a launcher on the desktop that I simply can double click on:

```
rdesktop -0 ip-number -u user -g 1280x973 -p password
```
-0 flag being you are logging in to the console session. The rest should be pretty self explanatory, just replace the placeholder.

---

