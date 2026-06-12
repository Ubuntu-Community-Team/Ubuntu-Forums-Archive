---
title: "Simple Temperature Monitor Instructions"
date: 2011-10-09
forum: New to Ubuntu
---

### Post by snerd on 2011-10-09
I've seen many posts on how to install a CPU temperature monitoring app, but they all seem to be different or too geeky to understand. I want a simple application for monitoring my CPU temperature, that's all! And I need it explained SIMPLY! I fold a lot of CPU-intensive work units for folding@home and I need to position my room fan for maximum cooling. This was easy in Win7 but not so easy in Ubuntu.

Thanks!

---

### Post by Smilax on 2011-10-09
conky!!

---

### Post by oldsoundguy on 2011-10-09
Gnome sensors applet.  Works for me.

---

### Post by Winelord on 2011-10-10
> **oldsoundguy said:**
> Gnome sensors applet.  Works for me.

Open Ubuntu Software Centre, search for sensors-applet and install it.

Right-click on your desktop's top panel - select Add To Panel and select Hardware Sensors Monitor.

---

### Post by snerd on 2011-10-10
> **Winelord said:**
> Open Ubuntu Software Centre, search for sensors-applet and install it.

Right-click on your desktop's top panel - select Add To Panel and select Hardware Sensors Monitor.

Thanks. Installed, but right-clicking on top panel does nothing. It's always something!

---

### Post by popper668 on 2011-10-10
> **snerd said:**
> Thanks. Installed, but right-clicking on top panel does nothing. It's always something!
same here

---

### Post by audiomick on 2011-10-10
According to your user profile, you are using 11.04. The "right click on the panel" doesn't work on the unity desktop. Unfortunately, I did not get as far as finding out what does. I had a quick look for temperature monitors just the other day, as it happens.

I found this just now, and went through it, but it also ends up with wanting to install something to the panel.
[https://help.ubuntu.com/community/SensorInstallHowto](https://help.ubuntu.com/community/SensorInstallHowto)

It looks like conky might be a solution, but I can't see at first glance how to make it behave usefully. I have installed it from synaptic and started it from a terminal with the command
```
conky
```, having installed and started the sensors in the link above.
Conky starts, and stays there after closing the terminal, but is partially obscured by the panel on the left of the desktop. I am afraid I don't really have time right now to fiddle with it. 
I know from having read several threads on the subject that it is just a matter of making the appropriate changes to the conky config file, but have never learnt how to do this.

Here are some links.

The last posts of this thread are from today, and refer to the unity desktop
[http://ubuntuforums.org/showthread.php?t=281865](http://ubuntuforums.org/showthread.php?t=281865)

Conky man page
[http://conky.sourceforge.net/docs.html](http://conky.sourceforge.net/docs.html)
Conky home page at sourceforge
[http://conky.sourceforge.net/](http://conky.sourceforge.net/)
Conky Wiki
[http://wiki.conky.be/index.php?title=Conky_Wiki](http://wiki.conky.be/index.php?title=Conky_Wiki)

---

### Post by Winelord on 2011-10-10
Hi, my advice (as Mick points out) is only good up to version 10.04. You could try [PSensor]("http://ubuntuguide.net/monitor-cpunvdia-gpushard-disk-temperature-in-ubuntu-using-psensor"). I've always found Conky tricky to set up properly.

---

### Post by grahammechanical on 2011-10-10
I use xsensors in both 11.04 and 11.10. Gui based showing real-time CPU and Motherboard temps as well as CPU fan speed and three chassis fan speeds + power fan speed and motherboard voltages.

It is in the software centre and installs as into the Launcher.

Regards.

---

