---
title: "Should I install Ubuntu on new HDD in Vostro 1310?"
date: 2012-11-14
forum: New to Ubuntu
---

### Post by biswas on 2012-11-14
Here is my situation:
[LIST=1]
[*]Hard disk (160GB SATA2) crashed on vostro 1310 (Celeron processor)running Vista Basic SP2
[*]ORdered new HDD (320GB SATA2)
[*]planning to use Dell Operating System Recovery CD to reinstall windows on new HDD
[*]Noticed that Product Key Sticker is completely worn off bottom of computer (not inside battery door where it should be) on the bottom of the 4-year old "LAPTOP" computer - of couse I did not write it down anywhere :(
[/LIST]

I want to use this computer on my sailboat in the summer to run OpenCPN Navigation software, wi-fi, some kind of internet browser, and maybe watch a few  movies.

Do I need Windows?

I am COMPLETELY new but I hear great things about Ubuntu. Here is my question:

When I get the new HDD into the laptop, can I go from there directly to installing Ubuntu as the only Operating System? What do I loose? What do I gain? How much pain will be involved?

I see that you have lots of information here about "HOW" to install and fix problems etc, but since I am a complete virgin to anything other than WIndows, I want to know "IF" I should pursue this avenue. Or would a newbie like me be better off to bite the bullet and give Microsoft some more money?

Is there a way that I could get a feel for Ubuntu before I decide? I do not know anyone who could show me. 

Your thoughts are appreciated. Sell Me.

By the way, I do have the Broadcom wireless card and I know from reading this forum that this can be an issue, but it seems as though it is fixable.

---

### Post by xiuix on 2012-11-14
I would use a SSD.  HDD's on boats do not last long :D

---

### Post by biswas on 2012-11-14
I hear you. 
Though the bad HDD was on the boat for 4 years and only went bad when I dropped the laptop on the floor...
However, I am trying to save $$$ right now, and I am not 100% sure this is going to work at all anyway, so I thought $50 for a 320GB HDD was a good idea . 
I am hoping to use this as a learning project and then I am going to build a 12V mini pc with SSD on the boat to handle Navigation, Communication etc.
I am interested in minimalism ie. no more hardware - or software - than needed. I want to keep power demands low and, to be honest, I am ashamed of being so dependent on Windows. 

For now though, I would like to use this opportunity to educate myself on alternatives to a big OS like Windows. Maybe with Linux only I could use a 30GB SSD?
Point is: I don't know - that's why I came here...
Is Ubuntu a good stand-alone?

---

### Post by Bucky Ball on 2012-11-14
We all started with Linux somewhere, and as newbies!

You can boot from the install disk, otherwise known as the LiveCD, and that will take you to a desktop. Start playing! It will be slower than a hard drive install, obviously, as it is running from CD. Any questions just post a thread here.

Once you're happy there is an icon on the desktop to install. Hit that and you're rolling. You would be good setting up the partitions by choosing 'Something Else' when you get to the partitioning section or you can select to let the install work that out itself (but that may not partition things how you would like). For a manual partition, normal is:

/ = root partition, where the OS goes, 15-20Gb plenty;
/home = where your documents, vids, music, etc will go, large as you like;
/swap = same as Windows pagefile, 2Gb is fine, at end of disk or end of install.

That's it. Depending on your hardware, install can be a breeze or not. If things run fine from the CD, that is a good sign. Be aware that you may be offered drivers for wifi and graphics etc if you get connected. Don't install when running from the LiveCD as there is nowhere for them to go, as you are running from the LiveCD! If you follow. This won't be the case once installed.

Once installed, plug in a cable (unless you are already getting wireless) and do an update (we can show you how) and then see what you have offered. You may also find something in 'Additional Drivers' after that.

Be aware that Ubuntu is really a base system with a desktop environment (currently Unity). There is choice, much. I use Xubuntu (xfce desktop environment), which is much more pared back and might suit you better as you aren't looking to do much with the machine (so it will be fast and slick). Kubuntu uses KDE desktop environment which has all bells and whistles and probably more than you need. You might like to try them all by making LiveCDs and booting from them to see which you prefer. The point is, they all use the same base, Ubuntu kernel and everything else is added to that (apps, DE, etc.).

@ xiuix: An SSD would be faster and probably better for a boat, yes, but OP has a new HD on order so that wasn't really the question. ;)

To both of you; welcome to the forums. ;)

* Update: and in response to your second post, Ubuntu is a great standalone. That's what it is! For what you want to do, no brainer. Will fit your purposes fine. 

A 30Gb hard drive? Possible, if you're not keeping lots of data and not using KDE. In that case, you might go for Xubuntu and:

/ = 10Gb
/home = 18Gb
/swap = 2Gb

That would work. 

Be aware, Ubuntu is no 'novelty' operating system. It is a fully blown and fully functional OS used exclusively by many. It is the pick of the bunch for a newcomer perhaps as the Ubuntu community is vibrant, vast, friendly and helpful. I have completed a uni degree and am still studying and used ONLY a Ubuntu based system over the five years it took.  ;)

---

### Post by biswas on 2012-11-14
> **Bucky Ball said:**
> We all started with Linux somewhere, and as newbies!.......

Be aware that Ubuntu is really a base system with a desktop environment (currently Unity). There is choice, much.......


* Update: and in response to your second post, Ubuntu is a great standalone. That's what it is! For what you want to do, no brainer. Will fit your purposes fine.......



Be aware, Ubuntu is no 'novelty' operating system. It is a fully blown and fully functional OS used exclusively by many. I have completed a uni degree and am still studying and used ONLY a Ubuntu based system over the five years it took. ;)


Thank You Bucky Ball. I feel much better giving it a shot. I ordered the Drive today, so I have a few days to research. Would I be ok to go with the most up-to-date version of the Ubuntu software? Anything to look out for?

---

### Post by Bucky Ball on 2012-11-14
> **biswas said:**
>  Would I be ok to go with the most up-to-date version of the Ubuntu software? Anything to look out for?

This may start a flood, but I would start with the current LTS release (long-term support release) 12.04 LTS which is supported for five years until April 2017 (Xubuntu for three years). That has been out for over six months and is therefore more stable. You might get a smoother ride as a newcomer re installation and hardware compatibility. 12.10 is a breeze for some but a nightmare for others. It has only been out for a few weeks so some way to go there.

I personally *always* have a stable LTS on one partition as my 'main squeeze', fully customised, tweaked and as I like it, then a couple of other partitions for trying out newer releases, my playthings. I always have the stable install (I have to) and it doesn't matter if my playthings get broken, so to speak. Then you learn something trying to fix or just reinstall. Most importantly you can report problems and bugs to help the developers improve Ubuntu.  Currently sticking 12.10 on one spare partition and 13.04 on another (which isn't due out til April next year so very much in the testing stages).

I think, as an experienced user of computers, you might like what you see as you start to understand the way this all works. Leave preconceptions at the door and dive in. You may need to move your computing brain a few degrees left or right in the process as there is a learning curve, but that's all good if you're up for it. ;)

---

### Post by biswas on 2012-11-14
Well, I think I should definitely go with the stable version as I am still puzzling a bit over the "manual partition" in your first remarks.

I may be (am) getting ahead of myself but....

You know what, on second thought, I will now thank you for your gracious words and consider this thread SOLVED.

I have to get reading, so I will be able to ask properly  intelligent questions in the future - and I am sure I will be doing so......

Thanks.

---

### Post by Bucky Ball on 2012-11-14
All good and no problems. Enjoy and remember to post a new thread with any further questions/issues with a descriptive title and as much info as you can muster. 

The following page might get you started. The 'Something Else' option I mentioned for manual partitioning is explained in full here:

[http://news.softpedia.com/news/Installing-Ubuntu-12-04-LTS-266201.shtml](http://news.softpedia.com/news/Installing-Ubuntu-12-04-LTS-266201.shtml)

Just change the partition sizes and other details to suit your situation. Also try here:

[https://help.ubuntu.com/12.04/installation-guide/powerpc/module-details.html#di-partition](https://help.ubuntu.com/12.04/installation-guide/powerpc/module-details.html#di-partition)

Good luck with it all. ;)

* Just a note to avoid confusion when downloading the install ISO: the i386 ISO is for _*all*_ 32bit systems, Intel and AMD. Likewise, the AMD64 ISO is for _*all*_ 64bit machines, Intel and AMD.

---

