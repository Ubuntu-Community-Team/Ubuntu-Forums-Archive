---
title: "Installing Ubuntu 13.10 on SD card + making it bootable from MacBook Pro"
date: 2014-02-21
forum: New to Ubuntu
---

### Post by Patrick_Boelens on 2014-02-21
Hello everyone!

I'm looking to get Ubuntu up and running as a dual-boot on my 2008 model MacBook Pro (currently running OSX 10.6.8 and Win7). I've installed it succesfully on a virtual machine, but it's a bit too slow for me. I really like having it run it parallel to OSX, but as I'll be using Ubuntu for programming and testing apps I'd like it to be a bit (read: lot) more responsive than it currently is.

Ideally I'd have Ubuntu installed on my SD card, being able to both boot into it and run it using VMware Fusion or Parallels. I've looked for how-to's and guides, but I'm coming across a lot of problems people are facing (i.e.: it not being bootable) and a lot of it seems either outdated or overly-complicated.

I would be very grateful if someone could give me an overview of how to approach this. Do I need something external like rEFIt!? Which partitions do I need to make and where? Which device should I put as my device for boot loader during the Ubuntu installer?

Any help will be very much appreciated!

Thanks,
Patrick

EDIT: I'm going to try following [this route]("http://www.weihermueller.de/mac/") in the morning and report back how it went.

EDIT 2: The installation appears to have been a succes, but I can't seem to boot into it. Holding the option key on startup does show rEFIt as an option (albeit with an "external HD" icon instead of an SD one), but choosing it, and then Linux, boots straight into Windows. Selecting rEFIt followed by Windows does the exact same thing. The flavour text for both is also nearly the same: "Boot into [Windows | Linux] on Partition 3". If anyone knows how to fix this, please let me know and I will be eternally in your debt for the next three days.

---

### Post by Patrick_Boelens on 2014-02-22
Bumping since the focus of the problem has (presumably) changed and I've gotten further along in the process.

---

