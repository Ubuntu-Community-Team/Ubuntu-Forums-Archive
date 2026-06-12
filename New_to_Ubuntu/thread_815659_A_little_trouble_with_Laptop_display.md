---
title: "A little trouble with Laptop display"
date: 2008-06-01
forum: New to Ubuntu
---

### Post by kimberly54 on 2008-06-01
I have a Sony Vaio PCG-FX340 Laptop that was totally over-ridden with 
Windows junk so I decided to try and install Ubuntu 8.04 from a disk my friend told me to try.  I went for the whole install and it went superbly except for the fact that my Laptop's display shows around a 1 inch black band around it...making my 800x600 display(the only choice in System/Prefs/Screen Resolution) kind of diminutive.

Also, I get some strange characters and bits and pieces that float around on my desktop.

Can anyone help this absolute Linux novice figure what to do?:(

---

### Post by spiderbatdad on 2008-06-01
Not sure but it could require a crash course in file editing...don't despair. It is fixable. Could you start by opening a terminal: Applications>>Accessories>>Terminal

Enter:```
sudo lshw -C video
```You will be asked for your password, and you will not get any feedback that you are pressing keys...just type your password and hit enter. Please copy/paste the output back here.

---

### Post by kimberly54 on 2008-06-01
A couple of characters after the password got messed up but here is what was on the screen...

kimberly@kimberly-laptop:~$ sudo lshw -C video
[sudo] password for kimberly: 
^[[B  *-display           
       description: VGA compatible controller
       product: 82815 Chipset Graphics Controller (CGC)
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 11
       width: 32 bits
       clock: 66MHz
       capabilities: pm vga_controller bus_master cap_list
       configuration: driver=i810_smbus latency=0 module=i2c_i810
kimberly@kimberly-laptop:~$ 
kimberly@kimberly-laptop:~$ 
kimberly@kimberly-laptop:~$

---

### Post by spiderbatdad on 2008-06-01
hmmm. not too sure. That card should work well with ubuntu. You may have to manually edit the file called /etc/X11/xorg.conf
but I hate to tell you to start out that way. Be a little patient, and hopefully someone familiar with that card will pick up on this post.

For a little light reading, here is an example of someone editing that file:[http://ubuntuforums.org/showthread.php?t=811813&page=2](http://ubuntuforums.org/showthread.php?t=811813&page=2)

You can view your xorg.conf by navigating to Places>>Computer>>File System
/etc/X11/xorg.conf  but you cannot edit the file from this view. Editing root files requires super user privileges...like running gksu nautilus then navigating to the file....always be very careful in super user mode.

---

### Post by kimberly54 on 2008-06-27
The latest HArdy update finally gave a choice of my native screen resolution 1024x786...so I am no longer stuck at 800x600:KS

---

