---
title: "Any engineers use Linux at work?"
date: 2006-12-12
forum: Programming Talk
---

### Post by sapienti sat on 2006-12-12
Hello everybody,

I'm a test engineer working at automotive (as cars) plant. 
Couple of weeks ago I've stumbled upon Linux, and so far I just love it. At least the networking part of it. Now I have to figure out how hard it will be to transfer my testing applications from Win to Linux.

If there is anybody working with National Instruments, or something like that, your advice would be priceless.

Thanks in advance!

---

### Post by Hendrixski on 2006-12-12
I'm a software developer for Geographic Information Systems.  It may not be considered an "engineer" in the traditional sense, but I think of the skills I use as engineering skills.

And I use LINUX at work when I can (though some things have to be done in Windows, so I dual boot).

---

### Post by sapienti sat on 2006-12-12
I write functional test stand software to test engine/transmission control units. It's all in C++ or VB. Is there a way to migrate my apps to Linux, or I would have to rewrite them from the scratch?

---

### Post by pmasiar on 2006-12-12
Not sure if you can migrate your tools. Possible - ask your vendor.

But let me ask you: Why? If it is not broken, don't fix it.

If you want to enhance your career and learn skills usable for free software later, try to switch to firefox browser, OpenOffice suite, and other tools you can use on both Windows and Linux. Learn some python and automate some tasks (file management, text parsing). At home, use ubuntu - double boot until you are ready.

At work, ask for a linux server and install a wiki for sharing documentation. maybe bug tracking system, like [TRAC]("http://trac.edgewall.org/"), could be usefull. Or you can run it on windows. If you run same program on both windows and linux, most skills are transferable.

---

### Post by samjh on 2006-12-13
> **sapienti sat said:**
> I write functional test stand software to test engine/transmission control units. It's all in C++ or VB. Is there a way to migrate my apps to Linux, or I would have to rewrite them from the scratch?

Your VB code would be extremely difficult, if not impossible, to port to Linux.  Unless if it is in VB.NET, in which case you *might* be able to use Mono.  However, VB.NET support in Mono has never been solid enough for serious development.  A major re-write is underway, but it might be while before they release a good enough VB.NET compiler and runtime environment for industrial work.

C++ might be easier to port.  It depends on what kinds of libraries, standard-compliant code, and design architecture you used.  If your programs depend on Windows-only libraries and/or are not designed in a modular fashion, you will have a major rewrite, if not a complete rewrite from scratch.

---

### Post by slimdog360 on 2006-12-13
There is another programming language similar to VB, gambas. Ive never tried it though. [http://gambas.sourceforge.net/](http://gambas.sourceforge.net/)

I know wine cant emulate programs written in wine so they are pretty much useless' unless you modify your code to run under gambas.

Im sorry to say that Ive never seen anything like lab view running under linux, also I couldnt imagine it running too well with an emulator like wine. From what Ive seen linux users tend to write their own programs for data acquisition.

Linux is great for many things but unfortunately not everything from Windows can be recreated.

---

### Post by pmasiar on 2006-12-13
> **slimdog360 said:**
> Linux is great for many things but unfortunately not everything from Windows can be recreated.

You placed cart ahead of the horse.

Windows carries a baggage on complicated quaasi-standards, which are hard to reimplement -- and reimplementing is dangerous too, because it is widely expected to be protected by many patents. Things like Mono. Why would you spend years reimplementing in free software some windows functionality, if your project can be shot any second by patent troll, or Microsoft itself? And even worse, you get sued for damages? Free software developer cannot afford to get to court and pay tens of thousands to lawyers even in s/he is 100% right - you are forced to settle out of court. It already happened.

It is much safer to stay away from Windows, implement new features on free platform from the ground up.

---

### Post by sapienti sat on 2006-12-13
Thanks for the replies, 

In short, I have to find out if its worth it to switch to Linux, and prove it to my boss.

We, as test engineering group, have to support our networks and all the systems on it. IT department guys don't have to do anything with it. It has been a real hustle to setup servers and all the services on them, create the user accounts. User accounts are especially a headache as we need to restrict our operators from doing anything in Windows (except for launching programs), when the apps they are running need to have all the rights and permissions. Remote control, here is another thorn in our butts.
I've tried some Linux networking at work, and could not believe the difference, how easy it is!

We don't use LabView or Measurement Studio or anything like that. Our systems are too complicated for the general distributions, so we write all the software ourselves, using instrument drivers provided by manufacturers. I've already checked and they all support Linux, it's good news. Now I need to find out what languages, beside C++, we can use with their drivers.

Windows tend to swallow all the resources without breaking a sweat. One simple thread can take up all 100% on our 3.4GHz industrial computer. Its just plain ridiculous, but we can't do much about that. About 2-3 times a year Windows on every machine would crash, not handling all the pressure, I guess. We even have times scheduled for that, when we reinstall all the systems from images to prevent another crush.

I did notice that if there's something not working in Linux, the chances are you will figure it out, with all the community help out there. With Windows it just another big mystery.

---

### Post by pmasiar on 2006-12-13
> **sapienti sat said:**
> It has been a real hustle to setup (Windows) servers and all the services on them, create the user accounts. User accounts are especially a headache as we need to restrict our operators from doing anything in Windows (except for launching programs), when the apps they are running need to have all the rights and permissions. Remote control, here is another thorn in our butts.
I've tried some Linux networking at work, and could not believe the difference, how easy it is!

If you think about the history, it is obvious. Windows was born and single-user machine, without any contact to outside world (beyond floppies). Everything above that was bolted on, with an eye for backward compatibility and "user friendliness". In opposite to this, Unix == Linux was created (30 years ago) as multi-user machine connected to other computers and users were expected to have some minimal expertize to use it. So protection of the system from users, and users from each other, was settled and mature. Linux errs on side of security, on the side of sysadmin responsible for the server. Windows is on the side of "convenience" of the naive trusting user, who cannot be bothered to learn proper way to do things. 

If you see it from this point, difference is obvious - and gap is not easy to close. Coming Vista aims to be more secure - and as a result, less convenient to use.

---

