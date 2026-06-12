---
title: "Not boot after power down by a cat"
date: 2023-07-24
forum: New to Ubuntu
---

### Post by stakano on 2023-07-24
I need help to repair booting.

What happen:
Cat press power button 5 sec and forced power off.
After the happening, PC does not boot.

What message shown on screen:
hub 8-0:1.0: config failed, hub doesn&#8217;t have any ports! (err -19)
/dev/nvme0np2: clean, xxx/yyy files, aaa/bbb blocks
nouveau 0000:01:00.0: unknown chipset (19300a1)

What I did:
>1st trial
1) Enter recovery mode from GRUB menue
2) root terminal and install boot-repair
3) resume and login (maybe ram disk env) with my account
4) run boot-repair and did standard repair
5) reboot -> not boot(same message)

>2nd trial
1) Enter recovery mode from GRUB menue (same as 1st trial)
2) update bootloader
3) reboot -> not boot(same message)

>3rd trial
1) Enter recovery mode from GRUB menue(same as 1st trial)
2) update bootloader
3) resume and login(same as 1st trial)
4) run boot-repair with default option
5) reboot -> not boot(same message)
[https://paste.ubuntu.com/p/CcsY9dG8Gn/](https://paste.ubuntu.com/p/CcsY9dG8Gn/)

Regards,
stakano

---

### Post by Impavidus on 2023-07-25
That you can boot in recovery mode indicates that your boot loader is fine (so nothing for boot repair to fix). You can even log in in recovery mode, so most of your system is fine. What's different in recovery mode is that you use an open source graphics driver, so I suspect the problem is there. Maybe your cat rebooted right when the computer was installing an update for the graphics driver. Try reinstalling the driver. Sorry, I don't use a proprietary one, so I don't know the details.

---

### Post by tea for one on 2023-07-25
> **stakano said:**
> 
Cat press power button 5 sec and forced power off.
After the happening, PC does not boot
Eons ago, there used to be a repair command for such feline events but it was removed after criticism from Puppy Linux users.
```
cat poweron -use -same -paw
```

In the meantime, you have two drives attached (lines 97 - 98), which are not completely recognised and may be the obstacle to a clean boot.
Can you remove them (also any other attached peripheral devices) and reboot?

---

### Post by stakano on 2023-07-25
> **Impavidus said:**
> That you can boot in recovery mode indicates that your boot loader is fine (so nothing for boot repair to fix). You can even log in in recovery mode, so most of your system is fine. What's different in recovery mode is that you use an open source graphics driver, so I suspect the problem is there. Maybe your cat rebooted right when the computer was installing an update for the graphics driver. Try reinstalling the driver. Sorry, I don't use a proprietary one, so I don't know the details.

Hi, thank you very much for you advice, I installed recent graphics driver then booting is done.
Maybe the cat (Nyanta) notified me the updating :).

Best,
stakano

---

### Post by stakano on 2023-07-25
> **tea for one said:**
> In the meantime, you have two drives attached (lines 97 - 98), which are not completely recognised and may be the obstacle to a clean boot.
Can you remove them (also any other attached peripheral devices) and reboot?

Yes, the drives are recognized by BIOS but not used, I will mount them, thank you.

Best,
stakano

---

### Post by MAFoElffen on 2023-07-25
The SATA drives can stay, and be further prepped and installed... I see those 8TB drives as not even having partition tables written to them yet... with no partitions, nor any filesystem.  After that, they could be added to the fstab and mounted. Right now, they are just 'there'.

I id see some stray artifacts in the report, which might lead me to suggest that you might want to do a fsck o your NVMe drive to insure you do not have a filesystem error from the sudden unplanned poweroff condition.

Just an observation.

---

