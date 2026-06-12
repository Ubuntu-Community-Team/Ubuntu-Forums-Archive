---
title: "Boot options grub?"
date: 2012-06-11
forum: New to Ubuntu
---

### Post by BuzzStPoint on 2012-06-11
Combining 2 pcs. 

I had one pc that was a Windows/Lubuntu dual boot.
This PC has crapped out and I got another one. 
Installed Lubuntu as a sole OS. 
Working good. 

I pulled the HD out of PC1 and put it into my current PC.
Now it doesn't boot to my Lubuntu (sole) anymore. It displays grub with the windows/linux options. 

How can I wipe that out and just have my Sole Lubuntu on PC2 working?

---

### Post by wilee-nilee on 2012-06-11
> **BuzzStPoint said:**
> Combining 2 pcs. 

I had one pc that was a Windows/Lubuntu dual boot.
This PC has crapped out and I got another one. 
Installed Lubuntu as a sole OS. 
Working good. 

I pulled the HD out of PC1 and put it into my current PC.
Now it doesn't boot to my Lubuntu (sole) anymore. It displays grub with the windows/linux options. 

How can I wipe that out and just have my Sole Lubuntu on PC2 working?

Grub may not be your problem, I would suspect the hardware is, different hardware different drivers.

If you could simplify your description as to which is which computer and explain exactly what happens on the one you want to run with the secondary HD it might help.

It may be as simple as the bios setting on the HD being read first you do not say if the computer you want to run is reading two HD's.

---

### Post by BuzzStPoint on 2012-06-11
Don't I feel silly.......

Never even thought of changing the BIOS. 
Moved my HD0 up above the HD1 and I have the correct Linux booting... 

Thanks...

---

### Post by drs305 on 2012-06-11
Change the BIOS to boot the original drive, which now may be sdb rather than sda. If you aren't sure, check the drive sizes in BIOS and select the one with the original drive's size.

Once you boot into your desired OS, you can install Grub to both drives (if you want to) so that no matter which one boots first it will take you to your current OS.```

sudo grub-install /dev/sda
sudo grub-install /dev/sdb
```

---

