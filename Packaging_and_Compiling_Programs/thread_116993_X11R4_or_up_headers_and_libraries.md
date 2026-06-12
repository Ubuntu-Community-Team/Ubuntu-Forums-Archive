---
title: "X11R4 or up headers and libraries"
date: 2006-01-14
forum: Packaging and Compiling Programs
---

### Post by lloydie on 2006-01-14
I am new to linux and l am trying to complie [http://synergy2.sourceforge.net/compiling.html]("http://synergy2.sourceforge.net/compiling.html")
 l have managed to get all the associated gcc "stuff" installed however l'm stuck now with the following error :

configure: error: You must have the XTest library to build synergy

As the title says the applications states that it requres the X11R4 or up headers and libraries but l simple have no idea where to get them. I have searched thru forums for XTest and can't seem to find simple howto.

cheers all :)

---

### Post by mo_x on 2006-01-14
Try the following command:
sudo apt-get install x-window-system-dev

---

### Post by satchm0h on 2006-04-12
[QUOTE=mo_x]Try the following command:
sudo apt-get install x-window-system-dev[/QUOTE]



FYI, this does the trick. Thanks!

---

### Post by stealth17 on 2010-01-25
What about for 9.10? x-window-system-dev doesn't seem to be in the repos. I didn't get this error in 9.04.... I've tried installing the following packages:

libxcb-xtest0
libxtst6
libxtst6-dbg

None of these seem to help. Any ideas?

---

### Post by Posthumane on 2010-03-14
Just had the same issue in 9.10 (Karmic). The packaged you need, as it turns out, is xorg-dev. :)

---

