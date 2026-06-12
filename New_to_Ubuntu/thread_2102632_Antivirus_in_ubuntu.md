---
title: "Antivirus in ubuntu"
date: 2013-01-07
forum: New to Ubuntu
---

### Post by 3sNova on 2013-01-07
hi all,
i have installed ubuntu 12.10 using wubi in windows xp. in XP i am using avast free antivirus and zone alarm free firewall. now i know we do not need antivirus for ubuntu but if i have to install it in ubuntu then does it arise problems because of 2 antiviruses(1 from xp and this 1 from ubuntu)? or my xp antivirus is enough to keep my all drives clean.
i have installed xp in c drive while ubuntu in g drive.plz comment. 
Thanks in advance.love ubuntu.

---

### Post by audiomick on 2013-01-07
I don't think it would cause problems, because, as I understand it, when Ubuntu is running, even in WUBI, then windows isn't, so  only one AV would be active at any one time. Even so, I wouldn't bother for the Ubuntu side of things. I think you can rely on the Windows AV to catch anthing that wanders over to the windows side. I have a dual boot rather than Wubi, but don't have any AV on the Ubuntu install, and I haven't had any Virus problems.

---

### Post by 3sNova on 2013-01-07
dear audiomic,thanks for quick reply..i will rely on my xp antivirus then.:p

---

### Post by siddharth007 on 2013-01-09
For Ubuntu you can use the Clamav antivirus.Its free and updates are available frequently.Plus it won't conflict with ur antivirus on xp.

To install clamav use this command
```

apt-get install clamav
```

---

### Post by puntigamer on 2013-01-09
I used Nod32 on Linux for a month (free testing), it's cool like on Windows, but I hadn't have a single issue on Ubuntu, not even a warning! There are viruses for Linux, of course, but this case you don't have to worry :)

---

### Post by mastablasta on 2013-01-09
> **3sNova said:**
> now i know we do not need antivirus for ubuntu but if i have to install it in ubuntu then does it arise problems because of 2 antiviruses(1 from xp and this 1 from ubuntu)? 

 
No becuase they are two different operating systems. antivirus on linux will mostly just scan for windows viruses as there are no unknwon viruses for linux (there are about 8 or 9 known ones and vulnerabilities they exploited have been patched)
 
> 
or my xp antivirus is enough to keep my all drives clean.
.
 
it will keep the MS format (FAT16, FAT32, NTFS) drives clean. it won't be able to scan the disk (or partition) in linux file format (e.g. EXT4).
 
clamav is free but it also doens't have good detection rate (from the tests i saw online). there are others commercial ones and a few of them are free. i think avast and avira both have linux version and these two are descent for a free product with a better detection rate than clamAV (from couple of tests i saw).

---

### Post by El Tito on 2013-01-09
I use clamav too (like siddharth007). Windows can't read the linux filesystem by default, so you would not have any problem. It is true that if you are careful, there is no need to install an AV in linux, but I found it useful to scan my windows partition from the "outside".

---

### Post by dolphin194 on 2013-01-09
I use avast! Home for Linux to scan my Windows partitions, and it works decently. That is another free for home but closed-source AntiVirus for Ubuntu (found [here]("http://www.avast.com/linux-home-edition")).

---

