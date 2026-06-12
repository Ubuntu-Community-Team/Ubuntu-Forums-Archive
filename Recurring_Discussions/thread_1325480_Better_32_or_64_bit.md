---
title: "Better 32 or 64 bit?"
date: 2009-11-13
forum: Recurring Discussions
---

### Post by Emanuele_Z on 2009-11-13
Hi guys,

I'm going to upgrade to 9.10 (I have 9.04 but I plan to format and re-install).
What do you recommend? 32 or 64 bit?
Naturally I have 2 GB Ram, so that's not a mandatory upgrade.
I usually develop and compile with gcc/g++ and OpenGL/GLSlang...
I'm more of a kind dev user, but I usually prefer not to compile the *big* apps but install via apt-get (don't want to mess with configs etc etc).

What do you suggest? Most of all why? (I'm downloading the 32 bit version right now...)

Cheers,

---

### Post by NoaHall on 2009-11-13
64 bit. Always in my book.

---

### Post by RiceMonster on 2009-11-13
512 bit is where it's at.

---

### Post by Emanuele_Z on 2009-11-13
Ok, I see, but why?
What is the reason of this?
I've read that flash doesn't properly work yet and wma 9 don't play...

(now I'll DL the 64bit version as well... will take 10 minutes.. :) )

---

### Post by gn2 on 2009-11-13
Just as 11 is more than 10, 64 is more than 32 therefore better.

---

### Post by The Funkbomb on 2009-11-13
32bit is fine.  The main advantage of 64bit is that you can use more than 4gb of ram.  One might need this for rendering a movie or model.  Other than that, 2gb is plenty and will run on 32bit fine.

---

### Post by dizee on 2009-11-13
I haven't really had any problems since using 64-bit. Particularly Karmic, very solid and stable so far.

Flash works well. Even though the 64-bit flash is an "alpha".

That said there's not that huge a case to switch either. Supposed to eat up more RAM, but I suppose compiling should be faster. 
> 
 Just as 11 is more than 10, 64 is more than 32 therefore better. 
That used to be the case for games consoles back in the day. 16 bit > 8 bit ;)

---

### Post by HappyFeet on 2009-11-13
> **Emanuele_Z said:**
> 

I've read that flash doesn't properly work yet and wma 9 don't play...



64bit flash works great for me. Everything works the same for me as it did in 32bit, only faster. Seems more stable too.

---

### Post by xuCGC002 on 2009-11-13
64-bit, trust me.

---

### Post by Sam on 2009-11-13
I was using 64 bit back in the days (dapper, IIRC), and that was a pain to run most of the applications I needed. I switched to 32 bit then. With karmic I gave 64 bit an another try and now everything works smoothly, even flash. I totally satisfied with 64 bit.

---

### Post by FuturePilot on 2009-11-13
Another satisfied 64bit user. It's definitely a lot better than it used to be way back when. Give it a shot.

---

### Post by Emanuele_Z on 2009-11-13
Ok guys, I see you like 64 bits. That's cool.
But, from a dev point of view the only advantage of 64 bit if you have more than 4gb memory.
Or is it that all the 64 bit compiled application come with optimizations/more registers as default (gcc *-march=i686* instead of *-march=i386*) and thus are faster on modern CPUs?

Because opposed to that we have for sure some downsides, like bigger executables, some issues with 32/64 bits libraries and most of precompiled packets are for 32 bits...

Really, apart *64 is better than 32*, any other proper reason?

Cheers,

---

### Post by gn2 on 2009-11-13
CPU intensive tasks like video encoding complete much faster with a 64-bit OS on the same hardware, up to 50% faster.
That's a huge performance increase for zero cash outlay.

---

### Post by starcannon on 2009-11-13
"Better" is not the word I would use; "easier" is how I look at it. Currently 32bit is easier to manage than 64bit, but that said, 64bit is closing the gap at a pretty rapid pace, indeed I look forward to using it as my main version before too much longer.

---

### Post by SunnyRabbiera on 2009-11-13
Yes but 64bit support is still flaky, its still not where I need it to be.
I dont care about speed boosts when I need certain apps to work and there are a few apps that are 32bit only.

---

### Post by blueshiftoverwatch on 2009-11-13
> **Emanuele_Z said:**
> I've read that flash doesn't properly work yet and wma 9 don't play...
Flash works most of the time. Sometimes what happens though is that the actual Flash object wont' load. But all you have to do is close your browser and reopen it to the page you wanted to view.
> **SunnyRabbiera said:**
> I dont care about speed boosts when I need certain apps to work and there are a few apps that are 32bit only.
Why does 64 bit Windows allow you to install 32 bit apps but Linux won't?

---

### Post by NoaHall on 2009-11-13
> **blueshiftoverwatch said:**
> Flash works most of the time. Sometimes what happens though is that the actual Flash object wont' load. But all you have to do is close your browser and reopen it to the page you wanted to view.

Why does 64 bit Windows allow you to install 32 bit apps but Linux won't?

Of course you can install 32 bit apps. And if the .deb doesn't work, you can compile them again, from source. Easy Peasy.
Flash 64 bit alpha works fine.

---

### Post by CharlesA on 2009-11-13
I use 64-bit if my processor supports it. All the machines I have minus 1 are 64-bit.

---

### Post by Tibuda on 2009-11-13
64bit ftw

> **NoaHall said:**
> Of course you can install 32 bit apps. And if the .deb doesn't work, you can compile them again, from source. Easy Peasy.
Flash 64 bit alpha works fine.

You can compile if you have the source, but this is not always the case. Skype provides a debian package for 64bit with the 32bit binaries and depends on the 32 libs wrapper.

---

### Post by jward3010 on 2009-11-13
If you type something like "Better 64-bit 32-bit" into Google, it brings you to a benchmark that was done pretty methodically by the looks of things which suggests that 64-bit Ubuntu had improved performance in a lot of it's tests. Hard Disk lack of performance will never be something that 64 or 32 or 128 bit will beat (SSD's should help) but intensive CPU performance based tests like video encoding, MP3 ripping, photo editing etc. in most cases showed up to be faster.

Realistically the effect is very negligible, I doubt you'll notice in ordinary everyday things.

In regards compatibility issues, I have never found it to be the case that 64-bit is less compatible with regards flash or WMA9 support (are you talking about the format or the actual player?). 64-bit is becoming uber-popular now with most CPU's being able to support it and the cheapness of RAM has meant over 4GB is going in a lot of units now so those issues are all but gone as far as I can see. I run 64-bit Ubuntu's more than 32-bit and NEVER have any problems.

---

### Post by blueshiftoverwatch on 2009-11-13
> **NoaHall said:**
> Of course you can install 32 bit apps. And if the .deb doesn't work, you can compile them again, from source. Easy Peasy.
Flash 64 bit alpha works fine.
Not if it's a .deb file of a proprietary commercial app. What I meant was that on Windows 7 I was able to install Steam and my Half-Life 2 games (which are 32 bit) and they ran just fine. But you can't do that with 32 bit apps on Linux, that I'm aware of.

---

### Post by Emanuele_Z on 2009-11-13
I have downloaded both ISO...
I'm seriously thinking to give 64bit a go.
I've already installed it on my test computer...the only closed source applications I use are Skype and (when I played) WoW (through wine).*

Apart generally developing C/C++, I'm developing a couple of GPGPU apps with OpenGL/GLSLang.
I have an nVidia card...how are the drivers?

Can someone report links to proper test showing that 64bits is better?
I don't doubt this, and quite frankly I'd be surprised if that wasn't true for math computations: usually gcc/g++ when compiled with *-march=i686* (default when compiling in x86-64 mode) uses the sse2 registers to do floating point math, so the boost can be impressive ( [http://gcc.gnu.org/onlinedocs/gcc/i386-and-x86_002d64-Options.html#i386-and-x86_002d64-Options](http://gcc.gnu.org/onlinedocs/gcc/i386-and-x86_002d64-Options.html#i386-and-x86_002d64-Options) see *-mfpmath* option).

Another issue I found was that the wma 9 wasn't playable with default codecs but one has to buy the closed source one. Is that true? ( [http://blog.thesilentnumber.me/2009/09/top-things-to-do-after-installing.html](http://blog.thesilentnumber.me/2009/09/top-things-to-do-after-installing.html) )

Cheers,

*Update I forgot I have bought World of Goo 32 bit. Will it work?

---

### Post by NoaHall on 2009-11-13
> **blueshiftoverwatch said:**
> Not if it's a .deb file of a proprietary commercial app. What I meant was that on Windows 7 I was able to install Steam and my Half-Life 2 games (which are 32 bit) and they ran just fine. But you can't do that with 32 bit apps on Linux, that I'm aware of.

ehm...
dpkg -i --force-architecture /file/name.deb

---

### Post by blueshiftoverwatch on 2009-11-13
> **NoaHall said:**
> ehm...
dpkg -i --force-architecture /file/name.deb
Thanks, works perfectly now.

---

### Post by NoaHall on 2009-11-13
> **blueshiftoverwatch said:**
> Thanks, works perfectly now.

:) Sarcasm or not?

---

### Post by blueshiftoverwatch on 2009-11-13
> **NoaHall said:**
> :) Sarcasm or not?
I forgot that on the Internet people can't hear the inflection in your voice. It actually did work.

---

### Post by misfitpierce on 2009-11-13
64 bit is always better. The support is there for linux too unlike using on windows. Mostly all apps have 64 bit counterparts on linux. Go 64 bit if you got the hardware. It also allows you to show over 3.5GB ram without issues unlike 32 bit. 64 Bit also has noticeable speed differences even on linux as fast as it is and you will notice the speed difference unless your blind! Go 64 bit!

---

### Post by Emanuele_Z on 2009-11-14
Ok, I'll go 64bit then...

One last question: if I compile in 32 bit mode, I guess I have to install 32 bit libraries as well (eg. gtkmm) ?

Cheers,

---

### Post by Andrey2009 on 2009-11-14
[All about 64-bit developing - http://www.viva64.com/guide/64-bit-development/]("http://www.viva64.com/guide/64-bit-development/")

---

### Post by Zoot7 on 2009-11-14
I'm still on 32bit in both Windows and Linux. I just haven't seen a compelling reason to switch yet. 
I might make the jump when Lucid gets out the gate.

---

### Post by Emanuele_Z on 2009-11-15
One quick question...

Given that you should not be able to call 64bit libraries from 32bit executables (when the arguments are put on the stack if there's a long everything gets screwed...), if I install a 32 bit app (World of Goo as example), will it require the install of all other 32 bit libraries as well?

Am I right?

Example:
```

ema@blademaster:~$ file /usr/bin/wine
/usr/bin/wine: ELF 32-bit LSB executable, Intel 80386, version 1 (SYSV), dynamically linked (uses shared libs), for GNU/Linux 2.6.15, stripped
ema@blademaster:~$ ldd /usr/bin/wine
	linux-gate.so.1 =>  (0xf77bf000)
	libwine.so.1 => /usr/bin/../lib32/libwine.so.1 (0xf7681000)
	libpthread.so.0 => /lib32/libpthread.so.0 (0xf764e000)
	libc.so.6 => /lib32/libc.so.6 (0xf7509000)
	libdl.so.2 => /lib32/libdl.so.2 (0xf7505000)
	/lib/ld-linux.so.2 (0xf77c0000)

```

---

### Post by NoaHall on 2009-11-15
Yes. But it's easy to do so. "sudo apt-get install ia32-libs" I think. Not sure, don't tend to use it - there's a 64 bit version of world of goo.

---

### Post by jward3010 on 2009-11-15
> **Zoot7 said:**
> I'm still on 32bit in both Windows and Linux. I just haven't seen a compelling reason to switch yet. 
I might make the jump when Lucid gets out the gate.
I mean there's no real advantage unless you have more than 3.3GB's of memory and you really need those 8 to 10 seconds advantage in a 45 minute video encode.

If there's any compelling reason it's that you may notice bugs, flaws, fixes to be made in 64-bit which you can give feedback on and hence improve the HELL out of it.

---

### Post by Emanuele_Z on 2009-11-16
> **NoaHall said:**
> Yes. But it's easy to do so. "sudo apt-get install ia32-libs" I think. Not sure, don't tend to use it - there's a 64 bit version of world of goo.

Hehe I forced the install..now happily using the 32bit on 64bit one...

Cheers,

---

### Post by NoaHall on 2009-11-16
> **Emanuele_Z said:**
> Hehe I forced the install..now happily using the 32bit on 64bit one...

Cheers,

No problem :) If you have any problems with it, try installing the 32 bit libraries anyway. I don't have them installed at all, but that's because I use only 64 bit apps, now that they are around :) It was a bit harder when 64 bit apps were rare.

---

### Post by naveen8888 on 2010-01-04
Not necessarily. Sometimes 64 bit is a bit unstable

---

### Post by jward3010 on 2010-01-04
Overall, the advantage of 64 bit over 32 is the amount of memory it addresses, secondly it's the up and coming CPU architecture and more than likely 32-bit will be slowly phased out. So it's worth if you have it to install 64-bit editions of Ubuntu, Windows 7, Slackware, whatever!

---

### Post by NoaHall on 2010-01-04
> **naveen8888 said:**
> Not necessarily. Sometimes 64 bit is a bit unstable

No, it's not.

---

### Post by alakazam on 2010-01-04
32 bit is what has the most potential to hold Linux & Windows back, All new Apple mac's are 64 bit bringing out the speed and opening up to knew technologies and by experience I know are rock solid, Apple need not focus now on 32 bit.

---

### Post by Roasted on 2010-01-04
> **noahall said:**
> no, it's not.

+1

---

### Post by sertse on 2010-01-04
Closing the 64bit subforums indicates even the powers here think 64bit has no particular issues. Thus no reason not to use it if you can.

-No longer a recurring discussion. :P

---

### Post by Astrals on 2010-01-17
I have used 32bit and 64bit, from my experience 64bit is better, the only issues you will find is there are more stability issues with 64bit.

Let's face it the world of computers keeps moving forward, unless people use it then the support for it just isn't there.

---

