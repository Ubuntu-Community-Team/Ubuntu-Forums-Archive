---
title: "AMD Fusion on Ubuntu 11.10 64bit"
date: 2012-04-05
forum: New to Ubuntu
---

### Post by CrazYoshi on 2012-04-05
Hi everybody. This is my first post.
I’m not able to install ati drivers for my ASUS E35M1-M into my Ubuntu 11.10 64bit minimal.
I download, successfully create .deb packages and install them. But  after that the screen is black and I’m not able to enter into the  console pressing alt+f2 key.
I follow those steps:
-	Install Ubuntu minimal 11.10
-	Install ssh
-	Install 3.31 kernel from this source: [http://kernel.ubuntu.com/~kernel-ppa/mai...1-precise/]("http://kernel.ubuntu.com/%7Ekernel-ppa/mainline/v3.3.1-precise/")
-	Install all prerequisites for compile amd driver 12.3 following the “Before you start” steps of this guide: [http://wiki.cchtml.com/index.php/Ubuntu_...tion_Guide]("http://wiki.cchtml.com/index.php/Ubuntu_Oneiric_Installation_Guide")
-	Create the packages for my distribution and install them.
-	Run sudo aticonfig --initial –f
-	Install HVDA: sudo apt-get install xvba-va-driver libva-glx1 vainfo
-	After that I would like to install the new verion of xmbc (that now support VAAPI) from the repository
Now I’m not able to see anything on the screen and I have access to the  system only through ssh. If I run fglrxinfo command an Error massage  occurs.
Please could you help me? I’m getting crazy…

---

### Post by Mark Phelps on 2012-04-05
Are you trying to install drivers from Precise into Oneiric?  That's what it looks like.

It's very unlikely that's going to work.

---

