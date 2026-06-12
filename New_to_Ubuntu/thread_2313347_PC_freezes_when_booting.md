---
title: "PC freezes when booting"
date: 2016-02-11
forum: New to Ubuntu
---

### Post by azerty0wxcvbn on 2016-02-11
Tried booting from USB and DVD, no difference. GRUB menu loads, i get 4 options: try, install, OEM install and check files or something, all 4 give me a bunch of errors, and then the PC freezes as the image shows

Help [SIZE=3][FONT=Microsoft Sans Serif]:[/FONT][/SIZE][FONT=Microsoft Sans Serif][COLOR=#000000](

Edit: i should add that i have not managed to install it yet
[/COLOR][/FONT]

---

### Post by ajgreeny on 2016-02-11
Have you checked the md5sum of the iso file you used?
[https://help.ubuntu.com/community/UbuntuHashes](https://help.ubuntu.com/community/UbuntuHashes)

---

### Post by Vladlenin5000 on 2016-02-11
Also please identify what machine are you trying to install.

---

### Post by azerty0wxcvbn on 2016-02-12
> **ajgreeny said:**
> Have you checked the md5sum of the iso file you used?
[https://help.ubuntu.com/community/UbuntuHashes](https://help.ubuntu.com/community/UbuntuHashes)
The file is good

> **Vladlenin5000 said:**
> Also please identify what machine are you trying to install.
Custom built desktop, what do you need to know in particular?

---

### Post by leunam12 on 2016-02-12
Try to boot with the hard drives disconnected from the SATA port. It it boots, shutdown and connect the drive to a different port and see what happens

---

### Post by Vladlenin5000 on 2016-02-12
> **azerty0wxcvbn said:**
> Custom built desktop, what do you need to know in particular?

The hardware specs, obviously. A known brand/model would be enough in most cases but in your some more details are useful because it can be something hardware related, something which require specific tweaks, etc.

---

### Post by azerty0wxcvbn on 2016-02-13
MSI Z87 MPOWER MAX (MS-7815)
Intel i7-4770
Disk 1: 120GB ADATA SP900 (Windows 8)
Disk 2: 2TB Toshiba DT01ACA200, (2 partitions; Windows 7, and hopefully Ubuntu)
Disk 3: 1TB WDC WD10EAVS-00D7B1 (used to be an external drive)

---

### Post by azerty0wxcvbn on 2016-02-13
> **leunam12 said:**
> Try to boot with the hard drives disconnected from the SATA port. If it boots...
Sadly it ends here
Same thing, but with a different error
[ATTACH=CONFIG]267282[/ATTACH]

---

### Post by sandyd on 2016-02-13
Have you tried unplugging the CD/DVD drive as well?

---

### Post by leunam12 on 2016-02-15
Bad RAM maybe. Looks like a hardware issue. Can you boot another operating system (Parted Magic, Clonezilla, Puppy, Windows...)?

---

### Post by Geoffrey_Arndt on 2016-02-15
What trips up about 2/3'rds of Ubuntu installs are incompatible gpu/video chipsets . . that require proprietary drivers up-front.   Lighter versions of Ubuntu (e.g., Xubuntu, Lubuntu) are not as particular.     Other times, it's things like dynamic partitioing, etc. 

Might be worth a try, as Leunam12 suggests to burn a Xubuntu iso and see if it will load.   If you have optical media drives, might also try a dvd.

---

