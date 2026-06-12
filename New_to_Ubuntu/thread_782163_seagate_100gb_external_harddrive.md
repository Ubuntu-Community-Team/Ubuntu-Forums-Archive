---
title: "seagate 100gb external harddrive"
date: 2008-05-04
forum: New to Ubuntu
---

### Post by gameryoshi600 on 2008-05-04
my seagate 100GB external harddrive does not work w/ ubuntu. the light goes on but the icon on the desktop or computer section does not appear... help please

---

### Post by gniltaws on 2008-05-04
Did you use the drive with windows before?
I have noticed that when a drive has not been removed properly, it prevents ubuntu from mounting it.  Try plugging it into a windows machine, and then clicking the "Safely Remove Hardware" icon in the system tray. Then plug the drive back in.

---

### Post by slibuntu on 2008-05-04
I've had similar trouble with my seagate drive, and as such have had to manually mount it - try running the command 
```

sudo mount -t vfat /dev/sdb1 /media/sdb1

```

It may work, if it doesn't, post the output here. 

Also, when you connect the drive, type the command dmesg into the terminal, and if there is anything in the output relating to the drive, post it here.

-------
-Shane-

---

### Post by gameryoshi600 on 2008-05-04
oh yes its a used one (my dad used it) its been used on a windows machine. i'll do that on my bros

---

### Post by gameryoshi600 on 2008-05-04
slibuntu the command didn't do a thing.
gniltaws please be more specific. i plugged it into a vista machine then clicked saftely remove hardware unplugged then plugged back in my ubuntu machine it does not show up.

---

### Post by slibuntu on 2008-05-04
Usually after running the command, the drive pops up on the desktop, or in the list of filesystems.

If your drives are labelled hda1 hda2 etc, change the command from sdb1 to hdb1. 

Any output if you run dmesg after the drive is plugged in?

---

### Post by gameryoshi600 on 2008-05-04
edit: sorry lol i had to plug the drive in now lets try em
edit2: i plugged it in it still doesn't work

---

### Post by slibuntu on 2008-05-04
.

---

### Post by slibuntu on 2008-05-04
When I posted about this problem, I was pointed to here, it wasn't really a fix for my problem, but it might work for you! [http://ubuntuforums.org/showthread.php?t=629865](http://ubuntuforums.org/showthread.php?t=629865)
It seems there is a problem with the drive being FAT32

---

