---
title: "[SOLVED] Flash Player Installation"
date: 2008-11-14
forum: New to Ubuntu
---

### Post by Sparty26 on 2008-11-14
I am having all sorts of trouble installing flashplayer for my Kubuntu. I tried doing it through the Adobe website, and it said that it was installed, yet nothing changed, and I tried installing Swedfc Flash Player through Adept Installer, and I got the same result. Everythime I go to a website that I need flashplayer for it tells me I need to install it, yet I think I already have?! Does anyone have any help?

---

### Post by Mardoct909 on 2008-11-14
[http://tombuntu.com/index.php/2008/10/16/install-adobe-flash-player-10-in-ubuntu-804-and-810/](http://tombuntu.com/index.php/2008/10/16/install-adobe-flash-player-10-in-ubuntu-804-and-810/)

---

### Post by jimmy the saint on 2008-11-14
```
sudo apt-get install kubuntu-extras
```

---

### Post by Sparty26 on 2008-11-14
When I tried the > sudo apt-get install kubuntu-extras it returned > Reading package lists... Done
Building dependency tree
Reading state information... Done
E: Couldn't find package kubuntu-extras

When I went to [http://tombuntu.com/index.php/2008/1...u-804-and-810/](http://tombuntu.com/index.php/2008/1...u-804-and-810/) , I was told to do the same thing I had aready done, which was download the .deb and install it, which I did (again) and it said that it was installed (again) and yet nothing's happened?!

---

### Post by jimmy the saint on 2008-11-14
sorry, that should be 
```
sudo apt-get install kubuntu-restricted-extras
```

WooHoo!!  my 500 mark!!

---

### Post by Mardoct909 on 2008-11-14
Are you on a 64 bit system?

---

### Post by jimmy the saint on 2008-11-14
If you are on a 64-bit system then difinitely use the extras package as it will be automatically optimized for your system.  Many flash debs floating aroudn are for i386.

---

### Post by ferral-cat on 2008-11-14
This is a great tutorial on setting up flash and all your codecs:

[http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683)

---

### Post by Sparty26 on 2008-11-15
Problem solved! Thanks for all of the help everybody. It turns out I just needed to open Adept Manager and install the updates. Now everything works fine, my sound still isn't working though...

---

