---
title: "LVM2 Ubuntu 12.04 Desktop??"
date: 2012-05-30
forum: New to Ubuntu
---

### Post by held7over on 2012-05-30
Ubuntu 12.04

I want to install Ubuntu 12.04 on an LVM2 hard drive, and then later, add another hard drive and make it also LVM2 and then have both hard drives appear as a single continuous hard drive to my OS.  

What is the most beginner friendly (gui?) way to create a LVM2 hard drive that I can then install Ubuntu 12.04 on top of?

--And what file format system (ext3 or 4, or what) should I use?

Thanks! :p

---

### Post by held7over on 2012-05-30
I should mention, the version of Ubuntu 12.04 that I want to do this on is the Desktop 64 bit version. The Server 64 bit version has the ability to create LVM2 in it's partitioning manager in the install, but I can't find it in the Desktop version...

---

### Post by Cheesemill on 2012-05-30
If you use the alternate install disk then you get the option to set up LVM during installation.

[http://releases.ubuntu.com/12.04/ubuntu-12.04-alternate-amd64.iso](http://releases.ubuntu.com/12.04/ubuntu-12.04-alternate-amd64.iso)

---

### Post by held7over on 2012-05-30
Thanks Cheesemill! I will give the alternate a spin!

My understanding of LVM and how it works isn't great. A lot of what I have tried to read about it, goes over my head. 

I tried using the server version to create an LVM install with Ubuntu 12.04 server and that appeared to work. Then when that was done installing, I then tried to install the desktop version into the partitions I had created with the server version, but the desktop version simply wiped out the LVM completely and I ended up with a normal desktop install without LVM existing...obviously, I either did it wrong or there is something extra I don't understand about LVM...

Thanks again!

---

