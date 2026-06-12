---
title: "Dell XPS m140"
date: 2014-05-20
forum: New to Ubuntu
---

### Post by gtravis3 on 2014-05-20
Howdy,
Firstly, i.e. INTRODUCTION:
Let me say that I have been an Apple kinda guy since the early 80s, hence, I know next to nothing about Windows software nor machines. I'm using a Mac now to access the forum.
Oddly enough, we found the Dell computer in a trash can, and decided to see what was wrong with it and perhaps give it to my rather computer dangerous son. Indeed it was thrown in the trash, I promise.  We attached it to an AC adapter and it came right up. 
The L key is missing and evidently not working, so I am going to replace the keyboard, and have replaced the battery, have some charging issues with it. The Dell is running Windows XP Media Center Version(which no doubt ya'll know is no longer supported). Seeing as I do not know windows, nor can I find any big time applications on the C drive (I can see that the Hard Drive is 70% full) but don't know what I can safely delete; does windows prevent one from deleting critical system files like the Mac? Why the Hard Drive was not wiped before it was trashed, I can't tell you. Also, the computer has one gig ram, but seeing as I have no Windows software, I really don't know about the optical drive (I played with all the Dell online diagnostics and everything was reported as working fine), also I have not tried to use a flash drive on it yet.
Alas, for painful reasons, it appears that my son will not be available for a rather lengthy time.
I apologize for all that history, but I am trying to provide as much info as I can, so that you can help me!

Seeing as how I am a Mac kinda guy, I do dabble, and dabble it is, in Unix. So, I am thinking about completely replacing Windows with linux; if I can get more room back on the hard drive, perhaps share it windows.  But given the "cost" of the Dell, I will not have any concerns it I just wipe it to linux. 
So I would appreciate it if you could suggest any further modifications I should make to this Dell, which gives me a chance to get under the hood.
Should  just completely delete windows and replace it with linux, or what I should do, or delete, to make room on the hard drive to share?
And what is the best way to get and install linux/ubuntu?

Thank you for your time,
trav

---

### Post by LastDino on 2014-05-21
Never delete critical files or files in C: (ROOT partition) irrespective of what platform you're unless you know exactly what you're doing and perfectly capable of dealing with one or two hiccups. 
Since it is XP, I would generally suggest you to wipe it out and install Xubuntu or Lubuntu on it. It seems to have decent RAM, but I would also like to know other hardware specs before getting specific.

---

### Post by gtravis3 on 2014-05-21
thank you for your reply. As an aside, I did not see a root partion using windows, my computer etc.  
I was able to create a boot USB flash drive, and restart the XPS from it. But is my face red. I did not really get it that Ubuntu Desktop actually meant a GUI; no wonder the download was so huge. I was expecting a command line kinda thing, but that's cool seeing as how the L key is missing and not working. I am expecting a new keyboard today (Amazon). I had hoped to wait until a 2 gig upgrade kit came in, CRUCIAL sticks, before I replaced the keyboard seeing as how one has to remove it to install the primary stick. I did try the Ubuntu console, and was happy with what I saw, but having no L key and using the command line is a bummer. 
Hardware specs are as follows, I hope that it is what you are looking for:
Intel Pentium M processor 1.86 GHz
Standard memory Physical Address Extension
Hitachi HD
 NEC DVD+RW
Vid. Card Mobile Intel 915GM
I have seen an interesting thing regarding the system report at first it showed something along the lines of 1.8 GHz, but lately it reads 782 MHz
trav

---

### Post by gtravis3 on 2014-05-21
Also, is there a reason for using Xubantu vs the Ubantu that I have on the flash drive?

---

### Post by LastDino on 2014-05-21
Alright, with that processor, Lubuntu should be the choice of distro from buntu family (You can also try Xubu but that would be pushing it). Linux has came far far ahead of its command line only days, however, that does not restrict you from using command line at all. In fact, if you can use it, you'll really be able to get maximum out of your system.

You can download Lubuntu from here 
[https://help.ubuntu.com/community/Lubuntu/GetLubuntu](https://help.ubuntu.com/community/Lubuntu/GetLubuntu)

You can burn it on DVD and install it as you seem to have DVD+rw drive(?)

There are quite a few other lighter linux distros available, to name few: Bodhi & DSL etc. 
Since Lubuntu is fairly modern distro with GUI, you can even try to install it without the ''L'' on the keyboard present :3

I'm bit confused about your XP situation, however, there shouldn't be any issues getting rid of it as it has been discontinued. I do recommend you to read up on how to install Lubuntu. **Especially the partitioning scheme of Linux.**

Edit: Yes, there is reason. The lesser the processor and RAM you have, it is better to install lighter versions of Buntu family as higher tier ones do consume lot of resources. Flagship Ubuntu unity may not be  as usable as Lubuntu or Xubuntu (which is heavier than Lubuntu) on your machine for that very same reason. 
I've P4 3.0 GHz with 4GB RAM and I use Xubu or equivalent distro's to get most out of my system. Your processor should be about close to mine but it is still mobile version, so it is better to stick with Lubuntu to get maximum performance and usability.

---

### Post by gtravis3 on 2014-05-21
Howdy,
Well, I had already did the erase and install Ubuntu Laptop software on it. It seems to be working ok, except that when I respond to the install new software message, the updater or whatever seems to be hanging up. A little bar thing tracks back and forth. It could be a slow connection? I have to run from computer to computer to do any message work etc. I don't trust that RW drive yet, the cover was ripped off and I have to press the green manual open to get it to errr. open. Thats why I made a startup flash drive to install Ubuntu.

---

