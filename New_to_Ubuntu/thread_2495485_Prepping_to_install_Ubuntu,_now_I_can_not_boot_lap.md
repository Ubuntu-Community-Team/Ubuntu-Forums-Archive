---
title: "Prepping to install Ubuntu, now I can not boot laptop ..."
date: 2024-02-20
forum: New to Ubuntu
---

### Post by cwmoser on 2024-02-20
Got a used Lenovo T470s laptop off Ebay.
It contained Windows 10, and I went and resized the Windows partition using the Windows utility.
Now I cannot boot Windows 10, nor my Ubuntu 22.04 thumb drive, nor can I get into the BIOS.

Is there a way I can recover this mess?  I don't give a hoot about Windows 10 and would prefer the hard drive to be all Ubuntu.
My Hard Drive is a 512GB Nme drive.
The PC was working OK before I started messing with it.

Appreciate any ideas so I can recover and get get Ubuntu installed.

---

### Post by cwmoser on 2024-02-20
I found the solution:
"Hold down the power button for 10-15 seconds to do a hard reset on your laptop or PC and reboot your computer. "
Then reboot and press F12 to enter BIOS where I enabled booting for both Legacy and UEFI.

I read that this works for both a black screen with a movable cursor and in my case a scrambled screen with a movable cursor.

---

### Post by oldfred on 2024-02-20
Microsoft Windows boots so slow that it required vendors to use UEFI with Fast Boot setting. That setting assumes no system change.
Normally system when booting checks system for what hardware you currently have. That only takes a few seconds, now particularly with fast SSDs.
So when making changes to system, make sure Fast boot is off in UEFI settings.

Windows also has a fast start up setting. That sets a hibernation flag & uses a small hibernation file to also speed boot.
And back when systems were HDD, Microsoft required small SSDs just for the hibernation file to speed boot. 

Ubuntu still booted faster than Windows with its kluges to try to be faster.

I now have NVMe drive and use Kubuntu which is a bit more lightweight than Ubuntu. And a bit of tuning to turn off some settings I do not need.
```
[FONT=monospace][COLOR=#54ff54]**fred@Z170-jammy**[/COLOR][COLOR=#000000]:[/COLOR][COLOR=#5454ff]**~**[/COLOR][COLOR=#000000]$ systemd-analyze [/COLOR]
Startup finished in 4.017s (kernel) + 5.833s (userspace) = 9.851s  
graphical.target reached after 5.805s in userspace
[/FONT]
```

Or system is functional in 6 sec.
I think that is from a warm reboot.
But a full shutdown & total reboot is about 20 sec.

---

