---
title: "Several Problems from the Start"
date: 2012-07-23
forum: New to Ubuntu
---

### Post by ahalstead on 2012-07-23
Hello everyone!

This will be my first time posting to the forums, and I have quite a few issues to discuss.  First, since last night, I have wiped out my hard drive in my Dell Inspiron 1526 and I first reinstalled Windows Vista.  Then today, I installed some of the necessary drivers.  Then I moved on to installing Ubuntu 10.10 (Maverick Meercat) from a CD-ROM.  After messing with the partitioning for about an hour, I finally got it installed.  Now here are my problems:

1.) The first time I logged in it worked for maybe twenty minutes before it froze.  Ever since, I either get the default background and the mouse cursor with nothing else or it will let me in with the desktop for about eight seconds before it freezes.  What could be wrong and how do I fix it?

2.) Once I can get in without it freezing, I want to install the necessary drivers for the Internet.  Does anyone know which drivers I need, where they are located, and how to install them?

3.) Once I am connected to the Internet, I want to upgrade from 10.10 to 12.04.  What is the easiest way to do this?

Thanks to anyone who contributes toward any solution I ask for.  It is greatly appreciated and will help me to use Linux better and to become a part of the community.

Oh, and in the meantime, I found this.  :guitar:  Thanks!

---

### Post by drudogg76 on 2012-07-23
I don't know if this applies to Dell machines, but I had a VERY similar issue on my Toshiba Laptop when I installed Ubuntu. After some "googling" I discovered that it had to do with my wireless network card. 

The solution was really one of the most ridiculous, but it worked.
Go into your boot order and set it to try a "network boot" first, then HDD or CD or whatever you want after that.  As long as "network boot" is before Ubuntu tries to load, then it lets me in without freezing. 

Anyway, just throwing it out there.. I was reluctant to try this seemingly odd solution - but it worked like a charm. :)

---

### Post by lakona on 2012-07-23
Do you have problems when you boot from the live CD?

---

### Post by Curtis6767 on 2012-07-23
> **ahalstead said:**
> Hello everyone!

2.) Once I can get in without it freezing, I want to install the necessary drivers for the Internet.  Does anyone know which drivers I need, where they are located, and how to install them?

3.) Once I am connected to the Internet, I want to upgrade from 10.10 to 12.04.  What is the easiest way to do this?  

In answer to your 2nd question, Ubuntu should be able to find and install the appropriate drivers during the install.  A lot of times people will think that they need to install drivers and then run into problems. I'd wait and see how things go before trying to install drivers for internet, etc.

Which leads me to your third question. Since this is a fresh install of 10.10, then I would recommend that you download the ***alternate*** 12.04 iso and then do a fresh install of 12.04 in the partition that you've created for 10.10. The upgrade from 10.10 probably won't go well and in the end you'll probably have to do a fresh install anyway. But don't go for the regular ISO. Go for the alternate ISO, which is text-based rather than graphical. It will be easier on your system.

Once you get 12.04 installed and if you are still having internet problems, then start a new thread with those problems and someone here can probably help with that.

---

### Post by Cheesemill on 2012-07-23
> **ahalstead said:**
> 3.) Once I am connected to the Internet, I want to upgrade from 10.10 to 12.04.  What is the easiest way to do this?

The easiest way is to install 12.04 to start off with.

There is no direct upgrade path from 10.10 to 12.04, you would have to upgrade to each of the intermediate releases on the way meaning 3 entire system upgrades:
10.10 > 11.04
11.04 > 11.10
11.10 > 12.04
Each one of these has the chance of breaking your installation, and troubleshooting these sort of upgrade problems can be tricky, you are much more likely to have no problems if you just perform a clean install of 12.04 to start with.

Also later versions contain drivers for more and newer hardware, so chances are you won't need to install any drivers to get your internet working.

---

### Post by ahalstead on 2012-07-23
Thanks for the help, guys!  The overall message I am receiving is what I knew I should have done from the start: just install 12.04 to begin with.  I am downloading the ISO for it as we speak and it will be burnt to a CD and installed shortly.  Do you have any advice for how I should go about overwriting 10.10 with 12.04?

---

### Post by lakona on 2012-07-23
Unless there is a reason you want to use an older version of Ubuntu (I choose to run 10.04), you might as well install the latest version. 

I don't like the new gnome desktop and have not worked much with the unity interface so that's why I am happy with my Lucid install.

Run the OS from the live CD first and make sure it is working before you install.

If you are still having a problem, let us know. Honesty, I don't see why you couldn't get the older version to run; but that the newest version would.

If it does work from the live CD, select the **Specify partitions manually (Advanced)** option during the installation and format over the current (10.10) installation. If you only have Ubuntu and windows you will see three partitions. One with windows which will be formated to NTFS, The other will be ext3 or ext4 that has Ubuntu, and the third (if it exist) is the swap partition (the Ubuntu equivalent of the page file).

Good luck.

---

