---
title: "Startup problem"
date: 2008-11-13
forum: New to Ubuntu
---

### Post by celticbhoy on 2008-11-13
Since upgrading to ibex I no longer have a splash screen on startup, and during the process I get the following error :-

Buffer I/O error on device sr0 logical block 171903.

What is device sr0, and how do I fix my probs .....

[-o<

---

### Post by binbash on 2008-11-13
> **celticbhoy said:**
> Since upgrading to ibex I no longer have a splash screen on startup, and during the process I get the following error :-

Buffer I/O error on device sr0 logical block 171903.

What is device sr0, and how do I fix my probs .....

[-o<

-sudo apt-get install libusplash-dev

Then go to your theme folder (i am using this : [http://gnome-look.org/content/show.php/Wideubuntu+Usplash?content=84632](http://gnome-look.org/content/show.php/Wideubuntu+Usplash?content=84632) )

-make
-sudo cp usplash-theme-wideubuntu.so /usr/lib/usplash
-sudo rm /etc/alternatives/usplash-artwork.so
-sudo ln -s /usr/lib/usplash/usplash-theme-wideubuntu.so /etc/alternatives/usplash-artwork.so
-sudo update-initramfs -u
-sudo update-grub


This will fix usplash

---

### Post by celticbhoy on 2008-11-13
From a quick look on google it seems that sr0 is an optical drive - whay is ubuntu probing this at startup???

---

