---
title: "Building up my first Unbuntu for 3d printer"
date: 2014-08-27
forum: New to Ubuntu
---

### Post by aric2 on 2014-08-27
[URL="http://www.amazon.com/gp/product/B00KMRGF28/ref=oh_aui_detailpage_o00_s00?ie=UTF8&psc=1"]http://www.amazon.com/gp/product/B00KMRGF28/ref=oh_aui_detailpage_o00_s00?ie=UTF8&psc=1
[/URL]

Just Ordered this laptop to install a fresh copy of Unbuntu or maybe Lunbuntu, not sure what is best.  I want a system that all it does is run my 3d printer.  I tried and old laptop, but hard drive failed during the install so instead of buying another hard drive decided to get a bare bones laptop and install it fresh.  Found it on the supported hardware and good deal on Amazon.

Hoping to join the linux world and learn some new things.  Lunbunto looks pretty nice and quick for what I need, but not sure it support mono 3.6 which is needed for Repetier to work correctly with custom 25000 baud.

---

### Post by Impavidus on 2014-08-28
Mono 3.2 is available from the repositories. For 3.6 you'll need to find a PPA or install manually (PPA is best). Usually that works, but it cannot be guaranteed. I wouldn't be surprised if 3.6 will be included in the next release of Ubuntu.

---

### Post by aric2 on 2014-08-28
Do the different versions of Ubuntu like Xubuntu and Lubuntu have any limits what can be installed?

---

### Post by QIII on 2014-08-28
Hello!

"Limits to what can be installed" is both broad and vague.

Pretty much anything that can be installed on one can be installed on another, but some packages may bring dependencies that wouldn't otherwise be included in a particular flavor of *buntu.  

What would you like to install?

Edit:  Sorry, had to switch to another machine.

If you have some 3d printer software that is designed specifically for Windows, you are not likely to be successful.  Linux is a completely different environment.  By and large, you cannot run Windows applications in Linux.  Some cross-platform applications will run without problems, but certain features may not be available.  Some Windows applications will run using Wine, but a specialty application is not likely to work well, if at all.  Some Windows applications written in C# (.NET) will run if you also install Mono -- but not all.  Hopefully your printer software is one of those.

---

### Post by aric2 on 2014-08-28
Thanks, Yes Repetier has the source code for Linux distros.  Just want to make sure I don't get limited by the flavor I use and have to start over finding out that I can't install a dependency needed.

---

