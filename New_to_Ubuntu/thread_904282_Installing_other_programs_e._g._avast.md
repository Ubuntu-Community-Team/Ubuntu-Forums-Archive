---
title: "Installing other programs e. g. avast"
date: 2008-08-29
forum: New to Ubuntu
---

### Post by soren thomsen on 2008-08-29
Installing programs with Add/Remove is quite easy, but I want to be able to install other programs as well. Right now avast.

On my PC I have installed Ubuntu 8.04.1 Desktop i386 and now I wish to install avast.
From avsat's homepage I have downloaded avast4workstation_1.0.8-2_i386.deb to my Desktop.

How to install?

I have tried
*  Applications > Add/Remove but the system don't find the file.
*  System > Synaptic Package Manager don't fin the file nether.
*  In System > Software Sources > Third-Party Software I have tried to add the Internet address to avast with and without deb in front(deb [http://www.avast.com/eng/download-avast-for-linux-edition.html](http://www.avast.com/eng/download-avast-for-linux-edition.html) and [http://www.avast.com/eng/download-avast-for-linux-edition.html](http://www.avast.com/eng/download-avast-for-linux-edition.html)), and I have tried the same the same with the pass to the Desktop, but +Add Source remains gray and without effect.

What to do

---

### Post by mlentink on 2008-08-29
Try double clicking the .deb file...

---

### Post by ffmpegfailure on 2008-08-29
Or right clicking and installing with Gdebi package installer

---

### Post by Nepherte on 2008-08-29
It is a good reflex to go to the synaptic package manager, but sometimes the solution is a lot easier than you think :)

---

### Post by renzokuken on 2008-08-29
or from the command line (making sure you have cd'd to the folder conatining the avast deb)

```
sudo dpkg -i avast4workstation_1.0.8-2_i386.deb
```

---

### Post by SunnyRabbiera on 2008-08-29
you mean avast antivirus?
you typically dont need antivirus in ubuntu.

---

### Post by freesitebuilder on 2008-08-29
You can read about virus protection (or why you don't need it) here:
[http://www.whylinuxisbetter.net/](http://www.whylinuxisbetter.net/)

---

### Post by soren thomsen on 2008-08-29
Thank you all of you

You hare convinced me that antivirus is no problem in Linux, so I won’t solve a problem I haven’t got. Instead I will benefit of a faster PC.

---

### Post by mlentink on 2008-08-29
> **soren thomsen said:**
> Thank you all of you


varsogod

---

