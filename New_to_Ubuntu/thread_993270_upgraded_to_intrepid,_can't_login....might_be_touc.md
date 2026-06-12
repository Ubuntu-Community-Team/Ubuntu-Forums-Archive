---
title: "upgraded to intrepid, can't login....might be touchpad or mouse config"
date: 2008-11-25
forum: New to Ubuntu
---

### Post by mdsmedia on 2008-11-25
I upgraded through update manager, to Intrepid, from Hardy. When I rebooted I came to the login screen to put in my username and password and I couldn't input my username.

I'm guessing it was simply that my mouse and touchpad weren't recognised, because ctrl-alt-del was recognised, but I wasn't able to click in the username field. The mouse cursor didn't move using either the touchpad or the mouse.

I'm using a HP Compaq nx6120 with synaptics touchpad and Logitech USB wireless mouse.

With earlier releases, Hoary through Hardy, this has not been a problem. It's all just worked.

---

### Post by Titan8990 on 2008-11-25
Use the following command from the recovery console:


dpkg-reconfigure xserver-xorg


Accept all the defaults as they should be preset. When you get asked about the mouse I always choose /dev/input/mice (the choice at the top) for my touchpads and it works fine.

---

### Post by mdsmedia on 2008-11-25
thanks, will reboot and try that, come back and let you know :)

---

### Post by mdsmedia on 2008-11-25
I'm not sure what you mean by "recovery console" but I entered Recovery Mode in GRUB, eventually did ctrl-alt-f2 to get into CLI.

I entered your command and accepted the defaults for the keyboard and it threw me back to the prompt without any mouse config options.

---

### Post by mdsmedia on 2008-11-25
bump

---

### Post by mdsmedia on 2008-11-25
I refuse to believe that Windows is the answer but at the moment I can't login to Linux.

I've been using Ubuntu for just over 3 years and never had a problem. This seems like a simple thing to fix, but I just don't know how.

I love Linux, and Ubuntu, and can't accept that this is simply un-fixable.

---

