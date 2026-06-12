---
title: "Ubuntu wont start after installing"
date: 2008-08-06
forum: New to Ubuntu
---

### Post by idodos on 2008-08-06
After installing Ubuntu to an empty hard drive i just get a black screen with a flashing cursor.
I tried to reinstall it for a couple of times but the result is the same, I don't get any error at all.
I installed Ubuntu to a 500gb hard drive giving 80gb to an ext3 partition and 2gb to swap.

Any help will be appreciated, thanks in advance.

---

### Post by idodos on 2008-08-06
Bump..

---

### Post by ibizatunes on 2008-08-06
Im not a expert, have u checked the CD for defects? What specs are your PC
How much ram do u have?

---

### Post by idodos on 2008-08-06
Inter(R) Pentium(R) 4 CPU 3.00GHz (2 CPUs)
1gb of ram
NVIDIA  GeForce 7600 GS

I did not check the CD for defects but i just downloaded ubuntu again and i will attempt to use another cd to install it.

---

### Post by ringorgoneHHO on 2008-08-06
I had the same problem with Ubuntu 7.10 on a seperate partition with XP. 
When starting XP it sometimes wouldn't start but only went to a blank screen and after a while rebooted my pc. Ubuntu only got to a black screen with white writing and a flashing cursor waiting for my user name and password. When I typed it in it would not accept it. So I scrapped XP. Now that I installed Ubuntu on the drive on its own with no operating system chooser It does not do it anymore. I guess Ubuntu runs better on its own. However you didn't say if it was on a partition with Windows or on its own.
Ringo

---

### Post by Megatog615 on 2008-08-06
What video card are you using?

---

### Post by idodos on 2008-08-06
well I installed ubuntu to an empty hard drive, not the same hard drive as windows xp.
and when i get the black screen it's just with a flashign cursor at the top left and it doesn't ask for a user name and password..

edit:
I'm using WinFast A7600 GS TDH

---

### Post by Megatog615 on 2008-08-06
Ok, it sounds like it's not even able to start X. Try using the recovery mode and try some of the options there. If all else fails try the root console mode in the recovery menu. If you can get to the root console, try doing this:
```
apt-get install nvidia-glx-new
```
Various NVIDIA cards have issues with getting the console to work under certain conditions(which is why you get the blinking cursor in the top-left corner). Recovery mode should work just fine, however.

If you can get the proprietary driver installed with nvidia-glx-new, you might be able to get it up and running. Make sure you change the driver in your /etc/X11/xorg.conf to nvidia to enable it after installing it.

You can exit recovery mode with ctrl-alt-delete.

---

### Post by prshah on 2008-08-06
> **idodos said:**
> After installing Ubuntu to an empty hard drive i just get a black screen with a flashing cursor.

Boot off a live CD, and check if your "/" or "/boot" (if you have one) partition is activated for booting; open a terminal (Applications-Accessories-Terminal) then give the command ```
sudo fdisk -l
``` and check if there is a "*" next to the any partition (should be /dev/sda1 in your case). If there isn't post back on how to activate it. In any case, post the output for further troubleshooting.

---

### Post by idodos on 2008-08-06
Device Boot      Start         End      Blocks   Id  System
/dev/sdc1           51076       60801    78124095   83  Linux
/dev/sdc2           50833       51075     1951897+  82  Linux swap / Solaris

this is what i get.
so um i guess it's not activated?

---

### Post by prshah on 2008-08-06
> **idodos said:**
> Device Boot      Start         End      Blocks   Id  System
/dev/sdc1           51076       60801    78124095   83  Linux
/dev/sdc2           50833       51075     1951897+  82  Linux swap / Solaris
so um i guess it's not activated?

If /dev/sdc1 is your boot partition (where grub is installed) then yes, it's not activated. If you have any other drives, you need to post the entire output of the fdisk command.

Here's what you need to do to activate /dev/sdc1```

sudo fdisk /dev/sdc
a
1
w
q

```

That's:

a(ctivate)
1(partition number one)
(w)write changes
(q)quit

---

### Post by idodos on 2008-08-06
> **prshah said:**
> If /dev/sdc1 is your boot partition (where grub is installed) then yes, it's not activated. If you have any other drives, you need to post the entire output of the fdisk command.

Here's what you need to do to activate /dev/sdc1```

sudo fdisk /dev/sdc
a
1
w
q

```

That's:

a(ctivate)
1(partition number 1)
(w)write changes
(q)quit


i haven't completely understood what i need to do, could you give me a more detailed explanation?
thanks in advance.

edit:
the entire output:

Disk /dev/sda: 60.0 GB, 60022480896 bytes
255 heads, 63 sectors/track, 7297 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x9e9f1df8

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        3264    26218048+   7  HPFS/NTFS
/dev/sda2            3265        7296    32387040    f  W95 Ext'd (LBA)
/dev/sda5            3265        5875    20972826    7  HPFS/NTFS
/dev/sda6            5876        7296    11414151    7  HPFS/NTFS

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xcc45cc45

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        3825    30724281    7  HPFS/NTFS
/dev/sdb2            3826        7650    30724312+   f  W95 Ext'd (LBA)
/dev/sdb3            7651       11475    30724312+   7  HPFS/NTFS
/dev/sdb4           11476       19457    64115415    7  HPFS/NTFS
/dev/sdb5            3826        7650    30724281    7  HPFS/NTFS

Disk /dev/sdc: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0000317a

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1           51076       60801    78124095   83  Linux
/dev/sdc2           50833       51075     1951897+  82  Linux swap / Solaris

---

### Post by prshah on 2008-08-06
> **idodos said:**
> 
the entire output:
   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        3264    26218048+   7  HPFS/NTFS


OK you do not need to activate anything in sdc, unless you have set your BIOS to boot off that particular disk. 

If you have set your BIOS options to boot off the third disk, set it back to boot off your 1st disk; do you then get a GRUB screen? (White on black, with a number of options listed).

If you do not get GRUB options, but it boots successfully into Windows, then you must have installed GRUB on your third drive. 

In that case, you need to activate sdc1. To activate sdc1, first, boot from the live CD (the CD you used to install ubuntu). Then open a terminal (Applications-Accessories-Terminal) and give the command ```
sudo fdisk /dev/sdc
```, then you will be taken to the fdisk program prompt that looks like ```
Command (m for help): 
```. In that prompt, type "a" press enter; it will ask for partition number, press "1" (number one) and press enter; then press "w"+enter (write changes), and when back at the prompt, press "q"+enter, that will drop you back to the command prompt. Now reboot.

Activating a partition will not cause any harm to the data and/or partition.

Note that there is a lot of guesswork here because I'm not quite sure how you have installed ubuntu. A detailed description of that, and your current setup, might be required, if you still face problems.

---

### Post by idodos on 2008-08-06
lol... apperently grub was installed to the second hard drive which i never boot from...
thanks a lot for all your time prshah.
i have one mroe question, could i move grub somehow to the first hard drive?
thanks.

---

### Post by prshah on 2008-08-06
> **idodos said:**
> could i move grub somehow to the first hard drive?

Yes, you can/could, but it will involve a lot more work; essentially;

1) Install GRUB to the first hard disk drive
2) Tell it where to locate the menu.lst file [hd(2,0)/boot/grub/menu.lst]
3) Change the menu.lst to reflect that grub is now on hd (0,0) instead of hd (2,0)
4) update-grub
5) Remove GRUB from hd (2,0) - not sure if it's required; but...

Basically it's a complicated process with the possibility of many things breaking inbetween, including, but not limited to; losing the ability to boot _any_ of your operating systems. However, you don't need to worry about losing any data. 

In short: if you're feeling adventurous and would like to take a try rather than reinstall, post back for detailed and hopefully correct but not guaranteed instructions. (Though there are many other GRUBbers and GRUBMasters who will also be glad to help out.) You will need the live CD and/or the [Super GRUB CD]("http://www.supergrubdisk.org/"). (In fact, this site contains a ton of documentation that can help you move GRUB yourself, if you like).

---

