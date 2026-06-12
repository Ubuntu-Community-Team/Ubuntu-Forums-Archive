---
title: "How to uninstall????"
date: 2008-04-25
forum: New to Ubuntu
---

### Post by pdave1s on 2008-04-25
how do I uninstall ubunu, and all it added to my system, without loseing any of the other operating systems on my puter?

---

### Post by TeoBigusGeekus on 2008-04-25
What are the other operating systems on your pc?

---

### Post by overdrank on 2008-04-25
> **pdave1s said:**
> how do I uninstall ubunu, and all it added to my system, without loseing any of the other operating systems on my puter?

HI and this link can help you uninstall
[http://www.users.bigpond.net.au/hermanzone/p18.htm](http://www.users.bigpond.net.au/hermanzone/p18.htm)

---

### Post by Calash on 2008-04-25
What operating systems are you running?

Assuming you are using Windows, then it is a 2 step process.  First you have to restore the MBR, so you get the fancy Windows Boot Loader.  This can be done by booting to your Windows install disk, running the "Recovery Console", then run FIXMBR at the command line.  A Microsoft focused forum may be able to help you better with this step.

The second step is to reclaim the space you used for Ubuntu.  You can just format the partitions NTFS and mount them as additional drives, or get a partition editor, like the one on the Ubuntu live CD, and merge the space together.  This is a potentially dangerous step, so make sure you defrag first and back up anything important.

---

### Post by forestpixie on 2008-04-25
If you have windows installed - use it to fixmbr and then format the partitions that ubuntu is on, if you format first you will not be able to boot. I assume that's what you don't want to lose as there is not much information to go on.

---

### Post by Bentai on 2008-04-25
If you used Wubi to install 8.04, just boot into Windows, go to the Control Panel then Add/Remove Programs. Ubuntu should be listed inside there for removal. No mess no fuss.

---

### Post by terabyte1 on 2008-04-25
I'm sorry you find that Ubuntu is not to your liking. Are you having problems trying to get it to work? There are a lot of us here who are just waiting to help someone like you. Please give Ubuntu a second-chance and you will be well rewarded - and probably make a lot of new friends too!:)

Terabyte1

---

### Post by SunnyRabbiera on 2008-04-25
remember you cant learn a new OS in one day...
if you give us your issues perhaps we can help

---

