---
title: "Intrepid : FIX Usplash / Get Usplash working"
date: 2008-11-12
forum: Outdated Tutorials &amp; Tips
---

### Post by binbash on 2008-11-12
At the moment if you change your usplash theme, it just does not change.To fix this  : 

-sudo apt-get install libusplash-dev

Then go to your theme folder (i am using this : [http://gnome-look.org/content/show.php/Wideubuntu+Usplash?content=84632](http://gnome-look.org/content/show.php/Wideubuntu+Usplash?content=84632) and the filenames used below is for this one )

-make
-sudo cp usplash-theme-wideubuntu.so /usr/lib/usplash
-sudo rm /etc/alternatives/usplash-artwork.so
-sudo ln -s /usr/lib/usplash/usplash-theme-wideubuntu.so /etc/alternatives/usplash-artwork.so
-sudo update-initramfs -u
-sudo update-grub

Ps 1 : 

If you used ubuntugeek's solution (remove usplash and install splashy ), completely (yes open synaptics and remove config files also) remove splashy and install usplash

PS 2 :

 If above method does not work, re-install usplash (completely remove & install )

---

### Post by gabor111 on 2008-11-28
Thank you for your howto

I have an eeePC 901 with intrepid, with eeepc-lean kernel from arrays.org.
Im very happy with it. But my usplash is not nice, because I have a wide-screen with 1024x600 resolution.

I tryed your how to, but I have a blank screen during boot with it.
I changed back to usplash in startup manager, and now I have the initial uslash on boot.

Is it possible to make directly a version for 1024x600?
Or have you any idea?

Tx in advance.

Ps. Sorry for my English...

---

### Post by bismark on 2008-12-03
How can you get one working if you only have the precompiled .so and not the theme source?

I've tried variations of modifying my menu.lst vga= line, the lines in /etc/usplash.conf and still all other usplash screens just hang on bootup.

---

