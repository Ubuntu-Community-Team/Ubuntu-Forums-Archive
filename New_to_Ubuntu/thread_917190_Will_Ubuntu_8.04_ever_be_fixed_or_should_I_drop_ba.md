---
title: "Will Ubuntu 8.04 ever be fixed or should I drop back?"
date: 2008-09-11
forum: New to Ubuntu
---

### Post by carusoswi on 2008-09-11
So, I upgraded to 8.04 and I lost all wine and crossover functionality.  Upgraded to crossover 7, no joy.

I and others have posted our problems, and I have kept up diligently with updates.  

Yet, it's been quite a while, and, updates or no, whatever is causing my problems is not getting fixed.

Is it time for me to give up on 8.04 and go back to an earlier version (7.10)?

I'm not bitter, but, I cannot get my work done in Linux unless wine and/or crossover will run at least MS Office and preferably, some other aps.

Caruso

---

### Post by Paqman on 2008-09-11
What doesn't work for you? Wine in general, or just certain apps?

I've never had any problems with Wine on Hardy, myself.

---

### Post by starcannon on 2008-09-11
I'm not sure why wine is not working for you, but I am able to use wine on Ubuntu 8.04 with no problem at all here.

My best guess is something in your local /home/user_name/.wine directory is haywire. Perhaps back the ~/.wine directory up, then delete it, then reinstall wine and reinstall your windows apps, thats the best I can figure.

GL

---

### Post by carusoswi on 2008-09-12
> **Paqman said:**
> What doesn't work for you? Wine in general, or just certain apps?

I've never had any problems with Wine on Hardy, myself.

Photoshop 7 still works, but Office does not (well, MS Word works, but I cannot save documents to NTFS drives) . . . Access will not open files created when I was using Access in Wine on Ubuntu 7.10.  I cannot create new databases in Access, either.  Excel works, but I cannot save the files.

Nothing new will install, period.  

Note that in 7.10, all my wine/crossover 6 installations worked fine, and I could share, for instance, database files created in Access between XP and Ubuntu platforms, no matter which platform the database was originated.

I've done the reinstall of crossover and wine, I've reinstalled Ubuntu 8.10.

I know from browsing and posting on this forum that there are issues with Crossover/Wine.  I just cannot believe everyone is suffering so severely as I, or more of a fuss would be raised.

Am I alone in this?

My computer system isn't new, but isn't archaic, either.

I have an XPC Shuttle, 3.0 mHz, 2gb ram, multiple HD's with plenty of storage space, ample space on my Ubuntu partitions. 

The only change was my installation of 8.04 when it became available.  I've installed from the CD, I've tried the server version, etc.

I have an open ticket on the Crossover site, also.

Any additional suggestions welcome.

---

### Post by Tatty on 2008-09-12
So it sounds like a possible regression in wine itself perhaps.  

What version of wine are you using? If you are using the wine from the ubuntu repos then perhaps you should try installing the latest build from the wine ubuntu repo:

[http://www.winehq.org/site/download-deb](http://www.winehq.org/site/download-deb)

---

### Post by carusoswi on 2008-09-13
> **Tatty said:**
> So it sounds like a possible regression in wine itself perhaps.  

What version of wine are you using? If you are using the wine from the ubuntu repos then perhaps you should try installing the latest build from the wine ubuntu repo:

[http://www.winehq.org/site/download-deb](http://www.winehq.org/site/download-deb)

Thanks.  I already have that version of wine running on my system.
Caruso

---

### Post by clive littlewood on 2008-09-13
Hi

Why not use Open Office instead ??

cl

---

### Post by carusoswi on 2008-09-13
> **clive littlewood said:**
> Hi

Why not use Open Office instead ??

cl

For the work that I do, OO does not cut the mustard.  First of all, I cannot get OO database to even compete a form.  Even if it did, OO does not include the capability to define data integrity rules.  I use Access to control data whose integrity determines whether my company survives or perishes.  Access has it, OO doesn't.  For me, that is the end of that debate.

Caruso

---

### Post by billgoldberg on 2008-09-13
> **carusoswi said:**
> So, I upgraded to 8.04 and I lost all wine and crossover functionality.  Upgraded to crossover 7, no joy.

I and others have posted our problems, and I have kept up diligently with updates.  

Yet, it's been quite a while, and, updates or no, whatever is causing my problems is not getting fixed.

Is it time for me to give up on 8.04 and go back to an earlier version (7.10)?

I'm not bitter, but, I cannot get my work done in Linux unless wine and/or crossover will run at least MS Office and preferably, some other aps.

Caruso

Run Windows in a VM if Office is really that important for you.

Or dual boot.

--

If you don't know what a VM is, look at [this]("http://www.youtube.com/watch?v=KXgKnd-u2R4"), you might want to try it.

---

### Post by carusoswi on 2008-09-14
> **billgoldberg said:**
> Run Windows in a VM if Office is really that important for you.

Or dual boot.

--

If you don't know what a VM is, look at [this]("http://www.youtube.com/watch?v=KXgKnd-u2R4"), you might want to try it.

Actually, I do dual boot - and I need to make a correction to some info in my previous post - I do not, have never run 8.10 - that's either a typo or a senior moment.

Apparently, there are other avenues by which I should take to go about solving this problem, so, I will have to investigate and try to use them.  I have never posted anything on Launchpad, so will have to familiarize myself.  

One thing that confuses me is the status of 8.04.  It is the official release version of Ubuntu, currently, right?

When I look to download Ubuntu, that's the only version offered.  Is that correct, or, if I need earlier versions, is there a place to get those?

Caruso

---

### Post by bumanie on 2008-09-14
You can [go here]("http://releases.ubuntu.com/releases/") to get ealier versions, but I don't see any advantage as within 6-8 months none of them, (bar the present 8.04 version and subsequent releases) will have support. Up until kernel 2.6.24-21, which I've had a couple of issues with, I've found 8.04 to be very stable. Sorry to hear about your hassles. Some sort of virtualization as already suggested may suit you, but some for business purposes often fees are involved - the ubuntu KVM virtual pc may not - not 100% certain on that. Here's a  [link]("http://kvm.qumranet.com/kvmwiki") to KVM info.

---

### Post by mikewhatever on 2008-09-14
> **carusoswi said:**
> So, I upgraded to 8.04 and I lost all wine and crossover functionality.  Upgraded to crossover 7, no joy.

I and others have posted our problems, and I have kept up diligently with updates.  

Yet, it's been quite a while, and, updates or no, whatever is causing my problems is not getting fixed.

Is it time for me to give up on 8.04 and go back to an earlier version (7.10)?

I'm not bitter, but, I cannot get my work done in Linux unless wine and/or crossover will run at least MS Office and preferably, some other aps.

Caruso

It seems that the problems encountered after the upgrade are related to wine/crossover. Is that so? What happened to the version of wine?

If I were you, I'd never venture to upgrade. Wine is in Universe, while upgrading is supported and tested (I think) for main repositories only. That being the case, I rather doubt it's ever going to be fixed.

What about reinstalling wine?

---

### Post by carusoswi on 2008-09-14
> **mikewhatever said:**
> It seems that the problems encountered after the upgrade are related to wine/crossover. Is that so? What happened to the version of wine?

If I were you, I'd never venture to upgrade. Wine is in Universe, while upgrading is supported and tested (I think) for main repositories only. That being the case, I rather doubt it's ever going to be fixed.

What about reinstalling wine?

Mike:
Are you saying that I should not have upgraded wine, or that I should not have upgraded to 8.04 of Ubuntu?

I know that Ubuntu isn't Windows, but until the functionality I need is available in some native Ubuntu ap, I don't see many other practical routes to take other than sticking with those Windows aps.  I do dual boot, so it's not like I'm strangling or have left myself out on a limb.

I just hate having to boot into Windows.  In 7.10, I almost never had to, even when I wanted to take databases from my home machine (ubuntu) into the office (XP only).

I am still biding my time until Ubuntu (or some form of Linux) has everything I, as a user and the person responsible for seeing that my work office environment remains productive, but as no expert or programmer by any stretch, need in order to migrate all workstations at the office over to Linux.

OO word processor is fine, the spreadsheet is ok, but the database seems to have broken parts and certain features lacking that I cannot afford to be without.  For these, I turn back to XP for now.

Someday, we'll look back on all of this and exclaim how much simpler things have become.

Thanks for the replies.

Caruso

---

### Post by carusoswi on 2008-09-20
Success with Crossover at last.  I have been toying around with this issue off an on since I first upgraded to 8.04, and I always upgrade as soon as a new release of Ubuntu is available.  

Why it worked this time around I'm not certain, but for others who have experienced the problem, this is what worked for me now:


sudo sysctl -w vm.mmap_min_addr=0



then, in order to keep this setting after a reboot:



sudo gedit /etc/sysctl.conf

edit to change this line: vm.mmap_min_addr = 65536  


to this: vm.mmap_min_addr = 0


Of course, none of the above is at all new, and I had tried changing it before.

Upon attempting to add Office using Crossover, I still experienced errors, but noticed that one of the Office install routine's complaints was that it could not find IE5.

I looked online for IE5 but couldn't find it.  Downloaded IE6 and installed it into a Crossover bottle in lieu of IE6.

I then installed Office into the same bottle.

Whether what I did is correct or not, the install completed, and I can now open existing Access database files that behave normally.  I haven't tried creating a new databse, but feel confident that things will work correctly, now.

Obviously, the installation of the new version of Ubuntu back when broke whatever IE verision I had installed in my existing Crossover installation of Office so that it would not work any longer.

Happy to report that things are working normally, now.

I am also glad that success came when it did.  I was about to revert to Ubuntu 7.10 in order to fix this problem, but, my guess is that I would have been disappointed.

To the forum:  thanks for being patient with me, and I hope the above information is useful to someone else experiencing the sort of frustration with which I have been grappling over the last six months or so.

Caruso

---

### Post by Therion on 2008-09-20
I know your issue is resolved, but just for future reference, running MS Office in XP via Virtual Box is about stupid-simple.  
I'd suggest you might want to look into some time.

[How to Install Virtual Box](http://n00buntu.blogspot.com/2007/11/howto-ubuntu-compiz-virtualbox-part-1.html)

Just a thought.  VB is a great little application and I understand how sometimes you've GOT to use the MS app; just no way around it.  VB makes it a snap!

---

### Post by carusoswi on 2008-09-20
> **Therion said:**
> I know your issue is resolved, but just for future reference, running MS Office in XP via Virtual Box is about stupid-simple.  
I'd suggest you might want to look into some time.

[How to Install Virtual Box](http://n00buntu.blogspot.com/2007/11/howto-ubuntu-compiz-virtualbox-part-1.html)

Just a thought.  VB is a great little application and I understand how sometimes you've GOT to use the MS app; just no way around it.  VB makes it a snap!

Thanks for the reply.  I've used VB and VMWare.  They worked fine, but I really would rather not work within XP if not necessary.  Also, if I recall, I had problems saving my work or exporting it to other than the virtual space.  One day, I'll load VB up again and see if I can sort through those other problems that were, no doubt, due to my own lack of expertise and understanding about how to do things.

Not to go totally OT, but I had problems getting my usb ports to work in VB - I'd have 'em working at one point, then lose them, etc.

Thanks again for the reply.

Caruso

---

