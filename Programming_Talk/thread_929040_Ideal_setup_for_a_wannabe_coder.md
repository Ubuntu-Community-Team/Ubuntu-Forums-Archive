---
title: "Ideal setup for a wannabe coder?"
date: 2008-09-24
forum: Programming Talk
---

### Post by Plan B on 2008-09-24
Hello all.

Current situation:
I've been using Ubuntu64 for about a year now.  My current setup is dual boot Ubuntu 7.14 & XP 64.  It works well for me, I use Ubuntu during the week for general use and studying, and Windows at weekends for playing games and movies.
I'm coming to the end of a software development diploma and soon it'll be time to go back to work :( and replenish the bank account.  Good thing about that is a computer upgrade is in the planning and I want to know how you more experienced coders have your computers setup and also some tips for the future. I did Java as my major and want to continue studying this further in my spare time and to go for J certification and also another language.

Problems:
Right now I sometimes have problems accessing media files on Windows NTFS partitions from Ubuntu.  This isn't really a big problem, but I have a large music collection and having to double it up on both Windows & Ubuntu seems like a waste of HD space. But I will do it if I have too.  My plans are to get a new 200G HD to run OS's on.

Questions:
What OS's are you running for coding or testing, Linux, Win or otherwise?
What jobs could you recommend for someone trying to start out in this business considering I'm not experienced or fully qualified?
What's a good second language to learn?
What other subjects should I be looking into? Db, web skills,other?
Is a dual monitor setup worthwhile?
Anything else you think might be useful?

A few questions and you've prolly covered these somewhere else so please feel free to cut and paste or link to relevant threads.

Thanks.

---

### Post by LaRoza on 2008-09-24
> **Plan B said:**
> 
Current situation:
I've been using Ubuntu64 for about a year now.  My current setup is dual boot Ubuntu 7.14 & XP 64.  It works well for me, I use Ubuntu during the week for general use and studying, and Windows at weekends for playing games and movies.


I am not sure what version 7.14 refers to ;) 8.04 is the latest.

> 
Problems:
Right now I sometimes have problems accessing media files on Windows NTFS partitions from Ubuntu.  This isn't really a big problem, but I have a large music collection and having to double it up on both Windows & Ubuntu seems like a waste of HD space. But I will do it if I have too.  My plans are to get a new 200G HD to run OS's on.

Use the latest version. The easiest solution is to have the Windows and Ubuntu partitions small, and use the rest of the drive for the sharing. 

> 
Questions:
What OS's are you running for coding or testing, Linux, Win or otherwise?

Ubuntu 8.04

> 
What's a good second language to learn?

See my learn to program site (in sig) and check out the language selector.

> 
Is a dual monitor setup worthwhile?

If it is worthwhile depends on if it is worthwhile. ;) You be the judge.

---

### Post by Plan B on 2008-09-24
> **LaRoza said:**
> I am not sure what version 7.14 refers to ;) 8.04 is the latest.

I'll be upgrading when I get the new drive, not much point doing it now.

> 
Use the latest version. The easiest solution is to have the Windows and Ubuntu partitions small, and use the rest of the drive for the sharing.

What format is the extra partition? 


> 
See my learn to program site (in sig) and check out the language selector.

Already have, thanks.  I was thinking what would be a good language to learn as well as Java, something complimentary or something completely different for a wider skill base. So far I've done bits of C, C++ Cobol and Java.

> 
If it is worthwhile depends on if it is worthwhile. ;) You be the judge.  

Yeah stupid question I guess. It was a bit annoying switching between IDE and APIs when studying.  The answer must be Yes. 
:)

---

### Post by LaRoza on 2008-09-24
> **Plan B said:**
> 
What format is the extra partition? 

You can use NTFS or EXT2. The ext2 driver for Windows works well (just don't use it to alter the / of Linux).

[http://www.fs-driver.org/](http://www.fs-driver.org/)

> 
Already have, thanks.  I was thinking what would be a good language to learn as well as Java, something complimentary or something completely different for a wider skill base. So far I've done bits of C, C++ Cobol and Java.

Try Scheme, Python or Ruby.

---

### Post by Tomosaur on 2008-09-24
> **Plan B said:**
> Hello all.

Current situation:
I've been using Ubuntu64 for about a year now.  My current setup is dual boot Ubuntu 7.14 & XP 64.  It works well for me, I use Ubuntu during the week for general use and studying, and Windows at weekends for playing games and movies.
I'm coming to the end of a software development diploma and soon it'll be time to go back to work :( and replenish the bank account.  Good thing about that is a computer upgrade is in the planning and I want to know how you more experienced coders have your computers setup and also some tips for the future. I did Java as my major and want to continue studying this further in my spare time and to go for J certification and also another language.

Problems:
Right now I sometimes have problems accessing media files on Windows NTFS partitions from Ubuntu.  This isn't really a big problem, but I have a large music collection and having to double it up on both Windows & Ubuntu seems like a waste of HD space. But I will do it if I have too.  My plans are to get a new 200G HD to run OS's on.


You could just run Windows in a virtual machine on Ubuntu, if you don't plan on playing games or anything like that. Removes the need for you to reboot if you want to test a program in Windows.

> 
Questions:
What OS's are you running for coding or testing, Linux, Win or otherwise?
Instant hypocritical statement :P : I dual boot Ubuntu and Windows XP. If rebooting is not an option, I have another PC which just has XP (family PC) which I can use for testing.

> 
What jobs could you recommend for someone trying to start out in this business considering I'm not experienced or fully qualified?Where I'm from (UK) - the biggest obstacle to finding a job in the development field was experience. Your best bet, without formal qualifications, is to get a good sized portfolio of programs you have created, complete with design documentation, user manual etc. Make it LOOK GOOD. Polish is everything if your potential employer doesn't appreciate the technical aspects (and a lot of them don't, although at least one of the interviewers will generally have experience, but do not just ignore polish to appeal to this guy / girl, as you want to impress every one of the interviewers individually).

> 
What's a good second language to learn?
Depends what you want to do, really :S Python is becoming more widespread, but it's always good to have experience with C, C++, or C#. The C-like languages (including Java) all share somewhat similar syntax, so picking up the language itself isn't really that hard. It's the libraries and limitations of each which will catch you out, and these are what you need to learn. Python's syntax is pretty different (much cleaner, more intuitive).

> 
What other subjects should I be looking into? Db, web skills,other?
Can't hurt. Database development is one of the biggest software development areas, so knowledge of database design and development is always a plus. Web dev skills can help - particularly XML, CSS (CSS is very often listed on the 'benefical' section of the job description), AJAX (or just JavaScript on its own), PHP, and server admin stuff - although these are generally not necessary unless you want a web dev job.

> 
Is a dual monitor setup worthwhile?
Well I don't use one - but I guess having the IDE and the documentation pages given a full screen each would be very helpful. If you haven't got one, I wouldn't spend any money on it if I were you. If you've got a spare monitor lying around, could be good.

> 
Anything else you think might be useful?
Be willing to admit when you don't know something - not least to yourself. I have the worst memory in the world. If you asked me now how to do pretty much anything more than a simple hello world app in most languages I'd probably stumble around like an idiot. I kind of 'remember as I go', if you see what I mean. If I'm in the process of doing it, I can generally do it without having to keep looking stuff up, but I'm not ashamed to admit I keep all kinds of documentation stuff open when I'm coding. If I forget, I don't waste my time racking my brain - I just re-learn it. No doubt it will have left my brain again in a day or two, but don't stress yourself out if you keep forgetting stuff. It's why it's written down in the first place.

---

