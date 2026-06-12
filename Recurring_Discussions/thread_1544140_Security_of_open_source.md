---
title: "Security of open source?"
date: 2010-08-02
forum: Recurring Discussions
---

### Post by noingwhat@yahoo.com on 2010-08-02
Hi! I am thinking of trying to build my own Linux distro, and I am thinking of making it open source. The reason I am posting under Ubuntu's forums, is because someone here should have already solved my problem, I am just checking out why.

What I want to know, is a little more about open source. To me, with a distro as large as Ubuntu, wouldn't it be pretty easy for someone to look at the source of the OS, and find a hole easily, so they can make a virus or something of the sort that would be nearly impossible to get around? Having everyone seeing the behind the scenes is nice, but I just am not sure if I would want people to know all of my inner working. I just don't find it to be safe. I am just begging to put my ideas together and everything, so I don't get opensource 100%, but so many different software companies are doing it and there are too many reasons why. I just don't know about open source on an OS.

Thanks to anyone who tried to help me out a bit!

---

### Post by dino99 on 2010-08-02
follow my links below first, you will learn the basics  ;) before trying to build your own

---

### Post by FuturePilot on 2010-08-02
Having something closed source doesn't make it more secure. Just look at Windows. Also, if you're the sole maintainer of said distro and someone finds a vulnerability you better sure as heck know how to fix it. However seeing as most Linux software is GPL you would *have* to release the source. It's not an optional requirement.

> wouldn't it be pretty easy for someone to look at the source of the OS, and find a hole easily, so they can make a virus or something of the sort that would be nearly impossible to get around?
No. When someone finds a vulnerability someone else is right there to fix it. Thousands of eyes on the source code is a good thing.

---

### Post by bodhi.zazen on 2010-08-02
MOved to recurring discussions. This is an old discussion.

---

### Post by splicerr on 2010-08-03
> **noingwhat@yahoo.com said:**
> Hi! I am thinking of trying to build my own Linux distro, and I am thinking of making it open source.


I don't quite understand what exactly you thinking about of making open source. If you are building your own Linux distro that means you will be using lots of software that you did not create and of which you do not own the copyright. Only if the software you did not create and not own the copyright of is licensed under a BSD like other permissive license you have a choice not to make it open source.  Lots of Linux software is licensed under the (L)GPL, this includes the Linux kernel and the GNOME desktop environment. You do not have a choice and cannot make that closed source.

Really, you shouldn't even be thinking about going in the distro business if you don't even have basic knowledge about open source and the different licenses out there. You could be in for a lot of legal trouble.

---

### Post by sydbat on 2010-08-03
I think the spamming troll bot is full. 

/Thread.

---

### Post by SunnyRabbiera on 2010-08-04
open source is actually more secure then closed source in the long term.
open source software offers the code up front so that patches can be made faster.

---

### Post by Frak on 2010-08-05
> **FuturePilot said:**
> No. When someone finds a vulnerability someone else is right there to fix it. Thousands of eyes on the source code is a good thing.

A good point to make is: if it is reported. There are probably exploits to some open source software that were created from reading the source. Nothing's 100%. As for the security of Open Source, eh, it's on par with proprietary software, it just has a longer lifecycle.

---

### Post by Lucradia on 2010-08-05
> **SunnyRabbiera said:**
> open source is actually more secure then closed source in the long term.
open source software offers the code up front so that patches can be made faster.

+1 to this. But most open source projects have stubborn bug squashers. You need to not only prove that the bug is real by various debug logs, screenshots, etc. But you also need to get the bug's mother involved! Plus a few dozen UPCs, box tops, and a few people who think you know as friends, but really don't, but you need their consensus on the bug being a bug to have the bug be a bug!

So, basically, even if you could report the bug, what's not stopping you from not reporting the bug because of past experiences?

Yours,
Strong Bad.

*cough* Sorry, had to write it out the way he would, rofl.

---

### Post by Shining Arcanine on 2010-08-05
> **splicerr said:**
> I don't quite understand what exactly you thinking about of making open source. If you are building your own Linux distro that means you will be using lots of software that you did not create and of which you do not own the copyright. Only if the software you did not create and not own the copyright of is licensed under a BSD like other permissive license you have a choice not to make it open source.  Lots of Linux software is licensed under the (L)GPL, this includes the Linux kernel and the GNOME desktop environment. You do not have a choice and cannot make that closed source.

Really, you shouldn't even be thinking about going in the distro business if you don't even have basic knowledge about open source and the different licenses out there. You could be in for a lot of legal trouble.

He could try forking FreeBSD. Unlike GPL software, People have the freedom to make closed source forks of BSD software.

---

### Post by 3rdalbum on 2010-08-06
> **noingwhat@yahoo.com said:**
> What I want to know, is a little more about open source. To me, with a distro as large as Ubuntu, wouldn't it be pretty easy for someone to look at the source of the OS, and find a hole easily, so they can make a virus or something of the sort that would be nearly impossible to get around?

Not at all. For a start, most code that runs on Linux has been written with Linux's security system in mind. This code has been written to be secure, basically. It's hard to find vulnerabilities in Linux software.

Secondly, if you could create a virus that takes advantage of a security hole, then it would run rampant for about 24 hours until said security hole is found and patched, and users run their distro's auto-update system. Patches for security happen very quickly, because Linux people take security very seriously. Reports of your Linux virus would come very quickly too - the major anti-virus vendors have a "Linux threats lab" that basically sits on their behinds because there's currently no work for them to do; I'm sure everyone in those labs would be eager to do some work. :-)

Thirdly, let's look at some history. Linux use has gone up, Linux viruses have become rarer over time. Linux is simply getting more secure, with attack vectors being closed all the time. Usage does not equal insecurity.

---

### Post by Frak on 2010-08-06
> **3rdalbum said:**
> Not at all. For a start, most code that runs on Linux has been written with Linux's security system in mind. This code has been written to be secure, basically. It's hard to find vulnerabilities in Linux software.

Secondly, if you could create a virus that takes advantage of a security hole, then it would run rampant for about 24 hours until said security hole is found and patched, and users run their distro's auto-update system. Patches for security happen very quickly, because Linux people take security very seriously. Reports of your Linux virus would come very quickly too - the major anti-virus vendors have a "Linux threats lab" that basically sits on their behinds because there's currently no work for them to do; I'm sure everyone in those labs would be eager to do some work. :-)

Thirdly, let's look at some history. Linux use has gone up, Linux viruses have become rarer over time. Linux is simply getting more secure, with attack vectors being closed all the time. Usage does not equal insecurity.
Well, really, let's think about this. We can't be assured that all code written is secure code, this is why projects like SELinux exist, to watch for suspicious activity.

As for your second point, there was a vulnerability in an Unreal IRC server that was there for a good seven months, and caused many users to become infected with a Trojan. There's no hard and fast rule that says things will be patched in a timely manner. It may get fixed, it may not. The malware may be known, it may not. Believe it or not, the most dangerous viruses are those that haven't been detected or reported and have already infected a large amount of computers.

Lastly, yeah, Linux use has gone up, but it's been almost exactly proportional to the amount that everybody else has. For the second part, you can't say Linux is more secure, because you don't know what vulnerabilities are out there and if they've been fixed or not. If I recall, there was a vulnerability in the Linux Kernel that was found roughly two years ago, but wasn't fixed until about five months ago. There's no hard and fast rule that says vulnerabilities, when found, will be patched immediately either.

It's like telling someone that USB 2.0 can really transfer 480Mb/s. Sure, it could do that, but only if the temperature is correct, there's a tiny amount of magnetic interference, radiation has to be at a point, you have to be at sea level, the planets have to be aligned correctly... So, yes, in a perfect world, everything would be patched timely, and there would be no malware, and we would all live happily ever after. Except, we're humans, we make mistakes, and the planets only align every so many years.

---

### Post by Zorgoth on 2010-08-06
Open source is a fundamentally more secure model than closed source (although in the end it varies from application to application) because the people looking for security holes in order to exploit them will indeed get a benefit from open source, but the people looking for security holes in order to close them get a much larger benefit, because the crackers will use methods of working on closed source technology that are illegal in order to break it.

---

