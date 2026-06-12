---
title: "[SOLVED] Screen Resolution"
date: 2008-06-17
forum: New to Ubuntu
---

### Post by prc320 on 2008-06-17
Hi

I have two screen resolutions. 800*600 and 640*480.

I would like at least 1024*768 I had done ddcprobe -?

symsr1@symsr1:~$ sudo ddcprobe -?
vbe: VESA 3.0 detected.
oem: NVIDIA
vendor: Build    071004.1
product: MCP73 - mcp73-80 Chip Rev
memory: 131072kb
mode: 640x400x256
mode: 640x480x256
mode: 800x600x16
mode: 800x600x256
mode: 1024x768x16
mode: 1024x768x256
mode: 1280x1024x16
mode: 1280x1024x256
mode: 320x200x64k
mode: 320x200x16m
mode: 640x480x64k
mode: 640x480x16m
mode: 800x600x64k
mode: 800x600x16m
mode: 1024x768x64k
mode: 1024x768x16m
mode: 1280x1024x64k
mode: 1280x1024x16m
edid: 
edidfail
symsr1@symsr1:~$ 

but xrandr -q shows

symsr1@symsr1:~$ xrandr -q
Screen 0: minimum 640 x 480, current 800 x 600, maximum 800 x 600
default connected 800x600+0+0 0mm x 0mm
   800x600        61.0* 
   640x480        60.0  
symsr1@symsr1:~$ 


What to do next!


Robert

---

### Post by benfindlay on 2008-06-17
Fire up a terminal and type ```
sudo dpkg-reconfigure xserver-xorg
```
and just follow the onscreen instructions! When you get to the stage asking for simple, medium or advanced, choose medium and it will display a list of screen resolutions. Select the ones you want with Spacebar and move to the next stage. Once you're done just reboot (to be sure) and you should be good to go!

Hope this helps!

P.S. if in doubt, just accept defaults on the various options such as the keyboard stuffp

---

### Post by kk0sse54 on 2008-06-17
Have you tried Application> Other> Screens and Graphics? Should be able to change your resolution through there.

---

### Post by N.N. on 2008-06-17
I believe the reason that you can't select a resolution of 1024x768 (or higher) is that Xorg is unable to detect the specifications of your monitor. Most importantly it fails to determine the correct horizontal and vertical frequency ranges of your monitor and therefore uses some generic values for these specifications. These generic values are set in such a conservative manner that they won't allow you to select a resolution of 1024x768.

Normally Xorg can detect the correct specifications of your monitor by querying it for EDID (Extended Display Identification Data). In your case, however, that query seems to fail, hence the following error message in the output of ddcprobe: ```
edid:
edidfail
```

A possible solution to your problem is to manually specify the correct horizontal and vertical frequency ranges of your monitor in the /etc/X11/xorg.conf file. You'll often be able to find these specifications in the manual that came with your monitor or by doing a Google search. If you manage to find them, see the following link for instructions on how to properly specify them in /etc/X11/xorg.conf: [https://help.ubuntu.com/community/FixVideoResolutionHowto#head-e2249d4bcb9fe0dea110f9b82ec7a40716221541](https://help.ubuntu.com/community/FixVideoResolutionHowto#head-e2249d4bcb9fe0dea110f9b82ec7a40716221541).

---

### Post by Pjotr123 on 2008-06-17
Check this:
[http://ubuntutip.googlepages.com/bugsinubuntu](http://ubuntutip.googlepages.com/bugsinubuntu)
(number 2 )

This assumes you have the restricted driver running (which you want). If not, do this first:
[http://ubuntutip.googlepages.com/thefirstthingstodo](http://ubuntutip.googlepages.com/thefirstthingstodo)
(number 2 as well)

---

### Post by bufsabre666 on 2008-06-17
well it says youre oem is nvidia, have you tried their proprietary drivers yet?

---

### Post by kestrel1 on 2008-06-17
I had a similar problem & to get to the Screens & Graphics have a look at part of the thread that I started:
[http://ubuntuforums.org/showthread.php?t=766846&page=2](http://ubuntuforums.org/showthread.php?t=766846&page=2)
At the top of this page you are given the details of how to enable the Screens & Graphics utility.

---

### Post by avtolle on 2008-06-17
You can also get to "Screens and Graphics" from the terminal```
sudo displayconfig-gtk
```

---

### Post by prc320 on 2008-06-17
Thanks one and all, I got to it Pjotr123's first tip.

Thanks

Robert

---

