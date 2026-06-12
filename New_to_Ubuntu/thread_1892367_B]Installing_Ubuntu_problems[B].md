---
title: "B]Installing Ubuntu problems[/B]"
date: 2011-12-07
forum: New to Ubuntu
---

### Post by barrykgerdes on 2011-12-07
**Installing Ubuntu problems**

Up until three weeks ago I had a successful instalation of 10.4 on a dual boot Intel pentium 3 based computer. with the default boot set to Windows XP. This computer failed and I had to initiate a new one. 

The replacement is a AMD pentium 4 dualcore platform with a nvidia video system. I tried to reinstall 10.04 into the old partition space but none of my 3 disks of 10.04 work on the new platform. They appear to boot but nothing seems to work.  I next tried 11.10 from a boot disk. This worked great and I got a Ubuntu 11.10 system operating. However the default operating system is Ubuntu and I could not change it to Windows which is necessary for the remote switch on for the computer as a server.

I eventually found and compiled the grub configuring program and installed it. This appeared to work and the first time I used it. Windows loaded OK from turn on. However after shutting down and attempting a restart Windows would no longer boot. To recover I had to use the windows install disc which of course killed the grub2 loader. 

Since then I have tried unsuccessfully to install Ubuntu as a "Wubi". I have used a separate partition rather than the windows XP boot partition. The installation appears to progress correctly for about an hour and on completion  a reboot is called for.

On reboot (to Ubuntu) the grub2 loader screen appears with the normal start or recovery start. On selecting the normal start Ubuntu appears to start and continues downloading, installing and configuring for about 30 mins. When this completes a reboot is called and the same grub2 screen and options. This time there is an error because the kernel is not found and nothing further happens and the only recovery is ctrl/alt/del

If I select recovery mode I get a lot of screen text activity which eventually ends with the Ubuntu (terminal) prompt. At this prompt I am able to operate ubuntu as a command line program.
What have I done wrong?   

Barry

---

### Post by critin on 2011-12-07
> Since then I have tried unsuccessfully to install Ubuntu as a "Wubi". I  have used a separate partition rather than the windows XP boot  partition.Interesting--I didn't know this could be done.  :)

> I got a Ubuntu 11.10 system operating. However the default operating  system is Ubuntu and I could not change it to Windows which is necessary  for the remote switch on for the computer as a server.Sometimes  Windows needs a little extra encouragement to boot with another os--Did you try -----   sudo update-grub      after installing and before restarting?  It doesn't hurt to make doubly sure grub is available for both os's before restarting.

Oh- sorry.  You meant you wanted Windows to be default, install Grub Customizer from Software center.  In preferences you can allocate which system to boot first.  Be sure to SAVE before closing.
> 
To recover I had to use the windows install disc which of course killed the grub2 loader. At this point, I believe you could boot from live ubuntu and run ---  sudo update-grub or use the Boot-Repair tool that is on the disk to get both os's running again.

---

### Post by barrykgerdes on 2011-12-08
Hi

The separate partition may be the problem. That was something I wanted confirmation of. I will try to install in the same partion.

Yes the grub customizer should be the way to set the default boot. I did build it and it apparently worked because the next time I ran the computer Windows was the default boot and it booted OK. I then rebooted and ran Ubuntu (OK). However the next time I tried to start the computer I could nolonger run Windows  It would not get past the start screen before crahing to a reboot.

I had to repair windows from the start up disc and then of course lost the grub loader.

I will try to load Ubuntu in the Wubi manner in the same folder as windows.

Thanks for the reply

Barry

---

### Post by mastablasta on 2011-12-08
you can't (shouldn't) update grub if you use wubi.

---

### Post by barrykgerdes on 2011-12-08
> **mastablasta said:**
> you can't (shouldn't) update grub if you use wubi.

The use of grub-customize was not refering to a Wubi installation. That was for the full separate installation that eventually crashed windows.

I have now installed a Wubi installation on another computer that has Windows XP on the primary partition
This appears to work correctly. Apparently a Wubi installation needs to be done on a Windows installation that is on the primary partition (C:)

---

