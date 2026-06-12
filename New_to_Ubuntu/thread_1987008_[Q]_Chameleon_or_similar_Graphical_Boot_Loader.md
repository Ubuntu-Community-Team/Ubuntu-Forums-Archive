---
title: "[Q] Chameleon or similar Graphical Boot Loader?"
date: 2012-05-25
forum: New to Ubuntu
---

### Post by mikeeey on 2012-05-25
I really like the chameleon bootloader and different themes available for it, but I was just wondering if you need OSX in order to install/manage/edit Chameleon? Can it be installed through Ubuntu and is there a "Chameleon Settings" or "Chameleon Wizard" app to switch different themes?

If Chameleon is not possible without OSX, then what are some other recomened bootloaders for Ubuntu which offer several themes and allow you to edit their settings?

Thanks!

---

### Post by MG&amp;TL on 2012-05-26
You could checkout grub-customizer, which edits the default Ubuntu bootloader.

There's also BURG, (which is awesome) but it won't get any better as it's undeveloped.

---

### Post by zombifier25 on 2012-05-26
I'll say BURG. It is very beautiful, and there are loads of themes for it that are very easy to install, using Super Boot Manager.
> **MG&TL said:**
> There's also BURG, (which is awesome) but it won't get any better as it's undeveloped.

Actually, it's not that bad. Recent versions of GRUB does not fix anything really major that has to make you switch from BURG anyway.

---

### Post by MG&amp;TL on 2012-05-26
> **zombifier25 said:**
> 
Actually, it's not that bad. Recent versions of GRUB does not fix anything really major that has to make you switch from BURG anyway.

No. But people do expect to see software upgrades and bugfixes. ;)

---

### Post by mikeeey on 2012-05-28
Thanks guys!

I haven't figured out how to get BURG to properly install yet.. Everything seems to go well, but when I restart my computer I still have boring grub.

I've tried based off these two websites:
[http://www.unixmen.com/how-to-install-burg-in-ubuntu/](http://www.unixmen.com/how-to-install-burg-in-ubuntu/)
[http://agnipulse.com/2010/09/graphical-boot-loader-burg/](http://agnipulse.com/2010/09/graphical-boot-loader-burg/)

I also installed Super-Boot-Manager, but it doesn't work either (maybe because BURG isn't sucessfully installed?). When I click on it it asks for the root password, I type it, hit enter, the window goes away, and nothing happens.

When trying to test run BURG within terminal per the 1st website's instructions, rather than getting a graphical bootloader as shown in the screenshot, I get this:
```
                        BURG  version 1.98+20100623-2.3

   Minimal BASH-like line editing is supported. For the first word, TAB
   lists possible command completions. Anywhere else TAB lists possible
   device or file completions.

grub> 

```

Also, the command sudo update-burg always ends up saying: "/usr/sbin/burg-mkconfig: 8: /etc/default/burg: Syntax error: "(" unexpected"

---

### Post by MG&amp;TL on 2012-05-28
```
sudo burg-install <disk>
``` is I think what you're looking for.

You need to replace <disk> with the correct hard disk.

---

### Post by mikeeey on 2012-05-28
Well I still can't get it working.
What command can I type to check my partitions, or better yet simply check where my MBR is?

I've read that burg can also be installed through burg manager or super boot manager.
When I install Burg Manager or Super Boot Manager I still can't get them working. When I click either of them it says "Please type root password" but after I type it and proceed the window disappears and nothing happens.

---

### Post by MG&amp;TL on 2012-05-28
> **mikeeey said:**
> Well I still can't get it working.
What command can I type to check my partitions, or better yet simply check where my MBR is?

I've read that burg can also be installed through burg manager or super boot manager.
When I install Burg Manager or Super Boot Manager I still can't get them working. When I click either of them it says "Please type root password" but after I type it and proceed the window disappears and nothing happens.

Post the output of:

```
sudo fdisk -l
```

and someone should be able to help you.

---

### Post by mikeeey on 2012-05-28
Well I found out Super-boot-manager wasn't working due to the version of buc that comes with ubuntu 12.04. I uninstalled buc and reinstalled from here:
[http://www.sourceslist.eu/blog/linux-blog/super-boot-manager-buc-version-download-installation/](http://www.sourceslist.eu/blog/linux-blog/super-boot-manager-buc-version-download-installation/)

But even installing burg through superboot manager isn't working.
/dev/sdb being my only selection of where to install burg, when clicking "burg-install" the terminal pops up downloading/installing, but at the end I start seeing errors and "could not download". Then a message comes up though super boot manager (or buc) about failed installation.


Here are my fdisk results btw. Ignore the first part, that is my storage HDD.
I see that /dev/sdb1 on my 750GB must be the MBR right?

```
Disk /dev/sda: 1500.3 GB, 1500301910016 bytes
240 heads, 63 sectors/track, 193801 cylinders, total 2930277168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x480a284b

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1              64  2930274303  1465137120    7  HPFS/NTFS/exFAT

Disk /dev/sdb: 750.2 GB, 750156374016 bytes
255 heads, 63 sectors/track, 91201 cylinders, total 1465149168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x08f9e1f3

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *        2048      206847      102400    7  HPFS/NTFS/exFAT
/dev/sdb2          211680  1366863119   683325720    7  HPFS/NTFS/exFAT
/dev/sdb3      1366863870  1465147391    49141761    f  W95 Ext'd (LBA)
Partition 3 does not start on physical sector boundary.
/dev/sdb5      1366863872  1399627775    16381952   83  Linux
/dev/sdb6      1399629824  1432385535    16377856   83  Linux
/dev/sdb7      1432387584  1465147391    16379904   83  Linux

```
And yes there are 3 versions of linux, Ubuntu, Linux Mint, and Pinguy.

**edit:** well after that last attempt to install it did get rid of grub, but it replaced it with the basic burg that says:
```
             BURG  version 1.98+20100623-2.3

   Minimal BASH-like line editing is supported. For the first word, TAB
   lists possible command completions. Anywhere else TAB lists possible
   device or file completions.

grub>
```

I have no idea how to navigate it and what to type in to get to my partitions, so right now I'm running off the live CD.

**edit:**
restored grub. Now back to step 1, trying to get Burg to work.

---

### Post by MG&amp;TL on 2012-05-28
Uh-oh. Not good, that means something's gone badly wrong.

Okay, what does running:

```
sudo burg-install "(hd1)"
```

do?

I am assuming as you managed to restore grub you are reasonably competent and have backed up your data. ;)

---

### Post by mikeeey on 2012-05-28
Well my Windows partition (The absolute MOST important) is working fine. Ubuntu works great. The other two linux's I am just trying out so if anything happens to them it's no big, but they're working fine as well.
I have no way to back up all my data, so as long as I don't overwrite a partition with an OS then I'm good.

running that to hd1 overwrote grub and installed burg, so when I restarted my computer just now it said:
```
         BURG  version 1.98+20100623-2.3

   Minimal BASH-like line editing is supported. For the first word, TAB
   lists possible command completions. Anywhere else TAB lists possible
   device or file completions.

grub>
```

Had to use a live CD to boot into this partition.
Is it a good or bad thing I'm seeing this message?

---

### Post by MG&amp;TL on 2012-05-29
> **mikeeey said:**
> Well my Windows partition (The absolute MOST important) is working fine. Ubuntu works great. The other two linux's I am just trying out so if anything happens to them it's no big, but they're working fine as well.
I have no way to back up all my data, so as long as I don't overwrite a partition with an OS then I'm good.

running that to hd1 overwrote grub and installed burg, so when I restarted my computer just now it said:
```
         BURG  version 1.98+20100623-2.3

   Minimal BASH-like line editing is supported. For the first word, TAB
   lists possible command completions. Anywhere else TAB lists possible
   device or file completions.

grub>
```

Had to use a live CD to boot into this partition.
Is it a good or bad thing I'm seeing this message?

Bad. As far as I can tell, it seems to have failed to load any sort of theme. At all. Sorry, no idea, but you could try one of the BURG support channels or pray someone turns up here. :)

---

### Post by mikeeey on 2012-05-29
Where would I find the support channel? Or do you mean contacting the developers?

**Edit** so I went to install gimp to resize some images for screenshots, and each time it failed to install, the error mentioned something along the lines of being unable to remove a burg theme?? Not sure how that has to do with installing gimp, so I just deleted my Ubuntu partition, reinstalled, and now I'm on the go, I'll try everything later.

**edit 2:** Unplugged my other HDD just incase it was somehow interfering, reinstalled Ubuntu, and the first thing I did was tried to install burg from this guide:
[http://www.unixmen.com/how-to-install-burg-in-ubuntu/](http://www.unixmen.com/how-to-install-burg-in-ubuntu/)

and I notice 404 not found errors throughout the install.
sudo update-burg has NEVER worked, I'm always provided with this message:

```
mike@Mike:~$ sudo update-burg
[sudo] password for mike: 
/usr/sbin/burg-mkconfig: 8: /etc/default/burg: Syntax error: "(" unexpected
mike@Mike:~$ 

```

Formatted and tried again except from burg manager, still didn't work.
I'm just wondering now if it's the repo that's down, it seems like it just isn't download whatever it needs to.

I can't find any alternative locations to get burg.

---

### Post by mikeeey on 2012-05-31
Would someone be able to install burg so I can see if it's just my computer or if there's something actually wrong with the repository?

---

