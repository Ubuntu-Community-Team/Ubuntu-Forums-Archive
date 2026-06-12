---
title: "Dual-Booting/Wubi/Laptop Question"
date: 2008-05-30
forum: New to Ubuntu
---

### Post by dph948 on 2008-05-30
Hello,
I've been running Ubuntu (Gutsy) since October, and I've loved it, but I since I usually only use it for the internet, open office, and some media I really haven't become too familiar with the terminal or any more advanced aspects of Linux, so I figured this forum would be the best place to start.

I'm going off to college next year, and I need a laptop.  Most likely I will use either the Dell Inspiron 1525 or the Dell Inspiron 1720, as I still need to determine the size/price range that will be best for me.

However, I'm not looking forward to the transition to Vista, and I would like to run Ubuntu in addition to Vista.  However, I had quite a few questions, and any help in answering them would be much appreciated.

My friend runs Fedora on her (older) laptop, and has had many compatibility issues which took great time and effort to resolve.  According to Ubuntu's wiki and Linux on Laptops, it looks like Hardy works  pretty well.  However, if there were some issue (say perhaps something fairly devastating, like the screen not being compatible) would Vista still work?

I've been considering partitioning, using a Virtual Machine, or using Wubi to install.  I've been told that if a partition is executed incorrectly, one partition may not recognize the other and unintentionally overwrite it, and that vmware and other Virtual Machines can reduce performance, while Wubi is fairly new and I haven't heard a ton about it yet.  Which of the three is easiest to use (I assume Wubi)?  Does a reduction in performance matter when I will have at least 2 GB of RAM?  Most importantly, which of the three is least likely to negatively affect the Vista partition of the laptop?  If I'm going to be spending a large amount of money on a laptop, I'd like to ensure that I don't destroy it or put myself in a position where my computer will be out of commission during the school year?

On a related note, Intrepid Ibex (which I understand is a LTS release) will come out in October.  When is the best time to upgrade the laptop to that edition?

Thanks so much,
dph948

---

### Post by eriqjaffe on 2008-05-30
> **dph948 said:**
> Most importantly, which of the three is least likely to negatively affect the Vista partition of the laptop?Neither Wubi or a virtual machine will affect the Vista partition in the slightest, as they don't repartition anything.

Wubi will get you the best performace of the two, since it won't be running a virtualized environment.  Hard drive access is a *bit* slower, although not enough to be a real issue unless you're doing something that does a ton of disk access.

---

### Post by Het Irv on 2008-05-30
If you are going to be running Vista I would highly suggest taking VmWare off of your list of options.  Vista needs 2 gigs of RAM to run smoothly BY ITSELF.  Wubi is your best choice if you want an easy way to run Linux. I tried using Ubuntu in VmWare and had to take it off because it was running to slow. 

Even if you use Wubi, Ubuntu is not going to change anything in Vista, so no matter how bad you screw it up, Vista will still work (as well as it can, the crappy OS). I have never had any problems with partitions as long as you think before you do anything.

ps 8.04 (Hardy) is LTS, Intrepid will be a normal release.

---

### Post by bumanie on 2008-05-30
Hardy heron is the present LTS distro. Intrepid will have the standard 18 months support. Personally I would use a classic dual boot, but wubi does seem to work OK, but takes 15g of hard drive space to install, a normal install, after extra software etc. will likely be 5-6g system files + data (best in a separate partition). Care is needed with partitioning, but if one is careful, one won't overwrite already installed OSes. A virtualised environment such as virtualbox, should also work OK.  I have used all three methods mentioned and prefer dual booting, but the other two environments work well enough, although there is some reduction in performance with them.
Ubuntu has good hardware compatablity - but there are no absolute guarantees. If there are any hardware conflicts they would not affect vista, seeing the two OSes are on different partitions.
Personally I prefer dual boots, it's really up to your personal preference. Try wubi or virtualbox first and if all works well, I would suggest a full dual boot.

---

