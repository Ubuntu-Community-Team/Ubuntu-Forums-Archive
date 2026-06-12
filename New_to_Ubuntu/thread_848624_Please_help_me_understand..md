---
title: "Please help me understand."
date: 2008-07-03
forum: New to Ubuntu
---

### Post by sparkyee on 2008-07-03
I am a beginner in Linux. I have some questions to ask to what they mean. I just got the book on ubuntu. The official ubuntu book, second edition. As my computer now is windows xp. I would just like to use more of Linux. I tried to install ubuntu on the boot up. It got to  where it was ready to start i think and it was just a light blue screen. And i quit after about 10 minutes of waiting for it to do something. 

  Can anybody explain what is going on? the computer is about 2.5 years old now. it has  chaintech motherboard and i think a chaintech video card.  this computer is wearing out so i did build a new computer with windows xp pro on it. I am right now posting this on the old computer. I want to see if i can get ubuntu to work on this computer. 

  I have other questions to of what does grub mean? and what is the meaning of beryl?

  I am a electrician and i have a saying on the job to keep it simple. Please just keep it simple. More people will try and switch to linux if it is simple to use in my opinion.

                                            thanks

---

### Post by bubba_169 on 2008-07-03
1. Not sure what happened when you tried to install, maybe wit more information we could diagnose...

2. Grub is the bit of code that lives at the very beginning of your harddrive (well it will be after you've installed linux) that tells the computer where to look for the important files needed to load the operating system

3. Beryl is a window manager (it draws windows on the screen and controls when you move them etc) with lots of special effects. Its a bit outdated now though and it was recently merged with compiz to form compiz fusion!
Compiz fusion is what makes your menus fade and windows wobble :D

---

### Post by atomkarinca on 2008-07-03
If the cd is hanging then probably it's not burnt properly. Try to burn your cd's at 4x (600 kiB/s) or less speeds. [GRUB]("http://en.wikipedia.org/wiki/GNU_GRUB") simply lets you select various OS's at the boot. You don't need to know about that a lot. Beryl is a composite manager which means you can do productive (*and* cool) stuff with your 3d-accelerated graphics card. Although now Beryl has merged with Compiz and it's called [Compiz Fusion]("http://en.wikipedia.org/wiki/Compiz_fusion").

---

### Post by defrex on 2008-07-03
Can you describe in more detail what happens when you boot from the CD? Do you get to a screen where you can pick a language?

Grub is what's called a bootloader. It is the first thing the computer runs, and it tells the computer where to look for the operating system.

---

### Post by easybake on 2008-07-03
A good way to test out Ubuntu is to simply use a livecd of it. Just burn the disk image from the website onto a cd.

---

### Post by Xzallion on 2008-07-03
It seems the regular install cd has problems running as a live cd on your computer. (Live CD means it allows you to test the OS before installing it).

Since its an old machine, if you can back up and files you want to keep to CD's, DVD's, or your newer computer then you could try to use the Alternate-Install cd.  It installs in a text mode (don't worry, it gives you the options and does a decent job explaining what its doing, you should make it through it just fine.)  Once thats installed you should be able to find and install the correct video-card drivers.  You can download the alternate cd here [http://www.ubuntu.com/getubuntu/download]("http://www.ubuntu.com/getubuntu/download") just make sure to check the little checkbox on the bottom for the alternate cd.  Instructions for burning the alternate cd can be found here [https://help.ubuntu.com/community/BurningIsoHowto]("https://help.ubuntu.com/community/BurningIsoHowto").

Grub is the bootloader for Ubuntu, and one of the two main bootloaders out there. (The other one is LILO).  Theres a good article on them on wikipedia here [http://en.wikipedia.org/wiki/Booting]("http://en.wikipedia.org/wiki/Booting") and here [http://en.wikipedia.org/wiki/GRUB]("http://en.wikipedia.org/wiki/GRUB").

Beryl / compiz etc are applications to add pretty effects to the desktop, like transparent windows, and weird minimizing/maximizing effects.  They aren't needed, can cause problems, but are pretty.  A quick search for Compiz-fusion on the forums will yield more information if your interested.

Hope that helps.

---

### Post by appi2012 on 2008-07-03
Try burning at a slower speed. Follow the guide here:
[http://www.psychocats.net/ubuntu/iso]("http://www.psychocats.net/ubuntu/iso")

---

### Post by gator42 on 2008-07-03
I noticed that you mentioned you got the official Ubuntu Book. It is the same one I used to learn more. It came with a cd right? And I think it is 7.04, my CD did not work also. I needed to down load the image and burn a disk to get it to work.

That is a good starter book, once you get it installed it will help out with the basics.

---

### Post by sparkyee on 2008-07-03
Yes the dvd/cd was in the back of the book. and it is the 7.04 version of Ubuntu.  i tried to install it like a live cd i think. it ran for a little bit. by that i mean i see the screen with ubuntu and the little line going back and forth and then across and then it just goes to a somewhat light blue screen. I let it sit for about 10 minutes like that and then had to shut it off as i had to go to work. 

   I am not going to give up yet.  the video card is a chaintech volari v3. If that helps?   and the mother board is a chaintech, a model 7njl6 with a nivida- nforce 2 ultra 400+ mcp-s.  I guess over the hill now.

  Just built a new one with a asus mother board. a m2n-mx se plus. i wonder if it will work with Linux? 
  
      thanks everybody for posting on here.

---

### Post by cariboo on 2008-07-03
How much ram does the computer have as that will make a difference. Also try running the LiveCD in safe graphics mode. Up until hardy that is the only way I could get the LiveCD to work on my system.

Just so everybody knows grub stands for GRand Unified Bootloader

Jim

---

### Post by kansasnoob on 2008-07-03
[http://www.psychocats.net/ubuntu/index](http://www.psychocats.net/ubuntu/index)

---

