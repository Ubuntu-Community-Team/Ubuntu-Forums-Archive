---
title: "Proposal for a new, unique Linux Distro"
date: 2012-12-14
forum: Recurring Discussions
---

### Post by MrLinux2011 on 2012-12-14
Fellow Linux Users,
 
 
My name is Noah Bangs. I have thought about this idea of an awesome Linux distro for quite some time. I think I should speak my mind.
 
This idea of mine is a Linux distro built with 100% open source libraries/software, and uses the power of Wine and Darling (A Mac Compatibility layer for Linux created by Lubos Dolezel) to natively run Windows, Mac (Yes, I know about their licensing restrictions), and Linux software in one.
 
Compatibility layers are cool, but the support for most programs need to be way ahead of the competition (Like what the people at ReactOS are doing with their open source implementation of Microsoft Windows).
 
Despite all that, I personally would love nothing more than to make this. The trouble is, thanks to my Asperger Syndrome, I can't program. That is why I am trying to find volunteers to help me out and make this thought a reality. I know it will be completely legal because only open source software will be used.
 
 
You don't have to help if you don't want to, but I would appreciate if any one did. Anyway I just thought I'd speak my mind.
 
 
Cheers,
 
Noah Bangs

---

### Post by grahammechanical on 2012-12-15
It is possible to install Ubuntu with only free software. There is a test case for it at Quality Assurance. It explains how to do it.

[http://iso.qa.ubuntu.com/qatracker/testcases/1307/info]("http://iso.qa.ubuntu.com/qatracker/testcases/1307/info")

Basically, we press enter at the first purple/aubergine screen. Then select the language and press F6 - select Free Software Only and press enter and then Esc and we are back to the options to TRY or Install.

Do you realize that someone who wants an entirely Free and Open Source Linux distribution would never use proprietary software on such a system?

You have a built-in contradiction in wanting an entirely Free and Open Source Linux and also wanting to run proprietary software.

Also, you will find that some of that proprietary software will not run unless you have proprietary fonts installed.

So, why object to installing third party software (which includes proprietary fonts) if you want to run proprietary applications?

Regards.

---

### Post by sffvba[e0rt on 2012-12-15
*Thread moved to **Recurring Discussions**.*


404

---

### Post by MrLinux2011 on 2012-12-15
> **grahammechanical said:**
> It is possible to install Ubuntu with only free software. There is a test case for it at Quality Assurance. It explains how to do it.
 
[http://iso.qa.ubuntu.com/qatracker/testcases/1307/info](http://iso.qa.ubuntu.com/qatracker/testcases/1307/info)
 
Basically, we press enter at the first purple/aubergine screen. Then select the language and press F6 - select Free Software Only and press enter and then Esc and we are back to the options to TRY or Install.
 
Do you realize that someone who wants an entirely Free and Open Source Linux distribution would never use proprietary software on such a system?
 
You have a built-in contradiction in wanting an entirely Free and Open Source Linux and also wanting to run proprietary software.
 
Also, you will find that some of that proprietary software will not run unless you have proprietary fonts installed.
 
So, why object to installing third party software (which includes proprietary fonts) if you want to run proprietary applications?
 
Regards.
 
 
thank you for the response.
 
the reason why is because of 2 things:
 
1. I don't want to run into legal roadblocks.
 
2. I just want a simple OS that can natively run proprietary stuff without the risk of crashing. I generally don't like running back and forth.
 
just thought I'd tell you

---

### Post by C.S.Cameron on 2012-12-17
Have you tried Virtual Box on a Ubuntu host?
You can run Windows and OSX but you need the install disks, (or iso's).

---

### Post by KiwiNZ on 2012-12-17
> **C.S.Cameron said:**
> Have you tried Virtual Box on a Ubuntu host?
You can run Windows and OSX but you need the install disks, (or iso's).

Please do not discuss the use of OSX on non Apple Hardware.

---

### Post by MrLinux2011 on 2012-12-17
> **C.S.Cameron said:**
> Have you tried Virtual Box on a Ubuntu host?
You can run Windows and OSX but you need the install disks, (or iso's).
 
I have.
 
One drawback is that you can't use all the ram, hard drive space, etc.
 
 
Look at the people at ReactOS. There making a open source implementation of Microsoft Windows using GPL software.
 
I don't understand why my Linux Distro idea isn't popular. I'm not complaining or anything, I just wonder why.
 
I would use stuff like NTFS-3G(FUSE), GNUStep, Wine, etc.
 
I guess I just wanted to try.

---

### Post by 3rdalbum on 2012-12-17
> **MrLinux2011 said:**
> 
I don't understand why my Linux Distro idea isn't popular. I'm not complaining or anything, I just wonder why.
 
I would use stuff like NTFS-3G(FUSE), GNUStep, Wine, etc.
 
I guess I just wanted to try.

It's okay to try.

There are a couple of problems with your idea (and trust me, you're not the first to think of it):

1. There's nothing that can run Macintosh programs on Linux without running the Mac OS too.

2. If you managed to write such a thing, it would probably take you as long as it took the Wine developers to write theirs - something like 8 years to achieve still a low amount of compatibility. Windows 8 apps are still totally unrunnable on Linux and may need a few years of Wine development to be usable, and every time a new Mac OS point version comes out it breaks compatibility.

3. You'd need some way of linking Windows and Mac programs seamlessly into the desktop. Not unsurmountable, but you'd need to be a pretty good programmer to write wrappers and modify Wine APIs.

4. If your project was a success and worked well, it would discourage people from writing native Linux programs.

5. If your project was a success and worked well, you'd be sued into oblivion. Even if you did everything legally. Apple and Microsoft would not sit by and let you take away any of their revenue streams.

It's a great idea in theory, but it would only ever stay in theory. Look at the ReactOS people; they've been working on their operating system for years, reusing Wine code, and still they can barely get the thing to boot up on real computer hardware. I'm not diminishing their efforts - in fact I admire how well they've done against the odds - but simply stating how difficult it is. Impossible for someone who can't program.

---

### Post by MrLinux2011 on 2012-12-17
> **3rdalbum said:**
> It's okay to try.
 
There are a couple of problems with your idea (and trust me, you're not the first to think of it):
 
1. There's nothing that can run Macintosh programs on Linux without running the Mac OS too.
 
2. If you managed to write such a thing, it would probably take you as long as it took the Wine developers to write theirs - something like 8 years to achieve still a low amount of compatibility. Windows 8 apps are still totally unrunnable on Linux and may need a few years of Wine development to be usable, and every time a new Mac OS point version comes out it breaks compatibility.
 
3. You'd need some way of linking Windows and Mac programs seamlessly into the desktop. Not unsurmountable, but you'd need to be a pretty good programmer to write wrappers and modify Wine APIs.
 
4. If your project was a success and worked well, it would discourage people from writing native Linux programs.
 
5. If your project was a success and worked well, you'd be sued into oblivion. Even if you did everything legally. Apple and Microsoft would not sit by and let you take away any of their revenue streams.
 
It's a great idea in theory, but it would only ever stay in theory. Look at the ReactOS people; they've been working on their operating system for years, reusing Wine code, and still they can barely get the thing to boot up on real computer hardware. I'm not diminishing their efforts - in fact I admire how well they've done against the odds - but simply stating how difficult it is. Impossible for someone who can't program.
 
I understand.
 
If I may address these problems:
 
1. There is a project called Darling that is in early development that is able to run Darwin/OSX programs.
 
2. I guess I should try and save up a ton of money then.
 
3. I try finding some in the future.
 
4. Needless to say, maybe there are die-hard OS fans out there.
 
5. But how come ReactOS isn't sued into oblivion by Microsoft by now? I really don't think people can sue a product, which has no code written by them except GPL code, just because they are losing money. It would just be totally unfair.
 
 
 
I just don't understand why there would be problems in the first place.

---

### Post by Primefalcon on 2012-12-17
if you are really concerned about only using free software try gnewsense ([http://www.gnewsense.org]("http://www.gnewsense.org/")), its ubuntu with all the good stuff ripped out

---

### Post by monkeybrain2012 on 2012-12-17
> **MrLinux2011 said:**
> I understand.
 
5. But how come ReactOS isn't sued into oblivion by Microsoft by now? I really don't think people can sue a product, which has no code written by them except GPL code, just because they are losing money. It would just be totally unfair.
 

Because it is already in oblivion?

It seems that you are not really interested in a Linux distro that uses only free software (there are already a few), but some kind of free hybrid of OSx and MS Windows clones.

If I have the coding skill I would rather contribute to Linux proper instead of wasting time and resources on making Windows and OSX clones, just saying.

---

### Post by C.S.Cameron on 2012-12-17
> **KiwiNZ said:**
> Please do not discuss the use of OSX on non Apple Hardware.

Hi, could you please point out which item in the Forums Code of Conduct forbids such discussion.
There are over a hundred threads in the Virtualisation section that discuss this.

---

### Post by KiwiNZ on 2012-12-17
> **C.S.Cameron said:**
> Hi, could you please point out which item in the Forums Code of Conduct forbids such discussion.
There are over a hundred threads in the Virtualisation section that discuss this.

"Users agree not to post anything abusive, rude, obscene, vulgar, slanderous, hateful, threatening, advertising or marketing related, or sexually-oriented. Material that suggests illegal activity or contains illegal content is also forbidden. We do not support circumventing TOS, EULA, etc here. Such threads will be closed and offending users will be penalised with infractions and warnings. Also, our forums are used by people at work and school and we want to ensure they will not encounter material that will cause them problems or cause their access to our site to be limited, so all content should be safe for work and school."

---

### Post by C.S.Cameron on 2012-12-17
> **KiwiNZ said:**
> "Users agree not to post anything abusive, rude, obscene, vulgar, slanderous, hateful, threatening, advertising or marketing related, or sexually-oriented. Material that suggests illegal activity or contains illegal content is also forbidden. We do not support circumventing TOS, EULA, etc here. Such threads will be closed and offending users will be penalised with infractions and warnings. Also, our forums are used by people at work and school and we want to ensure they will not encounter material that will cause them problems or cause their access to our site to be limited, so all content should be safe for work and school."

Running desktop OSX on a non Mac machine may be illegal, discussing it is a matter of free speech and is  not illegal, at least in civilized countries. Life Hacker does it all the time.

Anyway, as I understand, it is perfectly legal to run OSX on a virtual machine on a Mac as long as it is per the EULA, or to run OSX server on a non Mac machine.

---

### Post by KiwiNZ on 2012-12-18
> **C.S.Cameron said:**
> Running desktop OSX on a non Mac machine may be illegal, discussing it is a matter of free speech and is  not illegal, at least in civilized countries. Life Hacker does it all the time.

Anyway, as I understand, it is perfectly legal to run OSX on a virtual machine on a Mac as long as it is per the EULA, or to run OSX server on a non Mac machine.

My post was "Please do not discuss the use of OSX on non Apple Hardware."

You are free to exercise your freedom of speech in other venues.

---

### Post by whatthefunk on 2012-12-18
I dont understand the point of this proposed OS.  If you want to run Microsoft and Apple programs, use Windows.  It will be a whole lot easier and cheaper then spending the next decade of your life trying to emulate two different OS environments and the next ten years batteling patent and copywrite lawsuits in cout rooms around the world.

A much better thing to do would be to use Linux, donate to a Linux distro of your choice, and financially support program development for Linux by purchasing programs for Linux.  I think the computing world is starting to figure out that Linux users are actually more than happy to pay for high quality programs and games for Linux.   My guess is that in the next 5 - 10 years we're going to start seeing a lot more coming out for us.

---

### Post by iponeverything on 2012-12-18
> Re: Proposal for a new, unique Linux Distro

> Thread moved to Recurring Discussions.

Love the irony.. hope it was intentional.

---

### Post by MrLinux2011 on 2013-01-20
First, I am sorry for bumping this topic.
 
 
Second, I guess I just wanted some help. All I get is questions.
 
 
I'm not yelling at or putting down anyone, it just saddens me that no one has attempted to give it a try except me.
 
 
I just don't see the problem of using open source kernels, libraries, API's, & stuff to create a hybridized version of the three OS's.
 
If ReactOS is already in oblivion, why is it still being developed?

---

### Post by aysiu on 2013-01-20
> **MrLinux2011 said:**
> 
I'm not yelling at or putting down anyone, it just saddens me that no one has attempted to give it a try except me. Can you post up a download link to your first try? Maybe others can improve what you've started. Or are you just demanding others create something for you without paying them? If you don't pay people, they will just work on what *they* want to work on, not on what *you* want them to work on.

---

