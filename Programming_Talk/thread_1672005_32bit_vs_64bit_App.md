---
title: "32bit vs 64bit App"
date: 2011-01-20
forum: Programming Talk
---

### Post by worksofcraft on 2011-01-20
I noticed that programs I compile on a 32 bit platform seem to work just fine on 64bit Ubuntu, but programs compiled for 64bit do NOT work on 32bit Ubuntu.

Does anyone know if this in general the case and if so how I make gcc compile for 32bit target when I'm running on 64bit?

---

### Post by Arndt on 2011-01-20
> **worksofcraft said:**
> I noticed that programs I compile on a 32 bit platform seem to work just fine on 64bit Ubuntu, but programs compiled for 64bit do NOT work on 32bit Ubuntu.

Does anyone know if this in general the case and if so how I make gcc compile for 32bit target when I'm running on 64bit?

I think it's generally the case.

For gcc, there is the option -m32. But I've found in the one case so far where I've tried it that it can be at best a major hassle and at worst doesn't work, to cross-build for 32-bit on 64-bit.

---

### Post by Arndt on 2011-01-20
> **worksofcraft said:**
> I noticed that programs I compile on a 32 bit platform seem to work just fine on 64bit Ubuntu, but programs compiled for 64bit do NOT work on 32bit Ubuntu.

Does anyone know if this in general the case and if so how I make gcc compile for 32bit target when I'm running on 64bit?


I think it's generally the case.

For gcc, there is the option -m32. But I've found in the one case so far where I've tried it that it can be at best a major hassle and at worst doesn't work, to cross-build for 32-bit on 64-bit.

---

### Post by worksofcraft on 2011-01-20
> **Arndt said:**
> I think it's generally the case.

For gcc, there is the option -m32. But I've found in the one case so far where I've tried it that it can be at best a major hassle and at worst doesn't work, to cross-build for 32-bit on 64-bit.

Thanks, for that info' and yes I thought that might be the case... I mean I don't think I even have all the 32 bit libraries present  on my 64bit Ubuntu so it would be linking 32bit apps with 64bit library modules :shock:

---

### Post by Reiger on 2011-01-20
If by 64bit apps you mean the AMD64 instruction set and if by 32bit apps you mean the x86 instruction set, then yes: AMD64 is backwards compatible with x86. IIRC ARM processors are compatible with x86 instructions as well (though ARM processors are 32bit).

---

### Post by Queue29 on 2011-01-21
> **Reiger said:**
> If by 64bit apps you mean the AMD64 instruction set and if by 32bit apps you mean the x86 instruction set, then yes: AMD64 is backwards compatible with x86. IIRC ARM processors are compatible with x86 instructions as well (though ARM processors are 32bit).

Holy misinformed post, batman.

Code compiled to amd64 is not backwards compatible with operating systems compiled for x86. x86 code is not compatible with operating systems compiled to amd64 *unless* there are 32 bit libraries installed (such as Ubuntu's ia-32 libs package). The ARM and x86 micro-architectures are WILDLY different, and are most certainly not compatible.

---

### Post by worksofcraft on 2011-01-21
> **Queue29 said:**
> Holy misinformed post, batman.

Code compiled to amd64 is not backwards compatible with operating systems compiled for x86. x86 code is not compatible with operating systems compiled to amd64 *unless* there are 32 bit libraries installed (such as Ubuntu's ia-32 libs package). The ARM and x86 micro-architectures are WILDLY different, and are most certainly not compatible.

No I meant the other way round... code compiled for a 32bit x86 Ubuntu... will that always run OK on AMD 64bit Ubuntu?

---

### Post by amauk on 2011-01-21
> **worksofcraft said:**
> No I meant the other way round... code compiled for a 32bit x86 Ubuntu... will that always run OK on AMD 64bit Ubuntu?
No, not always

The 64bit system will need the 32bit libraries (ia32-libs) installed
It's a monster package, about 200Mb, and includes all the 32bit versions of libraries needed for a 64bit system to run 32bit programs

---

### Post by 1clue on 2011-01-21
Hang on.

32 bit code is not compatible with 64 bit code, and vice versa.

64 bit processors can run 32 bit code as a backward-compatibility feature, and 64 bit systems often have both 64 bit and 32 bit libraries installed.

However, the code must be compiled to whatever architecture and stay consistent.  So if you're on a 32 bit system and compile an app, then it links against 32 bit libraries and nothing else.  Same thing when you compile on 64 bit.  It compiles against 64 bit libraries and nothing else, because that's what the application you're compiling expects.

It's possible to make a wrapper that causes a 32-bit driver to be accessible to a 64-bit application, such as nspluginwrapper.  But that is a deliberate linking with steps taken to be compatible.

Compiling from 64 bit to run on 32 bit would be called cross compiling.  It's the same thing as compiling for a palm pilot or an iPhone from your Intel system.  Yes you can do it but you need to take steps.  I've never done it.

---

### Post by worksofcraft on 2011-01-21
> **1clue said:**
> Hang on.

32 bit code is not compatible with 64 bit code, and vice versa.

64 bit processors can run 32 bit code as a backward-compatibility feature, and 64 bit systems often have both 64 bit and 32 bit libraries installed.

However, the code must be compiled to whatever architecture and stay consistent.  So if you're on a 32 bit system and compile an app, then it links against 32 bit libraries and nothing else.  Same thing when you compile on 64 bit.  It compiles against 64 bit libraries and nothing else, because that's what the application you're compiling expects.

It's possible to make a wrapper that causes a 32-bit driver to be accessible to a 64-bit application, such as nspluginwrapper.  But that is a deliberate linking with steps taken to be compatible.

Compiling from 64 bit to run on 32 bit would be called cross compiling.  It's the same thing as compiling for a palm pilot or an iPhone from your Intel system.  Yes you can do it but you need to take steps.  I've never done it.

OK thanks :)
So it's a backward compatibility thing!

I was doing this [quick little program on another thread here]("http://ubuntuforums.org/showthread.php?p=10381495#post10381495") and happened to notice that the 32 bit executable I had made worked just fine on my 64bit system and wondered if that was reliably so. In theory it should all be compilable on Windows and Sun OS and Amiga and OS X too but I have no way to test that.

---

### Post by 1clue on 2011-01-21
Exactly, it IS reliably so as long as your 64-bit system has 32-bit libraries installed.

<rant>
This actually burns me a bit.  This backward compatibility thing is there simply to allow an easier transition from one architecture to the next.  It's intended to last for a year or so, but inevitably it causes a huge amount of confusion and will no doubt still be causing problems when the next batch of processors come around and we need to emulate the 64-bit architecture on whatever comes next.

I wish they would make an optional emulator that can be uninstalled.  Grrr.
</rant>

---

### Post by worksofcraft on 2011-01-21
> **1clue said:**
> Exactly, it IS reliably so as long as your 64-bit system has 32-bit libraries installed.

<rant>
This actually burns me a bit.  This backward compatibility thing is there simply to allow an easier transition from one architecture to the next.  It's intended to last for a year or so, but inevitably it causes a huge amount of confusion and will no doubt still be causing problems when the next batch of processors come around and we need to emulate the 64-bit architecture on whatever comes next.

I wish they would make an optional emulator that can be uninstalled.  Grrr.
</rant>

I'm in full support of your "rant" I use virtual machines for lots of different things... eh like compiling and testing 32 bit versions of my software on a 32 bit platform... and I hate having Giga bytes of disk space being eaten up with junk I don't want on those virtual machines :shock:

---

### Post by nvteighen on 2011-01-21
The current situation is exactly the same we had back in the 16-bit -> 32-bit transition. And I think we'll keep having backwards compatibility with 32-bit for a long time, the same as it happened with 16-bit. Remember all the 16-bit libraries Windows shipped up to WinMe? E.g. You had COMCTL.DLL and comctl32.dll, 16-bit and 32-bit respectively. And so for every single system library.

---

### Post by 1clue on 2011-01-21
Actually I don't remember.  I managed to not own Windows until last year, when I bought a 64-bit Windows 7 laptop with a web cam for $250.  Before that I either used some other architecture (atari, mac, etc) or ran Linux.  I bought the laptop so fast I hadn't actually realized that I officially owned a Windows license until it was all over.  44 years of effort down the drain....

Then everything sucked so bad I couldn't stand it and I wound up giving the thing away anyway.

---

### Post by Reiger on 2011-01-22
> **Queue29 said:**
> Holy misinformed post, batman.

Code compiled to amd64 is not backwards compatible with operating systems compiled for x86. x86 code is not compatible with operating systems compiled to amd64 *unless* there are 32 bit libraries installed (such as Ubuntu's ia-32 libs package). The ARM and x86 micro-architectures are WILDLY different, and are most certainly not compatible.
No sorry. I meant processors running AMD64 are able to run x86 and so on. Holy mistyped, but not holy misinformed. :P

---

