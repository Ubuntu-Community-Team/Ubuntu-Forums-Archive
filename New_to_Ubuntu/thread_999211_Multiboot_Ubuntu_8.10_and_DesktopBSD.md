---
title: "Multiboot Ubuntu 8.10 and DesktopBSD"
date: 2008-12-01
forum: New to Ubuntu
---

### Post by rhammer01 on 2008-12-01
Like everyone else in this thread, I am a beginner. I have an HP Pavilion 734n, 2Gig Intel processor, 1Gig ram, 80Gig hard drive. I have 3 partitions I made with SystemRescueCD(linux). The XP partion was made when I installed XP. Then I used SystemRescueCD to change the size to 23Gig and make 2 more partitions about the same size. I installed DesktopBSD on the 2nd partition, and Xp and DesktopBSD ran fine. I then installed Ubuntu 8.10. XP and Ubuntu then ran fine but I couldn't boot DesktopBSD. The loader showed a partition called other but would not boot when I chose that. So I loaded DesktopBSD again and the loader showed Linux but I couldn't boot to that. I can configure the loader and there is a place for Kernel and intrid. I suppose there is a command line or string I can enter to allow me to boot Ubuntu but, I don't know what it is. Maybe I need more than that, but any help will be appreciated. Thanks!

---

### Post by kk0sse54 on 2008-12-01
First off DesktopBSD and Ubuntu are both great OS's and one other thing which boot manager are you currently using? If you are using grub from Ubuntu you need to edit your menu.lst > sudo gedit /boot/grub/menu.lst and point it to where DesktopBSD is installed. If you still have the DesktopBSD bootloader installed but grub is installed to your mbr add something like this
> 
title FreeBSD
rootnoverify (hd0,0)
makeactive
chainloader +1
(this would be my entry for FreeBSD) Just replace FreeBSD with DesktopBSD and have rootnoverify point to the correct partition. Other wise if the DesktopBSD bootloader is installed in your mbr and you are looking for your Ubuntu vmlinuz and initrd they reside in your /boot folder in Ubuntu.

---

### Post by markbuntu on 2008-12-01
What I do with multiple OSs is install each with its own bootloader/grub in the same partition as the OS. Then I just add a chainloader into the grub on the first boot partition. 

This avoids all sorts of weird and nasty problems that can crop up with multiple systems and grubs which I have experienced numerous times. Plus it is really simple and easy to do.

One grub to rule them all!!!

---

### Post by rhammer01 on 2008-12-03
I used your suggestion C!oud and had it working in the time it took me to edit the file and reboot. Thanks!

---

