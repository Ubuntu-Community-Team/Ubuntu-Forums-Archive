---
title: "Ubuntu installation - Kernel error"
date: 2012-10-07
forum: New to Ubuntu
---

### Post by Inn33d4h3lp on 2012-10-07
Hi,

I'm trying to install the Ubuntu Server on an old Dell computer in order to host a website. I previously used WAMP-server on a Win7 environment, but I could only get my upload speed to 1/3 of what it was supposed to be. So I wanna try Ubuntu.

Though, when I boot from the CD, I immediately get the error "This kernel requires an x86-64 cpu [...]". Now, I see that the solution to this would be to try the x32 version, but when I boot that one, I get the opposite error, that I need the version I previously tried. I don't remember the exact error messages, I'm not at home at the moment.

Does anyone have a solution to this? Would be much appreciated :)

Computer information:

PC: Dell Dimension 5000 (Stationary, like 6 years old)
Processor: Intel(R) Pentium(R) 4 CPU 3.00GHz
Memory: 2034MB

---

### Post by jerrrys on 2012-10-07
Google tells me that it is a 32 bit processor with PAE (server kernel) support.  So a 32 bit server install should work.

You need to post the error message you got.

EDIT:  Could be a BIOS setting

Physical Address Extension (PAE), NX, and SSE2.  Most CPUs have support  for these features, so if you receive this error, it is likely  because  the NX feature is not enabled on your system.
  To resolve this error, follow manufacturer guidelines to enable NX  (&#8220;No eXecute bit&#8221;), or the equivalent XD (&#8220;eXecute Disabled&#8221;), feature  within the BIOS settings. This feature is typically found in the  Advanced or Security tabs within the BIOS settings, and can be referred  to by a variety of names, including but not limited to:
 ·        No Execute Memory Protect
 ·        Execute Disabled Memory Protection
 ·        EDB (Execute Disabled Bit)
 ·        EVP (Enhanced Virus Protection)

---

### Post by Inn33d4h3lp on 2012-10-09
Hi, thanks a lot for your reply.

The 32-bit version actually worked this time. I'm not sure what I did wrong the last time, unless if it's because I'm installing 32-bit Server version instead of Desktop version this time.

I did, how ever, have quite a struggle with the install media. First used "UNetbootin" and "LinuxLive USB creator" to create the USB-installer, and then burned several CDs with the Windows burner and ImgBurn. Either way, while it was extracting stuff on the install, I got the error that it was missing installation files etc.

The solution was the rename all the .ude files to .udeb in \pool\main\l\linux on the USB-stick and then it worked. :)

---

### Post by jerrrys on 2012-10-09
Wow, good fix.  Sounds like a bug, may want to report it.

[http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=report+bug&as_qdr=all&sa=Google+Search&lang=en](http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=report+bug&as_qdr=all&sa=Google+Search&lang=en)

[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

And welcome to the forums  :)

---

