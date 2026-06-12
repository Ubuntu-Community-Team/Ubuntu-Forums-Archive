---
title: "My Memory (RAM) is &quot;stuck&quot; at 80-90% ?"
date: 2013-01-10
forum: New to Ubuntu
---

### Post by sunjet on 2013-01-10
My specs:
RAM: 2.0 GiB
CPU: AMD Athlon(tm) II X3 425 Processor × 3 
Graphics : VESA: REDWOOD   (wtf?)
OS : 32-bit
HDD : 492.3 GB


Image of System Monitor : [http://i.imgur.com/zT8Uj.jpg](http://i.imgur.com/zT8Uj.jpg)


I'm using latest Ubuntu 12.10  installed on a clean formatted HDD.

And if I open 5-6 tabs in Chromium, and playing a movie, or searching thru Ubuntu Software Center, it's crashes the loading tabs, or sometimes the application opened :( due to low memory.

---

### Post by sandyd on 2013-01-10
2GB of RAM is a bit too little for the (current) ubuntu version

Try something lighter like Xubuntu/xfce Lubuntu/lxde

---

### Post by sunjet on 2013-01-10
I prefer Ubuntu, will 12.04 run fast?

---

### Post by Frogs Hair on 2013-01-10
12.10 System Requirements per the Ubuntu Wiki are as follows , but know I nothing about your graphics card/chip and how that may play into the memory use.  

> The minimum memory requirement for Ubuntu 12.10 is 768 MB of memory and 5 GB of disk space for Ubuntu Desktop. Note that some of your system's memory may be unavailable due to being used by the graphics card. If your computer has only the minimum amount of memory, the installation process will take longer than normal; however, it will complete successfully, and the system will perform adequately once installed.

[https://wiki.ubuntu.com/QuantalQuetzal/ReleaseNotes/UbuntuDesktop](https://wiki.ubuntu.com/QuantalQuetzal/ReleaseNotes/UbuntuDesktop)

---

### Post by sunjet on 2013-01-10
my graphic card is

ATI Radeon HD 5670 - 512 MB

---

### Post by dannyboy79 on 2013-01-10
I use Xubuntu 12.04 and I can attest to running Chromium with 7 tabs open, trying to do video editing in kdenlive, skype open, nautilus windows open, and a terminal open I run out of memory eventually also and an app will close due to running out of memory. Or chromium tab will bring up a box that says page is unresponsive. I have 2GB of RAM just like you.

You can check top, then hit shift+o, then sort by hitting o and it will put all the highest memory hogs at the top. there are some you can kill I beleive but not many.

2GB is just not enough for multi-tasking anymore like it used to be a few years back.

---

### Post by Peripheral Visionary on 2013-01-10
Part of it is the way the kernel works.  It's worth having a look at this page because it answers alot of frequently asked questions from new users about Linux and RAM:

[Help!  Linux ate my RAM]("http://www.linuxatemyram.com/")!

---

### Post by sunjet on 2013-01-10
So then why my Ubuntu is going so slow on 2GB RAM, if all RAM is free.

Few tabs with youtube, and => crash.


sunjet@sunjet:~$ free -m
             total       used       free     shared    buffers     cached
Mem:          2014       1647        367          0          8        158
-/+ buffers/cache:       1480        534
Swap:            0          0          0
 


NO apps running, 534 MB Free from 2gb?   =\

---

### Post by Cheesemill on 2013-01-10
With that amount of RAM you really should have a swap partition (or file). Swap is used when you are running low on RAM to prevent the system running out of memory and crashing.

[https://help.ubuntu.com/community/SwapFaq](https://help.ubuntu.com/community/SwapFaq)

---

### Post by Frogs Hair on 2013-01-10
Do you clean the Chromium cache and history regularly ? I use Chrome and it is bit of resource hog on my computer and the cache fills quickly. I rarely have more than three tabs open though.

---

### Post by snowpine on 2013-01-10
If you click on the Processes tab in System Monitor, you can see exactly which processes/applications are using the most RAM.

I agree with the suggestion above to create and mount a swap partition.

---

### Post by sunjet on 2013-01-10
Yeap, they are often clear. I was really happy going from Windows 7 to Ubuntu, like it allot, but when I saw how he's "eating" a lots of RAM, with cache and stuff, I'm confused what to do, reinstall the Ubuntu and create a 6-8Gb swap space, or to go back on Win 7 :\

With that swap space there will be a visible difference or not...?

---

### Post by sunjet on 2013-01-10
I reinstalled my Ubuntu 12.10 and added 10GB swap area.

and this is the System Monitor now:

[http://i.imgur.com/hZnD4.jpg](http://i.imgur.com/hZnD4.jpg)

And I see that there is Unknown Graphic card, while in the last was that "VESA: REDWOOD"


Maybe the problem was in the graphic driver? 

How to install a clear latest driver for my ATI Radeon HD 5670 ?

---

### Post by Cheesemill on 2013-01-10
To install your graphics card drivers open the Software Sources application, and click on the Additional Drivers tab.


System Settings always shows Unknown, even if you do install the correct drivers. You can fix this by installing the mesa-utils package.

---

### Post by sunjet on 2013-01-10
this is how it's supposed to be? :

[http://i.imgur.com/pafag.jpg](http://i.imgur.com/pafag.jpg)

Or to choose the second or third?

---

### Post by Cheesemill on 2013-01-10
You want to choose the 2nd option to install the fglrx driver.

---

### Post by sunjet on 2013-01-10
Thank you.

---

### Post by edeneen on 2013-01-10
nonsense,  I am running 12.04 on an ancient machine with 2 gigs memory and it runs great, system monitor says I have memory to spare

---

### Post by Cheesemill on 2013-01-11
> **edeneen said:**
> nonsense,  I am running 12.04 on an ancient machine with 2 gigs memory and it runs great, system monitor says I have memory to spare
Maybe you do, but it's not nonsense.

Did you look at the screenshot in the original post? It clearly shows that the system was using all of its RAM and not having any swap was causing it to crash.

---

