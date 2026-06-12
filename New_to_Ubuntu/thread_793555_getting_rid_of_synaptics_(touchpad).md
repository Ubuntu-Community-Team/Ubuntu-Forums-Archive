---
title: "getting rid of synaptics (touchpad)"
date: 2008-05-13
forum: New to Ubuntu
---

### Post by fontenot_1031 on 2008-05-13
Before I had to reconfig xorg after a kinit problem I had xorg loading SHMConfig under synaptics and loading dbe under modules so conky doesn't flicker.  Now when I went back to my xorg.conf file both of those are gone.  In fact everytime I reboot xorg.conf returns to its default state.  I need to have SHMConfig loaded so that I can disable the touchpad, the most annoying thing on my laptop.

Anyway, so if I ever want to write a bash script that executes
```
synclient TouchpadOff=1
``` on boot I will need to figure out how to get xorg.conf to stop reverting to its original setup.

Any ideas to get rid of synaptics?  I've been using [http://ubuntu.wordpress.com/2006/03/24/disable-synaptics-touchpad/](http://ubuntu.wordpress.com/2006/03/24/disable-synaptics-touchpad/) as a guide to turn of synaptics.

---

### Post by Inxsible on 2008-05-13
> **fontenot_1031 said:**
> Before I had to reconfig xorg after a kinit problem I had xorg loading SHMConfig under synaptics and loading dbe under modules so conky doesn't flicker.  Now when I went back to my xorg.conf file both of those are gone.  In fact everytime I reboot xorg.conf returns to its default state.  I need to have SHMConfig loaded so that I can disable the touchpad, the most annoying thing on my laptop.

Anyway, so if I ever want to write a bash script that executes
```
synclient TouchpadOff=1
``` on boot I will need to figure out how to get xorg.conf to stop reverting to its original setup.

Any ideas to get rid of synaptics?  I've been using [http://ubuntu.wordpress.com/2006/03/24/disable-synaptics-touchpad/](http://ubuntu.wordpress.com/2006/03/24/disable-synaptics-touchpad/) as a guide to turn of synaptics.

When you make the change in xorg.conf, are you using root privs and then saving the file?
```
gksudo gedit /etc/X11/xorg.conf
```Make the change and then save and close the file. Then see if the changes remain on the next boot.

Luckily, I have a button on my touchpad which I always keep it at off  :D

---

### Post by fontenot_1031 on 2008-05-13
> **Inxsible said:**
> When you make the change in xorg.conf, are you using root privs and then saving the file?
```
gksudo gedit /etc/X11/xorg.conf
```Make the change and then save and close the file. Then see if the changes remain on the next boot.

Luckily, I have a button on my touchpad which I always keep it at off  :D

I've been using ```
sudo nano /etc/X11/xorg.conf
``` to edit xorg.conf.  Actually when I type gksudo gedit /etc/X11/xorg.conf I have to wait forever for gedit to load (when I click on a text document it loads gedit immediantly).

---

### Post by Inxsible on 2008-05-13
> **fontenot_1031 said:**
> I've been using ```
sudo nano /etc/X11/xorg.conf
``` to edit xorg.conf.  Actually when I type gksudo gedit /etc/X11/xorg.conf I have to wait forever for gedit to load (when I click on a text document it loads gedit immediantly).Well as long as you are using root privs on it and then SAVING the file before closing it, it should work. I don't remember the shortcut to save in nano.

---

### Post by Thanoulis on 2008-05-14
Did you try to disable Touchpad from your BIOS settings?

---

