---
title: "reinstallation of Ubuntu with RAID &amp; LVM"
date: 2012-02-17
forum: New to Ubuntu
---

### Post by ormeskirk on 2012-02-17
I have had a lot of fun with my Ubuntu machine over the last few years.  I use it as a server and have experimented with a lot of different pieces of software on it.  I recently upgraded through three releases (without rebooting between each, stupid, I know) and now a lot of things do not work.

I am not too upset because I would like a fresh install to get rid of a lot of the "experiments."  My only concern is, while the Ubuntu installation is on a single hard drive, I have 6 hard drives on Software Raid 5 and LVM on top of that.  I really do not want to lose the data on these drives when I reinstall.

I found this: [http://tldp.org/HOWTO/LVM-HOWTO/recipemovevgtonewsys.html](http://tldp.org/HOWTO/LVM-HOWTO/recipemovevgtonewsys.html)
and thought it might be helpful, but it does not help me re set up my RAID.

So I was wondering if I could back up some configuration files, or some lines from some configuration files and copy them onto the new installation to make it work.  Or if what ever else I would need to do. . .

I am currently running Ubuntu Desktop 11.10 and will be installing the same back on to it.

Thanks ahead of time for your help. . .

---

### Post by ormeskirk on 2012-02-18
I got smart, and booted Ubuntu from a thumbdrive. . . installed MDADM and LVM2 and assembled the array, then boom!  There's my drives. . . So here I go with a fresh install. . .wish me luck.

---

