---
title: "Which Device File?"
date: 2012-04-12
forum: New to Ubuntu
---

### Post by heartofwhite on 2012-04-12
Hey everyone,

I am brand new to this site, and looking for help! I am currently installing Ubuntu on my machine which has Vista. I have partitioned my drive and renamed it Ubuntu D.(Please see attached file)

However, when I go to install it, I am asked where I want to install to.

SDA1 - 1.6GB
SDA2 - 100.8 GB
SDA3 - 34.8 GB
SDA5 - 62.9 GB

My question is how do I know which one is the ubuntu drive? I do not want to overwrite my windows system!!!!

Any help appreciated.

---

### Post by papibe on 2012-04-12
Hi heartofwhite. Welcome to the forums!

It looks like your target is sda5, however I would recommend this procedure so you are 100% sure.

When booting on the Ubuntu install CD/USB, choose 'Try Ubuntu' instead of install. When you get to the desktop, run gparted.

You'll see a graphical representation of your disk (something similar to this [pic]("http://gparted.sourceforge.net/larry/resize/big/resize-6-b.gif")). There you will have no doubt, because you are looking for empty NTFS partition that is around 60Gb in size.

Take note of the partition (like sda5 if my guess is correct). Close gparted, and click on the icon 'Install Ubuntu' to start the installation process.

IMPORTANT: although the installation process is pretty safe, it is always a good idea to backup your data before an OS install. Note that if something goes wrong, you may temporally loose the ability to boot into Windows. That can be easily solved by using the Windows recovery CD (or booting into the recovery partition).

Hope that helps, and tell us how it goes.
Regards.

---

### Post by heartofwhite on 2012-04-14
Hello Papibe,

Thank you for all the advice it was very helpful! It turned out to be sda 5. I am just getting started with Ubuntu now, but finding the forums very good.

---

### Post by papibe on 2012-04-14
Glad you solved it :). Please mark the thread [solved]("https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads") when you have the chance.

Come here often and have fan ):P

Regards.

---

