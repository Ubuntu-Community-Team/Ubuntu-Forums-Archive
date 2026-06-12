---
title: "Uninstall Linux"
date: 2008-08-31
forum: New to Ubuntu
---

### Post by nemesis8601 on 2008-08-31
Hello everyone, I'd like to uninstall Feisty but I don't know how. Unfortunately, Linux isn't supported for a lot of engineering programs I use, and obtaining a Linux student version from most software companies has been almost impossible, and they charge exorbitant fees. I installed Linux last year, but I haven't had the time to learn more and really customize it. I'm disappointed that it hasn't worked out. 

In any case, I tried removing Linux from my desktop by deleting the partitions using Partition Magic in Windows, but it deleted the boot window and now my computer won't start up correctly. Is there a way I can fix this? My laptop is still dual booting and I have yet to figure out how to safely remove Linux. 

Thanks everyone for your help!

---

### Post by halitech on 2008-08-31
if you have already deleted the partition, you will need to restore your windows boot loader. Boot from your windows cd in recovery mode and when you get to the command prompt, type
```
fixmbr
```

---

### Post by Gannon8 on 2008-08-31
You will need to use the windows install CD to get back your MBR, or you can install GRUB on your windows partition.

---

### Post by sharks on 2008-08-31
boot ubuntu live cd , go to system---administration---gparted(partition editor) and selct the drive where you have installed ubuntu and format it.

---

### Post by Rocket2DMn on 2008-08-31
If you have already deleted the partitions and resized the remaining ones to fill the space, you will need to restore windows to the MBR since GRUB is gone.
If you have XP, boot from the XP disc, enter the recovery console, and run
```
fixmbr
```
If you have Vista, see here - [http://support.microsoft.com/kb/927392](http://support.microsoft.com/kb/927392) - you will want /FixMbr and /FixBoot I believe.

---

### Post by deicidist on 2008-08-31
At what point does the boot fail (or go wrong)? Are you able to see the grub screen?

---

### Post by nemesis8601 on 2008-08-31
When starting up my computer would search for the boot loader, and say it couldn't find it, then freeze on that screen. I just re-installed the Windows boot loader, and everything is fine now. Thank you!

I'll decide if I'm going to uninstall Linux on my laptop. It's a lot more fun using Linux on it since I can run all my engineering programs on my desktop. It'll be a good compromise.

---

