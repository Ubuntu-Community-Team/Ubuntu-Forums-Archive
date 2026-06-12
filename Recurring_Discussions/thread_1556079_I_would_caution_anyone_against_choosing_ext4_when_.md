---
title: "I would caution anyone against choosing ext4 when you install ubuntu."
date: 2010-08-18
forum: Recurring Discussions
---

### Post by wizarddrummer on 2010-08-18
Hi, 
 :guitar: Let the flames begin. I already know that there are going to be tons of people that will disagree with me.
 

I’m an old geek and a worn out Rock Drummer. I was a geek before many of you, reading this forum, were born.

My first computer that I played on was this giant behemoth in my Dad’s telephone office; learned how to turn off alarms and other things. Later came the IBM 360’s much later … UNIX in the 80’s … still later; I got to play on Cray machines.

We had a very early version of Linux in circa ’91. I got to play with 64 bit DEC Alpha Machines in late ’92. By mid 1993 our R&D location had more than 200 NeXT machines, (the aforementioned Alpha), SGI graphics machines, Auspex File Servers, SUN, HP, IBM compute servers, ATM Fiber Optic Switches, the Internet WWW two weeks after Tim Berners-lee introduced it (he developed it on the NeXT) … bought the first 386 20 Mhz machine with EVGA … had the first 486 dx100 … bought the first EVGA 680i SLI MOBO and two EVGA 8800 GTX 768 cards. (later upgraded to 780i)

  The point is I have always liked bleeding edge stuff.

This is fun but sometimes it can be a bad thing.

  Recently, a few months ago, coming back to the Linux world, I dabbled with Mint, ubuntu Studio and a few other flavors. I’m too rusty, even though I was considered expert enough to talk to top tier people at Bell Labs in the early days of System III when EVERYTHING was shell, to fuss with Gentoo.

  Some things are familiar and many things have changed.

With all of the experiments that I tried regarding the ubuntu flavors, I used ext4. I had some minor problems with each installation in one form or another and, this last time, against my better judgment because the system seemed more stable than previous versions, I migrated a bunch of data from a smaller HD to the HD I installed the latest version of Ubuntu 10.4 LTS.

  One evening I downloaded several hundred files; turned off the machine (it took a very long time shut down – not a good sign) and the next time I tried to boot it was toast.

  In a later post, when I have some more time, I will give some details and specifics of what went wrong. Not knowing the specifics of ext4, it could be partly a machine problem. The clock is often wrong and I wasn’t syncing to Internet time for about a month with the new install because I had not noticed the time problem and had not messed with setting time in ubuntu. – did not notice the time problem all the time. However that being said, the same machine also has an XP disk in it and I have not had any problems with it or with chkdsk.

This is just my opinion; I think that a person that is considering loading Ubuntu should reconsider using ext4 and go with seasoned, stable, reliable ext3

Ext4 is not tried and true as ext3; in my opinion, it is still too new. In lieu of the new car smell it still has a little bleeding edge to it and severe teeth when you lose some very important data.

---

### Post by mikewhatever on 2010-08-18
Are you saying ext4 got corrupted because of the clock? Sounds like a very serious bug.

---

### Post by TNT1 on 2010-08-19
> **mikewhatever said:**
> Are you saying ext4 got corrupted because of the clock? Sounds like a very serious bug.

I thought he was saying ext4 corrupted the clock...

Either way, all four of my computers are using ext4, as well as my 1tb external drive, all with zero problems...

---

### Post by clhsharky on 2010-08-19
ext4 is good enough for Google, and its good enough for me

---

### Post by CharlesA on 2010-08-19
> **TNT1 said:**
> I thought he was saying ext4 corrupted the clock...

Either way, all four of my computers are using ext4, as well as my 1tb external drive, all with zero problems...

I've got it on a 4TB RAID5 array, a 1.5TB external and a 2TB external and haven't had any problems.

Of course, I don't really shut my machine down that often, and it's hooked up to a UPS.

The file system corruption bug (which was fixed I believe) happened when the machine unexpectedly lost power.

---

### Post by aysiu on 2010-08-19
> **wizarddrummer said:**
> 
This is just my opinion Sounds as if the Community Cafe is the perfect place for your thread, then. Moved.

---

### Post by Khakilang on 2010-08-19
If you download several hundreds files, don't you think it will make the computer slow to shut down? And what is the size of the file? Seem confusing to me. Anyway I never had any problem with ext4 even I leave it overnight to download Distro. Sometime on power up my computer, Ubuntu will check the hard disk for error. So, I can sleep soundly with ext4.

---

### Post by silbak04 on 2010-08-19
This sounds more like a personal problem to me...nothing to do with ext4...I've been using ext4 for awhile, and I've never heard of such problems....so personal problem...and I'm very dubious that it has anything to do with ext4

---

### Post by NightwishFan on 2010-08-19
I advise you to report these issues. If you are interested ask for help here at the forums and read this link. To fix the specific problems, several of our users are quite technical and may be able to solve it.

[https://help.ubuntu.com/community/ReportingBugs](https://help.ubuntu.com/community/ReportingBugs)

---

### Post by GoldenSun on 2010-08-19
ext4 has been stable for over 2 years now.  Major corporations ,ie Google, have adopted it as their standard.  My house stores over 5tb+ of data, all on ext4 drives.  Never had any problems.

I believe that this isn't an ext4 issue and more like a hardware issue, or perhaps, a personal problem.  
Why post a resume of you pretending to know what you're doing when you can't figure out something simple?  

Ext4 has been extensively tested and is "tried and true" as ext3.  Hence why it has been stable since October of 2008.

---

### Post by lovinglinux on 2010-08-19
I have been using ext4 since Karmic Beta and had no issues whatsoever, even with dozens of power outages. Never lost anything. Ext 4 is very reliable in my opinion.

---

### Post by doorknob60 on 2010-08-19
I still use ext3, but only because when I installed Arch a while ago, it was before ext4 was considered stable and included by default in the kernel. I think it will be quite a while before I have to reinstall, but when I do, I'll probably use ext4 then (although my home partition is also ext3, and I don't think I'll ever have to change that unless I buy a new HD). I have other computers using ext4, never had any problems with ext3 or ext4, both work fine for me.

---

### Post by fatality_uk on 2010-08-19
ext4 is stable, has been for a long time. I use it on several production machines and never had an issue. I would really be pointing a finger at something other than ext4.

---

### Post by Paqman on 2010-08-19
> **wizarddrummer said:**
> 
One evening I downloaded several hundred files; turned off the machine (it took a very long time shut down – not a good sign) and the next time I tried to boot it was toast.


Sorry to hear you've lost data, that sucks. Sounds like the machine was having a lot of trouble in general though. What specifically makes you think the fault was with ext4 itself?

---

### Post by Starks on 2010-08-19
Only thing that bugs me about ext4 is that can't be read on Windows unless the partition has extents disabled. Even then, you'll have to fsck the drive with a LiveUSB/LiveCD before booting into Linux again.

---

### Post by Swagman on 2010-08-19
> **wizarddrummer said:**
> Hi, 
 :guitar: Let the flames begin. I already know that there are going to be tons of people that will disagree with me.
 

I’m an old geek and a worn out Rock Drummer. I was a geek before many of you, reading this forum, were born.

My first computer that I played on was this giant behemoth in my Dad’s telephone office; learned how to turn off alarms and other things. Later came the IBM 360’s much later … UNIX in the 80’s … still later; I got to play on Cray machines.

We had a very early version of Linux in circa ’91. I got to play with 64 bit DEC Alpha Machines in late ’92. By mid 1993 our R&D location had more than 200 NeXT machines, (the aforementioned Alpha), SGI graphics machines, Auspex File Servers, SUN, HP, IBM compute servers, ATM Fiber Optic Switches, the Internet WWW two weeks after Tim Berners-lee introduced it (he developed it on the NeXT) … bought the first 386 20 Mhz machine with EVGA … had the first 486 dx100 … bought the first EVGA 680i SLI MOBO and two EVGA 8800 GTX 768 cards. (later upgraded to 780i)

  The point is I have always liked bleeding edge stuff.
snip!


But you never had an Amiga so you failed in your quest!!
:p

On a serious note, Ext 4 has been rock stable here. 

cue crash !!

---

### Post by wizarddrummer on 2010-08-21
> **Paqman said:**
> Sorry to hear you've lost data, that sucks. Sounds like the machine was having a lot of trouble in general though. What specifically makes you think the fault was with ext4 itself?

Before I decided to migrate from XP, I spent several months playing around with ubuntu, Mint, and ubuntu studio.

I did several installations just to see which flavor I liked best; tried different partitioning schemes and did some benchmarks. All of this was done with ext3 and I had no problems. 

However, during one experiment, for lack of a better word, I used ext4 and had problems with it one day when it failed to boot. 

I got the splash screen (this is version 9.04 by the way) that just hung there for 20 minutes. I turned the machine off, booted into XP cause I needed to read some email. A few days later, when I went to boot ubuntu again the problem had corrected itself WITHOUT my intervention.

So, the latest install was from my 9.04 CD and I used ext4 when I partitioned. After the install i upgraded to the 10.04 LTS version. It seemed stable and then it crashed.

You probably won't see this because this thread has been moved to the graveyard.

---

### Post by wizarddrummer on 2010-08-21
> **GoldenSun said:**
> ext4 has been stable for over 2 years now.  Major corporations ,ie Google, have adopted it as their standard.  My house stores over 5tb+ of data, all on ext4 drives.  Never had any problems.

I believe that this isn't an ext4 issue and more like a hardware issue, or perhaps, a personal problem.  
Why post a resume of you pretending to know what you're doing when you can't figure out something simple?  

Ext4 has been extensively tested and is "tried and true" as ext3.  Hence why it has been stable since October of 2008.

It was not a "resume" it was merely an expose that I've always liked cutting edge things. Gee, ext4 is stable for 2 years. Tested and proved stable on how many platforms?

I'll bet that if I had the computers that Google was using I wouldn't have a problem either.

Your arrogance shows you to be a young and ill mannered.

"Something simple". 

If it was simple it would be fixed.


I'd be willing to bet that in the last 40+ years of actively being involved in this grand, glorious and sometimes very frustrating computer industry, I have FORGOTTEN more information than you will probably learn about computers.

---

### Post by Dayofswords on 2010-08-21
btrfs seems bleeding edge even more =p

anyways
avoid this been-there-done-that, know-it-all, wiser-than-you, for example "I have FORGOTTEN more information than you will probably learn about computers. " attitude, as this is the feeling I'm getting
[IMG]http://ozguru.mu.nu/Photos/2005-11-11--Dilbert_Unix.jpg[/IMG]


make your point, prove it and wait for review, don't present yourself as better with your experience and use that to back up your point

---

### Post by mendhak on 2010-08-21
True - a lot of the post is spent on your experience, which is great, but surely you should baffle us with the reasoning behind the ext4-toast relation?  I probably wouldn't even understand it, but if it worked for you the second time, did you have a look at any logs to see what went wrong the first time?

---

### Post by regeya on 2010-08-21
> **wizarddrummer said:**
> Hi, 
 :guitar: Let the flames begin. I already know that there are going to be tons of people that will disagree with me.
 

I’m an old geek and a worn out Rock Drummer. I was a geek before many of you, reading this forum, were born.

My first computer that I played on was this giant behemoth in my Dad’s telephone office; learned how to turn off alarms and other things. Later came the IBM 360’s much later … UNIX in the 80’s … still later; I got to play on Cray machines.

We had a very early version of Linux in circa ’91. I got to play with 64 bit DEC Alpha Machines in late ’92. By mid 1993 our R&D location had more than 200 NeXT machines, (the aforementioned Alpha), SGI graphics machines, Auspex File Servers, SUN, HP, IBM compute servers, ATM Fiber Optic Switches, the Internet WWW two weeks after Tim Berners-lee introduced it (he developed it on the NeXT) … bought the first 386 20 Mhz machine with EVGA … had the first 486 dx100 … bought the first EVGA 680i SLI MOBO and two EVGA 8800 GTX 768 cards. (later upgraded to 780i)

  The point is I have always liked bleeding edge stuff.

This is fun but sometimes it can be a bad thing.

  Recently, a few months ago, coming back to the Linux world, I dabbled with Mint, ubuntu Studio and a few other flavors. I’m too rusty, even though I was considered expert enough to talk to top tier people at Bell Labs in the early days of System III when EVERYTHING was shell, to fuss with Gentoo.

  Some things are familiar and many things have changed.

With all of the experiments that I tried regarding the ubuntu flavors, I used ext4. I had some minor problems with each installation in one form or another and, this last time, against my better judgment because the system seemed more stable than previous versions, I migrated a bunch of data from a smaller HD to the HD I installed the latest version of Ubuntu 10.4 LTS.

  One evening I downloaded several hundred files; turned off the machine (it took a very long time shut down – not a good sign) and the next time I tried to boot it was toast.

  In a later post, when I have some more time, I will give some details and specifics of what went wrong. Not knowing the specifics of ext4, it could be partly a machine problem. The clock is often wrong and I wasn’t syncing to Internet time for about a month with the new install because I had not noticed the time problem and had not messed with setting time in ubuntu. – did not notice the time problem all the time. However that being said, the same machine also has an XP disk in it and I have not had any problems with it or with chkdsk.

This is just my opinion; I think that a person that is considering loading Ubuntu should reconsider using ext4 and go with seasoned, stable, reliable ext3

Ext4 is not tried and true as ext3; in my opinion, it is still too new. In lieu of the new car smell it still has a little bleeding edge to it and severe teeth when you lose some very important data.

At the risk of angering the older wiser geek...

What you present here is an argument from authority followed by anecdotal evidence.  I've no doubt you had problems with ext4 on your hardware, but it could be your hardware.  As with others, I've used ext4 with no problems.  Conversely, I've had problems with ext3, but it almost always ends up being the hardware.  The most bizarre was on a G4 Mac running Debian PPC; the dir structure would show major problems if I enabled the btree hash.  Last I checked it still wasn't resolved...but ext3 + btree hash has been rock-solid on other hardware for ages.

I guess what I'm getting at is that, with Linux at least, you're probably never going to have something that's rock-solid onI every piece of hardware out there.  Microsoft certainly hasn't gotten there. ;-)  I don't think anyone can.  However, Linux as a whole seems to be fairly cutting-edge; if you want something less cutting edge and more stable, go with a BSD.  If you're looking for something nice and solid but aimed at the desktop, PC-BSD is pretty nice.  Once they get ZFS solid on fBSD, getting a couple of drives and putting everything on ZFS will be super-solid.

---

### Post by wizarddrummer on 2010-08-21
> **regeya said:**
> At the risk of angering the older wiser geek...

What you present here is an argument from authority followed by anecdotal evidence.  I've no doubt you had problems with ext4 on your hardware, but it could be your hardware.  As with others, I've used ext4 with no problems.  Conversely, I've had problems with ext3, but it almost always ends up being the hardware.  The most bizarre was on a G4 Mac running Debian PPC; the dir structure would show major problems if I enabled the btree hash.  Last I checked it still wasn't resolved...but ext3 + btree hash has been rock-solid on other hardware for ages.

I guess what I'm getting at is that, with Linux at least, you're probably never going to have something that's rock-solid onI every piece of hardware out there.  Microsoft certainly hasn't gotten there. ;-)  I don't think anyone can.  However, Linux as a whole seems to be fairly cutting-edge; if you want something less cutting edge and more stable, go with a BSD.  If you're looking for something nice and solid but aimed at the desktop, PC-BSD is pretty nice.  Once they get ZFS solid on fBSD, getting a couple of drives and putting everything on ZFS will be super-solid.


Here is a quote from a post on another linux forum.

[quote="wizarddrummer"][quote="interaudi"]Hi Wizarddrummer, i`ve bad experience with ext4, gets died fsck status 8 and 16, occurs when the OS is interrupted (Power. Its a known bug of ext4), its safer to use ext3 actually, no more errors in fsck at init. To restart xorg (I`ve ATI): sudo dpkg-reconfigure xserver-xorg, drivers for nvidia are in the xserver-xorg ??? video at Synaptic, the packages that you erase are of gnome desktop, that has no relation with nvidia drivers. Hope you will fix it.[/quote]

Thanks for the reply.

I got trashed by some on the ubuntu forum for suggesting that ext4 was a little too new and not as stable as ext3.

comments like "Google is using it" ... well, Google has doubly fault tolerant hardware.

Some of us in the world are in bad shape financially because of circumstances beyond our control. We can not afford the best hardware and UPS's.[/quote]

But, if there are known bugs in ext4 regarding power that DO NOT EXIST with ext3 then ext4 is NOT AS STABLE as ext3. Can't say it any more simple than that.

The other fact is that i never had any problems with ext3 and in many hours of research (yes I try to figure out things before I ask questions) I came across many different views. A greater percentage saying ext4 has problems than the percentage saying ext3 has problems. Get what I mean?

The fact is that every indication I had, with what I was seeing on the screen, indicated that the repair process with fsck was not happening. I was getting cryptic messages about time being in the future and other problems. Yes there was a hardware problem, the machine did die a few days later. Doesn't even power up now.

---

### Post by wizarddrummer on 2010-08-21
> **Swagman said:**
> But you never had an Amiga so you failed in your quest!!
:p

On a serious note, Ext 4 has been rock stable here. 

cue crash !!

HA HA!

Not true... simply forgot about it; old motorola 68000. Loved the Sprites.

I also used had a PET computer in the late 70's and wrote an SMPTE Time Code Calculation on an old TRS-80 hand held computer with variables that were limited to one or two characters. Wrote the initial program in the IBM PC and then converted the variable names to the ones that TRS-80 would recognize and typed it in.

---

### Post by wizarddrummer on 2010-08-21
> **Dayofswords said:**
> btrfs seems bleeding edge even more =p

anyways
avoid this been-there-done-that, know-it-all, wiser-than-you, for example "I have FORGOTTEN more information than you will probably learn about computers. " attitude, as this is the feeling I'm getting
[IMG]http://ozguru.mu.nu/Photos/2005-11-11--Dilbert_Unix.jpg[/IMG]


make your point, prove it and wait for review, don't present yourself as better with your experience and use that to back up your point


> **Dayofswords said:**
> btrfs seems bleeding edge even more =p

anyways
avoid this been-there-done-that, know-it-all, wiser-than-you, for example "I have FORGOTTEN more information than you will probably learn about computers. " attitude, as this is the feeling I'm getting
[IMG]http://ozguru.mu.nu/Photos/2005-11-11--Dilbert_Unix.jpg[/IMG]


make your point, prove it and wait for review, don't present yourself as better with your experience and use that to back up your point

Everyone that has this opinion about me completely misunderstood my point. 

I was merely stating I have seen, experienced and learned an incredible amount of things in this industry and that my main point in all of that  was to illustrate that l love cutting edge stuff. Things. ATT&T has Bell Labs WilTel (before it became MCI-Worldcomm) had its version called ATG, where I worked. For 4 years I lived and breathed cutting edge and I loved it.

It was not in any way shape or form in the slightest way to represent myself as being better than anyone. Good grief! And I apologize to anyone that thinks that is what I was intending to do.

Two years is an insignificant amount of time to say that ext4 may or may not be as stable as ext3 in various hardware configurations.

The machine I was using died, so the fsck problems could be completely hardware related. Everything I was seeing on the screen indicated a fsck failure, when it could have been related to the hardware going bad. That computer had problems since the day I bought it. 

I am unable to write down all of the error and failure messages I was getting.

I am, due to circumstances beyond my control (a terminal illness and other factors) very poor at the moment and I have to try and scramble to see if I can borrow a computer and see if I can fix it on that.

The reason I said what I said about the forgotten part is the guy alluded that my problem was SIMPLE.

I wish Mr. Expert had been here at the moment the fsck process was puking on itself, for the fifth time, to tell me what my next plan of action should be.

---

### Post by NightwishFan on 2010-08-21
It is not that we doubt you, or even doubt that ext4 may have unresolved issues. It is just they have not revealed themselves through our use of the software. I personally thank you for the warning of caution, and indeed would use a more tested codebase on a production server. (I would probably be using Hardy with XFS or ext3).

---

### Post by fatality_uk on 2010-08-21
Here goes! Lets see if I got this right

You installed Ubuntu using ext4 despite having> "had some minor problems with each installation in one form or another"

Then you:> migrated a bunch of data from a smaller HD to the HD I installed the latest version of Ubuntu 10.4 LTS.

As an experienced "old geek" I would have thought that you would at least be aware that if a system has given you issues, previously, that you certainly wouldn't migrate data to it. Have it as a test system, but my no means use it to store data you might want to keep safe.

Seems to be that your didn't take the very basics steps to ensure your data integrity and as such you really don't have much cause to blame a file system which by your own words gave you issues on your hardware!

---

### Post by del_diablo on 2010-08-21
> **Swagman said:**
> On a serious note, Ext 4 has been rock stable here. 

Turn of directly the power, and watch some random files get deleted.
It is quite fun to provoke the effect :P

---

### Post by 73ckn797 on 2010-08-21
I have used ext4, on new drives, and within a week have had those drive become corrupted, with resulting bad sectors being created and one drive completely failed. I replaced the failed drive and using ext 3 have not had a problem in a year.

Never was having drive problems prior to ext4.

Maybe I was not holding my mouth right.

---

### Post by MCVenom on 2010-08-22
Ext4 has been great for me personally. That being said, I'd say this:

On one hand, ext4 is fine for desktop use, IMO.

On the other, you have a great point; Google's infrastructure is greatly redundant. If what I was doing was mission critical, or a server, or something like that, personally I'd use ext3 or another FS.

---

### Post by NightwishFan on 2010-08-22
I like ext4 because I personally like Theodore Ts'o, who is a developer. He seems to know what he is talking about ;), maintains the Debian ext* packages, and I have seem him around bug reports.

Keep up the good work.

---

### Post by Paqman on 2010-08-23
> **wizarddrummer said:**
> 
However, during one experiment, for lack of a better word, I used ext4 and had problems with it one day when it failed to boot. 


I'm not having a go, but this seems a bit circumstantial. You're not really describing anything that's conclusive diagnostically. Unless the ONLY thing you changed was switching the filesystem then there's way too many variables. Did you save some logs?

I'm not saying ext4 *wasn't* the cause of your problem, it's quite possible that it was. I just don't think you've proved it either way.

---

