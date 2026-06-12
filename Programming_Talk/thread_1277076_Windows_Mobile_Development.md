---
title: "Windows Mobile Development?"
date: 2009-09-27
forum: Programming Talk
---

### Post by jacensolo on 2009-09-27
Is there anyway to program for a windows mobile phone from Ubuntu besides Java? Is there a way to program for it natively? 

I even attempted to do it from windows, but .Net Compact (I know it isn't native) requires visual studio professional.

---

### Post by SunSpyda on 2009-09-28
I did a bit in Windows CE 5 development using C++ and native APIs. I did, however use VS .NET '08 for this. But seeing as it might not have the .NET dependency, you might be able to do it without VS .NET.

Bear in mind, that C++ native development is a LOT harder than C#/.NET.

---

### Post by chrisjsmith on 2009-09-29
You cannot do this without Visual Studio .Net.  

a) GCC doesn't support the PE format used on WinCE.  Only CL does on Win32.

b) CIL is subtly different (smaller instruction set - unmanaged code is different) on WM so that kills Mono.

c) No one has any GCC-oriented libs for it so you'd have no WinCE kernel/libs to link it to successfully.

Fun eh?  Proprietary at it's best.

Throw it away and buy a cheap Nokia for 100 EUR and use Eclipse+Java :-)

I spent 2 years writing horrible WinCE apps for delivery companies to do PODs and the like.  It's a horrid platform.  Get rid of it ASAP!

If you are lucky, you might be able to bring Linux up on the hardware though (unlikely).

---

### Post by directhex on 2009-09-29
Mono could do CF if anyone cared enough to enable it and send the patches upstream. Short version is, nobody's bothered because Mono's own equivalent, MonoLinker, is ten thousand times more programmer-friandly and useful than Compact Framework (creating a per-app cut down "compact framework" with *any* piece of the full thing you need, not a subset picked by Microsoft)

---

