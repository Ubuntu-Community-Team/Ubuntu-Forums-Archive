---
title: "Kernel 3.0.1 is out"
date: 2011-08-06
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by paul_in_london on 2011-08-06
[http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.0.1-oneiric/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.0.1-oneiric/)

Working ok here:

```
paul@oneiric:~$ uname -a
Linux oneiric 3.0.1-030001-generic #201108060905 SMP Sat Aug 6 10:43:25 UTC 2011 i686 i686 i386 GNU/Linux
paul@oneiric:~$
```

---

### Post by Harry33 on 2011-08-06
Kernel 3.0.1 is also in Launchpad, it has been built, but the state is new ATM.
So you have to download the packages manually.
I did that and installed them with dpkg.
Working fine.

Here:
[https://launchpad.net/ubuntu/oneiric/+source/linux/3.0.0-8.10](https://launchpad.net/ubuntu/oneiric/+source/linux/3.0.0-8.10)

> **Changelog**
linux (3.0.0-8.10) oneiric; urgency=low

  [ Adam Jackson ]

  * SAUCE: drm/i915/pch: Fix integer math bugs in panel fitting
    - LP: #753994

  [ John Johansen ]

  * [Config] Enable missing IPv6 options

  [ Leann Ogasawara ]

  * [Config] Disable config IWLWIFI_DEVICE_SVTOOL
    - LP: #819925
  * Rebase to 3.0.1

  [ Upstream Kernel Changes ]

  * x86, intel, power: Correct the MSR_IA32_ENERGY_PERF_BIAS message
  * ALSA: hda - Turn on extra EAPDs on Conexant codecs
    - LP: #783582
  * KVM: Remove SMEP bit from CR4_RESERVED_BITS
    - LP: #796476
  * KVM: Add SMEP support when setting CR4
    - LP: #796476
  * KVM: Mask function7 ebx against host capability word9
    - LP: #796476
  * KVM: Add instruction fetch checking when walking guest page table
    - LP: #796476

  [ Upstream Kernel Changes ]

  * rebase to v3.0.1
 -- Leann Ogasawara <email address hidden>   Fri, 05 Aug 2011 11:32:25 -0700

---

### Post by VinDSL on 2011-08-07
Interesting!

I *think* that's the first time I've installed a new kernel, and it didn't  rebuild the nVidia binary driver kernel module.

Hrm...

Everything seems to be working fine, but...

Maybe I should re-install nvidia-current, just to be sure.   ;)

---

### Post by Harry33 on 2011-08-07
> **VinDSL said:**
> Interesting!

I *think* that's the first time I've installed a new kernel, and it didn't  rebuild the nVidia binary driver kernel module.

Hrm...

Everything seems to be working fine, but...

Maybe I should re-install nvidia-current, just to be sure.   ;)

Same here. I had to reinstrall nvidia-current to get the module in its place.
I remember once testing (not with 3.0.* kernel though) what happens without the module, when rebooted.
Then, nvidia driver did not load at all.

---

### Post by VanR on 2011-08-07
I uninstalled the new 3.0.1 because it broke the ability to mute my PC speakers when I plug my headphones in that I had with 3.0-300. Weird. My conputer just got that function with 3.0 and I'm not going back there.

---

### Post by tad1073 on 2011-08-07
I just installed 3.0.1 and nvidia 280.13 built just fine but I am using 10.10 though.

---

### Post by Harry33 on 2011-08-07
> **tad1073 said:**
> I just installed 3.0.1 and nvidia 280.13 built just fine but I am using 10.10 though.

Nvidia builds just fine in Oneiric also.
The issue however is that Oneiric's cairo is gl enabled and that is incompatible with nvidia-current or vice versa.
On the other hand Natty's cairo is not gl enabled and thus not troublesome at all.

---

### Post by VinDSL on 2011-08-07
Hrm...

Like most 'things Linux', there are several ways to install kernels.  I suppose it all depends on the methodology that you use.

Personally, I download the pertinent files to /home/user/Downloads/Kernel and invoke dpkg from CLI.

I put the terminal in fullscreen mode, and watch dpkg do "its thing".  I love work.  I can watch others do it all day long.  :D

In the middle of the process, the nVidia binary driver module rebuilds, and I pay particular attention as to whether it passes or fails.

The last process is the grub update.  I watch this closely too, to make sure it recognizes Ubu 10.10 (on a separate partition, e.g. dual boot).

In this instance, the nVidia binary driver kernel module didn't even attempt to rebuild, so I manually rebuilt it by reinstalling nvidia-common.

This is quite common when you're running nVidia OEM drivers, but I've never had it NOT happen with nVidia drivers from the official Ubu repos.

Anyway, no harm, no foul.  Everything is working fine.  ;)

---

### Post by garvinrick4 on 2011-08-07
Kernel 3.0.1 running in 10.10 thru 11.10 and all stable, 64 bit.
10.10 and 11.04 need module-init-tools 3.13-1 also. 
[Index of /~kernel-ppa/mainline]("http://kernel.ubuntu.com/%7Ekernel-ppa/mainline/") 
#Just in case you need assistance.
Need, all.deb, headers, image of your 64 or 32 bit installed in that order.
Module-init-tools in launchpad in .deb

---

### Post by vene on 2011-08-09
> **tad1073 said:**
> I just installed 3.0.1 and nvidia 280.13 built just fine but I am using 10.10 though.

I just installed 3.0.1 and nvidia 280.13 built on natty but had to switch back my gcc from 4.5 (or 4.6) to 4.2 because otherwise i got kernel crash and black screen during boot.

dmesg of the crash in attachment for interested ones.

---

### Post by tad1073 on 2011-08-09
> **vene said:**
> I just installed 3.0.1 and nvidia 280.13 built on natty but had to switch back my gcc from 4.5 (or 4.6) to 4.2 because otherwise i got kernel crash and black screen during boot.

dmesg of the crash in attachment for interested ones.

I got the same error while building 280.13 on 3.0.0 but everything was fine after I rebooted, so when installed 3.0.1 280.13 was already there.

---

