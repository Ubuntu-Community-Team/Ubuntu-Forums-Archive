---
title: "small *nix help"
date: 2009-01-10
forum: Other OS Talk
---

### Post by this is new york not l.a. on 2009-01-10
hey, I want to put a new os on my archaic laptop and I was just wondering about some recomendations. my laptop is a compaq armada. it has something like 38 mb or ram, 2.01 gb hd, and a pentium processor. I got it for free from my school and I just want to futs around with some smaller systems. i have a lilttle bit of knowledge with ubuntu. so any recomendations?

---

### Post by JoshuaRL on 2009-01-10
Try DSL.  If anything will work on that, it's gotta be a small distro.  And DSL is based off of Debian, so you can add APT to it.

---

### Post by RomeReactor on 2009-01-10
Hi. Maybe [DSL]("http://damnsmalllinux.org/") can be of help there. There's also [Puppy]("http://www.puppylinux.org/"), but I don't know if it would run well enough (or run at all).

---

### Post by this is new york not l.a. on 2009-01-10
thanks, i was looking into that but i would think that theres more ram than that on my laptop but oh well. i'll see what happens then report back. thanks for the help

---

### Post by JoshuaRL on 2009-01-10
Id suggest searching eBay for a little more RAM.  Then, you could install to the drive.  But man, that thing is ancient.

Does it even have any way of getting on the net?

---

### Post by crazyness003 on 2009-01-10
arch is also not a bad way to go. its a bit bigger than DSL and puppy, but it could get the job done.

---

### Post by this is new york not l.a. on 2009-01-10
about the internet. yes and no, i know it was used for internet but i couldn't get it to work for some reason. it has windows 98 but idk if that has anything to do with it. i'm dling dsl right now and i'll see what that does. i'll try puppy and the other one mentioned.

---

### Post by Bachstelze on 2009-01-10
Moved to Other OS Talk.

Oh, and OpenBSD. :3

---

### Post by Sorivenul on 2009-01-10
Any BSD (I prefer FreeBSD, though OpenBSD or NetBSD may work better in this case). I also second the suggestion for more RAM.

Good luck!

---

### Post by cardinals_fan on 2009-01-11
NetBSD

---

### Post by Bachstelze on 2009-01-11
> **cardinals_fan said:**
> NetBSD

I totally saw that coming. ;)

---

### Post by handy on 2009-01-11
> **crazyness003 said:**
> arch is also not a bad way to go. its a bit bigger than DSL and puppy, but it could get the job done.

To use Arch you will need to use LowArch:

*_[http://ubuntuforums.org/showthread.php?p=6490013#post6490013](http://ubuntuforums.org/showthread.php?p=6490013#post6490013)_*

---

### Post by lmno386 on 2009-01-11
Q: What did the female cat say to the male cat? A: You're the purrfect cat for me! .............................................................................................................................................[**warhammer online gold**](http://www.warhammergold119.com/) [**Maple story mesos**](http://www.warhammergold119.com/Maple-Story-EU) [**swg credits**](http://www.warhammergold119.com/Star-Wars-Galaxies) [**SilkRoad gold**](http://www.warhammergold119.com/SilkRoad) [**maple story mesos**](http://www.warhammergold119.com/Maple-Story)**[http://www.warhammergold119.com](http://www.warhammergold119.com)**

---

### Post by darrelljon on 2009-01-11
Have you seen the operating systems for old computers thread?

---

### Post by cardinals_fan on 2009-01-11
> **HymnToLife said:**
> I totally saw that coming. ;)
Just because you know it's the best... :D

---

### Post by Sorivenul on 2009-01-11
> **cardinals_fan said:**
> Just because you know it's the best... :D
I think we have three different opinions on the matter... ;)

---

### Post by this is new york not l.a. on 2009-01-11
alright, heres the situation. I downloaded dsl and made an iso cd. the problem is it doesn't boot when I restart like my ubuntu disk does. would there be anyway to get the disk to boot manually?

---

### Post by crazyness003 on 2009-01-11
have you checked the boot-order in bios? it may have defaulted to first boot your hdd.
Usually after post you can hit a key like F8 to give you a list of boot options.
Or go into BIOS (sometimes f10, or Del, or esc, it should tell you somewhere on the post screen) and modify your boot order.
Other than that, idk.
either you iso was incorrectly burned, the iso contents may be corrupted, or you burned it at a too fast speed for your drive to even read it.

---

### Post by this is new york not l.a. on 2009-01-11
I burned the iso cd at 6x and I can't seem to get into the bios =[
is there a way to get the cd-rom to boot first using comd-prompt?

---

### Post by crazyness003 on 2009-01-11
are you talking about the grub prompt or from within windows? Windows has no control at which device boots first. In fact, no OS can do it. 
when you first start up. just keep hitting esc, F1-F12. del repeatedly, until you see something happen. Thats all i can tell you.

And what do you mean you "cant get into the bios"? A password, or you cant get the right key-hit?

---

### Post by this is new york not l.a. on 2009-01-11
can't get the right key hit. and what I meant was going to start- run- command and going from there. if theres nothing i can do I'll just go burn the thing ;]

---

### Post by smartboyathome on 2009-01-11
You hit the f1-f12 keys when the computer first boots up, and you see your computer's manufacturer on the screen. If it goes by before anything happens, shut it down and boot it up again and keep going where you left off.

---

### Post by crazyness003 on 2009-01-11
> **this is new york not l.a. said:**
> can't get the right key hit..... if theres nothing i can do I'll just go burn the thing ;]
nah. you didnt burn for nothing. its just that some BIOS's are a pain. Depends on the manufacturer. Just keep repeatedly hitting all the keys. Its nearly impossible for there NOT to be an entry into BIOS.\

as for 
> **this is new york not l.a. said:**
> and what I meant was going to start- run- command and going from there
no. not any way that i remember of. i highly doube any operating system can control what's set in the bios (excepton is BIOS flash...which is not the case here)

---

### Post by handy on 2009-01-11
> **Sorivenul said:**
> I think we have three different opinions on the matter... ;)

Only three? ;-)

---

### Post by Sorivenul on 2009-01-11
> **handy said:**
> Only three? ;-)
Well, between HymnToLife, cardinals_fan, and myself regarding the BSDs. At least in this particular thread. At least, for this week before cardinals_fan decides to like MidnightBSD and I switch entirely to pfSense... :D

---

### Post by handy on 2009-01-11
> **Sorivenul said:**
> Well, between HymnToLife, cardinals_fan, and myself regarding the BSDs. At least in this particular thread. At least, for this week before cardinals_fan decides to like MidnightBSD and I switch entirely to pfSense... :D

:lolflag:

I enjoyed PC-BSD a couple of years ago.  At the time (at least) it would not run Cedega, so it never got beyond my testing machine.

Apart from that problem, I don't remember it having any problems for me at the time.  

I don't like KDE much, though the PC-BSD implementation was the best I've seen, really quite tidy.

Currently I run FreeNAS, which as you know, is a brilliant, tiny & incredibly effective FreeBSD based installation.

From my tiny amount of BSD experience, I must say that I like it a lot.  I haven't poked around too much in the guts of FreeNAS, though one day I'm sure I will run a BSD again, it will be interesting to compare its init to that of Arch, I may perhaps notice some similarities?

---

