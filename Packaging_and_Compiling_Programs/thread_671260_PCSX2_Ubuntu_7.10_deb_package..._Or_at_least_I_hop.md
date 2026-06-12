---
title: "PCSX2 Ubuntu 7.10 deb package... Or at least I hope..."
date: 2008-01-18
forum: Packaging and Compiling Programs
---

### Post by Festor on 2008-01-18
Hello everyone! My name is Festor Wailon Dacoba and I am a love GNU/Linux

First of all to say that I am not an expert, but for some months I am trying to create deb packages for distribution Ubuntu.

With this emulator I did not have much luck and I do not know if it reaches doing well among other things because of pcsx2 compiled in linux is nothing "easy" and is not very well designed for the packaging process.

I found some faults, if you can call it

+ Errors in the compilation process with parameters (such as -enable-vmbuild and others)
+ There is no icon to the menu of KDE or GNOME, or at least not what I have seen
+ The emulator does not create a folder called .program (in this case will be ***.pcsx2***) in the home with the configuration files and plug as usual in applications of GNU/Linux

Please, it will be very helpful that the docs folder had a file with the dependencies to compile and make a package. The dependencies I used do not know if they are the right ones. I had to search hard for google and read post on various other users and suggestions

Please download the deb and try

Sorry for my bad English... :(

Some logs:

[http://build.getdeb.net/abs/build_log/pcsx2_0.9.4-1~getdeb1_2008_39_16_01_1200494342_i386.log](http://build.getdeb.net/abs/build_log/pcsx2_0.9.4-1~getdeb1_2008_39_16_01_1200494342_i386.log)
[http://build.getdeb.net/abs/build_log/pcsx2_0.9.4-1~getdeb1_2008_06_18_01_1200636361_i386.log](http://build.getdeb.net/abs/build_log/pcsx2_0.9.4-1~getdeb1_2008_06_18_01_1200636361_i386.log)
[http://build.getdeb.net/abs/build_log/pcsx2_0.9.4-1~getdeb3_2008_33_18_01_1200663181_i386.log](http://build.getdeb.net/abs/build_log/pcsx2_0.9.4-1~getdeb3_2008_33_18_01_1200663181_i386.log)
[http://build.getdeb.net/abs/build_log/pcsx2_0.9.4-1~getdeb4_2008_15_18_01_1200665702_i386.log](http://build.getdeb.net/abs/build_log/pcsx2_0.9.4-1~getdeb4_2008_15_18_01_1200665702_i386.log)

I make this same post here:

[http://forums.ngemu.com/pcsx2-official-forum/98797-pcsx2-ubuntu-7-10-deb-package-least-i-hope.html](http://forums.ngemu.com/pcsx2-official-forum/98797-pcsx2-ubuntu-7-10-deb-package-least-i-hope.html)

---

### Post by barius on 2008-01-18
See this [guide]("http://ubuntuforums.org/showthread.php?t=631979") for compiling SVN on Ubuntu.

Good luck!

---

### Post by Festor on 2008-01-19
> **barius said:**
> See this [guide]("http://ubuntuforums.org/showthread.php?t=631979") for compiling SVN on Ubuntu.

Good luck!

thanks! :D

---

### Post by Festor on 2008-01-30
Deb package:

[http://www.getdeb.net/app/PCSX2](http://www.getdeb.net/app/PCSX2)

---

### Post by Mr.mouse on 2008-02-01
so after installing this deb, i can run ps2 games just by put the ps2 disk in the computer ?
do i need to install ps2  BIOS or is it with an open-source BIOS ?
is it all gpl ?

---

### Post by sit22 on 2008-03-06
Works great, thanks for making it. just one small bug: background image is not there  (Couldn't find pixmap file: pcsxAbout.bmp). Anyway it works great thanks again :)

---

### Post by fbuchele on 2008-03-30
Thanks, that's great. Really saved me some time. Thanks!

---

### Post by CryptSphinx on 2008-08-11
I applaud your brilliance :)


This will be an excellent way for me to never move away from my pc, whatever it is I want to do (hang on...)

No where's the .deb to control your kettle via bluetooth?

---

### Post by Dev'olution on 2008-10-23
Brilliant! Absolutely Brilliant!

---

