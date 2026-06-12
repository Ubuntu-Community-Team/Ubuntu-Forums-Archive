---
title: "Ubuntu's slower than XP?"
date: 2008-12-04
forum: Recurring Discussions
---

### Post by dorkdork777 on 2008-12-04
On my (fairly outdated) P4, 3.2ghz with 1GB RAM, I've noticed something that doesn't really fit in with the "Linux is faster" philosophy. For some things, especially media tasks and flash games, Ubuntu is simply a lot slower than Windows XP on the same box.

For example, dvd::rip on Ubuntu ran at about 19 fps tops, simply ripping the DVD, while DVD Decrypter on Windows ran at a stable 2.2x, which I worked out at 52.8 fps. 52.8! Meanwhile, on Ubuntu, DVD Decrypter running in Wine maxed out at about 2.0x, but frequently dropped below 1.0x - meaning at the end, the average was about 1.1x. That's half what I got on Windows.

As well as this, flash games ([this one in particular]("http://www.ferryhalim.com/orisinal/g3/bells.htm") - try not to get addicted) runs silky smooth on WXP, while on Ubuntu it gets jerky and laggy at the slightest thing.

Is this a stupid comparison? I know it would make more sense to compare a recent Linux distro to a recent version of Windows rather than one that's seven years old, but I have to admit, I found this surprising.

But if the comparison makes sense - why is Ubuntu so much slower than XP on my machine?

---

### Post by squeabs on 2008-12-04
I've noticed a decrease in speed from hardy to ibex. I actually switched back to hardy for the time being because it's a little more stable.
As far as ubuntu vs xp, I wouldn't know. But I can state that ubuntu is much faster than vista on my pc.

---

### Post by dorkdork777 on 2008-12-04
So Ibex is slower than Hardy? Interesting... That does kind of make sense, but aren't they trying to optimise things at the moment?

Anybody have anything else to add?

---

### Post by klambert on 2008-12-04
ive noticed the operating system, itself is faster, but some tasks take a bit longer, but i think it is because of the way linux works with the every application starts up by it self, separate from the OS unlike in windows where its all tied togheter...thats my logic behind it anyway

---

### Post by sedawk on 2008-12-04
Here I experience exactly the opposite. When storing video files
after removing commercials from tv recordings with avidemux the
task runs 6-10 times faster on Ubuntu than on WXP, both writing
to the same NTFS FS.

May be you can try yourself playing around with some big avi file
and avidemux on Ubuntu and WXP.
Try first to only copy the file - so you mostly measure i/o performance.
Next recode the video file to create cpu load so you can compare
the cpu performance.

What is the performance when copying big files from (unencrypted)
data-dvds?

---

### Post by snowpine on 2008-12-04
Why would Ubuntu be faster than XP? I'm not saying it is or isn't :), just curious why you would assume this is the case since XP is an 8 year old operating system and Intrepid Ibex is 2 months old--they are designed with very different minimum system requirements.

Your computer might even have a "designed for Windows XP" sticker somewhere on it, whereas Ubuntu didn't even exist yet when your computer was built. ;)

---

### Post by dorkdork777 on 2008-12-04
I think the sysreqs are more similar than you think, snowpine. XP wants 128MB RAM, while Intrepid wants 256 (for the alternate installer). Pretty damn similar for OSs with a 7-year time gap.

And I'll do some tests with my DVD drive, sedawk.

Thanks to everyone for their help so far :)

---

### Post by Nostalos on 2008-12-04
I think you're comparision there is a little skewed in my opion. (And it is just that, my opinion so take with a grain of salt.)   If you compare the base OS's  somethings will be faster in one or the other purely on the way each of them handles things differently based in differing idealogies. 

Example Complaint from a coworker of mine.... IE loads so much faster in windows than Firefox does on my linux box.  Reason:  IE is preloaded into memory on bootup.  Firefox is loaded purely from the drive first time its ran.   Windows also prefetches various apps into memory on bootup.  Windows is trying to create a sense of speed at the cost of ram.  Linux uses less ram at the cost of speed of loading. 


On your DVD Decrypter issue.  I was having a similar problem.  Worked really fast in Vista.  Slower than hell in Linux.  Issue turned out the be the mode the DVD Drive was using required an 80Pin IDE cable instead of the 40Pin i was using.  Windows worked around it by swithing to a different Mode, Linux did not.   Changed the Cable and and both where equivelent.   You're problem might be similar, or just purely the fact it is 2 differing programs as well.   dvd::rip is a full encoding program, DVD Decrypter does one thing and one thing alone. Decrypts the DVD to a file.   Handbrake in Linux for me smokes my Vista by 10%. (same physical machine)


And plain and simply. Programs run under Wine will Never Ever be as fast as running it in Windows natively.  Wine is an API shim between the windows app and the Linux kernel.  Not an emulator per say, but it has to burn extra cycles translating Windows API calls to the Linux Kernel.  

And finally as for Flash.  Flash works in Linux.  However far more time has been spent poking and prodding Flash for Windows and it got ported to Linux purely as an after thought.   Linux constitutes only 1% maybe of the desktop market.  Squeeky Wheel gets the oil, and right now windows users are far more Squeeky by numbers alone. 

In short, if Linux seems slower than windows at something.  Is it Linux thats slow? or the fact that its a 3rd party app that just happens to run on Linux.

---

### Post by hyper_ch on 2008-12-04
try Arch or DSL

---

### Post by bodhi.zazen on 2008-12-04
Moved to recurring discussions, knock yourselves out :)

---

### Post by SunnyRabbiera on 2008-12-04
it depends on specs, and what you have.
On older computers you will probably see slowdown, as each ubuntu adds more stuff in.
But there is a way to make ubuntu use less, use XFCE for starters.

---

### Post by Eclipse. on 2008-12-04
What people forget is xp was released in 2001, this is now 2008.;)

Not a very fair comparison.

---

### Post by lzfy on 2008-12-04
> **Eclipse. said:**
> What people forget is xp was released in 2001, this is now 2008.;)

Not a very fair comparison.

True. You should compare Ubuntu with Vista. My Experience is that a fresh install of Windows is very fast but after a while using it, it crawls down. Ubuntu stays at the same speed, even after using it for a year.

---

### Post by tsali on 2008-12-04
> **lzfy said:**
> True. You should compare Ubuntu with Vista. My Experience is that a fresh install of Windows is very fast but after a while using it, it crawls down. Ubuntu stays at the same speed, even after using it for a year.

I run Vista Home and Ubuntu Hardy dual boot. The Vista install has been running since Mar 2007. It is faster than Ubuntu at almost every task except large file transfer operations.

---

### Post by magmon on 2008-12-04
Hmm, I think this may be due to your hardware. The provided flash game, which I played for about 20 minutes, worked perfectly. As do all other flash games, youtube, etc.

Btw, vista is by no means faster than ubuntu. Maybe for those of you with UBER computers, but on my laptop it ran, on a scale of 1-10, at about a 7. Ubuntu runs at a 9-10

---

### Post by CraigPaleo on 2008-12-05
Windows uses prefetch, which caches certain programs into RAM causing those applications to load faster. 

The equivalent in linux would be preload, which is in the repositories. There are also prelink and readahead. Readahead is installed by default in Intrepid but preload and prelink aren't. Here's some info on preload: [http://www.techthrob.com/tech/preload.php]("http://www.techthrob.com/tech/preload.php")

---

### Post by tsali on 2008-12-06
> Btw, vista is by no means faster than ubuntu. Maybe for those of you with UBER computers, but on my laptop it ran, on a scale of 1-10, at about a 7. Ubuntu runs at a 9-10

E6400 Core 2, 2Gb RAM, nVidia 7300...UBER COMPUTER?

---

### Post by dorkdork777 on 2008-12-06
Sure beats mine :) 3.2Ghz P4, 1GB RAM, NV GeForce 6200. That's the absolute minumum for a fully-fledged Vista install (including Aero effects), from what Wikipedia tells me - I wouldn't think of installing Vista on this, while Intrepid runs at a very acceptable speed.

---

### Post by doorknob60 on 2008-12-06
Are you using flash 10? It works very smooth for me with only using like 20% CPU also. Using Flash 10 64 bit alpha. EDIT: Got 35840 points :D Either it's a problem with flash, or with the video drivers. It's probably not ubuntu's fault or linux's faukt. It's the fault of closed source software.

---

### Post by dorkdork777 on 2008-12-08
I have both flash 9 and 10 installed as plugins, but only 10 is enabled. BTW, I hate to say it, but my high score is over 10 mil. I get addicted easily :)

---

