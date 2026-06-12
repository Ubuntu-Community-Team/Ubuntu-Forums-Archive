---
title: "Problem with VNC/GDM when inputing keyboard."
date: 2008-07-04
forum: New to Ubuntu
---

### Post by ghosterius on 2008-07-04
Hi! First post in ubuntu forums, and hope to get into this community helping instead of beeing helped. I came from gentoo into ubuntu, though i've used Debian, Arch, RedHat... well I think the only distro I've never used/tested is SuSe :P hehe... Though I'm going to start getting helped, or trying to... 

The problem is as following, I've installed vnc4server and configured the "Load vnc" in the xorg.conf as it's required, and started gdm... I can reach the server, mouse works and clicks as a happy bird in spring time, the problem is, when I click in my keyboard, the connection gets closed instantly! It's like a shortcut for Alt+F4 in my VNC client software... In the server side, no error is reported (or I'm not search it right...) and the client side only tells "Connection Closed" in the log file... witch points to a server problem! If I start the gdm without the vnc module, and then do 'x11vnc -auth /var/run/0:.Xauth -display :0' it works fine, though no resolution is applicated and it sucks... 320xsomething resolution is WAY low... hehe... Though I wanted to make it work fine only by loading the module in the X configuration and not needing of xinetd! And it seems possible.. if it was not this keyboard error and problem!

Does anyone know how I can debug this kind of problem in the server side by "listening" the vnc module "execution" in the X log? Or anything that might solve this?

Thanks in advance and hope I get some help in this! :)

---

### Post by ghosterius on 2008-07-04
*bump*

---

### Post by ghosterius on 2008-07-04
](*,) bump ](*,)

---

### Post by ghosterius on 2008-07-04
Anyone? Or no one knows how I can log the information on the server side of this problem? :( I really need some help people!

---

### Post by ghosterius on 2008-07-04
Well... going to try a few work arounds in this subject... since no one can help.

---

