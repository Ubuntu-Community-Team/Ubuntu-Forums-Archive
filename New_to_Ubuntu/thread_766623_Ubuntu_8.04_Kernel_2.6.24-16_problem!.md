---
title: "Ubuntu 8.04 Kernel 2.6.24-16 problem!"
date: 2008-04-25
forum: New to Ubuntu
---

### Post by avkhatri on 2008-04-25
I'm left without an Ubuntu distro on my computer and I would really like some help :(

Ok the first part of this is my fault. I wanted to get 8.04 so I decided to use the Update Manager to do so. It took a long time and  when I had one package left it said that it lost connection or something and I had to restart the updater and resume from where it left off. Once it was done I came to the boot menu and there were three options, there was "Ubuntu 8.04 Kernel 2.6.24-16" and "Ubuntu 8.04 Kernel 2.6.24-14" (I think it was 14 it could have been 15, it was the kernel that was for 7.10) I chose "Ubuntu 8.04 Kernel 2.6.24-16" and when it was booting the orange bar was moving side to side (as though there was a live cd). 

Then after a while I get dumped to something called Busy Box it was all in console and I got a bunch of weird ATA2 errors. I didn't know what to do so I rebooted and tried "Kernel 2.6.24-16" and that one did not do the side to side scrolling of the orange bar but started at the left and kept getting more to the right like a normal hard drive boot.  The kernel 2.6.24-16 kernel booted fine but the system was really slow. I thought it was because that downloaded update screwed something up so I made a disk of 8.04 burned it and just reformatted my Ubuntu partition. After I did that the only option I had left was the 2.6.24-16 kernel and I am still having the problem with that busy box thing and Ubuntu is not loading. Does this problem have to do with my computer not being compatible with the latest Kernel? This computer is only about a year old :(.

If I could get ANY help on this it would be greatly appreciated:) I really don't want to use Windows.

---

### Post by Blastomorpha on 2008-04-25
I can't help you but, after the upgrade, for me the only way to boot fine with 8.04 it's to select the old kernel used by 7.10...

---

### Post by avkhatri on 2008-04-25
> **Blastomorpha said:**
> I can't help you but, after the upgrade, for me the only way to boot fine with 8.04 it's to select the old kernel used by 7.10...

That is exactly what I did but for some reason the 7.10 kernel was going slow so I got an 8.04 CD and thought a fresh install would fix it but it didn't

---

### Post by avkhatri on 2008-04-25
okay, now I'm getting the same error when I boot the live cd :(

---

### Post by Blastomorpha on 2008-05-01
Do you have a wifi connection?

---

### Post by aberry5555 on 2008-05-01
When you boot from the livecd do you get stuck at "start hardware abstraction layer HALD" and then, after a while, get random errors like "ata3 hot unplug, read error" etc... If so then you seem to have the same problem as me with 8.04 :S I can't boot at all from the livecd, installation option or anything. Weirdly though, when I install it from windows (on to a windows partition with wubi) I can actually get Xorg to start, but then it freezes on "checking disks".

---

