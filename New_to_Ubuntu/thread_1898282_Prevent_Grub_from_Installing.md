---
title: "Prevent Grub from Installing"
date: 2011-12-21
forum: New to Ubuntu
---

### Post by pteri498 on 2011-12-21
I just broke my Mac Mini because Grub overwrote the bootloader and I couldn't for the life of me get back into OSX. Then I destroyed the machine with partition wizardry. I am now on a journey to recovery my Mini that will take anywhere between 1 and 108 hours. (I'm hoping the latter was an estimation fluke) (**Edit:** It was a fluke. I'm down to just over an hour. I'm 9000% better off!)

rEFIt is fine at this job on its own, so I don't need or want Grub. When I installed Ubuntu 11.10, I didn't see an option to NOT install Grub. Did I miss that checkbox or is that option actually lacking in the installer?

---

### Post by heyandy889 on 2011-12-21
Ah, that stinks, dude. 

Well . . . one complicating factor might be that Macs use the Extended Firmware Interface (EFI) to boot up, where Windows and Ubuntu (I think) use the Basic In-Out System (BIOS). When you turn on the computer, the BIOS runs by default. This is that splash screen you see, like, "HP! Magic!" After some Pure F-ing Magic, the BIOS calls the GRand Unified Bootloader (GRUB).

So, I don't know how EFI plays into this whole bit.

I know that you can run Ubuntu with Windows without GRUB. (Might be WUBI install?) Instead, you use the Windows bootloader.

No answer here. Just my experience on the matter. Good luck, pteri498!

---

### Post by ajgreeny on 2011-12-21
I am also not sure about doing this in a mac machine, but in windows with a BIOS system, you would need to put the bootloader files on to the ubuntu partition, not onto the root of the disk, is grub onto /dev/sda2, not /dev/sda.  I do not think you can stop grub being installed completely, but putting it on the partition means in a windows machine it will not be used at boot time.

There is a chance to choose where it should be installed, but only if you choose the "Something else" option at disk preparation stage, if I remember correctly.

I presume things will be the same in mac systems as far as this choice is concerned, but I've never used a mac, so treat this answer with a degree of caution.

---

### Post by pteri498 on 2011-12-21
Funny story, I installed Xubuntu first and it didn't overtake the rEFIt bootloader. In fact, it just loaded Grub after I selected the Ubuntu partition from rEFIt.

Then I try to experiment and install Ubuntu, and rEFIt goes away.

---

