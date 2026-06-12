---
title: "screen flickers then wigs out."
date: 2013-01-28
forum: New to Ubuntu
---

### Post by Maxfield Solar on 2013-01-28
Hi,
I am new to Linux but I love it so far. I installed Ubuntu 12.10 (32 bit) on my laptop It runs fine until it I try to run to many things at once. If I ever try to install anything, or I have two many taps up on Firefox Then my screen starts to flicker really bad and if it gets to bad then the screen goes half black and the other half gets all scrambled. Even if I kill all the software I have been using, the flickering does not go away until I reboot. I read the thread named[+%28rev+a2%29"] "Screen Flickering"]("http://ubuntuforums.org/showthread.php?t=2061180&highlight=driver+NVIDIA+Corporation+C77+[GeForce+8200M+G) So I figured I would provide the information requested on that thread.

To "cat /etc/lsb-release" I got 
```
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=12.10
DISTRIB_CODENAME=quantal
DISTRIB_DESCRIPTION="Ubuntu 12.10"
```

To "uname -a" I got
```
Linux Maxfield-Solar 3.5.0-22-generic #34-Ubuntu SMP Tue Jan 8 21:41:11 UTC 2013 i686 athlon i686 GNU/Linux
```

To "lspci -nnk | grep -iA2 vga" I got
```
02:00.0 VGA compatible controller [0300]: NVIDIA Corporation C77 [GeForce 8200M G] [10de:0845] (rev a2)
    Subsystem: Hewlett-Packard Company Device [103c:360a]
    Kernel driver in use: nouveau
```

To "env | grep DES"
```
DESKTOP_SESSION=ubuntu
GNOME_DESKTOP_SESSION_ID=this-is-deprecated
XDG_CURRENT_DESKTOP=Unity
```

Thank-you,
Kienan

---

### Post by DuckHook on 2013-01-29
I suspect that you are trying to do too much with your notebook. The GeForce 8200M G is a tiny little graphics chip that uses shared system memory to do its work. You will have to look up in your bios the amount of your system memory that it "borrows", but I suspect it isn't more than about 128MB. If that's the amount, I'm surprised that you even got Ubuntu to run.

I want to commend you on including as much info as you have... it shows forethought and is appreciated by those trying to help, but we need just a little more. Please tell us the make, model and specs of your laptop. The most important stuff will be cpu, amount of system memory and portion hived off to your graphics chip.

You can provide much of this with:

```
sudo lshw
```but we likely don't need it and can tell all that we need from the simple system summary requested earlier. You will still have to look in your bios for amount of graphics memory.

Currently, you are running the open source "nouveau" graphics module that is installed by default. This is not optimized for the nvidia, although many like it because it is completely open-source. You may wish to install the proprietary driver for the nvidia (found in the dash under "additional drivers"), but I strongly suspect that your biggest bottleneck will prove to be an underpowered system for the modern high-powered OS you are trying to run.

Alternatives: Xubuntu or Lubuntu. Kubuntu needs just as much resources as Ubuntu so not recommended.

---

### Post by Maxfield Solar on 2013-01-29
Thank-you,

This computer was running Windows Vista from the factory. Someone told me that Vista would need more resources than Ubuntu. Is this wrong?

Getting to the actual specks, My laptop is an HP Presario CQ60 or more specifically  CQ60-215DX. I opened my bios and searched it as thoroughly as I could, but I could not find anything about the graphics memory. I have the factory  2GB of ram and the AMD Athlon X2 64bit dual core processor. I found a site [(http://www.cnet.com/laptops/hp-compaq-cq60-215dx/4507-3121_7-33496182.html)]("http://www.cnet.com/laptops/hp-compaq-cq60-215dx/4507-3121_7-33496182.html") that has specs for the CQ60-215DX It claims that it has 895mb of Total available graphics memory. Would this be what I am looking for?

As far as the ram and CPU
Here is what I found in the terminal concerning the physical memory 
```
*-memory:0
          description: System Memory
          physical id: 4
          slot: System board or motherboard
          size: 2GiB
        *-bank:0
             description: DIMM DRAM Synchronous 667 MHz (1.5 ns)
             physical id: 0
             slot: S1
             size: 1GiB
             width: 32 bits
             clock: 667MHz (1.5ns)
        *-bank:1
             description: DIMM DRAM Synchronous 667 MHz (1.5 ns)
             physical id: 1
             slot: S2
             size: 1GiB
             width: 32 bits
             clock: 667MHz (1.5ns)
```

Here is what I found about my cpu
```
*-cpu:0
          description: CPU
          product: AMD Athlon Dual-Core QL-62
          vendor: Advanced Micro Devices [AMD]
          physical id: 3
          bus info: cpu@0
          version: 15.3.1
          slot: Socket A
          size: 1GHz
          capacity: 2GHz
          width: 64 bits
          clock: 133MHz
          capabilities: boot fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt rdtscp x86-64 3dnowext 3dnow constant_tsc nonstop_tsc extd_apicid pni cx16 lahf_lm cmp_legacy svm extapic cr8_legacy 3dnowprefetch osvw skinit hw_pstate lbrv svm_lock nrip_save cpufreq
        *-cache:0
             description: L1 cache
             physical id: 5
             slot: L1 Cache
             size: 128KiB
             capabilities: asynchronous internal write-back
        *-cache:1
             description: L2 cache
             physical id: 6
             slot: L2 Cache
             size: 512KiB
             capacity: 2MiB
             capabilities: synchronous internal write-through unified
```and```
 *-cpu:1
          physical id: 5
          bus info: cpu@1
          version: 15.3.1
          size: 1GHz
          capacity: 1GHz
          capabilities: cpufreq
        *-cache:0
             description: L1 cache
             physical id: 0
             size: 128KiB
        *-cache:1
             description: L2 cache
             physical id: 1
             size: 512KiB
```

Did I miss anything? I will look into the "additional drivers," but if my laptop is to week for this anyway, I may as well not worry about that.

Thank-you,
Kienan

P.s. I posted these two posts from the laptop in question, so It does work so long as I am not installing any software or overloading it.

---

### Post by DuckHook on 2013-01-29
Your laptop should run Ubuntu just fine. The graphics chip is more robust that I thought. It likely doesn't take all 895MB of system memory at once. This would leave you only a little over 1 GB for main system memory, which seems unlikely. Some of these graphics subsystems share memory dynamically and will only take what they need at any given time. Not sure how the default nouveau driver deals with that.

Re: Vista. Generally, it is true that any laptop capable of Vista should be capable of running Ubuntu. Certainly true before Unity 3D became the default. However, with the adoption of Unity as the default DE, I fear that Ubuntu is approaching the same level of bloat as Windows. All of that eye-candy and 3D special effects requires far more resources than the old 2D-based environments.

I suggest trying the proprietary driver.

Have you looked for this in your "additional drivers" app?

If it isn't there, you should make sure that "restricted drivers for devices" is checked in your "software sources" in Update Manager.

---

### Post by tgalati4 on 2013-01-29
Put a temperature monitor on the desktop.  It's possible that your graphics chip is getting too hot and declocking or shutting down.  The fans/heatsinks might need cleaning.

---

### Post by Maxfield Solar on 2013-01-29
> **DuckHook said:**
> I suggest trying the proprietary driver.

Have you looked for this in your "additional drivers" app?

If it isn't there, you should make sure that "restricted drivers for devices" is checked in your "software sources" in Update Manager.

I could not find an "additional drivers" app, but I did find an additional drivers tab in the "software updater" settings menu.  There are four different proprietary drivers for the graphics.  I will experiment with these drivers and give an update post. Hopefully I will be able to mark "solved" on this thread!

As to the suggestion made by "tgalati4" on the temp monitor,
That's a good Idea, I will try it. Is there a specific monitor you recommend? This does make sense because sometimes my laptop can run pretty hot.

Thank-you both,
Kienan

---

### Post by Maxfield Solar on 2013-01-30
> **tgalati4 said:**
> Put a temperature monitor on the desktop.  It's possible that your graphics chip is getting too hot and declocking or shutting down.  The fans/heatsinks might need cleaning.

I think you may be right that it was getting to hot and then throttling down. But I when I changed the driver it started working much better! I am guessing that the Nouveau driver may have been running the GPU in such a way that it would overheat. I will do some further testing with that temperature monitor to ensure that this is the case.

I will do a few tests with all five drivers and post my results. Other than that I think that my case is pretty much solved. I will mark it as such after doing my tests.

Thank-you guys!!!
Kienan

---

### Post by Maxfield Solar on 2013-03-21
I'm sorry for leaving this thread as unsolved for so long. I've realized that I will not be able to do the tests I thought I would do so this thread is now solved. My laptop runs great now, thank-you all!!

---

