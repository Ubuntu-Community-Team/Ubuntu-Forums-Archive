---
title: "Nvidia drivers"
date: 2008-08-24
forum: New to Ubuntu
---

### Post by Ogma on 2008-08-24
Hi there !

I had a new computer with a geforce gtx260 in.
I tried to install the drivers on ubuntu 8 but after several hours impossible to do it :(.

So first, does it have drivers for this graphic card ?
If yes, how do I install it ? I try using envyNG with the 173.14.12 driver from nvidia but no result (but installation succeed, it seemed).

I don't understand ! Some help ? ^^


PS : I'm french, so sorry for the faults, french forum closed ><.

---

### Post by neurostu on 2008-08-24
Is the gtx260 a new or old card? If it is an older card you are probably looking for the legacy driver?   Does EnvyNG allow for the installation of the legacy driver?

---

### Post by drs305 on 2008-08-24
Here is the nvidia page for the gtx 260 linux drivers:
[http://www.nvidia.com/object/linux_display_ia32_177.13.html]("http://www.nvidia.com/object/linux_display_ia32_177.13.html")

There are instructions on the site or you can search the forums or post back here.

Their general page for entering driver search data is here:
[http://www.nvidia.com/Download/index.aspx?lang=en-us&ptid=1&psid=52&pid=0]("http://www.nvidia.com/Download/index.aspx?lang=en-us&ptid=1&psid=52&pid=0")

---

### Post by alienexplorers on 2008-08-24
Try going into synaptic and search for envy.  Select envy-core and envy-gtk.  Let them load and then goto applications>system tools>envyng.
run envyng and choose nvidia.  If the card is a new release choose auto install.  If the card is an old release select manual install and choose the bottom choice in the driver list. Let it run through and reboot.

---

### Post by Ogma on 2008-08-25
It is a recent card, so with envyNG it doesn't work.

I will try the link of drs305.

Thank you !

---

### Post by keyboardslave on 2008-09-17
Greetings,

This goes out to all owners of a [COLOR="Red"]GTX260[/COLOR], I have got my [COLOR="Red"]ZOLTEX GTX260 OC EDN [/COLOR] working perfectly, after a few days of screwing around and reading i have sucessfully got Ubuntu Hardy to Reconise my GTX260. All my problems stemed from using incorrect drivers.
The drivers you _**NEED**_ are 177.68 (BETA).

Starting from a _fresh install_ i suggest the following.

[CENTER][COLOR="DarkGreen"][U]Download the Drivers.
[/U][/COLOR][/CENTER]

"wget ftp://download.nvidia.com/XFree86/Linux-x86_64/177.68/NVIDIA-Linux-x86_64-177.68-pkg2.run"
(x86_64 version)

"wget ftp://download.nvidia.com/XFree86/Linux-x86/177.68/NVIDIA-Linux-x86-177.68-pkg1.run"
(x86)

[CENTER][COLOR="DarkGreen"]_then follow this fantastic tutorial,_[/COLOR] [/CENTER]

([http://ubuntuforums.org/showpost.php?p=5086971&postcount=](http://ubuntuforums.org/showpost.php?p=5086971&postcount=))


Just make sure u use the 177.68 drivers and you will be amazed at how easy it is, those drivers even AUTO detected my GTX260, and set the resolution perfectly.

OS: Hardy
MOBO: 790i
CPU: 6600 Quad
GFX: GTX260

Regards,
:guitar:

---

### Post by nbayiha on 2008-09-17
Just follow this thread and you should be fixed .

[http://ubuntuforums.org/showthread.php?t=880787&highlight=install+nvidia+driver+hardy](http://ubuntuforums.org/showthread.php?t=880787&highlight=install+nvidia+driver+hardy)

---

