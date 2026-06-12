---
title: "What to do when your dear son deletes your non-Ubuntu operating system?"
date: 2011-09-19
forum: New to Ubuntu
---

### Post by trilogy1011 on 2011-09-19
So here's the scoop-

My son, who likes to dabble in computers, decided to install Ubuntu on our family desktop (reserved for homework and music storage).  It was an XP machine, and we could boot either to Windows or Ubuntu at startup.  Well, the little darling was messing with some setting yesterday, and it looks like he deleted the partition on the hard drive that contained the XP OS (which is why I said it WAS an XP machine...).  While I can see the benefits of moving to a Windows-free computing experience, the reality is that we have a significant amount of our life over there in XP Land, and I want it back.

I've done some research on the net about ways to recover said partition through Ubuntu with a program called Testdisk.  Testdisk isn't installed on the desktop machine, so I located and downloaded it to a CD, but here's my dilemma:  Ubuntu doesn't recognize the CD within the Package Manager, but can see the cd and its contents through the file manager (apologies if my terminology isn't correct - I'm at work and typing from memory).  I've copied the Testdisk installation (zipped) program onto the Ubuntu desktop, but can't figure out how to get the Package Manager to "see" it there to install it.  All I have for options are http addresses or an added CD. The desktop machine doesn't have an internet connection, nor is there any way to connect it, so I can't get Testdisk that way.  

Is there a relatively uncomplicated way to utilize the Testdisk program to recover the missing partition through Ubuntu?  As I said before, the second OS was the kid's idea, not mine, and I'm not really in any mood to wade through a slug of code -- not 10 minutes after he deleted the partition, he broke my dishwasher.  Yesterday was not a good day.  

Marcie

---

### Post by wildmanne39 on 2011-09-19
Hi, welcome to the forum! here is a guide for using testdisk.
[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step)
Thank you

---

### Post by pqwoerituytrueiwoq on 2011-09-19
```
sudo apt-get install testdisk
```
you may need to have the universe enabled under software sources for that to work
one you install it run ```
sudo testdisk
```


unless you need to recover data that was on the xp partition i see no reason to bother with it ubuntu can do far more than xp can with homework and music only thing windows is good for is gaming (and i don't mean facebook games)

---

### Post by seawolf167 on 2011-09-19
First of all, can you boot into Ubuntu? (i.e. lets first ensure that the XP partition was deleted and that Grub was not simply removed). If Grub was removed, you can re-install following the guide here, if not, take a look under GParted (hit [ALT][F2] and type in gparted) and see if the XP partition is flagged as unallocated space. If it is, try Testdisk as you suggested.

You can download the program through their website [here]("http://www.cgsecurity.org/wiki/TestDisk_Download"), install it through the software center or type in this line at a terminal

```
sudo apt-get install testdisk
```

Then run it by typing

```
sudo testdisk
```

Additionally, you could also use a LiveCD and boot to that and run TestDisk. The LiveCD list is [here]("http://www.cgsecurity.org/wiki/TestDisk_Livecd").

Once you have Testdisk running, there is a step-by-step guide located [here]("http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step").

After you finish with TestDisk and [hopefully] recover your deleted partition, ensure that going forward you have appropriate backups of your critical information. One easy way to backup your system, settings, boot configurations, data, etc is to use [Clonezilla ]("http://www.clonezilla.org")to create an image of your hard disk.

---

### Post by trilogy1011 on 2011-09-19
Thanks for your thoughts thus far - who knew I'd get such a quick response!?!

I will try these suggestions as soon as get home, and let you know how I made out.  As for not needing XP - you're probably right.  I just would have preferred to make the leap to Ubuntu on my own terms, if you know what I mean!

M.

---

### Post by Monsuco on 2011-09-19
Just a quick thought. It might be a good idea to make a backup image of your current system's HDD, just in case test disk goes haywire you'd get a second chance (or third, fourth, whatever). If you have a copy of clonezilla (or just use DD I guess) and a USB hard drive,

I've learned from experience it never hurts to make a backup raw image when trying to restore data.

---

### Post by Elfy on 2011-09-19
If it is the case that it's been removed then only boot with the livecd.

However, unless you've already checked it could be that it's there anyway - no way of anyone telling as you've not said what it was your son actually did :)

As you can't get online with the machine - go here to get testdisk - [http://packages.ubuntu.com/natty/testdisk](http://packages.ubuntu.com/natty/testdisk)

Copy it to the desktop from whatver you use and 

right click and use the install with the software centre option

If you get the livecd booted - open a terminal and run 

```
sudo fdisk -l
```

Post the output and we'll know for certain.

---

### Post by anewguy on 2011-09-19
And as a small side note, to answer your title/question in a slightly different way, when I was a kid they had this thing they called a "switch"......could make my behind hurt ;)

Dave ;)

---

### Post by Jerry N on 2011-09-19
> **pqwoerituytrueiwoq said:**
> 

unless you need to recover data that was on the xp partition i see no reason to bother with it ubuntu can do far more than xp can with homework and music only thing windows is good for is gaming (and i don't mean facebook games)

This is baloney and if I was a new Ubuntu user and got a reply like this it would probably stifle any desire I had to become a part of the Ubuntu community.  The OP said he wanted XP back and this kind of comment is not helpful.

Jerry
Edit:  I believe I committed a faux pas.  It looks like I should have written "The OP said _she_ wanted XP back......"

---

### Post by Mark Phelps on 2011-09-19
> **trilogy1011 said:**
> ...the reality is that we have a significant amount of our life over there in XP Land, and I want it back...

If testdisk finds the files you need ... then great!

However, if it does not, then you need to consider using a Windows-based utility to recovery your files.  The best I've used is from Runtime Software, known as GetDataBack for NTFS.

If you want to try that, you will need to do the following:
1) Remove the drive that previously contained the files from your current PC
2) Hunt down another, working, Windows PC
3) On that PC, download and install the trial version of GetDataBack for NTFS.
4) Hook up the drive that previously contained the files to the other Windows PC
5) Run GetDataBack in deepest discovery mode -- best to let it run overnight
6) Check in the morning to see if it located your old files.
7) IF it did, to recovery them, you will have to purchase GetDataBack -- but you can then download the activation key, activate the product, and then recover your lost files.

Your files ... your money ... your decision.

---

### Post by PayPaul on 2011-09-20
> **trilogy1011 said:**
> So here's the scoop-

My son, who likes to dabble in computers, decided to install Ubuntu on our family desktop (reserved for homework and music storage).  It was an XP machine, and we could boot either to Windows or Ubuntu at startup.  Well, the little darling was messing with some setting yesterday, and it looks like he deleted the partition on the hard drive that contained the XP OS (which is why I said it WAS an XP machine...).  While I can see the benefits of moving to a Windows-free computing experience, the reality is that we have a significant amount of our life over there in XP Land, and I want it back.

Marcie

I'd have to begin my possible answer with a few questions of my own. Do you have the original XP disk? Do you have all of your Windows based program installation files? Did you back up data and documents from Xp Land? 

Considering that the partition containing the Xp installation was deleted my choice in that case would be to first turn that unpartitioned space into a partition ready for another fresh Windows installation. As I've found out, Ubuntu is an OS that needs to be installed after Windows in a dual boot scenario. A new Windows installation would certainly mess with the grub it would see something that wasn't there before. The dual boot scenario that I've most heard of being the safest one involves installing ubuntu using Wubi while in Windows. It worked for me without much of a hitch. I would do a clean install of XP, perhaps even reformatting the entire drive beforehand and then do a clean install of Ubuntu in a Windows created partition of that drive. The sequence of installations is important for stability it appears.

This is something I may have to do myself if I want to reinstall Win7 properly. No biggie as I'm almost certain both installs will be clean and perhaps Windows will behave better than it has been. It's misbehavior is why I dove into Ubuntu. I like Ubuntu for it's often more direct interface and quicker response time but there are some programs out in Windoze Land that I have a real need for. Ubuntu does serve most of my requirements though and at least at present is much more stable and responsive than the microsoft product.

---

