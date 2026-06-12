---
title: "windows overwrote mbr"
date: 2008-09-07
forum: New to Ubuntu
---

### Post by KeithF40 on 2008-09-07
i had ubunutu installed and then installed windows on a seperate partition, xp pro

well windows over wrote the mbr, how do i get it back so i can boot ubuntu

also is there a way to set the ubuntu mbr so that if you dont press a button it goes to windows instead of ubuntu, i just have ubuntu installed on other partition to learn it, windows is still my main os as of now

---

### Post by stevoo on 2008-09-07
Well you will need an bootable cd. From there you can fix the mbr. 

[http://www.arsgeek.com/2008/01/15/how-to-fix-your-windows-mbr-with-an-ubuntu-livecd/]("http://www.arsgeek.com/2008/01/15/how-to-fix-your-windows-mbr-with-an-ubuntu-livecd/")

In order to limit it down too not display it , you can install startup-manager and from there set the timeout to Zero.

---

### Post by KeithF40 on 2008-09-07
No I want to do it the other way around.  I am already booting into windows, I want to add ubuntu to the mbr.

---

### Post by kansasnoob on 2008-09-07
Boot up your live CD
In the desktop, open terminal (Applications -> Accessories -> Terminal). Then type (or copy-n-paste):

```
sudo grub
```

This will set it to grub mode, then:

```
find /boot/grub/stage1
```

And post the results here.

---

### Post by Rocket2DMn on 2008-09-07
I tend to recommend using the Super Grub Disk - [http://supergrubdisk.org/](http://supergrubdisk.org/)
You can also check out [uhelp]community/RecoveringUbuntuAfterInstallingWindows[/uhelp]

---

### Post by KeithF40 on 2008-09-07
grub> find /boot/grub/stage1
 (hd0,0)
 (hd0,2)

---

### Post by kansasnoob on 2008-09-07
> **KeithF40 said:**
> grub> find /boot/grub/stage1
 (hd0,0)
 (hd0,2)


Arrgh, it just had to give m,e two choices!

Go back to terminal and clear it, we don't want to be in grub now!

Then post the output of 

```
sudo fdisk -l
```

That's a lower case L not a one.

We'll probably need to know what this shows anyway so we can add windows to the menu list.

---

### Post by KeithF40 on 2008-09-07
Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x31d531d5

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        2432    19535008+  83  Linux
/dev/sda2            2433        3040     4883760   82  Linux swap / Solaris
/dev/sda3            3041        5472    19535040   83  Linux
/dev/sda4   *        5473       14593    73264432+   7  HPFS/NTFS

---

### Post by kansasnoob on 2008-09-07
I see that both sda1 and sda3 are linux partitions. Do you have more than one linux operating system installed?

---

### Post by kansasnoob on 2008-09-07
> **kansasnoob said:**
> I see that both sda1 and sda3 are linux partitions. Do you have more than one linux operating system installed?

Actually it's not a huge deal, I just like to get things right the first time, but you could go ahead and try, once again from the live CD environment, go to terminal and:

```
sudo grub
```

Then:

```
root (hd0,0)
```

Then:

```
setup (hd0)
```

And finally:

```
quit
```

Then reboot (get out of the live CD environment) and if it doesn't work you'll have to try it again repalcing the "root (hd0,0)" command with "root (hd0,2)".

Don't be surprised if Windows is unbootable at this point. We'll more than likely have to edit the menu list, but don't worry, it's not at all hard to do.

---

### Post by kansasnoob on 2008-09-07
Well, once you get past this point, and if you have to edit the menu list (because Windows is not bootable) open the terminal again (this time you don't need to go into live CD environment). In terminal:

```
sudo cp /boot/grub/menu.lst /boot/grub/menu.lst_backup
```

This creates a backup of your original menu list in case something should get totally hosed!

Then:

```
sudo gedit /boot/grub/menu.lst
```

Once again that's a lower case L in menu.lst.

This opens the menu list in a text editor. At the very end of the menu list you'll want to add:

> title Windows XP
root (hd0,3)
makeactive
chainloader +1 

Then click on SAVE, then File > Quit.

Actually you could also edit the hiddenmenu text string and change it to #hiddenmenu and also edit default timeout 3 to something more appropriate like timeout 10, but I much prefer to just install startupmanager:

```
sudo apt-get install startupmanager
```

It'll then show up under System > Administration > Startup Manager and you can select many things:

[ATTACH]84518[/ATTACH]

You should then have a fully bootable dual boot.

---

### Post by KeithF40 on 2008-09-07
Yeah I got ubuntu and xubuntu.  Ill give it a shot later thanks.

---

### Post by kansasnoob on 2008-09-07
> **KeithF40 said:**
> Yeah I got ubuntu and xubuntu.  Ill give it a shot later thanks.

That's cool!

The instructions I gave should work fine then.

---

### Post by KeithF40 on 2008-09-08
Unfortunately I can't get ubuntu to work with my wireless card in my laptop and I have no PCMCIA slot so I can't use my card, the desktop is pretty old and doesn't run ubuntu very well, oh well.

---

