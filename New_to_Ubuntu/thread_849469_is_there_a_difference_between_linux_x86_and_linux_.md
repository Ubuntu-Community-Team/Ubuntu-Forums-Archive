---
title: "is there a difference between linux x86 and linux i686?"
date: 2008-07-04
forum: New to Ubuntu
---

### Post by sonaural on 2008-07-04
i'm trying to install an ati driver from the website and they only list linux x86 and linux x86_64 as options.  when i open a terminal and type in uname -a it said i was running i686.  is that the same as x86?

i've had problems with my ati drivers.  when i installed driver prompted by the system the graphics got worse.  does this mean my version of linux is unsupported by the ati drivers possibly?

thanks

---

### Post by YaroMan86 on 2008-07-04
i686 and x86 are the same architecture. The only difference being some slightly enhanced instructions.

If you're having issues, it's likely ATI, which has horrible Linux support.

---

### Post by ZabiGG on 2008-07-05
Well, if you chose x86_64 and you are running a 32-bit system, the driver is not suited to your use. You should purge the driver and download the regular x86 driver.

a uname -a on a 64-bit system would give you something like this:

Linux zabi-desktop 2.6.24-19-generic #1 SMP Wed Jun 18 14:15:37 UTC 2008 **x86_64 **GNU/Linux

Hope this helps,

Z.

---

### Post by zzatz on 2008-07-05
Ubuntu comes in a 32bit version labeled 'i386', and a 64bit version labeled 'amd64'. The i386 version runs on all modern x86 processors, including 64bit processors running in 32bit mode. The amd64 version runs on all 64bit x86 processors.

Oddly enough, the i386 version won't run on a 386 - too old, needs a 486 or better. Think of 'i386' as meaning 'x86-32' and amd64 as meaning 'x86-64'.

Within each of those version, there are kernels tuned for specific models of processors. That's where you see 686 and k7. Don't bother with that, the generic kernel runs fine on them all. ATI doesn't care about that, they just need to know if you are running 32bit or 64bit.

---

