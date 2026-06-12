---
title: "During Installation, the Dual Boot Option is Missing"
date: 2023-03-28
forum: New to Ubuntu
---

### Post by punishedchumbucket6000 on 2023-03-28
Hello, 

When I try to install Ubuntu 22.04 on my HP Windows 10 computer the Install Ubuntu alongside Windows 10 is not present. I am installing it with a bootable USB flashdrive.

After research, I made sure secure boot is off and double checked that the boot order was correct. 
I get up to the point in the installation where I only get two options:
-Erase Disk and Install Ubuntu (don't wanna do that!)
-Something else (create or resize partitions) 

In all the tutorials I watched, there was an initial option present where it allows for dual boot alongside Windows. I also heard that HP are not Linux friendly so I might need a workaround. 

Is there anything I am missing that will make the Install Ubuntu alongside Windows 10 option show up?  

Thanks for your help!

---

### Post by Impavidus on 2023-03-28
If you have to resize your partitions, do it using Windows tools. Allow Windows to perform some disk checks, or Ubuntu won't read the Windows partitions. Just reboot Windows a few times and it should run the checks. Make sure FastStartup is switched off. With that option on, Windows doesn't cleanly unmount the filesystem; it's a kind of hibernation. In that state, Ubuntu can't read the Windows partition. Sometimes, Windows switches that setting back on automatically during upgrades.

Ubuntu should work with secure boot enabled, but may require some workarounds.

---

### Post by punishedchumbucket6000 on 2023-04-02
Impavidus, 

Thank you so much for help.  I finally got the chance to implement all those steps and I am commenting right now in Ubuntu.  I think mainly what I had to do is create a 20 GB partition that was not allocated.

---

