---
title: "VirtualBox sharing folders?"
date: 2008-06-03
forum: New to Ubuntu
---

### Post by coubury on 2008-06-03
Im running xp on virtualBox and im looking to take a folder from xp and put it in Ubuntu 

how do i do this?

---

### Post by SlappyPappy on 2008-06-03
Do you have USB working well in VB? I'd just copy it to a USB flashdrive and then copy it to Ubuntu. I was doing the reverse to move a bunch of files into my W2K install for writing purposes.  :)

---

### Post by serador on 2008-06-03
1. start up virtual box then start up xp
2. go to the top panel click Devices-->Install Guest Editions
3. Download and install Guest Editions
4. Set up your shared folders in virtual box. Example share folder home/Crimthinc
5. start up windows go to Start-->Run enter cmd and press enter
6. once in the dos console deal type net use t: \\vboxsvr\Crimethinc(only put in the last folders name on the end of the command for example if you selected a folder under home/Crimthinc/music the command would be net use t: \\vboxsvr\music)

---

