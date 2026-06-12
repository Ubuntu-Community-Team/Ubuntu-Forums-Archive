---
title: "[SOLVED] youtube, cinetube, and brother printer do not work"
date: 2008-09-02
forum: New to Ubuntu
---

### Post by ejv on 2008-09-02
Hi
I just installed ubuntu some hours ago, but I've been having some problems. Please note that I've got absolutely no idea how to type in codes or bashes or those things.  I did find the terminal and tried to create a directory 

cd ~/Desktop

but it didn't work.

1) When I try to look videos in internet, for example in youtube or cinetube or yahoo videos, the pages appear complete on the screen, but the videos don't work.  I tryed to install Adobe flash player but I'm not sure if it worked. 

2)  My Brother DCP 110C is also not working.  I've already read the threads about similar problems, but they are a step ahead of me.  I have not been able to find out which ubuntu (Hardy Heron, or Gnome, or ...) I downloaded. Where should I look for all that information?

Thanks to anyone willing to help...

Cheers

ejv

---

### Post by Vadi on 2008-09-02
1) Try clicking [here]("apt:ubuntu-restricted-extras"). It'll install a whole bunch of programs that are commonly used, like Flash. Restart Firefox, and youtube should work.

By the way, a Desktop folder is created automatically at installation. You can also see it via Places - Desktop.

2) Chances are, you're using Ubuntu, with the Gnome desktop enviroment (sorry if it sounds confusing at first). 

To verify that, click on System (in the top bar), do you see it saying "About Gnome"? If yes, then you're on Gnome. And for the Ubuntu version, go to System - Administration - System Monitor, and click on the first tab. Does it say "8.04" anywhere? If yes, then you're on Ubuntu 8.04 "Hardy Heron".

---

### Post by SunnyRabbiera on 2008-09-02
> **Vadi said:**
> 1) Try clicking [here]("apt:ubuntu-restricted-extras"). It'll install a whole bunch of programs that are commonly used, like Flash. Restart Firefox, and youtube should work.

By the way, a Desktop folder is created automatically at installation. You can also see it via Places - Desktop.

2) Chances are, you're using Ubuntu, with the Gnome desktop enviroment (sorry if it sounds confusing at first). 

To verify that, click on System (in the top bar), do you see it saying "About Gnome"? If yes, then you're on Gnome. And for the Ubuntu version, go to System - Administration - System Monitor, and click on the first tab. Does it say "8.04" anywhere? If yes, then you're on Ubuntu 8.04 "Hardy Heron".

the link you gave does nothing in firefox you know.

here is one way to get media though:
[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

---

### Post by Vadi on 2008-09-02
It should work fine if you have apturl installed (which is by default since 7.10)...

---

### Post by ejv on 2008-09-02
So.  I tried both of them.  I dowloaded the whole package and the complete Medibuntu repositories.  Youtube still doesn't work.  What now?

I now know that my version is a Hardy Heron with Gnome enviroment.

Thanks

ejv

---

### Post by kansasnoob on 2008-09-02
I recently found what seems to be the perfect work-around for flash in Hardy, look here:

[http://ubuntuforums.org/showthread.php?t=906896](http://ubuntuforums.org/showthread.php?t=906896)

But read it all! I did a bass-ackwards job with the instructions.

I'd have to do some research on the printer problem.

---

### Post by ejv on 2008-09-02
Hey, thanks a lot, to all of you.

In the meantime I also found something. A Thread called

**Comprehensive Multimedia & Video Howto ** from  ubuntu freak

Simply great.  It solved the video problems.

Thanks for doing the research on the printer.  Everything seems to be ok, automatically recognized and when i give the order to print the little icon appears on the upper bar, but... no result, nothign comes out of the machine!

ejv

---

### Post by plucky on 2008-09-03
> 2) My Brother DCP 110C is also not working. I've already read the threads about similar problems, but they are a step ahead of me. I have not been able to find out which ubuntu (Hardy Heron, or Gnome, or ...) I downloaded. Where should I look for all that information?


The Brother drivers are now packaged in the Synaptic package Manager.
Go to **System > Administration > Synaptic** and search for "brother" without the quotes.Select the boxes for "brother-cups-wrapper-extra" and brother-lpr-drivers-extra" and select **Apply**.

This will install the drivers for your printer.Plug your printer in and turn on,then go to **System > Administration > Printing** and select "New Printer" .The system will find your printer and install it.Just select it as default and configure the options you want.


Good Luck

---

### Post by ejv on 2008-09-06
Everything ok now.  Thanks a lot. Thread solved.

=D>

ejv

---

