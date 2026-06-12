---
title: "Damn Dangerous Pointer!..."
date: 2010-01-09
forum: Programming Talk
---

### Post by Mathew Roy on 2010-01-09
Yesterday I created a small program involving pointer that crashed the windows system!..
Well I knew that what I was doing was damn dangerous but not to this extend!. I boasted to my frends that using uninitialised pointer will crash the program, and I made a simple program involving a uninitialised pointer. But it did not work!. I was suprised & my friends teased me for the same. So I did something bit more dangerous!..

I executed the 5 line program and the program crashed!. But it was not all that happened!. Even the XP (at college) hang up (I thought it might be b'case my program currupted some system variables!). So I restarted the system only to find that my program had caused more extensive damege to the system!..The windows simply did not boot and there where a lot of symbols and lined on the screen, as if the RAM was loose or something. (OR did the RAM burn out??).

Here is the dangerous code 
[php]
int main()
{
  int *p=0,i;
  for(i=0; ;i++)    //Infinite loop
  {
    *p=0;             //most dangerous step ? 
     p=p+1;
  }
}
[/php]I just dont know what happened, can anyone explain what happened? Is there any way to resore the computer?.

Well I tried to execute the same program in Ubuntu and it returned segmetation fault! and nothing else.

The compiler I used in college is TURBO C (16 bit).
Plz help before I get caught for damaging that computer!..

---

### Post by nvteighen on 2010-01-09
> **Mathew Roy said:**
> Yesterday I created a small program involving pointer that crashed the windows system!..
Well I knew that what I was doing was damn dangerous but not to this extend!. I boasted to my frends that using uninitialised pointer will crash the program, and I made a simple program involving a uninitialised pointer. But it did not work!. I was suprised & my friends teased me for the same. So I did something bit more dangerous!..

I executed the 5 line program and the program crashed!. But it was not all that happened!. Even the XP (at college) hang up (I thought it might be b'case my program currupted some system variables!). So I restarted the system only to find that my program had caused more extensive damege to the system!..The windows simply did not boot and there where a lot of symbols and lined on the screen, as if the RAM was loose or something. (OR did the RAM burn out??).

Here is the dangerous code 
[php]
int main()
{
  int *p=0,i;
  for(i=0; ;i++)    //Infinite loop
  {
    *p=0;             //most dangerous step ? 
     p=p+1;
  }
}
[/php]I just dont know what happened, can anyone explain what happened? Is there any way to resore the computer?.

Well I tried to execute the same program in Ubuntu and it returned segmetation fault! and nothing else.

The compiler I used in college is TURBO C (16 bit).
Plz help before I get caught for damaging that computer!..

First, let's see what's your program doing. (btw, you missed the "return 0;" at the end of main).

In the loop you access the memory pointed by p and set it to 0. Then, you increment p to make it point to the next memory address. The code is actually redundant, as you could have done this by using just p to count the for-loop without using i... but well...

Is this dangerous? Depends on the OS. Try this program in GNU/Linux and you won't get any issue except the segfault because the Linux kernel has a pretty decent memory protection system (don't expect me to explain it to you... I just know the very basics). What troubles me is that Windows **was** infamous because of its poor memory protection... **before WinXP**. WinXP inherited WinNT's kernel, which was pretty much solid in this respect... it was the Win9x line which had issues with this.

But, IMO, your program couldn't have done any permanent damage. Supposing you actually overrode the memory protection somehow and overwrote vital parts of memory with 0, you couldn't have affected the disk. A reboot should have solved this. It could have become dangerous if you assigned p with a pointer-to-function which did something to the disk, e.g. Assigning to NULL should have just made stuff segfault and make the computer crash.

So, are you sure that computer wasn't already broken?

EDIT: How did you reboot the system? Those lines remind me to a faulty suspension/hybernation waking up...

---

### Post by Mathew Roy on 2010-01-09
> **nvteighen said:**
> 

But, IMO, your program couldn't have done any permanent damage. Supposing you actually overrode the memory protection somehow and overwrote vital parts of memory with 0, you couldn't have affected the disk. A reboot should have solved this. It could have become dangerous if you assigned p with a pointer-to-function which did something to the disk, e.g. Assigning to NULL should have just made stuff segfault and make the computer crash.

So, are you sure that computer wasn't already broken?

EDIT: How did you reboot the system? Those lines remind me to a faulty suspension/hybernation waking up...

Nope. the computer did no seem to have a problem before!... NO VIRUS also!..

The OS installed in that computer is XP!

Yes I also strongly believe that it wont have dome some permanent damage. But well, will this program cause some damage to RAM?. 

When I rebooted the system (after getting hang up!) the whole screen (including BOOT SCREEN) was filled with lines and ascii charaters!. (The same did happen to my system once when there was some dust in the RAM slot, and after cleaning the RAM and reinserting it there was no more issue). 

OK! well this is how i restarted the system!.
I pressed the reset button only to find that the boot screen was corrupted!. So I switched off the power and after a few seconds I switched on and pressed the button for booting (err...what u call power button?). But this too didn't help!.

I had plan to remove RAM from it and reinserting it after cleaning, but it is not practical because the computer is College's property!..

Well, I have recently heard that
" if one try to insert a RAM that was used in another computer instantly into another computer, the he/she may get a corrupted boot screen, just like the one I got.  And if you insert the very same RAM after a couple of hours, there will be no issue!". I don't know about it personally, but my friend said so! (b'caz he had an experience).

Hoping that my program had not done any permanent damage!.

---

### Post by grayrainbow on 2010-01-09
Well, actually the pointer in this program is not uninitialized, it's initialized to 0(NULL), and trying to dereference it will crash your user space program, not the system. I guess the system(hardware or OS) has another problem, which you just encounter, good look in solving it(sometimes unproper shutdown could cause a lot of problems, especially with the disk).
And yea, Windows has memory protection - meaning you can not just write to some other process memory, you can not execute code from non executable page, and so on...but there's always room for bugs :) and XP has problems with many heavy programs running simultaneously.

---

### Post by The Secret on 2010-01-09
Windows XP SP3 - Segmentation fault ( Don't Send .. ) with no side effects.

---

### Post by The Cog on 2010-01-10
Whatever the cause of the hangup, I suspect that the cause of failure to reboot is filesystem corruption caused by pressing the reset button while the disk was being written to. 

I have read that NTFS is journalled, so such problems shoudn't happen but that's still my guess.

---

### Post by Reiger on 2010-01-10
In that case you should run chkdisk /f. Or rather you must inform sysadmins that it is necessary -- since you probably do not have sufficient privileges on that machine.

---

### Post by cliddell on 2010-01-10
> **Mathew Roy said:**
> 
The compiler I used in college is TURBO C (16 bit).


This may be a significant factor. IIRC, ntvdm.exe creates a single 16 bit, non-protected memory virtual machine for *all* 16 bit executables, unless configured to do something else for a given executable - I think you can set a given executable so that it gets its own 16 bit VM.

So if the 16 bit Turbo C (TC) exe hasn't had any special treatment, it will be running in the same memory address space as the 16 bit exe it created - thus the offending program *could* adversely affect the running of the TC GUI. If the TC GUI was running full screen, and froze as a result of the memory corruption, it could appear as though the entire Windows GUI has frozen.

As mentioned above, the problem after rebooting is most likely due to the unclean shutdown. It *could* be worse than might be expected if XP was installed on a VFAT (rather than NTFS) partition - which I've seen more in education establishments than elsewhere.

Chris

---

### Post by Mathew Roy on 2010-01-10
> **cliddell said:**
> This may be a significant factor. IIRC, ntvdm.exe creates a single 16 bit, non-protected memory virtual machine for *all* 16 bit executables, unless configured to do something else for a given executable - I think you can set a given executable so that it gets its own 16 bit VM.

So if the 16 bit Turbo C (TC) exe hasn't had any special treatment, it will be running in the same memory address space as the 16 bit exe it created - thus the offending program *could* adversely affect the running of the TC GUI. If the TC GUI was running full screen, and froze as a result of the memory corruption, it could appear as though the entire Windows GUI has frozen.

As mentioned above, the problem after rebooting is most likely due to the unclean shutdown. It *could* be worse than might be expected if XP was installed on a VFAT (rather than NTFS) partition - which I've seen more in education establishments than elsewhere.

Chris

Well TC was running full screen and got frozen due to  my program! So, I tried Alt+Enter to get out of the full screen mode and it did!. Then I pressed the close button of TC (now not maximised) and clicked END NOW. The TC quit without taking much time. This is exactly the point when XP froze. Not only did it froze the screen also got corrupted with odd colours and symbols!...
What could that mean?!

When I rebooted the system the screen was corrupted from the beginning, ie. from the boot screen (Before loading XP).

Any help? plz....

---

### Post by Mathew Roy on 2010-01-10
oops, System froze even before restarting!...

---

### Post by nvteighen on 2010-01-11
Ok. I think you'll have to talk with your college's IT people; I know you may be frightened by the idea that they make you pay the computer or blame you have the fault but you have read all responses including mine that tell you that your program is very unlikely to be the issue, but the faulty reboot... which can happen to anyone. Explain them exactly what happened, apologize and I guess this will be solved.

You know, college computers are under the user's responsability while the user is logged in. Fault and responsability aren't the same; you didn't break the computer in purpose, but it broke under your responsability so you have to report this incident.

I think they won't make you pay a fine or anything if you explain them honestly what happened and are willing to help. You could also point to this thread if necessary, I guess.

---

### Post by Mathew Roy on 2010-01-12
Ok!. I will do that!..
Hoping that I wont have to pay for it!. 
Well even if something is broken will it be RAM?

---

