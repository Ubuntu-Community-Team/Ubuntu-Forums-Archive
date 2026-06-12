---
title: "Custom kernel's initrd.img is too big."
date: 2007-09-16
forum: Packaging and Compiling Programs
---

### Post by bbruing on 2007-09-16
Hello everyone. I was hoping someone could help me figure out why my custom kernels have such large initrd.img files and modules directories?

On average, I've found that each custom kernel I compile from the vanilla sources has an initrd.img that is 6 times larger than its official kernel counterpart. For example:
```
/boot/*
408K    abi-2.6.20-15-generic
83K     config-2.6.20-15-generic
80K     config-2.6.21.5-custom
179K    grub
[B]6.7M    initrd.img-2.6.20-15-generic
40M     initrd.img-2.6.21.5-custom[/B]
12K     lost+found
94K     memtest86+.bin
794K    System.map-2.6.20-15-generic
794K    System.map-2.6.21.5-custom
1.7M    vmlinuz-2.6.20-15-generic
1.7M    vmlinuz-2.6.21.5-custom
```
... is the output from the /boot partition on one of my machines using a custom kernel. Everything is similar between the kernels **except** for the initrd.img files (and, strangely, the lack of an abi file for the custom kernel).

Also, my /lib/modules directory has a custom kernel directory that is eight times larger than its official counterpart:
```
/lib/modules/*
66M     2.6.20-15-generic
498M    2.6.21.5-custom
```

I've followed the Ubuntu-based kernel compilation How-tos available here in the forum as well as on How-to forge and elsewhere, and no one else seems to have or notice this problem. I did find one other user with the same issue, but with no response to his question: [http://ubuntuforums.org/showthread.php?t=417077]("http://ubuntuforums.org/showthread.php?t=417077")

I need a custom kernel on several machines that use new-ish nVidia ethernet adapters. Kernel 2.6.21 provided significant updates to the Forcedeth driver which seems to fix the hang-ups I've had with the official Ubuntu kernels. I also enjoy building custom kernels on my machines as it gives me more control over when I want to upgrade to a newer kernel before Ubuntu releases a new version.

Any ideas about why I'm having this trouble? Do I need to patch something in the vanilla sources? Is there a better way of doing this that would solve my troubles? Is there any other information I can provide to help figure this out?

Any response would be appreciated. Thanks in advance!

---

### Post by dwhitney67 on 2007-09-16
I can't speak much about the initrd.img, but as for the /lib/modules, I would guess that you are creating more modules than is in the generic counterpart.  The fact that your custom kernel is bigger than the generic also implies that you are probably including (within the kernel itself) more drivers.

I occasionally build kernels for a simple "PC", that has a touch-screen, HDD, network card, CD-RW drive, and my resulting kernel image is usually in the 1.3-1.4 MB range.  That size does not include the modules.

All I can surmise is that you are adding more than is necessary to your custom kernel.

---

### Post by bbruing on 2007-09-17
Thanks for the reply. I'm not sure, but I think the kernel itself is the same size, at 1.7 MB. The problem is the initial ramdisk (initrd.img) that is much larger than it should be, as well as the actual .ko files **inside** the modules directory.

For example:
```
/lib/modules/2.6.21.5-custom/kernel/net/ipv4
184K    ah4.ko
188K    esp4.ko
192K    ipcomp.ko
216K    ip_gre.ko
200K    ipip.ko
2.6M    ipvs
6.8M    netfilter
176K    tcp_probe.ko
164K    tunnel4.ko
164K    xfrm4_mode_beet.ko
160K    xfrm4_mode_transport.ko
164K    xfrm4_mode_tunnel.ko
160K    xfrm4_tunnel.ko

```

Versus...
```
/lib/modules/2.6.20-15-generic/kernel/net/ipv4
12K     ah4.ko
12K     esp4.ko
12K     ipcomp.ko
20K     ip_gre.ko
16K     ipip.ko
204K    ipvs
420K    netfilter
12K     tcp_probe.ko
8.0K    tunnel4.ko
8.0K    xfrm4_mode_beet.ko
8.0K    xfrm4_mode_transport.ko
8.0K    xfrm4_mode_tunnel.ko
8.0K    xfrm4_tunnel.ko

```

Everything is just, well, BIGGER... I'm sure it is something relatively simple, though I just can't figure it out. The other person in the link I provided above had the same issue months ago, but no one was able to help him.

I also don't think that it has to do with *more drivers*, as I used the config file from the stock Ubuntu kernel, updated only a bit for the minor kernel revision. The kernel itself, as well as the modules, all work fine.

It isn't a huge issue, though part of the reason I compile my own kernels is to make them leaner and more efficient, and these larger files seem to have done the opposite (though I see no effect on performance). What might I have done wrong?

---

### Post by bbruing on 2007-09-17
Well, you might as well ignore all that. I just got a response from the person in the other thread who had figured out the problem.
[http://ubuntuforums.org/showthread.php?t=417138]("http://ubuntuforums.org/showthread.php?t=417138")

Apparently kernel debugging gets enabled by default, for some strange reason, and I never noticed. Check out the post above for more information if anyone who stumbles upon this has the same issue.

---

### Post by Cuto on 2009-11-05
Hi!
 
I had the same problem. Looking into Internet I tried everything... and finally I fixed my problem [COLOR=red]**disabling one setting in my Bios related to "Hole memory"**[/COLOR]... and now Ubuntu 9.10 is working fine in my old Pentium II Desktop (400Mz and 256Mg RAM)... :D
 
Hope that helps...
 
Regards

---

### Post by B00Bonic41 on 2011-03-01
Hello all - I am a Linux newbie and have had the same issues as listed here - I get the error:  initrd.img is too big.   I have Ubuntu 9.10 installed on en external HDD (500 GB) and I have a Windows 7 desktop.   I choose to boot from the external HDD and then I see the GRUB loading.. menu.   Then when I choose to load the Ubuntu image - any of them listed, I get the initrd.img is too big.   I have 8 Gb of RAM installed on this machine so I am at a loss as to why this is happening.   Anyhow, can someone explain to me in laymans terms what I need to do step by step to fix this?   Any help would be greatly appreciated.
 
Thanks!!

---

