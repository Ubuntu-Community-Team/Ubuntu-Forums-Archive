---
title: "Ubuntu won't boot up"
date: 2012-04-03
forum: New to Ubuntu
---

### Post by msinfo on 2012-04-03
Hello Experts,
1. I have computer with dual boot system with Window 7 Ultimate and Ubuntu 10.04.
2. For past few months I was not using Ubuntu.
3. But when yesterday, I tried to log on machine using Ubuntu it failed.
4. Kindly suggest a solution without need to format Ubuntu partition as some data is very important.

Part of error message : 
mount: mounting /dev on /root/dev failed: No such file or directory
mount: mounting /sys on /root/sys failed:  No such file or directory
mount: mounting /proc on /root/proc failed:  No such file or directory
Target filesystem doesn't have /sbin/init.
No inint found. Try passing init=bootarg

(initramfs) _

Error Image:  I have attached a picture of what I see on screen, because I am in doubt that error is because of hard disk. Since Windows 7 part is running perfect, but it is Ubuntu which is not running.

With regards : msinfo

---

### Post by kc1di on 2012-04-03
Have you upgrade to grub 2 or still using grub legacy?

if you have grub two you can try the following page to reinstall grub and see if it will correct the problem.

[http://www.dangibbs.co.uk/journal/repair-restore-grub-2-with-ubuntu-10-04-live-cd]("http://www.dangibbs.co.uk/journal/repair-restore-grub-2-with-ubuntu-10-04-live-cd")

---

### Post by starz677 on 2012-04-03
Not sure your ultimate goal but if recovering the data is your primary goal, you may not have to repair grub at all.

Place the hard drive in another computer (even Windows) and you should be able to access and copy any important files as long as the file system is not damaged.  (documents, photos, audio files etc).

It's not always necessary to have a hard drive or OS boot up to get important files off of it.

In fact, if recovering important files is your main goal, I would try that first since once you start attempting to reinstall grub etc, it can damage the file system index tables.

---

### Post by critin on 2012-04-03
starz677

Good idea.  Couldn't he do that where it is since he has Win7?  I used to have both systems on one comp and could get to my ubuntu partition through Win.

---

### Post by msinfo on 2012-04-04
Hi,
Thanks friends, for your suggestions.

>kc1di
Going through that link and trying to understand how to use that info. Would update soon about results.

>starz677 and critin
I have got through data recovery problem, using live CD. I transfered data from Ubuntu to Win 7 partition. 
I had to use Live CD because I had used different file system for Ubuntu and Win 7. So I can access my Win 7 partitions from Ubuntu but can't access Ubuntu partitions from Win 7.
 
So now, is there any repair or recovery method available which can correct Ubuntu boot problem.
(Currently reading more about option given by kc1di)

With regards : msinfo

---

### Post by msinfo on 2012-07-13
Hey hi,
1.  As, through this forum, we come to know that problem was with boot manager/grub settings.
2. So, I wanted to know more about it, and wanted to troubleshoot it by myself.
3. But my work/job and other things, kept me away from this. And, I continued using Windows 7.
4. But, today some blue screen error, occurred, and I chose, Repair option in boot menu of Windows 7.
5. I restarted computer, and since, my default OS is Ubuntu it got started.
6. This may sound, strange, but this happened, and my problem got solved.
7. Thank you Window7 . . . for making my Ubuntu on.
8. I am still wondering, on inner working of boot/grub system.

With regards : msinfo

---

