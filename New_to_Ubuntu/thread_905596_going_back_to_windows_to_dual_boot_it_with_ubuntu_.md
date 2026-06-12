---
title: "going back to windows to dual boot it with ubuntu help"
date: 2008-08-30
forum: New to Ubuntu
---

### Post by Periswell on 2008-08-30
hi

i have had ubuntu for the last 2 years and the only thing that is bugging me is my extensive game collection (about 5 games) that i cannot play on ubuntu, either through wine or codeweavers crossover games. so i have now decided to go back to windows and then daul boot it with ubuntu (ubuntu being the main distro i would use) so i could play my games. but the problem is i can not install windows onto my machine. my computer has always had ubuntu (brought it with it) but when i install windows xp it say 'please load a windows 95, 98, me or nt disk'. now for some strange reason i have a windows 98 disk but when i put that in it goes wrong (can not remember how, will post it when i find out). even when i do it through wine it doesn't do a thing. please help.

-josh

---

### Post by pytheas22 on 2008-08-30
It probably won't work to try to start the Windows installation from within wine.  Try booting directly to the Windows CD instead; it will probably work.  If you don't know how to boot to a CD, look at the first or second screens that get displayed when you first turn your computer on; it should mention something like "Press XXX for boot menu."  Press the key (usually F8 or delete) and you will be given the option to boot to CD.

---

### Post by shankhs on 2008-08-30
I had the same problem while experimenting the "dual boot theory".I did the following things:

**_TRY 1._**
I had 7.04 which took all the disk space so I used gparted and freed 80 GB (I have 250GB sata hard disk) and when I tried to install windows
(a.change the boot preferences.
 b.Press any key to continue...
)
it repeatedly said windows cant be installed.

**_TRY 2._**
This time I took the whole system backup:
[http://ubuntuforums.org/showthread.php?t=35087](http://ubuntuforums.org/showthread.php?t=35087)

Then I completely formatted the hard disk and installed windows(from cd) and the then I installed ubuntu 7.04.
I tried to restore my previous ubuntu system but the GUI didnt show up.I googled and found that I have overwritten the fstab file needed for partition-info with the older one so I changed the contents of fstab (actually changed the UUID of the partitions I had) and everything was fixed.
So if you try to take backup do exclude the fstab file from the backup file.
This might be a rough way but it worked for me.

---

### Post by Periswell on 2008-08-30
i did that and it says i need to put in a win 98 or whatever disk

now it wont even start the disk when i tried it half an hour ago

-josh

---

### Post by kansasnoob on 2008-08-30
> **Periswell said:**
> hi

i have had ubuntu for the last 2 years and the only thing that is bugging me is my extensive game collection (about 5 games) that i cannot play on ubuntu, either through wine or codeweavers crossover games. so i have now decided to go back to windows and then daul boot it with ubuntu (ubuntu being the main distro i would use) so i could play my games. but the problem is i can not install windows onto my machine. my computer has always had ubuntu (brought it with it) but when i install windows xp it say 'please load a windows 95, 98, me or nt disk'. now for some strange reason i have a windows 98 disk but when i put that in it goes wrong (can not remember how, will post it when i find out). even when i do it through wine it doesn't do a thing. please help.

-josh

Exactly what are you doing? Did you resize Ubuntu first? Or are you trying to install Win XP to a separate drive?

You say dual boot so I think I can rule out VMWare or the like. Or did you entirely wipe the drive? (BTW, that's not necessary!)

I just need to know more about what you've done and what exactly you're trying to do as far as partitions, etc.

---

### Post by kansasnoob on 2008-08-30
The very first dual boot I did was on a machine that had Gutsy installed and I dual booted Win XP using this guide. It worked flawlessly but you should know exactly what drive and partition your Ubuntu boot partition is on before you start as the section regarding restoring brub may nedd some tweaking unless Ubuntu is on sda1.

Actually I shouldn't say "flawlessly" as I did find that some older Win software was "keyed" to install only to Drive C, and since Windows is getting installed second it'll likely end up as drive E or F depending on how the Win installer reads other drives, ie: cdrom, cdrw, etc.

Here's the guide I used:

[http://apcmag.com/how_to_dual_boot_linux_and_windows_xp_linux_installed_first.htm?page=1](http://apcmag.com/how_to_dual_boot_linux_and_windows_xp_linux_installed_first.htm?page=1)

---

### Post by Paqman on 2008-08-30
First of all, you might want to find out what version of Windows you'll need to play your games. Win98 is pretty old, most games made within the last few years won't run on it.

Then once you've got an install disk for the correct version of Windows, just repartition your drive to include a large area of free space at the start and boot into your Windows disk to install to that free space.

---

### Post by kansasnoob on 2008-08-30
Oh crap, you said:

> but when i install windows xp it say 'please load a windows 95, 98, me or nt disk

That's typical of an "upgrade" disc! I'll bet at some point someone upgraded from 98 or ME to XP and to validate reinstallation you must first have 95, 98, or ME installed on the Hard Drive.

You see there are three basic versions of Win: full retail that runs about $200.00 and has all the toys, upgrade that has all the toys but must see a previous version of win to even install ($120.00), and oem that's fairly worthless after the initial installation other than to repair the installation ($100.00).

It's the windows way of doing things!

---

