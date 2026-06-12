---
title: "Wubi Not Working, 'error prefix', purple screen"
date: 2013-11-03
forum: New to Ubuntu
---

### Post by candyshimmer7 on 2013-11-03
I downloaded the dual boot on a windows 7 HP computer. It's a 32 bit laptop. The install went fine and when it rebooted itself, it went fine; and I could use ubuntu. Then when I cut the computer off and back on, it gives me the options of Windows or Ubuntu. When I choose windows it's fine. But, when I choose Ubuntu some quick words pop up. Then it says something so fast I can't read the whole thing. It's one line and what I can make out after the standard initial booting words is:

error prefix (and about eight other words that flash too fast for me to read)

Then it goes to a purple screen, then it goes to a screen that's the same purple for about 3 inches on the top and black for 6 inches on the bottom. Then it goes to black screen. 

I have uninstalled and reinstalled wubi 3 times. Is this a problem I can fix? I had the dual boot on an old computer and loved having both the systems. it was a great way to get used to Ubuntu and learn it, but I had to pawn that old computer. I wish I could get it on this one so I could get back using it again. The whole boot disk and usb thing never worked for me then when I tried it and it's confusing now when I try to figure it out. Is there any way to get this wubi working?

---

### Post by Impavidus on 2013-11-04
Sounds like a graphics driver issue to me. Adding the nomodeset parameter may help. See [http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132), read post #8, method 2. It's somewhat older, but I think it should still work.

Wubi is being discontinued, mostly because it doesn't work with Win8, but it has never been a very reliable way of installing Ubuntu and has always been confusing. A wubi install is no dual boot. It is an Ubuntu installation in a virtual partition on a Windows partition, relying on both the Linux and Windows file systems. It does allow you to test Ubuntu for a while without repartitioning the drive, but it's so confusing that many beginners don't realise this and think they have a normal dual boot, just installed the easy way. Then they wonder why they only have 30GB disk space available or why it doesn't work anymore when they delete Windows.

As wubi is being discontinued and has never been used much by the more experienced Ubuntu users, there isn't too much experience with it to be found on these fora. We usually recommend true dual boots, installed from a live disk. So, if you'd like to try that road after all, what problems do you have with the live dvd/usb?

---

### Post by mastablasta on 2013-11-04
to try it out it is easier to try it in live session, live session with persistence or to use virtualbox (or similar virtualisation software): [http://www.psychocats.net/ubuntu/virtualbox](http://www.psychocats.net/ubuntu/virtualbox)

---

### Post by candyshimmer7 on 2013-11-04
Okay. I'm going to the store now to pick up the usb. I just really don't know why it didn't work. I tried pendrive linux and tried burning it to a cd and it wouldn't work or I just didn't understand the directions. I know that I'm very confused with most things I read regarding Ubuntu installs, so maybe if you can point me to directions that say things like:

**type, "run"**

*instead of*

**now run boot loader**

It took me so long to figure out that **"run boot loader"** might mean type **"run"** and I'm still not so sure that I'm right about that either. 

The basics of what I want to do:


[LIST]
[*]I'm getting a usb drive 4mb and
[*]would like to put a dual boot
[*]on an hp laptop
[*]running windows 7
[*]32 bit
[/LIST]

---

### Post by candyshimmer7 on 2013-11-04
I deleted this post (which was an addendum to the question above), but I still do need an answer to the previous question, if anyone has the time or the ability to help.

---

### Post by Impavidus on 2013-11-04
Read the documentation on live usb here: [https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

A complication you may encounter is that you drive may use mbr formatting with all primary partitions already in use. This is often the case with HP laptops with Win7. When running the live usb you can open the program gparted (installed by default on the live disk) and have a look at the partitions. If it shows four primary partitions and no extended partition with mbr partitioning, you have a small problem. If you don't understand, post a screenshot of gparted here. This page has some ideas on how to solve it: [http://askubuntu.com/questions/149821/my-laptop-already-has-4-primary-partitions-how-can-i-install-ubuntu](http://askubuntu.com/questions/149821/my-laptop-already-has-4-primary-partitions-how-can-i-install-ubuntu). Feel free to come back for any more questions.

---

