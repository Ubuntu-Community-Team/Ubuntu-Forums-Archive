---
title: "Please help me complete the Linux desktop experience"
date: 2018-06-13
forum: Programming Talk
---

### Post by allcoms on 2018-06-13
Hi Linux devs

I am a long time Linux user and advocate. I started using Linux back in '96 with Slackware 3.1 when it was Linux 1.2.13 and before KDE and GNOME/MATE and all the other great desktop and user friendly goodness arrived that many will take for granted. I have tried every desktop environment that is available but the one that works best for me is MATE. Fast forward to 2018 and the release of Ubuntu MATE 18.04 with its HiDPI support and the ironing out of several kinks and I feel that Linux as a desktop OS is 99.9% perfect for my use case; there is really only one final flaw I want to see fixed and that is the ability to have thumbnail previews of video files stored on a samba network drive when using MATE's otherwise fantastic file manager caja. I have reported this bug to the MATE team here:

[https://github.com/mate-desktop/caja/issues/1009](https://github.com/mate-desktop/caja/issues/1009)

I'm pretty good at writing shell and python scripts and I know the basics of C and using gdb so I've spent a good few hours trying to get to the bottom of this bug myself but I've had to concede defeat and admit its a bit out of my depth as I'm really not a C programmer. Caja is a pretty big and complex multithreaded program so its quite a lot to get your head around if you're not experienced at this sort of stuff. I reported this bug over a week ago and the MATE devs have yet to respond as I expect they're busy working on other tasks and this bug clearly isn't the priority for them that it is for me. I'm hoping that there will be someone who is much more experienced in Linux C programming and debugging who would is also interested in seeing this bug fixed and/or would like to contribute to the community by helping me fix this bug by stepping me through the process over IRC, mumble, jitsi, google hangouts or whatever mode of communication you prefer. I expect that if someone can show me how to fix this I'll be able to reuse that knowledge to help fix several more bugs in other apps in the future - I'd love that.

Do we have any kind devs with a few hours to spare to help me and the MATE project out by stepping me through the debugging process?

Thanks

---

### Post by trilobite2 on 2018-06-14
Hi allcoms -  

 I can't help with this myself but I do have a suggestion - you may want to log this bug with the Caja team as well.  Two bug reports should mean twice the chance of help. 
 Just my 2c worth.....  :)   

 Cheers -  
- trilobite2

---

### Post by allcoms on 2018-06-14
Hi trilobyte!

The github bug report I linked to above is the official bug tracker for caja / MATE. This is the same team who are responsible for Ubuntu MATE. I have also reported it as a bug with the caja maintainer for Arch Linux, which is the other Linux distro I use. I use Ubuntu for day-to-day use and Arch to try the latest and greatest software out without trashing my main OS. I know about VMs of course but I prefer to see how stuff runs on the metal, hence me dual booting. In some cases thats the only proper way you can test, esp graphically intensive software that requires your GPU to run properly.

---

### Post by allcoms on 2018-06-19
I have now filed this bug with the MATE project (which is also the Ubuntu MATE team), Arch Linux and now Fedora/Redhat too so I hope one of the the big three distros agrees with me that this is a useful missing feature.

[https://bugzilla.redhat.com/show_bug.cgi?id=1592572](https://bugzilla.redhat.com/show_bug.cgi?id=1592572)

---

