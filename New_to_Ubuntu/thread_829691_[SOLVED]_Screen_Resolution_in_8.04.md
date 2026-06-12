---
title: "[SOLVED] Screen Resolution in 8.04"
date: 2008-06-15
forum: New to Ubuntu
---

### Post by marvis on 2008-06-15
I installed Ubuntu 8.04 ... The screen resolution is at 800*600 I tried to change it the first time but it didnot give me any option. I restarted the comp and it gave me all the options! So I changed it to what I wanted :). But when I restarted again it gives me the same problem. It goes back to 800*600 resolution and it doesnt give me an option to change. Kindly Help. Thanks in advance

---

### Post by housam on 2008-06-15
try this : System > Preferences > Screen Resolution
If you didn't find your settings , try the following :


```
sudo nano /etc/usplash.conf
```

you will got something like that 


> # Usplash configuration file
# These parameters will only apply after running update-initramfs.  



add the required resolution 


> # Usplash configuration file
# These parameters will only apply after running update-initramfs.

xres=[COLOR="Red"]1280[/COLOR]     
yres=[COLOR="red"]800[/COLOR]      

 
or the settings you want
then reboot and type :


```
sudo dpkg-reconfigure usplash
```

then check for the new settings -- System > Preferences > Screen Resolution and select the new one.
__________________

---

### Post by sailor2001 on 2008-06-15
gksudo displayconfig -gtk

---

### Post by marvis on 2008-06-15
Thanks housam... I tried the 2nd method and even after I restart it is in my desired resolution... Thanks a lot!

> **housam said:**
> try this : System > Preferences > Screen Resolution
If you didn't find your settings , try the following :


```
sudo nano /etc/usplash.conf
```

you will got something like that 






add the required resolution 



 
or the settings you want
then reboot and type :


```
sudo dpkg-reconfigure usplash
```

then check for the new settings -- System > Preferences > Screen Resolution and select the new one.
__________________

---

### Post by japhyr on 2008-06-15
I've had lots of trouble getting screen resolution to work.  I'm stuck at 1024x768.  I upgraded from Feisty to Gutsy to Hardy, worked with xorg.conf and the Screen and Graphics dialog, all to no avail.  I saw a couple references to nano and splash, but never tried anything with it.  Is there any reason not to try this?

---

### Post by simontaylor on 2008-06-15
Hi japhyr,
I started a thread re red eyes for running at 60 Hz. Went through xorg.conf and tried to insert a frequency value of "70 Hz." This killed my monitor for half an heartpounding hour: it came up completely blank.Not the blue wall but the black wall of idiocy - my own. So I'm twice shy of biting into usplash - 

But I have to ask: will usplash deal with refresh rates?

simon

[www.squarewhiteworld.com](www.squarewhiteworld.com)
[www.brazilcoffee.co.nz](www.brazilcoffee.co.nz)

---

### Post by housam on 2008-06-16
> **japhyr said:**
> I've had lots of trouble getting screen resolution to work.  I'm stuck at 1024x768.  I upgraded from Feisty to Gutsy to Hardy, worked with xorg.conf and the Screen and Graphics dialog, all to no avail.  I saw a couple references to nano and splash, but never tried anything with it.  Is there any reason not to try this?

No reason not to try to fix your problem as long as you know what you are doing.

---

### Post by alienexplorers on 2008-06-16
Usplash will set your resolution, but not your refresh rate.  That must be done in xorg.conf using a modeline and modes command.  For you it would look like:
> Modeline "1024x768_70.00"  76.16  1024 1080 1192 1360  768 769 772 800  -HSync +Vsync

> Modes "1024x768@70"

---

