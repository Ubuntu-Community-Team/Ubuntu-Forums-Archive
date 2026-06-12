---
title: "64-bit or 32-bit? Need help because IDK which one!"
date: 2008-09-26
forum: New to Ubuntu
---

### Post by HighCommander540 on 2008-09-26
No, I am not a beginner but this is the place to post about. I installed the 64-bit version of Ubuntu on my computer because I have an AMD 64 Dual core 6400+.  I though wow I can finally have a OS that is 64-bit.

Right after I install the system because pretty buggy and lots of programs like to crash a lot. I found out that I might have a glitch someone on one of my RAM chips, but I checked and my RAM is fine. All except for some 84mb that it holds back from the check for something.

IDK, what do to at this point so I switched to the 32-bit, but I have more than 3 gigs of RAM and I want all of them to be used, because I want to be able to give my virtual machine 3 gigs of RAM for itself.

But the 32-bit machine also runs faster. So IDK what to do is there something wrong with the 64-bit that is causing this problem or should I switch back and get everything that I want.

If there is something that I can do about it please tell me!

---

### Post by Orange_and_Green on 2008-09-26
Hello HighCommander540

I am running 64-bit Ubuntu 8.04 Hardy Heron on this PC and I have no problems at all (except, possibly, finding binaries for some programs that only come for 32-bit).

I was wondering what version of Ubuntu you have? If it's Intrepid Ibex (8.10) I would suggest a downgrade to 8.04 as 8.10 is still in Alpha stage.

If not, what hardware do you have?

Have a nice day :KS

P.s.[Off-topic]This is actually my 100th post as one got duplicated by mistake...Wow cool:)[/Off-topic]

---

### Post by Cadmus on 2008-09-26
What applications were crashing? What did your freezes look like? If we can narrow down the culprit we can figure out if a change of OS is the Right Thing.

---

### Post by Kevbert on 2008-09-26
Did you test your memory with memtest (in the grub boot menu) ?  You may need to run it for two or three passes to give it a chance to warm up. POST is not really good enough (unless you have a catastrophic failure). Hardy is pretty stable on my AMD2 and I wouldn't recommend using Intrepid as the main OS as it still has some issues.
It is possible to use more than 4Gb of ram with 32 bit as long as the bios has support for [[COLOR="Red"]PAE.[/COLOR]]("http://en.wikipedia.org/wiki/Physical_Address_Extension") Please take a look at this [[COLOR="Red"]link[/COLOR]]("http://ubuntuforums.org/showthread.php?t=855511").

---

