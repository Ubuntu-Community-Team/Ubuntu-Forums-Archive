---
title: "Dual boot on 128gig possible?"
date: 2012-12-10
forum: New to Ubuntu
---

### Post by shimbalama on 2012-12-10
Hi All,

Just wondering if I can have both win 7 (64) and ubuntu on a 128 gig SSD and if so whats the best way to do it?

Cheers,
Liam

---

### Post by levlaz on 2012-12-10
This is absolutely possible, and should be pretty simple. 

All you have to do is make a new partition for Ubuntu. 

If windows 7 is currently installed and is taking up all 128GB of space you can shrink this using the built in tool in windows 7.  You can choose how much space you want to devote to the Ubuntu installation. 

For example if this is a fresh install of Windows 7 you should be able to get anywhere from 60-80GB out of the 128GB for the Ubuntu installation. 

After you shrink the drive. You can reboot with either the Live DVD or a USB stick and Ubuntu will automatically recognize the free space and install side by side with Windows 7. 

After you let it install, you should be able to dual boot when you reboot. Each time you reboot you will be given a choice of which partition you want to boot from. 

Just an FYI if this is a completely empty drive, make sure you install Windows 7 BEFORE installing Ubuntu, from past experience installing Windows on top of Linux always messes things up. 

Let me know if you need more detail on how to perform these specific tasks, but it should be straight forward. Just make sure you back up all of your data before you begin! :)

---

### Post by Jmackxxx on 2012-12-10
Lev, hit it on the head...Don't forget a Logical partition  for swap space... I also installing Home folder on separate partitions

---

### Post by PapaNerd on 2012-12-10
I have a dual-boot MacOS/Ubuntu laptop running on a 60G drive, but things are tight.  Some of the answer depends on how many extra apps you install under Windows, but 50%:50% arrangements are possible, or even 60% (Windows) : 40% (Ubuntu).

---

### Post by pqwoerituytrueiwoq on 2012-12-10
128gb sounds like a ssd, don't put swap on a ssd

---

### Post by Jmackxxx on 2012-12-10
> **pqwoerituytrueiwoq said:**
> 128gb sounds like a ssd, don't put swap on a ssd
Good point if its solid state.  Thats a question to ask..

---

### Post by levlaz on 2012-12-10
OP said it was a 128GB SSD. 

I just did this same thing on a Win7 Dell, not SSD but the new 12.10 Installer is a breeze for dual booting.

---

### Post by shimbalama on 2012-12-10
thanks heaps for ur prompt responses guys. Was just trying to decide if I want to buy a new laptop. think I will. Any comments on the pros cons of running ubuntu inside windows as a virtual machine vs dual booting?

---

### Post by SparkyPrawn on 2012-12-10
> **levlaz said:**
> OP said it was a 128GB SSD. 

I just did this same thing on a Win7 Dell, not SSD but the new 12.10 Installer is a breeze for dual booting.

Even 12.04 made dual booting a breeze. I haven't tried it on a SSD, so I wouldn't know the logistics of it.

On a normal drive it is easy peasy!

> **shimbalama said:**
> thanks heaps for ur prompt responses guys.  Was just trying to decide if I want to buy a new laptop. think I will.  Any comments on the pros cons of running ubuntu inside windows as a  virtual machine vs dual booting?

For me, I prefer to just dual boot or only run Ubuntu. I know many people who run it inside a Virtual Machine, which would get rid of any difficulties of partioning. Plus, you're still running Windows for any programs that you can't run through WINE. 

I know my brother runs Ubuntu in a virtual machine on top of Windows 7 for any development he needs to do, and to make testing any applications a breeze. I find it overwhelming to be running both, and since I rarely use any programs I can't run natively on Linux or through WINE, I just use Ubuntu or some other flavor of Linux.

---

### Post by mastablasta on 2012-12-11
> **shimbalama said:**
> thanks heaps for ur prompt responses guys. Was just trying to decide if I want to buy a new laptop. think I will. Any comments on the pros cons of running ubuntu inside windows as a virtual machine vs dual booting?
 
 
a few are layed out here: [http://www.psychocats.net/ubuntu/virtualbox](http://www.psychocats.net/ubuntu/virtualbox)
 
also virtual ubuntu has no 3D (or at least not porpper one) i believe.
 
depends why you need it for. if oyu need a fast boot OS on your disk then dual boot is better if you want to just browse internet do some testing then vbox is better.

---

### Post by audiomick on 2012-12-11
> **pqwoerituytrueiwoq said:**
> 128gb sounds like a ssd, don't put swap on a ssd

Look at this
[http://www.storagesearch.com/ssdmyths-endurance.html]("http://www.storagesearch.com/ssdmyths-endurance.html")

In short, in the section about the "Rogue Data Recorder", the author relates how he had calculated that if a program were to be writing data constantly at the highest rate to a 64GB SSD, it would take about 50 years to reach the limit of the write endurance.

Given that a modern system with a "normal" amount of RAM and during "normal" use barely ever has to use the swap space, I don't think there is a real problem.

---

### Post by NightsShadeQueen on 2012-12-11
IMO, swap takes up significant space on a ssd (4gb/128gb vs 4gb/320gb) and OP's going to be pretty space-tight already.

If it's rarely used, why have it?

---

### Post by memilanuk on 2012-12-11
So don't use 4 GB of swap.  Use 2 GB.

Honestly... with modern systems and the copious amounts of RAM... when was the last time you used *any* significant amount of swap?  For most people the answer is very rarely or never.

---

### Post by audiomick on 2012-12-11
> **NightsShadeQueen said:**
> IMO, swap takes up significant space on a ssd (4gb/128gb [COLOR="Blue"]vs 4gb/320gb[/COLOR]) 

Where did the OP mention having a second drive?

> 
If it's rarely used, why have it?

In fact, it is quite likely  that the system would run without any swap. For most usage, 1GB would be more than enough.

If the system needs to be able to hibernate, the swap needs to be a little larger (a couple of MB) than the installed RAM. The hibernate function writes the contents of RAM to the swap space in order to be able to re-instate it later.

> 
and OP's going to be pretty space-tight already.

With 128GB. My last desktop, which I used up until about 5 years ago, had two drives for a total of 16GB...

Space and lack thereof is relative. 128GB is enough to get two installs going quite comfortably. If the OP has need for storage more than the machine allows, then an external drive is likely the answer. I would suggest that before changing the 128GB internal, which I assume is the one that the machine came with, for a larger internal. There are many ways to get to a desired outcome, however.

---

### Post by Toriku on 2012-12-11
do you need to put Ubuntu on your SSD? What Ubuntu apps will you be running in a hurry? Perhaps you will want it on SSD but think about how you will use the Windows partition (space for intensive games for example)

---

### Post by soccnut on 2012-12-12
> **Toriku said:**
> do you need to put Ubuntu on your SSD? What Ubuntu apps will you be running in a hurry? Perhaps you will want it on SSD but think about how you will use the Windows partition (space for intensive games for example)

Im currently running the configuration OP mentioned, with my win 7 installation taking up about 70GB and Ubuntu 16GB, still have space to spare.

One reason for installing Ubuntu on my SSD is to reduce the amount of time needed to boot up.

---

### Post by squakie on 2012-12-12
One reason FOR swap is that the OP said they were looking at a new laptop.  IF they want to hibernate they must have swap.

---

### Post by asifnaz on 2012-12-12
I think he should have 1GB swap

---

### Post by squakie on 2012-12-12
a 1gb swap would normally be enough for the average user while running.  However, since they are looking at a laptop, and they might want to hibernate, it now becomes a matter of a minimum size of the physical memory size plus 100k or so to allow for overhead.

---

