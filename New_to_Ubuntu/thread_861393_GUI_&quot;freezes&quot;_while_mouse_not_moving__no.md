---
title: "GUI &quot;freezes&quot; while mouse not moving / no keypress"
date: 2008-07-16
forum: New to Ubuntu
---

### Post by StressedOne on 2008-07-16
Hey guys,

this Thread refers to [http://ubuntuforums.org/showthread.php?t=839000](http://ubuntuforums.org/showthread.php?t=839000) (posting at bottom) since i've been slapped for thinking this is a Samsung R60 Plus only problem.

I'm running Hardy Heron 8.04 with gnome. 20-50 Minutes after booting my System, everything containing GUI starts to behave quite strange.

Note that I'm talking about *everything* not just a specific program, for instance my "System Monitor" embedded in my Panel - it just freezes.

Well, nothing special, I agree, but it starts unfreezing as soon as I move my mouse / press a key.

I wonder what the problem could be, since it's pretty annoying, and it happens very random. dmesg says nothing special. Any ideas?

Thanks.

---

### Post by unutbu on 2008-07-17
Please post the output of 
```

cat /proc/cmdline
cat /proc/interrupts 
```

---

### Post by runtimecsharp on 2008-09-16
Hello!
  I'm having exactly the same problem with my Samsung R60 plus. The output of the cat requested are:

cat /proc/cmdline

root=UUID=f656ab1a-f404-46f0-94a4-ab12f6cf6998 ro single


cat /proc/interrupts

           CPU0       CPU1       
  0:     363938          0  local-APIC-edge-fasteoi   timer
  1:       2231          0   IO-APIC-edge      i8042
  8:          7          0   IO-APIC-edge      rtc
  9:        845          0   IO-APIC-fasteoi   acpi
 12:       2640          0   IO-APIC-edge      i8042
 14:       9895          0   IO-APIC-edge      libata
 15:          0          0   IO-APIC-edge      libata
 16:       1048          0   IO-APIC-fasteoi   ohci_hcd:usb1, HDA Intel
 17:         26          0   IO-APIC-fasteoi   ohci_hcd:usb2, ohci_hcd:usb4
 18:      36536          0   IO-APIC-fasteoi   ohci_hcd:usb3, ohci_hcd:usb5
 19:      17080          0   IO-APIC-fasteoi   ahci
 20:         26          0   IO-APIC-fasteoi   ehci_hcd:usb6
219:       6650          0   PCI-MSI-edge      eth0
NMI:          0          0   Non-maskable interrupts
LOC:      40458     157126   Local timer interrupts
RES:     335475     407826   Rescheduling interrupts
CAL:         85        402   function call interrupts
TLB:        465        907   TLB shootdowns
TRM:          0          0   Thermal event interrupts
SPU:          0          0   Spurious interrupts
ERR:          0
MIS:          0

Any help?

Thanks in advance!

---

### Post by unutbu on 2008-09-16
I do not know the solution for sure.

I suggest booting with the kernel option "irqpoll". 

Here is a link explaining how to boot with kernel options: [http://ubuntuforums.org/showpost.php?p=5586563&postcount=4](http://ubuntuforums.org/showpost.php?p=5586563&postcount=4).

Try the temporary method just to see if helps. If it does, the linked page has instruction on how to make the kernel option permanent. 

If "irqpoll" doesn't work, try the other boot options listed here:
[http://ubuntuforums.org/showpost.php?p=438398&postcount=1](http://ubuntuforums.org/showpost.php?p=438398&postcount=1)

Whatever you do, take notes on what options you try, so if it doesn't work you can tell us what you've tried.

I have not been able to find clear posts with solutions to this problem on the web, so if this works please post back to let us know. 

In any case, let us know how it goes.

---

### Post by runtimecsharp on 2008-09-16
Hi!
  I tried irqpoll, but unfortunately it doesn't work. It's really odd, because the desktop freezes, but after some keypress or some mouse movement it keeps working perfectly. I have checked all files at /var/log, but no error seems to appear.

Any other clues?

Thxs again!

---

### Post by unutbu on 2008-09-16
Does it only happen once in an entire session, or does it happen periodically, and if so is the timing predictable (like once every hour) or is it random?

Edit: I did a search on [https://bugs.launchpad.net/bugs/](https://bugs.launchpad.net/bugs/) for "Samsung R60" and came up with this:
[https://bugs.launchpad.net/ubuntu/+source/acpi-support/+bug/249188](https://bugs.launchpad.net/ubuntu/+source/acpi-support/+bug/249188)
It probably would be a good idea to start a conversation with developers there.

---

### Post by runtimecsharp on 2008-09-16
Hi again!
  I think it happens at random (at least, I cannot find any timing pattern). Thanks for the links! I will post the problem there as well.

  By the way, I also realized that it also occurs in Debian ([http://groups.google.se/group/linux.debian.bugs.dist/browse_thread/thread/fc187831030400de/6f647e1ad5f6134e#6f647e1ad5f6134e](http://groups.google.se/group/linux.debian.bugs.dist/browse_thread/thread/fc187831030400de/6f647e1ad5f6134e#6f647e1ad5f6134e)), so may be not a Ubuntu-specific problem but a kernel problem?

Edit: It seems that booting with the kernel option nohz=off fix this problem. No "freeze" since yesterday night. Hope it helps.

---

### Post by RodGer GR on 2009-12-21
I have the same problem using ubuntu 9.10. Adding the kernel option nohz=off stops the freezing problems but it's not a real solution; it's just a work-around. Adding nohz=off disables dynamic ticks resulting reduced power saving.

There must be another way to fix the problem.

Any ideas?

---

### Post by Objekt on 2010-01-03
I see I'm not the only one hearing about this problem.

"Hearing about" in my case, because somebody I Linux-ized a few weeks ago is now having frequent lock-ups of the type discussed in this thread.  He also has Ubuntu 9.10, with all packages updated as of 16 December 2009.  

Fortunately I did only a Wubi install, and he is savvy enough to understand how to still boot Windows XP, if desired.  I guess he's been doing that a lot lately, because XP doesn't freeze up.

I initially assumed the lockups had something to do with his failing hard drive, which Ubuntu noticed upon installation had "many bad sectors" (but which Windows had said nothing about, disturbingly!).  However, since XP is stable - at least as much as Windows ever is - I don't think that's the cause.

His machine is very old, a Dell Dimension 2350, and will soon be replaced.  I'm building the replacement, and had planned to put Ubuntu on it as well.  Now I'm having doubts.  I guess I need to hang on to it for a "burn in" period, to make sure the random lockups don't happen, or else use an older Ubuntu version.  8.04 was stable for me for a long time, on a machine almost as old as his current one.  I can use Ubuntuzilla to get him the latest version of Firefox.

---

### Post by slooksterpsv on 2010-01-04
I'd run a memory check, and also run the following as a super user in a terminal prompt:
[php]fsck -fy[/php]

---

### Post by Objekt on 2010-01-07
Replacement machine is built and I installed Ubuntu 8.04.3 LTS, 32-bit last night.  I didn't want to take the chance of some of the odd problems that have been popping up with 9.04/9.10, plus he'll get updates until, what, 2012?  Thank goodness for the LTS releases.

Only problem I'm having now is configuring the display - but there's another thread on that.

---

