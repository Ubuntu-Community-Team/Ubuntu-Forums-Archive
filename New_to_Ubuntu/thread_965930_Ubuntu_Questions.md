---
title: "Ubuntu Questions"
date: 2008-10-31
forum: New to Ubuntu
---

### Post by avery1555 on 2008-10-31
Okay, so I just ordered my disc of Ubuntu and have 9 weeks to kill until I get it, however, I do have some questions.

I like my Windows, I will not lie, but I want to Dual Boot. Can anyone supply a tutorial on how to Dual Boot using the CD Ubuntu offers? Or, if I do replace Windows, is there any way I can get it back after, im not very good with formatting and that without system recovery.

Will my standard EXE files work on Ubuntu?

Im on a laptop, will my Wireless Adapter work with Ubuntu without installation? This is important.

I appreaciate answers, thanks!

Avery1555

---

### Post by phidia on 2008-10-31
You need to tell us what make and model laptop you have-the more detailed the better.

Dual booting guides are available [here]("https://help.ubuntu.com/community/WindowsDualBoot") at the ubuntu wiki. While you're at the wiki you can browse around there are many useful howtos there.

---

### Post by avery1555 on 2008-10-31
Its a Gateway laptop running XP. Its about 3 years old, but I dont know exactly what it is.

---

### Post by OutOfReach on 2008-10-31
> **avery1555 said:**
> 
Will my standard EXE files work on Ubuntu?

Im on a laptop, will my Wireless Adapter work with Ubuntu without installation? This is important.


.exe files *do not* work under Ubuntu or any other Linux distro for that matter. There is WINE ([www.winehq.com](www.winehq.com)) to run .exes but it is still under development and it may not work all the time.

For the wireless adapter, try out the LiveCD (when your CD comes) to see if it works correctly.

---

### Post by avery1555 on 2008-10-31
Thanks, guys.

Avery

---

### Post by melojo on 2008-10-31
> **avery1555 said:**
> Okay, so I just ordered my disc of Ubuntu and have 9 weeks to kill until I get it, however, I do have some questions.

I like my Windows, I will not lie, but I want to Dual Boot. Can anyone supply a tutorial on how to Dual Boot using the CD Ubuntu offers? Or, if I do replace Windows, is there any way I can get it back after, im not very good with formatting and that without system recovery.

Will my standard EXE files work on Ubuntu?

Im on a laptop, will my Wireless Adapter work with Ubuntu without installation? This is important.

I appreaciate answers, thanks!

Avery1555

howto install
[http://www.howtoforge.com/the-perfect-desktop-ubuntu-8.04-lts-hardy-heron](http://www.howtoforge.com/the-perfect-desktop-ubuntu-8.04-lts-hardy-heron)
This shows you how to install using the entire disk but you can choose to repartion and use free space and keep windows.

Geting it back if you don't like Ubuntu.

Yes you can, you will have to use your Windows installation disk to remove grub, but then you will have an unused partition.  

You can use the ubuntu installation cd to delete and repartition your windows drive.  This should work but nothing is fail safe, make backups of all important stuff just in case something goes wrong.

Running .exe files

Natively Linux does not run window programs but some emulation software is available called wine or you can install a virtual terminal that will allow you to run other operating system within linux.

Wireless

It may work out of the box or maybe not, it depends on the card.

Try the live cd when you get it and if it picks it up then you won't have any problem.  If it does not pick it up then extra work will be involved in getting it to work.

Hope this helps

---

### Post by cariboo on 2008-10-31
One other thing to do is to have a look at this:

[http://ubuntuforums.org/showthread.php?t=63315](http://ubuntuforums.org/showthread.php?t=63315)

Read the first post, it will put you in the right frame of mind.

Jim

---

