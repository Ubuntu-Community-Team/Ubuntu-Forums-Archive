---
title: "What should an OS be?"
date: 2006-12-12
forum: Other OS Talk
---

### Post by wrycatcher on 2006-12-12
Quick background, I started programming on AppleIIe circa 1983.  I have been doing system admin and programming ever since, mostly in DOS/Windows environment, and UNIX (college).  The command line was, and still is, my best friend, though.

I have come back to Linux after a 5 year hiatus.  Back then, I had played with RedHat Linux and Debian for a time, but nothing serious developed.  I was turned off by the some issues just getting hardware detected and then appropriate drivers installed.  Another pain point was my internet connection (dial-up) which was prohibitively slow for any package management.  So, it was simply easier to go back to what I knew worked (Windows 98 and 2000) with my hardware and ran all my apps and games.  

Fast forward 5 years.  My 3-year old underpowered system started to blue screen Windows XP on a _daily_ basis.  Something about an "unknown command" (driver issue).  After much error log analysis, hardware testing, and Googling, I still didn't have a good explanation.  I even tried to upgrade all my device drivers to the latest versions.  Nothing fixed the BSOD (blue screen of death), so I performed a disk wipe and re-install.  As a Windows user who's been through several buggy OS releases, this is nothing new.  I've actually been conditioned to expect it as crazy as that sounds.  After re-install of XP, it only takes BSOD 24 hours to make its return.  ](*,)  I wonder what Linux has been up to the last few years?  

Fast forward about 1 month.  Been running Ubuntu (Edgy) for about 4 weeks with no problems and **ZERO** crashes.  I have had to search out a lot of "newbie" documentation as well as some more involved system admin "how to's".  I've learned so much, but I'm only scratching the surface on what is possible.  I did take a detour down a DSL (Damn Small Linux) distro path, but that ended quickly after I realized how tricky some things like Printing and Networking were compared with Ubuntu's GUI config.  I'm being selectively ignorant here, but it's in the interest of time.

Fast forward a week.  DSL experiment over, there's a week I won't get back, but it wasn't a total waste.  DSL has developed my craving for the simple and the fast.  Ubuntu reinstalled.  Learning how boost performance with tips from the Ubuntu forums.  XFCE is quicker than Gnome, so its my new windows manager.  I've gotten my feet wet with several core applications.  It's not _all_ painless.  I'm taking time to selectively learn where it shows promise of being useful.

So, here's my perspective today on all the OS wars.  Windows might be the best OS for someone depending on what they seek.  If they want the OS to make the majority of the decisions and settings for them (by default or based on a wizard), perhaps Windows (or maybe Mac OS X) is for them.  For those who are willing to *attempt to learn* how to do some "lower level" system configuration and tweaking, in response for greater control over their environment, Linux is a compelling option.  Linux is started to get a little more "out of the box" friendly now, however, with better hardware support, more GUI admin tools, and these LiveCD versions (or embedded ones).  This will go a long way toward wider exposure and adoption of Linux as a viable alternative to Windows, but Windows will still continue to dominate because there still exists (and will continue to exist) a large user base that wants the "for dummies" version that they do not have to invest _any_ significant time into learning.  That's the barrier as I see it.  Too many folks too content with the status quo, not realizing the alternatives available to them, and not really motivated enough to really try anything else.  Old habits die hard, my friends.

One thing I do think is good is that Windows, BSD distros, MacOS, and all the Linux distros, they are all written with enough different perspective as to what an OS/distro should be that the user is the winner in the end.  Innovations in one generally make their way into the others.  Each one pushes the others to be that much more innovative, secure, robust, fast, powerful, pretty, self-maintaining, etc.  Of course, each OS/distro producer has their own ideas about what is most important in that list, which is why we have so many choices.  It's also nice to have so many choices so the user can sift through and find one they think fits them best, too, even if at the end of it all their selection ends up being MS Windows.

---

### Post by aysiu on 2006-12-12
[quote=wrycatcher]It's also nice to have so many choices so the user can sift through and find one they think fits them best, too, even if at the end of it all their selection ends up being MS Windows.[/quote] Couldn't agree more. Of course, it would be even nicer if people could walk into a store like Best Buy and see side by side a Linux laptop, a Windows laptop, and a Mac laptop. On any hardware they were thinking about purchasing, they could potentially see the Windows logo, the blue Apple face, or a Linux penguin--indicating compatibility with up to three major platforms.

By the way, you may want to look into IceWM. It's lighter than XFCE. If you already have Gnome installed, I have an easy little script you can run to make IceWM look a little nicer than its default and a bit more Gnome-friendly.

Just download it to your desktop and ```
cd Desktop
tar -xvzf icewm.tar.gz
chmod +x setupicewm.sh
./setupicewm.sh
``` Finally, log out of of XFCE/Gnome, select IceWM from the session menu, and log back in again.

---

### Post by Henry Rayker on 2006-12-12
I agree totally about the hardware compatibility thing.

Honestly, I would try OSX if I wouldn't have to pay for THEIR hardware. I prefer to bargain hunt and, if something fails, or I want to upgrade the processor/mobo/whatever, I don't want to have to replace the whole thing or go through them.

It's also a shame that Linux is plagued with the hardware incompatibilities (although that IS getting better). I just think it would be interesting to see the market if all the OSes had an even playing field, in terms of hardware support.

---

### Post by wrycatcher on 2006-12-12
> **aysiu said:**
> 
By the way, you may want to look into IceWM. It's lighter than XFCE. If you already have Gnome installed, I have an easy little script you can run to make IceWM look a little nicer than its default and a bit more Gnome-friendly.

Just download it to your desktop and ```
cd Desktop
tar -xvzf icewm.tar.gz
chmod +x setupicewm.sh
./setupicewm.sh
``` Finally, log out of of XFCE/Gnome, select IceWM from the session menu, and log back in again.

Thanks for the tip!  I'm always looking for little nuggets like that.  It's nice to be able to "flip" the look and feel so easily, too, and also save CPU cycles...

---

### Post by mips on 2006-12-12
> **wrycatcher said:**
> 
After re-install of XP, it only takes BSOD 24 hours to make its return. 

If you had a system that ran fine for ages and the starts getting a BSOD and you do a clean re-install of the os and it still happens it could mean there might be a hardware issue. Not always the case but a possibility.

---

### Post by wrycatcher on 2006-12-12
> **mips said:**
> If you had a system that ran fine for ages and the starts getting a BSOD and you do a clean re-install of the os and it still happens it could mean there might be a hardware issue. Not always the case but a possibility.

True.  That's what I feared, too.  I ran a couple of hardware analysis tools (ram analyzer was one).

I had a device that was relatively new to that PC.  I have since removed (as it's not compatible with _any_ flavor of Linux that I've found).  It's an older, parallel scanner.  Older driver, unsupported in XP.  Could have been the cause.  I'll never know for certain, but I'm definitely not going back to XP.  I've become rather attached to Ubuntu in my brief time using it.  Ubuntu has rekindled the hope I once held for Linux to change the landscape of computing.  Might be naive, but I'm an idealist at heart.

---

### Post by SunnyRabbiera on 2006-12-12
I personally like a balance in my ideal OS, the stability and security of linux and BSD, the ease of use of windows and a nice interface like OSX.
Linux has the capacity of all 3 when you think about it, as it can be very easy to use, its stable and it can be dressed up real smooth.
Linux and BSD have a lot of potential, now to get the recognition!

---

### Post by neemz on 2006-12-12
For me an ideal operating system would operate the system and I would operate the applications to do some work.

However no matter what OS I use (apart from OSX) I spend half my time operating the operating system :p

---

### Post by Phototrek1 on 2006-12-12
An os should be about choice, open formats, compatablity and modularity. 
- Choice, Go to any computer vendor and pick 1 of 5 OS's to use.
- Open Formats  Every OS should use universal free open formats for data storage. Excludeing DRM materials.
- Compatablity Every pice of software and hardware should work for the top 5 OS's
- Modularity Every Os should be modular so that one may remove IE       with out it being a dependancy for any application. 


This is what i want an OS to be.  This would make a much better competive playing field. Thus pushing computeing even further and faster. And out law vendor lockin. These principles, if everyone adopted them, would recreate the DOS era business landscape. Where one had a choices of MS DOS, PC DOS, DR-DOS or any other dos that may have been.

---

