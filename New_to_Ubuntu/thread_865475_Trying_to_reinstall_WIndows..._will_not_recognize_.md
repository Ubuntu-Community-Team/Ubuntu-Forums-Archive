---
title: "Trying to reinstall WIndows... will not recognize hard drive?"
date: 2008-07-20
forum: New to Ubuntu
---

### Post by Lilibette on 2008-07-20
Hello all, I'm ready to go back to Windows because for the life of me, I can NOT get my wireless to work on this laptop (Gateway ML6720 + Realtek 8187b driver).  Amongst other reasons.  Blah blah blah.

I have my Windows disk, I have the Gparted disk, I have it all.  But no matter what I do, Windows tells me it can not find my hard drive.  When I put GParted in, it shows me my drives just fine.

I'm typing now from the laptop in question, and all I want is crappy ol' Windows back so that I can get back online and away from this plug-in internet.  It was fun while it lasted, but it's too much upkeep for me.

That being said, yes, I installed Ubuntu OVER the old Windows, so I'm aware that it is not there anymore, and yes, I've deleted partitions and formatted, but no matter what I do, when I go to install Windows, it just tells me it can not find my hard drive(s).

What do I do!? :confused: :mad:

---

### Post by flytripper on 2008-07-20
what type of hdd is it? pata or sata?

---

### Post by Lilibette on 2008-07-20
> **flytripper said:**
> what Type Of Hdd Is It? Pata Or Sata?

Sata

---

### Post by flytripper on 2008-07-20
you will prolly need the driver for the disk as xp was before sata drives came out. download it and when you restart the install,hit f6

(i think. it will tell you which f button) when it says so along the bottom of the blue screen. you should then be able to proceed. I could be wrong but i think it needs to be put on a floppy disk

---

### Post by dhughes on 2008-07-20
> **Lilibette said:**
> Hello all, I'm ready to go back to Windows because for the life of me, I can NOT get my wireless to work on this laptop (Gateway ML6720 + Realtek 8187b driver).  Amongst other reasons.  Blah blah blah.

I have my Windows disk, I have the Gparted disk, I have it all.  But no matter what I do, Windows tells me it can not find my hard drive.  When I put GParted in, it shows me my drives just fine.

I'm typing now from the laptop in question, and all I want is crappy ol' Windows back so that I can get back online and away from this plug-in internet.  It was fun while it lasted, but it's too much upkeep for me.

That being said, yes, I installed Ubuntu OVER the old Windows, so I'm aware that it is not there anymore, and yes, I've deleted partitions and formatted, but no matter what I do, when I go to install Windows, it just tells me it can not find my hard drive(s).

What do I do!? :confused: :mad:

 I think it's GRUB interfering, you need to restore the Master Boot Record (MBR) if you put in a Windows install disk and can get to a command prompt try: fdisk /mbr

 You could also try Darik's Boot and Nuke (DBAN) should wipe the MBR, I doubt you have to let it go any more than a ten minutes or so I'd say the MBR is wiped in the first few minutes. [http://dban.sourceforge.net/](http://dban.sourceforge.net/)


**EDIT**: Oh and there's Microsoft's support page on how to remove Linux: [http://support.microsoft.com/kb/314458](http://support.microsoft.com/kb/314458)

---

### Post by flytripper on 2008-07-20
that too , possibly 

also > perhaps. try the "repair from recovery console" option on the xp bootdisk and if it picks up the drive type fix mbr or fixmbr (cant remember).if this doesnt work i have found that the windows 98 boot disk and the fdisk command will enable you delete the partitions and rebuild some semblance of a readable partition for your xp install. alternatively you could run a program call activekilldisk (normally from a floppy or ahem.... hirens bootcd ....ahem.)to wipe the drive completely and restart the installation from there.. hope this helps

---

### Post by bobbob1016 on 2008-07-20
Is the Windows disc you have the original one for that computer?  It might need a driver if there is a special card for the SATA or something.  I think DBAN derick's boot and nuke, however it is spelled, would be best and easiest way to remove grub, not through the Windows disc.

---

### Post by brons2 on 2008-07-20
> **Lilibette said:**
> Sata

You need to use the option to install a driver at the start of windows setup by pressing F5 or F6, I forget which it is.  Windows XP will not be able to see your SATA controller otherwise.

---

### Post by dhughes on 2008-07-20
> **brons2 said:**
> You need to use the option to install a driver at the start of windows setup by pressing F5 or F6, I forget which it is.  Windows XP will not be able to see your SATA controller otherwise.

 Yeah flytripper mentioned that above but I had Grub on my brain, you're probably both right.

 Although the Grub problem may also be a problem too, it could be both.

---

### Post by Xerp on 2008-07-20
Yes, the native Microsoft Windows XP media doesn't support SATA drives or large drives (> 130 GB). You'll need Windows XP SP2+ for drives > 130GB, and a manufacturer's floppy for SATA drives.

---

### Post by brons2 on 2008-07-20
Speaking of, there are tools to slipstream the SP2 files into an ISO, if you're so inclined towards putting in the extra work.  For that matter, you could slipstream the SATA drivers into it as well.  The XP CD is not close to full, unlike Vista's massive install files.

---

### Post by Vorian Grey on 2008-07-20
> **Lilibette said:**
> 
That being said, yes, I installed Ubuntu OVER the old Windows, so I'm aware that it is not there anymore, and yes, I've deleted partitions and formatted, but no matter what I do, when I go to install Windows, it just tells me it can not find my hard drive(s).


Did you format as NTFS?

---

