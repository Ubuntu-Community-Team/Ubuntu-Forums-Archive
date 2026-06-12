---
title: "windows"
date: 2008-06-05
forum: New to Ubuntu
---

### Post by ja660k on 2008-06-05
hey guys, 
i have a seporate partition for windows ... which i hardly use.. only for gaming

is there any way i can open up windows thru ubuntu?
like an app like parrallels for mac...?

can anyone point me in the right direction?

---

### Post by abn91c on 2008-06-05
installing Wine will let you run some windows programs, not sure if you can run all windows games

---

### Post by Sef on 2008-06-05
You are talking of a [virtualbox]("https://help.ubuntu.com/community/VirtualBox").  


What games are you talking about?

---

### Post by ja660k on 2008-06-05
steam games... i only have cs1.6... it annoys me booting into windows whenever i want to play it...

its basically the only time i need to use windows

its XP SP2 if that helps....

---

### Post by chrisdugdale on 2008-06-05
Wine lets you open and run Windows programs. Playonlinux lets you install them without having Windows on your computer, it works with Wine. You get them by searching in:
System>Administration>Synaptic Package Manager. Just click the checkbox and then the Apply button and they'll load into your pc and appear on the Applications menu. Vmware lets you startup on Ubuntu and then run windows inside the Ubuntu linux system.

---

### Post by ja660k on 2008-06-05
yeah, the respos couldnt find playonlinux, 

virtualbox sounds like what i need

---

### Post by ja660k on 2008-06-05
and im gonna need some help with it... im truing to set it up and its looking for a virtual version, but i have a partition with XP on it and it doesnt seem to recognize it

---

### Post by Paqman on 2008-06-05
Virtualbox (or any other virtualisation software eg: parallels) is not a good option for gaming. Virtual machines are slow and don't support 3D graphics acceleration.

The best option for playing Windows games is to boot into Windows i'm afraid. Wine is an option for some games, [including Counterstrike](http://appdb.winehq.org/objectManager.php?sClass=version&iId=3731) but performance can be patchy and installation can be a gigantic headache.

---

### Post by ja660k on 2008-06-05
dam, allright ill look into it but thanks alot.... dam windows

---

### Post by hyper_ch on 2008-06-05
or you could use vmware.

I personally think networking and usb device support is better in vmware... however virtualbox is lighter on system resources and seamless mode is also nice.

---

