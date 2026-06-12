---
title: "Do I need swap?"
date: 2008-04-23
forum: New to Ubuntu
---

### Post by dwally89 on 2008-04-23
Hi,

I'm running Hardy, and have 2GB of RAM, and 200MB of SWAP.

1. Do I need SWAP with this amount of RAM?
2. Can having SWAP actually slow down my computer?
3. How do I get rid of SWAP? (I have GParted)

Thanks

---

### Post by Cypher on 2008-04-23
No you don't NEED to have a SWAP partition, if you have enough RAM and aren't running a crazy number of applications taking up all the avaiable memory. If you're a "regular" user, then the 200MB of SWAP you have there is most likely sufficient. You can keep an eye of the "top" output and see that the SWAP partition is almost never touched..

Having a partition defined for SWAP is that never used will have no affect on your system performance.

---

### Post by Meghnaad on 2008-04-23
Hello,

Generally it is advised on most of the websites that swap should be twice the size of your RAM

1. I've even installed linux without any swap my system never crashed.
2. [COLOR="DarkRed"][SIZE="5"]I think[/SIZE][/COLOR] swap is used to put unwanted portions of processes out of RAM
   If u r not going to run process which will require more RAM than your                system has it won't crash.
3. although i've not tried removing swap from existing system u can try to do it by booting in rescue mode use fdisk to del swap and create a new partition
make necessary changes in /etc/fstab (?)

let me know how it goes

---

### Post by Trail on 2008-04-23
3) If you REALLY need to get rid of it, it should go like this (haven't ever tried myself, though)

Open up a terminal and type
```

sudo swapoff -a

```

This should disable swapping. Then with gparted, remove the partition. It should adjust your /etc/fstab file automatically, but if you get errors reported while loading, ask for more help.

---

### Post by Trail on 2008-04-23
The "twice the RAM size" is a Windows "feature" I'd say. On Linux I pretty much never swap, unless I load Windows applications through Wine like DC++. And, to correct, the original suggestion is "twice your RAM size but no larger than 3Gb" (and to nitpick, I used to use 1.5xRAM)

The only valid reason I see for having a large swap partition is hybernate?

---

### Post by dwally89 on 2008-04-23
I never hibernate my computer, so is it OK if using GParted I turn the swap off, and then format it as ext3?

---

### Post by Cypher on 2008-04-23
The "Twice the RAM" language is a little old, it came from the days when people has 32/64MB of RAM on their PCs. I think we're way beyond the need to   devote 4Gigs of HD space to SWAP on a PC with 2Gigs of RAM..

If you're really hurting for that 200MB of space, by all means disable the swap, remove the entry from the /etc/fstab file and reformat it as EXT3. But if you have a 150+ Gig HD, then the 200MB devoted to SWAP can't be all that bad..

---

### Post by skymera on 2008-04-23
i have a 2GB parititon for SWAP and i have NEVER used any of it.
vm.swappiness=0 you see.

I keep it there just in case.
But i doubt Ubuntu will ever need swap again, since most newer machnies come with 1GB -2GB standard system memroy.

---

### Post by dwally89 on 2008-04-23
Thanks

---

### Post by FiOth on 2008-09-10
In that case since I have 8GB I'd never need swap right?

---

### Post by GepettoBR on 2008-09-10
> **FiOth said:**
> In that case since I have 8GB I'd never need swap right?

Unless you're doing something really heavy (like, say, running the Adobe Premiere NLVE in a Virtual Machine) I can't imageie when a x64 system with 8GB of RAM would ever need swapping.

Do keep in mind that if you don't have a 64-bit processor and OS, the computer will only recognize up to a maximum of 4GB of RAM (this is not an issue with Linux itself, rather with how 32-bit data handling works. Any 32-bit Os will suffer the same limits).

---

### Post by FiOth on 2008-09-11
I know my friend, that's the whole reason I decided to use the horrific Vista OS.My system is 64-bit but the process of installing Ubuntu as a dual boot troubles me...I wouldn't like to ruin my main installation.

---

### Post by GepettoBR on 2008-09-11
> **FiOth said:**
> I know my friend, that's the whole reason I decided to use the horrific Vista OS.My system is 64-bit but the process of installing Ubuntu as a dual boot troubles me...I wouldn't like to ruin my main installation.

I can guarantee it won't harm your main installation. The only thing that could go wrong is if you resized the Vista partition, and even then it's a maybe. If you don't do anything to it, the Ubuntu 64-bit installer will take care of preserving your Windows setup and adding an entry to the bootloader for you, no need to worry. I speak from personal experience.

---

