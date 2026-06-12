---
title: "Boot Changes after changing GPU ?Drivers."
date: 2013-09-21
forum: New to Ubuntu
---

### Post by Alduin on 2013-09-21
This is a problem I have in almost every single Linux Distros. After a clean installation and update, I go fo installing the GPU Drivers (GPU Nvidia GT 630 DDR5) usually i go for the latest drivers 319 or 313 . After installing the driver the boot changes compleatly and doesnt have that kewl look of the first times.
The boot becomes simple and changes first the resolution to 640x480 i mostly go for 1024x768x32 but i havent figured out how to restore the first boot look...

---

### Post by grahammechanical on 2013-09-21
I do not understand. Is this a spelling mistake? "[COLOR=#000000]kewl"  The Grub boot menu appears before any video driver is activated. It is only after the Linux kernel begins to load that video driver modules are loaded. Most of the boot process should be covered by a splash screen. First it is the background image behind the Grub boot menu (usually purple). Then it is the Plymouth splash screen (purple with the four or five dots).

There is not much to change between the look when using the install video driver (Nouveau) and the look when booting with a proprietary video driver. Any text that appears on the screen becomes finer. I do not see much else different.

Regards.[/COLOR]

---

### Post by The Cog on 2013-09-21
Like Alduin, I find that the appearance while booting changes dramatically after installing the proprietary nvidia drivers. No splash screen, and a truly horrible low-resolution (800x600?) font in the console. 

I eventually found that adding this line to /etc/default/grub:
```
GRUB_GFXPAYLOAD_LINUX=1920x1200
```
and then running this command:
```
sudo update grub
```
pretty-much fixed the console font. It's not quite as good as the font that Nouveau gives, but it's OK.

I live without the early splash screen while booting.

---

### Post by Paqman on 2013-09-22
It's just an unfortunate consequence of installing the proprietary Nvidia drivers. If you don't do a lot of gaming on the machine and need top-notch 3D performance you might find switching back to the open source Nouveau driver is good enough for you.

---

### Post by stinkeye on 2013-09-22
[_[COLOR="#B22222"]THIS GUIDE[/COLOR]_]("http://news.softpedia.com/news/How-to-Fix-the-Big-and-Ugly-Plymouth-Logo-in-Ubuntu-10-04-140810.shtml") for 10.10 works for me in 13.04 to fix plymouth after installing nvidia drivers.

---

