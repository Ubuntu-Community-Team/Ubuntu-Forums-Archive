---
title: "Bowtie: Running out of memory with 2GB memory?!"
date: 2013-10-03
forum: New to Ubuntu
---

### Post by adam20 on 2013-10-03
So I'm trying to run a program called bowtie 2 through terminal and I almost instantaneously get the error:

Out of memory allocating the ebwt[] array for the Bowtie index.  Please try
again on a computer with more memory.

I have a 32 bit processor and 2 GB of memory, which should be plenty.

---

### Post by DuckHook on 2013-10-03
Please explain what Bowtie 2 is. What does it do? What resources does it use? Is it a GUI app or a CLI app?

What flavour and version of 'buntu are you running? Are you using a swap? If you are running the Unity desktop, Unity is a resource hog and you might indeed reach the limit with only 2GB of memory. This depends on the memory requirements of the Bowtie 2 app and also on how many other services and apps you are running concurrently. But at this point,m this is just a general observation so lacking proper foundation that it is almost meaningless. Cannot advise you further without far more info.

---

### Post by adam20 on 2013-10-03
Bowtie 2 is alignment software for DNA analysis.  It uses terminal (CLI).  Basically, it takes a large 3.3 Gb data set and compares it to a large genome (~8 Gb).  This software worked fine on my 64 bit laptop, which runs windows 7 for which I downloaded Wubi.  Because it was so slow and it would freeze up, I installed the actual Ubuntu 12.04 LTS operating system on my older 32 bit laptop, complete replacing windows XP.  I'm quite new to Ubuntu and Bowtie 2, so I don't know about what resources each takes up.

---

### Post by DuckHook on 2013-10-03
Additional info clarifies many things...

WUBI boots up a regular instance of Ubuntu. Difference is only in the way the OS is stored.

Therefore, the obvious difference between your earlier experience and your current one is your hardware. Your 64-bit machine likely has enough memory and a powerful enough processor that it can handle Bowtie 2. Your current machine does not. *Please post the specs for both machines*, but this more than likely accounts for the difference in your experience.

You mention that your current machine is 32-bit. Are you sure about this? Even quite old laptops are actually 64-bit. But if it is truly only 32-bit, then it is a very underpowered laptop and I am not surprised that you cannot get a huge data set (you mention 3.3 GB and ~8 GB) to process. And if you are running it on top of Unity rather than a plain command line interface, then so much of your resources are being used to support all of Unity's fancy effects that there is little left for apps. **NOTE** This is a generalization based on the fact that any laptop with a 32-bit processor is likely to be highly resource constrained for modern OSes.

---

### Post by rocketfish201 on 2013-10-03
> **Memory requirements**: Bowtie uses approximately as much memory as  the size of the bowtie indices. For the human genome, this is about 3.4  GB. You should run this job on a node with at least 4 GB of RAM.

Source: [http://biowulf.nih.gov/apps/bowtie.html](http://biowulf.nih.gov/apps/bowtie.html)

I don't know if this is relevant or not.

---

### Post by DuckHook on 2013-10-03
> **rocketfish201 said:**
> ...I don't know if this is relevant or not......extremely, I would say. Clearly a laptop with 2GB is insufficient, even if Ubuntu wasn't hogging most of 1 GB for its OS overhead. Thanks for researching the reference, rocketfish.

---

### Post by adam20 on 2013-10-03
The newer laptop that the ware worked on is a 64 bit, Windows 7, 4 Gb RAM, i5 processor

The old laptop that it's not working on is a 32 bit, Windows XP, 2 Gb RAM, Celeron processor.

I am using a 64 bit version of Bowtie2 on my 64 bit system but a 32 bit version on the older system.  I believe my processor only runs at 32 bit because when I click on "details" under "system settings" it says it's indeed 32 bits.  

I kind of follow with the whole unity thing, but is there a way around that on my older system?  I'd hate to have to buy a new computer just to run this program

---

### Post by adam20 on 2013-10-03
> **rocketfish201 said:**
> Source: [http://biowulf.nih.gov/apps/bowtie.html](http://biowulf.nih.gov/apps/bowtie.html)

I don't know if this is relevant or not.

This is definitely useful; however, I am using a 32 bit version of Bowtie 2 which is said to use less memory.

---

### Post by rocketfish201 on 2013-10-03
> **adam20 said:**
> This is definitely useful; however, I am using a 32 bit version of Bowtie 2 which is said to use less memory.

That doesn't change the fact that you have to load a 3.4GB file into RAM. You can't put 2 liters of water in a 1 liter bucket.

---

### Post by DuckHook on 2013-10-03
The app may use less memory (and only marginally at that), but your resource hog/constraint is the size of your data-set.

EDIT

rocketfish and I gave the same response to two different ways.

/EDIT

---

### Post by adam20 on 2013-10-03
> **rocketfish201 said:**
> That doesn't change the fact that you have to load a 3.4GB file into RAM. You can't put 2 liters of water in a 1 liter bucket.

Damn, I didn't know it worked like that.  I was hoping it would parse into readable sections at a time.  Guess I might have to get another computer to run this.

---

### Post by rocketfish201 on 2013-10-03
> **adam20 said:**
> Damn, I didn't know it worked like that.  I was hoping it would parse into readable sections at a time.  Guess I might have to get another computer to run this.

If you plan on using Bowtie 2 a lot, then a new computer might be a smart idea. You could also look into getting a VPS.

---

### Post by DuckHook on 2013-10-03
Perhaps not. I can think of three alternatives:

1. You can go back to using your old machine for regular work and new machine for Bowtie (at least until you are done using Bowtie)
2. You can add more memory to your old Laptop and beef it up to 4GB
3. You can borrow a machine for the time needed to run Bowtie.

...more to come shortly.

---

### Post by DuckHook on 2013-10-03
I have a special place in my heart for obsolete underpowered HW that are years past their glory days. Maybe because, in this respect, they share so much with me! 

At any rate, what I've found generally, is that they can still be plenty useful. You just have to give them tasks within their capabilities. The reason that they often get shunted aside is because the latest and greatest OS is outrageously bloated compared to the OSes of yesteryear. Therefore, if you don't saddle them with a big fat OS, they can still run like champs because there is really nothing wrong with the basic machine underneath. If this sort of repurposing interests you, then you can bring the most utility back into your old laptop by getting rid of the GUI altogether. In your case, the GUI just gets in the way of running a command line app anyway.

The key items to consider are:

1. Processor type and speed. On your old laptop, please post back the results of:```
lscpu
```If this app is not installed,```
sudo apt-get install lscpu
```then run first command.

2. Type of RAM and expansion slots. This info is often available in the documentation that came with your laptop. Or you can Google its specs. What RAM modules does it use? Older RAM is available on e-bay for peanuts.

3. Are results from Bowtie time-critical? Do you need results quickly or can it just chug away until it's done? Depending on what sort of analysis you are doing, modern CPUs can be an order of magnitude faster than old ones.

Last but not least, installing Lubuntu on your old laptop might be enough to make it sufficiently useful that it is usable to you again. I don't know what your daily computing demands are, but if it's just general word processing/spreadheet stuff, then it is possible to install Lubuntu on your old computer, use apps like LibreOffice, and turn it back into your main computer while your more powerful one is tied up running Bowtie.

If this strategy is worth pursuing, then it would still be nice to have your system info.

---

### Post by Pako Pako on 2013-10-04
Indeed, Bowtie 2 does not require 4GB  of RAM... but still 3.2GB

  [http://bowtie-bio.sourceforge.net/bowtie2/manual.shtml](http://bowtie-bio.sourceforge.net/bowtie2/manual.shtml) > **DuckHook said:**
> 2. Type of RAM and expansion slots. This info is often available in the documentation that came with your laptop. Or you can Google its specs. What RAM modules does it use? Older RAM is available on e-bay for peanuts.Considering this is a Celeron-based 32-bit core laptop, the limit might be 2GB. (It sounds very similar to my 10-year old notebook, an M200, which has that limitation.)

  I will also add that *really-*older RAM (pre-2008) may still cost a bit, especially if you're using a miniaturized machine. (I [i[wish[/i] they cost peaunts.)  A quick webcrawl can find your system and its maximum RAM. Then either open it up or run LSHW to find out if you have available space to upgrade. ```
sudo lshw -short |grep memory
```As a laptop, you'll see how many SODIMM memory sticks you have installed. Most laptops I see support two slots for SODIMM memory sticks, but some have one slot taken up by a built-in stick.

 (e.g. The system maximum is 4GB of RAM, with one empty slot and 1GB built-in. To upgrade, instead of buying two 2GB sticks, you would need to install a single 4GB stick in the empty slot.)

---

