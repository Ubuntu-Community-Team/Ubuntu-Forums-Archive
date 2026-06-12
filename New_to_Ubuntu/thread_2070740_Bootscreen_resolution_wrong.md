---
title: "Bootscreen resolution wrong"
date: 2012-10-13
forum: New to Ubuntu
---

### Post by LeeHP on 2012-10-13
Hey guys im fairly new to linux(only had for a month or two) and i installed it on my stationary pc, but the bootscreen and in general the grub bootloader is in, i think, 640x400 resolution. How am i able to change this? Please help me in details since i am new to this ^^ thank you so much !:lolflag:

---

### Post by bob-linux-user on 2012-10-13
You might find Daniel Richter's program useful, I did

[http://ubuntuforums.org/showthread.php?t=1664134](http://ubuntuforums.org/showthread.php?t=1664134)

Bob

---

### Post by LeeHP on 2012-10-13
> **bob-linux-user said:**
> You might find Daniel Richter's program useful, I did

[http://ubuntuforums.org/showthread.php?t=1664134](http://ubuntuforums.org/showthread.php?t=1664134)

Bob

Sorry i dont understand what i need to do :)

---

### Post by oldfred on 2012-10-13
the link is a complete how-to on installing grub customizer. 

Grub Customizer will let you change many settings in grub.

If you do not want an easy gui, you can just modify grub's settings.

Use command line editor grub's on set gfxmode=640x480
and just remove the # as that makes that line a comment to default to 640x480.
OR Use this with your monitor size in /etc/default/grub:
GRUB_GFXMODE=1024x768
Change above to exactly your video setting or you may have issues booting.

sudo nano /etc/default/grub
or
gksu gedit /etc/default/grub
# then 
sudo update-grub

---

### Post by LeeHP on 2012-10-14
> **oldfred said:**
> the link is a complete how-to on installing grub customizer. 

Grub Customizer will let you change many settings in grub.

If you do not want an easy gui, you can just modify grub's settings.

Use command line editor grub's on set gfxmode=640x480
and just remove the # as that makes that line a comment to default to 640x480.
OR Use this with your monitor size in /etc/default/grub:
GRUB_GFXMODE=1024x768
Change above to exactly your video setting or you may have issues booting.

sudo nano /etc/default/grub
or
gksu gedit /etc/default/grub
# then 
sudo update-grub
Oh alright, i'll let you two know if i was able to get it working:) :popcorn:

---

