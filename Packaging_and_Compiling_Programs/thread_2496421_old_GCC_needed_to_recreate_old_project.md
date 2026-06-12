---
title: "old GCC needed to recreate old project"
date: 2024-03-27
forum: Packaging and Compiling Programs
---

### Post by sky59 on 2024-03-27
Hello all!, 

I need this version of GCC :

GCC: (Ubuntu 5.4.0-6ubuntu1~16.04.9) 5.4.0 20160609


I have only this (below), but it compiles function with 4 parameters in different way, different alocation of parameters in
different processor registers.
Yes, it is more optimal (less RAM) but I need to recreate old project to be sure I have right source code.
I installed old Xenial but GCC in the image was already upgraded.

GCC: (Ubuntu 5.4.0-6ubuntu1~16.04.12) 5.4.0 20160609


How can I downgrade GCC? Or where to download needed GCC version? Is it possible to run newer GCC as older version GCC?

thank you!

---

### Post by TheFu on 2024-03-27
The entire build-stack will likely need to be downloaded too .... so the best answer is to use a 16.04 system.  Since it hasn't been under standard supported for 3 yrs, you'll need to find an ISO from somewhere (I'll leave that to you), then sign up for ESM to get all the patches so it is safe on a network.  When you did the install, did you get the "16.04.0" version?  Appears not. Looks like you need to find 16.04.9 as the starting point.

You could completely disconnect the system from a network and do everything offline too.

To be clear, I didn't go check exactly what the shipped version of gcc was to know if that specific version was shipped or not.

And after all this, the program will likely only run on a 16.04 system, unless you statically link it.  That will make for quite the bloated program, but whatever.

I'd find it difficult to believe that it wouldn't be possible to disabled via GCC options the stuff you don't want, but again, I didn't go check.

I used to earn my living doing compiles like this and porting software to new platforms, but that was before Ubuntu was even contemplated, so it isn't much direct help - just experience with GCC from 25+ yrs ago.

---

### Post by sky59 on 2024-03-28
:(  yes, the iso image has already 16.04.12 gcc   (but I need 16.04.9)

may be, if I could force gcc somehow to allocate registers .... for instance, original code (looked in asm) passes function argument2 to rbx and keeps it there through whole subroutine, my compilation keeps in rbx argument3

                                                                                                     original keeps argument3 (it is both pointers on uint8_t) in stack-E0                                            my compilation keeps argument2 in stack-D8

I tried many different sequences of arguments in function declaration but it seems to have no effect, always the same allocation

what seems to have an effect is, if I change for instance  argument from uint8_t to uint64_t   but still not getting what I need

any idea how gcc works?

if I do reverse of original and my compilation I get the same result in C-level, I use GHidra, IDA gives stilghtly differnt code but funcionally it is the same as original

---

### Post by &amp;KyT$0P# on 2024-03-28
> **sky59 said:**
> I installed old Xenial but GCC in the image was already upgraded.

What "old Xenial" did you install?  It looks like [FONT=Courier New]gcc-5[/FONT] version [FONT=Courier New]5.4.0-6ubuntu1~16.04.9[/FONT] should be included in the Ubuntu **16.04.4** ISO from [here]("https://old-releases.ubuntu.com/releases/xenial/")

---

### Post by Tadaen_Sylvermane on 2024-03-28
> Yes, it is more optimal (less RAM) but I need to recreate old project to be sure I have right source code.

I don't understand this statement. Either the program can be compiled or it can't. At the end of the day you can't rely on out of date software to build your stuff.

---

### Post by TheFu on 2024-03-28
In a business, there are all sorts of reasons to use old software.  It is our job to convey the issues and liabilities to upper management, but in the end, it is their risk to accept.  I've had to get formal, written, signed, risk acceptance letters from CxOs in some of the largest companies in the world because there wasn't any other way to accomplish something that we were required, by law, to provide.  

However, it isn't my risk to accept. It was theirs and I wasn't going to be fired for not being very clear about the risks and suggest a solution.  For nearly all these **risk acceptable letters** the CxO who signed didn't like it and they pushed funding through to get it resolved ... or to drop the offering to our clients. 

I know of some physical therapy equipment that was/is used by elite professional athletes that was based on 8.06 Ubuntu.  Everything about the software had been customized by an IT company that died off in 2010, leaving all the users with their $20K equipment, but nobody who actually knew the software or hardware enough to work on it.  It wasn't a general Ubuntu and had specific display drivers compiled into the kernel, so normal Ubuntu wouldn't boot.  Of course, there were no backups and the guy who showed up at our LUG seeking help didn't really like our answers.  Nobody could help him - at least not for the price he was willing to pay, so this guy effectively went out of business.  We suggested that he swap out built-in screen for something else, but that would take some effort to learn the software to ensure it would work.  The guy wanted a guaranty that someone in the LUG could achieve the desired answer without paying for the time.  I told him my hourly contracting rate and that I'd need 5-10 hours to look over the equipment, manuals, and speak with him before I could say **if** I might be able to help or not.  He freaked out at the potential costs.  He just didn't have the background to do the work himself and LUGs aren't really the place to get free business solutions.

Just a few examples.

---

### Post by sky59 on 2024-04-04
> **halogen2 said:**
> What "old Xenial" did you install?  It looks like [FONT=Courier New]gcc-5[/FONT] version [FONT=Courier New]5.4.0-6ubuntu1~16.04.9[/FONT] should be included in the Ubuntu **16.04.4** ISO from [here]("https://old-releases.ubuntu.com/releases/xenial/")

thank you very much! 

I do not know why I could not google-out that "old-releases" of Xenial?

and it is:  ubuntu 16.04.4  .....  gcc 5.4.0  16.04.9    a bit confusing

---

### Post by &amp;KyT$0P# on 2024-04-04
You're welcome. :KS

> **sky59 said:**
> and it is:  ubuntu 16.04.4  .....  gcc 5.4.0  16.04.9    a bit confusing

For what it's worth, to clarify, that .9 is related to how many times gcc had been updated specifically for Ubuntu 16.04 at that point.  It has nothing to do with the Ubuntu point release number.

---

