---
title: "why is it so easy for a process to reach 100% CPU usage?!"
date: 2008-06-10
forum: New to Ubuntu
---

### Post by paranoid_humanoid on 2008-06-10
hi, i've been on ubuntu for a couple of months now. coming from a windows environment, which i used to beat the crap of in cpu and memory usage - if you know what i mean - and everything would still be okay and the system running smoothely, i find that on ubuntu it's really easy for a process like amarok or firefox or azureus to reach 100% rendering the whole system unusable for a couple of seconds every once in a while..
is that okay?
my pc is a 3.0GHz PIV with 1 GB of ram..

---

### Post by philinux on 2008-06-10
With firefox its probably the nasty flash. Complain to adobe.

With azureus it's java. Try deluge instead.

Try using the command

top

in the terminal to see whats hogging your pc. It might be trackerd, the indexing app.

---

### Post by skymera on 2008-06-10
You can try htop.

```
 sudo apt-get install htop 
```

It's easier to read/interperet that standard top.

---

### Post by paranoid_humanoid on 2008-06-10
i disabled trackerd along time ago, that massacred my cpu usage from the first moment. and i know the processes that can go up to 100%, it's usually amarok, firefox, azureus or the musicbrainz client.. i've been using them all on windows and they wouldn't do that..

---

### Post by skymera on 2008-06-10
Do you have desktop effects?

Turn them off and see if it still happens.

---

### Post by signseeker on 2008-06-10
Memory leak associated with Firefox?

---

### Post by philinux on 2008-06-10
> **signseeker said:**
> Memory leak associated with Firefox?

Fixed in FF 3

---

### Post by signseeker on 2008-06-10
> **philinux said:**
> Fixed in FF 3

Really? Cool. 

The other thing that really ate my memory was adesklets.

---

### Post by SunnyRabbiera on 2008-06-10
it depends on the app and computer really, I never had any issues like this.

---

### Post by paranoid_humanoid on 2008-06-10
guys, i know the processes that take up my cpu, it's not the desktop effects (which i don't have much of btw).. it's those i've mentioned earlier.. i'm just surprised of how linux allows them to take over 100% of the cpu when they need it so easily.. i'm not doing anything out of the ordinary to them, just regular usage, the way they were meant to be used...
on windows when an app requires so much resources like that, it usually slows itself down, not the whole system with it..
am i making any sense?! :confused:

---

### Post by niteshifter on 2008-06-10
Hi,

Let me try ...

> guys, i know the processes that take up my cpu, it's not the desktop effects (which i don't have much of btw).. it's those i've mentioned earlier.. i'm just surprised of how linux allows them to take over 100% of the cpu when they need it so easily..

For most of last year I ran XP and Edgy dual-boot (different OS/applications, same hardware). I was surprised at how XP, in particular Microsoft Update would grab 100% CPU 20 seconds after networking was up and keep it there, forever, rendering XP unusable. Luckily, I had Edgy, which never over utilized the Pentium M.

So ... what SunnyRabbiera said (more or less): it depends on the software (including the OS!) and the computer. My problem was a known bug with MS Update - and the official "fix" from MS was: use Windows Update. Some fix. A bit of searching, a couple of friendly web-sites later, a little back and forth with some of those site's users, I found the real fix which allowed me to return to using MS Update.

Rather than debate with those attempting to help, you could consider taking their advice: examine process usage closely, over time. Remove some of the heavy resource users like compiz (there's more there than just effects), and tell us what you see. Some other info would be nice, like what version of *buntu you're using.

---

### Post by paranoid_humanoid on 2008-06-10
okay, it's an Intel Pentium 4 CPU 3.06GHz, 1 GB of Ram, 250 GB SATA Hard Drive. I'm running ubuntu hardy which i upgraded from gutsy on a 10 GB partition an a 1 GB swap parition..

---

### Post by markbuntu on 2008-06-10
First, more ram would help as would a bigger swap. Swap should be 3 times the ram. If you have a lot of processes running the cpu will spend most of its time moving stuff around from ram to swap to the file system, etc.

When I went from 1GB of ram to 3GB and the difference was amazing. I thought I needed a faster processor but it was the lack of ram that was tying things up. My little AMD64 3800+ 2.4GHZ single core cpu hums right along now. No need to change that.

Ram is cheap these days, get some.

---

### Post by sam_delta on 2008-06-10
> **markbuntu said:**
> First, more ram would help as would a bigger swap. Swap should be 3 times the ram. If you have a lot of processes running the cpu will spend most of its time moving stuff around from ram to swap to the file system, etc.

When I went from 1GB of ram to 3GB and the difference was amazing. I thought I needed a faster processor but it was the lack of ram that was tying things up. My little AMD64 3800+ 2.4GHZ single core cpu hums right along now. No need to change that.

Ram is cheap these days, get some.
swap 3x the ram??  ive heard 2x the ram if your below 2g and if your 2g+ then the same swap as your ram would be ok


sam

---

### Post by markbuntu on 2008-06-10
Yeah, you can probaly get away with that. My system rarely uses more than 1.2GB and never uses swap as far as I can tell. But I don't do that much to stress it out anyway.

If you have on board video it can use a lot of your ram so more ram is the best bet for that.

---

### Post by sam_delta on 2008-06-10
> **markbuntu said:**
> Yeah, you can probaly get away with that. My system rarely uses more than 1.2GB and never uses swap as far as I can tell. But I don't do that much to stress it out anyway.

If you have on board video it can use a lot of your ram so more ram is the best bet for that.
yeah, i agree more ram will get better performance, but i was a little clued on the 3x swap thing you mentioned
thx for the explanation
sam

---

### Post by mdsmedia on 2008-06-10
While I agree that more RAM would probably increase performance, I can't imagine that it's purely a RAM problem, as Windows doesn't require any more capacity than what the OP has.

I would tend to think that a larger SWAP would be beneficial....I'd say 2xRAM.

I'd say the problems are more deeply rooted though. I can't see those programs sucking up all that CPU.... so easily. I've got a lower specced machine....a 3 year old HP Laptop with 512MB RAM and it doesn't require any more than that. Admittedly I'm running Dapper on the laptop, but Gutsy on my desktop with similar specs, and it doesn't eat up all my modest CPU or RAM.

---

### Post by philinux on 2008-06-10
My system rarely uses more than 400 meg and zero swap, I've set swap to 2gig same as ram.

Using Virtualbox I then see 1gig ram use and about 300 meg swap.

---

### Post by gr4nf on 2008-06-10
Poorly written software can shoot to 100% all the time, easily. watch:
```

#include <iostream>

using namespace std;

int main()
{
     while(1)
     {
          do_something();
     }
}

```
this awful program would cause 100% cpu usage no problem. It is things like this that make processes use up so much of the CPU.

---

### Post by Sham885 on 2008-06-10
So far I've found ubuntu to be great with cpu and ram usage.  Xp is currently not working outside of safe mode because it maxes cpu usage even after shutting down everything possible in msconfig.  It's always been an issue with this computer.  Right now in ubuntu I have 3 firefox windows open with 3-4 tabs in each, azureus running, watching a movie, and a few other random things and my computer isn't having a single issue.  I have 2GB ram and 3GB swap.  1GB of ram is nothing anymore.  I wouldn't run a computer with less than 2 unless it had some specific use and os that was known to require less.

---

