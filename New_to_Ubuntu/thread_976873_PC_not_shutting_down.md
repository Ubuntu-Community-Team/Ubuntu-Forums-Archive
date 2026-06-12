---
title: "PC not shutting down"
date: 2008-11-09
forum: New to Ubuntu
---

### Post by Chapeen on 2008-11-09
I've just made a clean install of ubuntu Intrepid.When ever I restart the PC or shut it down it stops on black screen and it doesn't do anything.
Some these text shows up.
* Saving the system clock
* Stopping firewall: ufw...   [OK]
* shutting down ALSA...

and that's it nothing happens, it stays there.
Anyone can help ?

---

### Post by ferdostar on 2008-11-09
Hi, I suppose  your problem is listed [**here**]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/274995"). I'll propose you to update your system, or wait for a resolution of the problem. You can try to do ```
sudo ln -sf /etc/init.d/networking /etc/rc0.d/K40networking
``` which are going to set the computer to do ```
sudo ifdown eth1
``` when you shut it down.

---

