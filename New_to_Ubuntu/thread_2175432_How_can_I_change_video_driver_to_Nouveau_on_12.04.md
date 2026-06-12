---
title: "How can I change video driver to Nouveau on 12.04"
date: 2013-09-19
forum: New to Ubuntu
---

### Post by GrouchyGaijin on 2013-09-19
A few weeks ago I reinstalled my system and after that I noticed that sometimes when I open nautilus the window flashes a sick blue for a short time.
Additionally, at times when I am reading a PDF or even a text file, the text becomes blurry and I need to select all to get it to refocus.

I *think *this may be a problem with the video driver or maybe my system is old and nearing death, I don't know.  I hope it is the former, but could also be something else.

I was thinking it may be a good idea to try the Nouvaeu drivers.  The problem is the last time I tried to switch drivers, from one Nvidia to another Nvidea, I was not able to boot my system.  Well, it may have booted, but all I saw was a black screen with no way to input anything.



[IMG]http://screencloud.net/img/screenshots/e6ccf43563a0b5920a0320e70cb436e7.png[/IMG]

In the above screenshot  you can see that currently I am using the version labeled post release updates version 173-updates.
The version 319 driver (recommended) is the one that resulted in the black screen.

My questions are:

1. Do the symptoms I am describing sound like they are video driver related?
2. What is the recommended way of removing Nvidia and using Nouvaeu?

---

### Post by GrouchyGaijin on 2013-09-19
**[COLOR="#FF0000"]UPDATE[/COLOR]**

[COLOR="#000000"]I poked about on the forums and found another guy with the same blue window problem.  He wrote that when he changed to the 304 Nvidia driver, his problems ended.

So holding my breath, I chose to download and activate that driver.

So far so good.  If I don't have anymore problems in a couple of days, I'll mark this thread as solved.[/COLOR]

---

### Post by deadflowr on 2013-09-19
FYI, since this thread seems to have been originally about getting the nouveau driver installed, you should already have the nouveau driver.
Unless you purposely removed the nouveau driver, when you installed the nvidia driver the nouveau driver was merely blacklisted.(There should be a folder or file in /etc/modprobe.d for nvidia)
Removing the nvidia driver(best to use the additional drivers program) will revert the system to nouveau.
Sometimes it is needed to remove the /etc/X11/xorg.conf file as well.

But anyway, best of luck with the 304 driver.

---

### Post by Frogs Hair on 2013-09-19
The 173 driver is for older cards and If you have options to use a newer driver including Nouveau I would try it out . As stated it looks like Nouveau is black listed.

---

