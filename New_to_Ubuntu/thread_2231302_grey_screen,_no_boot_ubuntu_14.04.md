---
title: "grey screen, no boot ubuntu 14.04"
date: 2014-06-24
forum: New to Ubuntu
---

### Post by Mokoyombi on 2014-06-24
I have a home built system running Windows XP. I've been trying to  install ubuntu 14.04 LTS by various methods with varying degrees of  "success", but have not been able to boot the OS. I get as far as  selecting ubuntu on the boot choice menu, then the screen goes black.  After about two minutes the screen goes grey, no mouse pointer, no  keyboard input and locks in this state. The HDD LED flickers/flashes on  and off indicating hard disk activity. The only way to come out of this  lockup is to reboot into XP! (The ungrateful thing!!) This behaviour has  also happened trying to install other ubuntu distros, leading me to  believe there is a problem with my system/hardware settings, but I have  no idea how to work around this problem. Any help will be greatly  appreciated, I have tried the OS on a friend's computer and it works  just the way I need, "right out of the box". Please help! I'm  desperately trying to ditch Windows permanently, mainly because it  forces regular hardware upgrades, which can become quite expensive for a  person with limited budget...

---

### Post by arieleoar on 2014-06-24
Hi! you managed to finish the instalation of ubuntu or you are stuck in the reboot process? i had a similar problem and the solution was to change the vga connector (the connector of the monitor, display) from the graphics card (i've a nvdia GF6200) to the motherboard plug. try this way and if you can get to the system install the privative controllers for you vcard.

Another thing, maybe im not too updated (haha) but for a extrange reason when i installed every linux distro after an installation of windows, the loader of windows recognised linux but when it was selected the screen went to "prompt" (that scary black screen with the _ pointer alone). the solution maybe (try to google it) is to install a GRUB loader, but that goes out of my knowledge :p

Hope this helps you!

---

### Post by ibjsb4 on 2014-06-24
This could be "nomodeset".

[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)

---

### Post by yancek on 2014-06-24
Try editing the boot menu by adding nomodeset as suggested or try the Recovery option.  Open a terminal and type:  sudo gedit /etc/default/grub and look for the line below:

> GRUB_GFXMODE=640x480

If there is a hash mark (#) at the beginning of the line, delete the hash mark so it looks like the above entry.

---

### Post by squakie on 2014-06-25
I also would consider the nomodeset or other boot options.  However, before you do that:

when the screen goes black/grey, hold down ctrl/alt/F1 then release .  Do you get a text-mode login screen?

If so, log in with your normal userid and password.  Be aware the password isn't echoed to the screen so while it looks like nothing is being accepted it really is - just press enter when you've finished the keystrokes for your password.

After the login you will eventually get to a line with a flashing cursor at the end.  Please type:

lspci | grep VGA  

Please post the output of that back here.

Also try typing:

startx and press enter.

Do you get any error messages?  If you don't, if you press ctrl/alt/F7 do you get a gui'd screen or still the black/grey screen?  Ctrl/alt/F1 will get you back to the text mode terminal.  If you want to reboot you are much easier on your hardware if you just type

sudo shutdown -r now <press enter>  If it asks for your password just type your regular password and press enter.

---

