---
title: "Installed DeliLinux but it won't boot from hard drive"
date: 2008-09-13
forum: Other OS Talk
---

### Post by Laxton14 on 2008-09-13
I am trying to install DeliLinux on an old laptop with 32mb ram and 2 a gig hard drive (dont know much more about it, other than it has a pentium processor and came with windows 95)..i just installed DeliLinux with no errors any thing but when i reboot to boot from the hard drive it just stays at the BIOS screen and doesnt boot, does anyone have any ideas of what i might be able to do to get it to boot?

---

### Post by ironcitypete on 2008-09-14
I'm not familiar with Deli Linux but did you install lilo to the MBR as it mentions in the [wiki]("http://www.delilinux.org/wiki/doku.php?id=installation:cdrom").

---

### Post by zmjjmz on 2008-09-14
Did you make a swap partition before you did the install?
Use cfdisk to create a, say, 100MB partition on the drive, then use mkswap on the partition you created.

---

### Post by Laxton14 on 2008-09-14
it didnt ask me to install lilo as it does int he wiki.. it just kinda skips that part.. and yes i made a swap partition, any other ideas? (im gonna reinstall again to see if anyhting different happens, thanks for the quick responses

---

### Post by zmjjmz on 2008-09-14
> **Laxton14 said:**
> it didnt ask me to install lilo as it does int he wiki.. it just kinda skips that part.. and yes i made a swap partition, any other ideas? (im gonna reinstall again to see if anyhting different happens, thanks for the quick responses

Did you use the swap partition before install?

---

### Post by Laxton14 on 2008-09-14
The first time all i did was create a partition with cfdisk and made it a linux swap file, i didnt do the whole.. mkswap /dev/hda2, this time i did, though and im currently installing when it asks me if i wanna make a new swap, i should hit no, because i manually made one, right?

---

### Post by tdrusk on 2008-09-14
> **Laxton14 said:**
> The first time all i did was create a partition with cfdisk and made it a linux swap file, i didnt do the whole.. mkswap /dev/hda2, this time i did, though and im currently installing when it asks me if i wanna make a new swap, i should hit no, because i manually made one, right?
hit no

---

### Post by ironcitypete on 2008-09-14
> **Laxton14 said:**
> The first time all i did was create a partition with cfdisk and made it a linux swap file, i didnt do the whole.. mkswap /dev/hda2, this time i did, though and im currently installing when it asks me if i wanna make a new swap, i should hit no, because i manually made one, right?

If you manually made a swap partition and activated it you can skip that step.

---

### Post by Laxton14 on 2008-09-14
i think that not installing lilo was my problem, its finishing up the install right now (install all the extra goodies) and then i'll be able to try to boot it up for the first time (i kinda think it'll work) but anyways... thank you guys a lot for all the help.. these forums can be a life saver

---

### Post by zmjjmz on 2008-09-14
> **Laxton14 said:**
>  these forums can be a life saver

The DeLi wiki helps too.

---

