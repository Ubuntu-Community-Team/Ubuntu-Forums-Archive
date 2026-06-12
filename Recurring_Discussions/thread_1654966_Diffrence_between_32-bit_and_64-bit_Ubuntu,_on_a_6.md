---
title: "Diffrence between 32-bit and 64-bit Ubuntu, on a 64-bit computer"
date: 2010-12-29
forum: Recurring Discussions
---

### Post by poetzmij on 2010-12-29
Ok i know there have been a decent amount of posts on this already, now before you get all flustered and send me to an older thread I want to tell you that things change especially with support for 64-bit becoming much more common.
Now i would like to know what peoples personal opinions on the matter are, there really isn't a real answer that is right i'm just curious. Since there is now a lot more support for 64-bit and those threads are obsolete.
I would also like to ask why 32-bit always says [recommended] when you go to download, is that simply to ensure that anyone who is downloading the os with no experiance cant get a 64-bit edition on accident for there 32-bit computer or is it more because (if its even the case)  32-bit packages have more support, and also what about flash, hows is it doing on 64-bit nowadays?

---

### Post by garvinrick4 on 2010-12-29
The one thing that cross's my mind is that it is a lot easier for 32 bit users to install .deb packages than 64 bit users tar packages and their cousins.

---

### Post by bikeboy on 2010-12-29
> **garvinrick4 said:**
> The one thing that cross's my mind is that it is a lot easier for 32 bit users to install .deb packages than 64 bit users tar packages and their cousins.

Therefore we 64 bit users install deb files as well...

---

### Post by mips on 2010-12-29
> **garvinrick4 said:**
> The one thing that cross's my mind is that it is a lot easier for 32 bit users to install .deb packages than 64 bit users tar packages and their cousins.

I'm trying very hard to find the logic in that statement...

---

### Post by poetzmij on 2010-12-29
> **garvinrick4 said:**
> The one thing that cross's my mind is that it is a lot easier for 32 bit users to install .deb packages than 64 bit users tar packages and their cousins.

I thought like maybe he meant that certain software isn't build for 64 by default? idk i gave it more thought and idk... i didn't understand. But oh well thank you for replying and giving your opinion :p

---

### Post by GabrielYYZ on 2010-12-29
i've been using the 64 bit version and, so far, i haven't had an "ahh wish i was on 32 bit" moment. everything works great but, then again, all the apps i use are pretty standard, maybe if i used more "fringe" apps i might have trouble finding/compiling them for 64 bit.

---

### Post by NightwishFan on 2010-12-29
There are a few apps with only 32-bit debs, but nothing I have ever direly needed.

---

### Post by samalex on 2010-12-29
Another major limitation is you can only have up to 4 Gigs of addressable RAM on a 32-bit system.  To go beyond 4 Gigs of RAM you'll need to move to 64-bit.

Unless Ubuntu or the latest version of the kernel is working some magic to get past this limitation...

---

### Post by Helkaluin on 2010-12-29
> **samalex said:**
> Another major limitation is you can only have up to 4 Gigs of addressable RAM on a 32-bit system.  To go beyond 4 Gigs of RAM you'll need to move to 64-bit.

Unless Ubuntu or the latest version of the kernel is working some magic to get past this limitation...

PAE kernel.

---

### Post by oldos2er on 2010-12-29
Read the whole sordid story of 64-bit Ubuntu labeled "Not Recommended" [https://bugs.launchpad.net/ubuntu-website-content/+bug/585940](https://bugs.launchpad.net/ubuntu-website-content/+bug/585940)
What the page says now regarding 32-bit being recommended is a "bug fix" for the above.

I've used 64-bit Ubuntu for years, and there's no going back (do you know anyone still using an 8- or 16-bit PC? I don't.). Also, 64-bit flash is fine.

---

### Post by Sef on 2010-12-29
Moved to Recurring Discussions.

---

### Post by SunnyRabbiera on 2010-12-29
A 32bit OS will work fine on a 54bit system, though it wont read more than 3GB without PAE.
I got myself a home built computer and its running 64bit windows and 32bit linux.
I only use 32bit as some of my hardware only works with 32bit

---

### Post by Verbeck on 2010-12-29
might be worth checking out
[http://www.phoronix.com/scan.php?page=article&item=ubuntu_32_pae]("http://www.phoronix.com/scan.php?page=article&item=ubuntu_32_pae&num=1")

---

### Post by SunnyRabbiera on 2010-12-29
> **Verbeck said:**
> might be worth checking out
[http://www.phoronix.com/scan.php?page=article&item=ubuntu_32_pae]("http://www.phoronix.com/scan.php?page=article&item=ubuntu_32_pae&num=1")

Indeed, but benchmarks dont mean a thing.
Especially from Pharonix, they dont test every single thing and wind up wrong on many counts (7 better then Ubuntu on their benchmarks but Ubuntu is better on my system)

---

### Post by poetzmij on 2010-12-29
Ok so of course there is RAM as a factor but it can be fixed with a kernel change which im pretty sure is automatically default on Ubuntu 32 with more then 4G of RAM, and if there are any improvements to performance it wont really be noticed by the user, and in other ways software will preform better because of more stability and native 32-bit libraries and such... hmm almost seems like a stalemate. I guess its still all opinion...

---

### Post by johntaylor1887 on 2010-12-29
> **oldos2er said:**
> 
I've used 64-bit Ubuntu for years, and **there's no going back** (do you know anyone still using an 8- or 16-bit PC? I don't.). Also, 64-bit flash is fine.

This. 

Btw, is there a sub-forum inside of recurring discussions? Maybe call it "beat a dead horse recurring"?

---

### Post by johntaylor1887 on 2010-12-29
> **poetzmij said:**
> in other ways software will preform better because of more stability and native 32-bit libraries and such

32bit is more stable? Really? If you ask me, 64bit *seems* more stable and faster than 32bit. I call FUD on that.

I once read an article that said 64bit is inherently more stable than 32bit. If I can find it, I'll post back. 

And no, software does not perform better in 32bit. That made me laugh. ):P

If you can't provide solid proof of what you say, then you're better off saying nothing.

---

### Post by oldos2er on 2010-12-29
What 32-bit libraries? Anyway, here's more opinion, if interested (it's a couple years old, but most of the info is still relevant): [http://ubuntuforums.org/showthread.php?t=765428](http://ubuntuforums.org/showthread.php?t=765428)

---

### Post by poetzmij on 2010-12-29
> **johntaylor1887 said:**
> 32bit is more stable? Really? If you ask me, 64bit *seems* more stable and faster than 32bit. I call FUD on that.

I once read an article that said 64bit is inherently more stable than 32bit. If I can find it, I'll post back. 

And no, software does not perform better in 32bit. That made me laugh. ):P

If you can't provide solid proof of what you say, then you're better off saying nothing.

Alright alright cool if johntaylor i'm new to a lot of this so if i say something dumb i want to know (which you did) so i will be quite... 

But one more thing, ok seems ive done a little looking there isnt really any reason to go to 32-bit but what about wine... its confusing to a noob such as myself it running 32-bit and 64-bit windows apps, and it using 32-bit libraries on my 64-bit... and i would like to know just exactly is going on with all that confusion is it going to have a positive or negative impact because i know running a game in 64-bit in windows makes a difference?

...that is all.

---

### Post by johntaylor1887 on 2010-12-30
> **poetzmij said:**
> Alright alright cool if johntaylor i'm new to a lot of this so if i say something dumb i want to know (which you did) so i will be quite... 

But one more thing, ok seems ive done a little looking there isnt really any reason to go to 32-bit but what about wine... its confusing to a noob such as myself it running 32-bit and 64-bit windows apps, and it using 32-bit libraries on my 64-bit... and i would like to know just exactly is going on with all that confusion is it going to have a positive or negative impact because i know running a game in 64-bit in windows makes a difference?

...that is all.

You can use 32bit libraries on a 64bit machine.(but not the other way around) And I've used wine in 64 no problems. I just wish people in general would stop spreading FUD about 64bit OS's. 

If you have capable hardware, there's really no reason *not* to use 64bit OS, especially if you are a heavy multi-tasker or number cruncher. You will definitely notice that it is faster and makes better use of memory.

---

### Post by ErikNJ on 2010-12-30
Wider multiplexers are cooler.  That's why you use 64 bit.  

In theory, a 64 bit cpu could also pass more information per-clock.  I'd suspect in most case it doesn't (I've not looked into it in detail anyway).  Anyway, there is a chance that you will see some improvements in speed in 64 bit but it very much depends upon the applications and what it is they are up to.  Passing 6 bits of information within 32 bits, 64 bits, or even 1024 bits is still going to be a single pass.  However, passing 40 bits of information via 32 bit would require more cycles than 64 bit (of course the application must handle the 64 bits as 64 bits to do it).

---

