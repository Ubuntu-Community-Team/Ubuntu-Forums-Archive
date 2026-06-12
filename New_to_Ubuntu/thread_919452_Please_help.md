---
title: "Please help"
date: 2008-09-14
forum: New to Ubuntu
---

### Post by kevinm86 on 2008-09-14
Alright so,
today i was looking at the ubuntu website from windows vista
so i decided to download it
and i did.
so i installed it and so on, but now i want vista back but only Ubuntu starts up.
[i not that i don't like Ubuntu its very great but im a digital DJ and i use Torq and it wont run on Linux]
can anyone help me on how to get vista back?

---

### Post by NovaAesa on 2008-09-14
When you installed Ubuntu, did you install it as a duel boot setup, or did you erase Windows then install Ubuntu?

---

### Post by dRock1286 on 2008-09-14
well...did you install ubuntu over your vista partition or did you set it up to dual boot?

---

### Post by dRock1286 on 2008-09-14
> **NovaAesa said:**
> When you installed Ubuntu, did you install it as a duel boot setup, or did you erase Windows then install Ubuntu?

damn...beat me too it.

---

### Post by OutOfReach on 2008-09-14
Can you goto Applications>Accessories>Terminal and type in:
```
sudo fdisk -l
```
It will ask you for a password, type it in (but you won't be able to see it, because, well it's your password)

---

### Post by kevinm86 on 2008-09-14
Well im not too sure what dual boot means but im pretty sure i didnt erase vista. but vista won't load up
just ubuntu.



ok i typed it in and this is what it gave me:
kevin@kevin-laptop:~$ sudo fdisk -l
[sudo] password for kevin: 

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x23962a8a

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       19083   153284166   83  Linux
/dev/sda2           19084       19457     3004155    5  Extended
/dev/sda5           19084       19457     3004123+  82  Linux swap / Solaris
kevin@kevin-laptop:~$

---

### Post by btmiller on 2008-09-14
> **kevinm86 said:**
> Well im not too sure what dual boot means but im pretty sure i didnt erase vista. but vista won't load up
just ubuntu.



ok i typed it in and this is what it gave me:
kevin@kevin-laptop:~$ sudo fdisk -l
[sudo] password for kevin: 

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x23962a8a

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       19083   153284166   83  Linux
/dev/sda2           19084       19457     3004155    5  Extended
/dev/sda5           19084       19457     3004123+  82  Linux swap / Solaris
kevin@kevin-laptop:~$

Hmmm ... I don't see any Windows partitions there, just the Linux root and swap permissions. I think it's unfortunately likely that you erased your Vista and will have to reinstall it. Do you remember in the disk partitioning in the Ubuntu setup if you deleted the existing partitions? Given that this machine is a laptop, I am guessing you only have one hard drive, correct?

Just to be on the safe side, do "df -h" (no quotes). If it looks like all of the space on your hard drive is accounted for in the Linux partitions then it appears Vista is gone.

---

### Post by TeoBigusGeekus on 2008-09-14
Have you made recovery disks from vista? If so, stick 'em in and you're ok.
Otherwise...

---

### Post by OutOfReach on 2008-09-14
> **kevinm86 said:**
> Well im not too sure what dual boot means but im pretty sure i didnt erase vista. but vista won't load up
just ubuntu.



ok i typed it in and this is what it gave me:
kevin@kevin-laptop:~$ sudo fdisk -l
[sudo] password for kevin: 

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x23962a8a

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       19083   153284166   83  Linux
/dev/sda2           19084       19457     3004155    5  Extended
/dev/sda5           19084       19457     3004123+  82  Linux swap / Solaris
kevin@kevin-laptop:~$

It looks as if Ubuntu erased the entire drive, would you by any chance have a Vista recovery disk?

---

### Post by kevinm86 on 2008-09-14
actually i have a vista boot cd
but when i enter the product key located on the bottom of my laptop it says that theres a file missing, something like this "D:/???/install.wim"
something like that and theres this too "Error Code 0x80070002"

---

### Post by bumanie on 2008-09-14
You may need to use testdisk to try and recover the lost partition of vista. It can be run from the ubuntu live cd  > sudo apt-get install testdiskOnce downloaded, > sudo testdisk in terminal to run it. Try to not read/write too much to your hard drive in case you overwrite something that prevents testdisk from recovering. Here's [a walk through]("http://www.users.bigpond.net.au/hermanzone/p21.html") of how to use testdisk. Read it well, there is also a tutorial on the [testdisk site]("http://www.cgsecurity.org/wiki/TestDisk"), where you can download a testdisk specific live cd if you wish. Another alternative is to install ntfsprogs > sudo apt-get install ntfsprogs and use ntfsundelete. The data needs to be saved to s different hard drive, equal to or larger than the one where the information is being read from. Good luck.

---

### Post by TeoBigusGeekus on 2008-09-14
According to this
[http://forums.techguy.org/windows-vista/510129-pops-up-when-trying-install.html]("http://forums.techguy.org/windows-vista/510129-pops-up-when-trying-install.html")
it might be a bad burn of the dvd...
Could you find a different vista installation disk?

---

### Post by kevinm86 on 2008-09-14
would anyone of you have an idea of where to download a good .iso image?
or how to run vista on the virutalbox program?

---

### Post by Bucky Ball on 2008-09-14
[quote=kevinm86]would anyone of you have an idea of where to download a good .iso image?[/quote]

hmm ...

Is there anything in particular you really need windoze for? Just a hint that what you're suggesting is illegal and perhaps advice on where to get a good download of Windoze is not within the guidelines ... if that is what you mean of course ... :) Oh, someone just mentioned public and private domain ....

---

### Post by kevinm86 on 2008-09-14
i need windows to run torq (dj software) because it wont run on linux.

but this is really frustrating me :/

---

### Post by Bucky Ball on 2008-09-14
Now you're confusing me. Widoze and Ubuntu are two totally different beasts. Not related. Not even half cousins. You have wiped your Windoze drive. 

Installl windoze then Ubuntu. If you had any data, you have lost it, unless someone knows of any software to retrieve it. This is what I know, but if it manages to retieve Windoze, Ubuntu would have put your boot menu pretty out of whack so doubtful if it will work anyhow:

[http://trinityhome.org/Home/index.php?wpid=1&front_id=12](http://trinityhome.org/Home/index.php?wpid=1&front_id=12)

---

### Post by kevinm86 on 2008-09-14
ok, i have a vista boot/recovery cd
but  it's missing two files, the install.wim and the X13-49120.exe

---

