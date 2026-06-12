---
title: "Resolution Problem"
date: 2008-11-11
forum: New to Ubuntu
---

### Post by waffleturd on 2008-11-11
I need a too change the resolution of my screen. Right now every thing is ridiculously big. I have already tried the system> preferences > screen resolution. However the maximum it would allow me to go to is 640X480.
I want it to get to about 1024X780.

I have a geforce 8000 GT if it helps. I also already have the graphic card enabled.

Help me

---

### Post by w4ett on 2008-11-11
If you don't have it installed already:

```
sudo apt-get install nvidia-settings
```

---

### Post by Willthebeeguy on 2008-11-11
I have the same problem except yesterday I had the option of going to a higher resolution with the system>preferences option.  Did the window forget it could go higher?

---

### Post by waffleturd on 2008-11-11
it wouldn't go high than 680X480

---

### Post by w4ett on 2008-11-11
Sound as if something isn't right. :(  Try and re-enable the restricted driver for your card....if it still does not work, go to Synaptic and install envyng .....uninstall the nvidia driver and then reinstall it using Envy.

---

### Post by pirattrev on 2008-11-11
go to system -> administration -> screens and graphics

---

### Post by waffleturd on 2008-11-11
i searched envy using synaptic package manager.
nothing appears

---

### Post by Willthebeeguy on 2008-11-11
It seems that "screens and graphics" isn't a part of my system>administration.  I can set high resolution on my guest user's desktop, but not on the main one.  This JUST worked!!

---

### Post by Crafty Kisses on 2008-11-11
Try booting into recovery mode from the GRUB menu and at the prompt, reconfigure your X server.
```
sudo dpkg-reconfigure -phigh xserver-xorg
sudo shutdown -r now

```

---

### Post by Willthebeeguy on 2008-11-11
With respect, Codename.  I have no idea what any of that is! :)  I've been using this system a little over a week.

---

### Post by balaknair on 2008-11-11
> **Willthebeeguy said:**
> With respect, Codename.  I have no idea what any of that is! :)  I've been using this system a little over a week.
Basically what Codename said was copy down the lines you see in the box in his post(print it out or write it down on a piece of paper

[I]sudo dpkg-reconfigure -phigh xserver-xorg
sudo shutdown -r now[/I]

Restart the system, when you get to the screen where you have to choose which OS to boot to(the GRUB menu) choose the second line(it says recovery mode). This will boot the system into a command line mode(no graphics).
When all the lines stop scrolling by, you should type in the two commands given above. It will ask for your password after each command, just type it in carefully(you won't see any ***s appear as you type it in) and press enter.
The "sudo dpkg-reconfigure -phigh xserver-xorg" command will start a window where you will be guided step by step through configuration of your graphical interface. Just stick with the defaults in most cases to be on the safe side.

The last command reboots the system in an orderly way.

---

### Post by m_l17 on 2008-11-12
Try this:

[http://ubuntuforums.org/showpost.php?p=6134272&postcount=4]("http://ubuntuforums.org/showpost.php?p=6134272&postcount=4")

---

