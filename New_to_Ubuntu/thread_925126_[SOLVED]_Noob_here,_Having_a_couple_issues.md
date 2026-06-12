---
title: "[SOLVED] Noob here, Having a couple issues"
date: 2008-09-20
forum: New to Ubuntu
---

### Post by bulletbikeguy on 2008-09-20
Hey all, I just can't help posting now.  I'm at work and the machine that I'm loading Ubuntu on is at home.  That being said I have only so much info but I'm excited to learn so I'm posting :)

I have loaded Ubuntu on a 50gig partition on the 200gig hdd that also has XP loaded on it.  The machine is a P4 3.2HT with only 512 ram at the moment.  It has an Intel MB.

When I tried to post Ubuntu it threw an error code.  It allows me to use the setup utility and I can reboot the machine etc from that “DOS” window but I can’t get it to load.

I also viewed the loading data or whatever it’s called by pressing insert.  Among a host of other things it said my bios size is large then the drive size?  Doesn’t make sense to me because I allotted 10gigs for the OS alone (simply because I didn’t want to deal with any space problems)

Let me know what you guys think it could be and I’ll get more info.  

Thanks!

---

### Post by Sef on 2008-09-20
1) Moved to Absolute Beginners.

2) > When I tried to post Ubuntu it threw an error code.

Do you mean boot into Ubuntu?

3a) > When I tried to post Ubuntu it threw an error code. It allows me to use the setup utility and I can reboot the machine etc from that “DOS” window but I can’t get it to load.

So all you get in a command prompt instead of a GUI (Graphical User Interface); have you installed Ubuntu or just booting from the Live CD?  

3b) If installed, what happens if you run the Live CD?  Do you have the same problem?

---

### Post by bulletbikeguy on 2008-09-20
> **Sef said:**
> 1) Moved to Absolute Beginners.

2) 

Do you mean boot into Ubuntu?

3a) 

So all you get in a command prompt instead of a GUI (Graphical User Interface); have you installed Ubuntu or just booting from the Live CD?  

3b) If installed, what happens if you run the Live CD?  Do you have the same problem?



In case it helps I downloaded the ISO from the Ubuntu website and burned it to a CD.
Answers
*1 Thanks

*2 Yes I mean boot into Ubuntu.  I have the computer set up as a dual boot.

*3a I am able to get into Command Prompt (sorry I am not familiar with the lingo yet but I'll be reading a book soon :lolflag: don't want everyone thinking I'm talking about windows or regular cmd because the regular commands do not work,IE cls, shutdown etc)  I am unable to get into any graphical interface.  I have installed Ubuntu and it now runs from my HDD, atleast I think it should...

*3b my noobish knowledge doesn't know about a live CD.  Do you mean the CD that I burned the ISO onto?  

You guys are great I truely am thankful for your patience with me!

---

### Post by starcannon on 2008-09-20
When you get home lets have a look at your hdd:

```
sudo fdisk -l
```

post it here, that will give us something to start working with.

And please, before you do anything else, backup anything important to you. When one is new to partitioning, and installing multiple operating systems, the chance for "losing everything" grows to a probability factor of near certainty. I'm not trying to scare you away, indeed quite the opposite, so please before we continue forward, boot into windows and back up anything that if lost would lead to a life of binge drinking, viz. photos, mp3's, the novel you've been writing, email, bookmarks, work related documents.... 

GL, have fun

---

### Post by hyper_ch on 2008-09-20
It is advised to use a descriptive topic title; that means use a topic title that gives some clue about the content in the thread itself...

A generic topic title like "noob here" or "need help" does not help at all. As you may have notices, just about everyone posting in here has some kind of a problem or issue or question ;) 

Just imagine what these forums would look like if everybody would just post "Help" or "Noob here". What do you think how many people will still look at such threads?

Furthermore, for unrelated questions it's also adviced to open a seperate thread for each one, so that each problem can be addressed (and eventually marked as solved) individually.

---

### Post by bulletbikeguy on 2008-09-20
Alright I'm home now.  
As for backing up the system, I have two computers that are going to be strictly for learning this stuff.  The one I have already described which I just cleaned the dust off of and reformatted with XP.  And an old windows 95 machine which I think I may end up throwing in the trash, too much trouble finding the drivers etc.  Both machines have nothing of value so we're ready to rock!  Oh and I'm using my laptop to communicate with you guys for now, and we will not be messing with it, I can't afford the drugs I would need to calm me down if I deleted all that.

First of all I just tried to boot Ubuntu and received this error, "Error 1: Filename must be either an absolute pathname or blocklist"  The same error that I receive every time.

I tried to do what you told me with code "sudo fdisk -1" none of that is recognized and I'm trying to remember how to get into regular old fdisk but I'm retarded..

---

### Post by starcannon on 2008-09-20
its -lower case L -l

---

### Post by starcannon on 2008-09-20
Okay let me see if I understand whats happening so far.

You set up a dual boot machine.

You first installed MS Windows XP.

Then you installed Ubuntu on a separate partition.

Then you tried to boot into Ubuntu and it is dumping you out at a command line?
[INDENT]if so is the words "Busy Box" on the screen anywhere?
or are you being given any sort of login prompts?
[/INDENT]
I'll keep checking in on your thread.

GL and keep it fun, you'll figure this stuff out, its only hard the first time.

---

### Post by bulletbikeguy on 2008-09-20
[PHP]Booting CRLDR...
hard drives: 1, int13: F0009950, int15: F000F859
get)diskinfo(80), int13/41(80),version-AA210005, int13/48(80),err=0, C/H/S=16
383/16/63, SEctor Count/Size-390719855/0, int13/08(80),verison=0, C/H/S=1024/2
55/63, int13/02(80),err=0,
Warning: MBR cylinders(24322) is not equal to the BIOS one(16383).

Warning: MBR total sectors(390732930) is greater than the BIOS one(390719855).
Some buggy BIOSes could hang when you access sectors exceeding the BIOS limit.
LBA, C/H/S=24322/255/63, Sector Count/Size=390732930/512
boot drive=80, int13/4B01(80),err=1,drive=80, NOT CD
get_cdinfo(7f), int13/4B01(7f),err=1,drive=7F, cdrom_drive == FFFFFFFF.
Starting cmain() ... Open /default ... failure.
[/PHP]

That is what I see if I tap insert after selecting the Ubuntu boot upon startup.  Sorry if I made an error while typing it out.  I still can not manage to get fdisk to work I'm typing it exactly as you have shown with no success.  It says it's not a known command

I am having a great time learning, I only worry that I'm asking stupid questions about topics that have been covered but I am doing my best to search for answers here and online before posting questions.

Thanks once again!

---

### Post by bulletbikeguy on 2008-09-21
Have you given up on me :(

---

### Post by bulletbikeguy on 2008-09-22
Ok I don't want to jump the gun here but I decided to download Ubuntu again from scratch and I ripped a new ISO CD today and guess what I was able to boot from the CD.  Now so many things that everyone was talking about are making sense!  Looks like the stupid files were corrupted on my last burn!

So yeah I'm about to rip it to a partition again and I bet it's gonna work this time :guitar:

Soon to be marked solved!


*A few minutes later*
OH MY BAD WORDS!
I loaded it to the partition again and it is still saying the same crap!  I'm going bananas here!




*Several painful minutes later*
The cd is working just fine which is good.  I decided to go through the program to load, yeah I know that's what I should have done in the first place but cut me some slack I'm admittedly dumber then crap.  Will keep you posted!

*well geez*
Rather than try to figure out the partition tools I just used the auto settings.  It's loading up as we speak, 61% and counting...

---

### Post by bulletbikeguy on 2008-09-22
It's working!  Looks like I deleted XP which sucks but hey it was a fresh copy so no big deal!

Oh and I'm posting from my Ubuntu account right now ! ! ! !

I will be having tons more issues I'm sure but at least this major problem is solved.

Thanks to all of those who read and were thinking and more importantly those who gave me support.

To all those having similar issues, download again and reburn a cd.  I could have slammed my head against the wall for a week trying to figure it out another way:lolflag:

---

### Post by kansasnoob on 2008-09-22
Well, I was going to suggest you look at some things here:

[http://users.bigpond.net.au/hermanzone/](http://users.bigpond.net.au/hermanzone/)

Specifically here:

[http://www.herman.linuxmaniac.net/p22.html](http://www.herman.linuxmaniac.net/p22.html)

Just for the screenshots!

But, now that you have an Ubuntu only system and want to reinstall Windows look here:

[http://apcmag.com/how_to_dual_boot_linux_and_windows_xp_linux_installed_first.htm?page=1](http://apcmag.com/how_to_dual_boot_linux_and_windows_xp_linux_installed_first.htm?page=1)

Other helpful links:

[http://www.howtoforge.com/the-perfect-desktop-ubuntu-8.04-lts-hardy-heron](http://www.howtoforge.com/the-perfect-desktop-ubuntu-8.04-lts-hardy-heron)

[http://www.psychocats.net/ubuntu/index](http://www.psychocats.net/ubuntu/index)

---

