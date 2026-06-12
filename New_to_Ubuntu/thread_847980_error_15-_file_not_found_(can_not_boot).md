---
title: "error 15- file not found (can not boot)"
date: 2008-07-03
forum: New to Ubuntu
---

### Post by copperco2 on 2008-07-03
i am having a problem with booting in ubuntu.
it shows error 15.

pl. help.

---

### Post by natirips on 2008-07-03
Since I don't know what error 15 would be, I would backaup all important files (using the live CD) and reistall, but don't do it just yet, maybe someone has a better solution (if you can afford, wait for a few days for a possible better reply).

Also, to help those that might have a better solution, did the GRUB (boot loader) or Ubuntu itself give the error*. Also, does it say anything else. Also, do you have any idea what might have caused the probles (i.e. another OS installation, kernel updates, ...)/when did the problem occur.

* If you didn't see anything like the Ubuntu splash screen, or "kernel alive" message, it was GRUB (or whatever boot loader you might be using), otherwise it was probably Ubuntu.

---

### Post by ChameleonDave on 2008-07-03
> **copperco2 said:**
> i am having a problem with booting in ubuntu.
it shows error 15.

pl. help.

Are we talking about GRUB error 15 here?

---

### Post by copperco2 on 2008-07-03
i have dual boot, and i have installed 8.04 in windows d drive.
once i start i have made ubuntu first boot after it selects ubuntu, it starts to load..like
the message shows that 'loading upper memory' and couple of more messages and then this error kicks in.

i believe it has occured because of sudden shut down of the machine, i dont know much else.

it also gives option of pressing any key to continue...but that only gives some options which again do not work except for reboot,
some of the options are going to command line and halt.
I am using the same machine so will be unable to give you exat options.

---

### Post by natirips on 2008-07-03
> **copperco2 said:**
> ...
I am using the same machine so will be unable to give you exat options.
When the modern scinese fails, use the ancient methods (paper and pen in this case). :)

---

### Post by copperco2 on 2008-07-03
This is it, the whole thing. once i choose ubuntu to install, the following message comes up-

"find --set-root --ignore-floppies /ubuntu/install/boot/grub/menu.lst

Error 15: file not found

Press any key to continue"

when a key is pressed,

"GRUB4DOS 0.4.3 2008-04-22 Memory 638k/1269M, CodeEnd: 0x41228"

The options which i can chose and select are as-
"find /ubuntu/disks/boot/grub/menu.lst
find /ubuntu/install/boot/grub/menu.lst
find /menu.lst
ubuntu /boot/grub/menu.lst
ubuntu /grub/menu.lst
commandline
reboot
halt"

thats all.
pl. help

---

### Post by bumanie on 2008-07-03
Boot live cd and post output of > sudo fdisk -l (lower case L)

---

### Post by copperco2 on 2008-07-03
the result is here-
"Disk /dev/sda: 40.0 GB, 40007761920 bytes
255 heads, 63 sectors/track, 4864 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier : 0x3a593a58

Device Boot          Start      End       Blocks    Id    System
/dev/sda1 *           1         1785    14337981    7    HPFS/NTFS

/dev/sda2             1786      4863    24724035    f    W95 Ext'd (LBA)

/dev/sda5             1986      4863    24724003+   7    HPFS/NTFS"


pl. help

---

### Post by bumanie on 2008-07-03
Your ubuntu installation has not worked, fdisk -l shows that windows is the only OS on the hard drive. You have c\: and (I assume) a data partition inside an extended partition - that's all.

---

### Post by ChameleonDave on 2008-07-03
This should perhaps be in the Wubi forum.

---

### Post by Elfy on 2008-07-03
I got caught out yesterday by wubi :)

---

### Post by bumanie on 2008-07-03
> **ChameleonDave said:**
> This should perhaps be in the Wubi forum.

Good pick-up ChameleonDave, I never thought of it being a wubi install. Probably need to muck around in vbox to with a wubi install to see how it all works.

---

### Post by copperco2 on 2008-07-03
any specific advice for me? how do i view the files in ubuntu? is it possible to do that?

---

### Post by jingo811 on 2008-07-03
> **copperco2 said:**
> the result is here-
"Disk /dev/sda: 40.0 GB, 40007761920 bytes
255 heads, 63 sectors/track, 4864 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier : 0x3a593a58

Device Boot          Start      End       Blocks    Id    System
/dev/sda1 *           1         1785    14337981    7    HPFS/NTFS

/dev/sda2             1786      4863    24724035    f    W95 Ext'd (LBA)

/dev/sda5             1986      4863    24724003+   7    HPFS/NTFS"


pl. help

Could you use the Ubuntu Live CD and take a snapshot of your partitions in Gparted and then upload the image to [http://tinypic.com/](http://tinypic.com/) or something?
System > Admin > _Gnome Partition Editor_

Someone said you didn't have a Linux partition maybe you can use that empty space and install Ubuntu the usual way?
But first I like to analyse your hard drive graphically those fdisk numbers gives me a headache :confused: If you're lucky you might have a big chunk of unused space on the hard drive like me, then you just install a fresh Ubuntu the vanilla way sans Wubi.

[IMG]http://i31.tinypic.com/29gkh9t.png[/IMG]

---

### Post by natirips on 2008-07-03
> **copperco2 said:**
> any specific advice for me? how do i view the files in ubuntu? is it possible to do that?

If you have normal installation, you'll see viewing files is easier that on Windows (XP and older at least, I've never used Vista so far). There is a menu at the top of your screen by default, called Places, which is very neat and easy-to-use, and has links to your computer's all drives, to you home folder, etc. Anyway, just by taking a look around the screen you should be able to get around.

---

### Post by copperco2 on 2008-07-03
[http://www.screenshots.cc/show.php/13197_ScreenshotdevsdaGParted.png.html](http://www.screenshots.cc/show.php/13197_ScreenshotdevsdaGParted.png.html)

the adviced scree shot is ready for your reference. jingo811.

pl. help

---

### Post by copperco2 on 2008-07-03
> **natirips said:**
> If you have normal installation, you'll see viewing files is easier that on Windows (XP and older at least, I've never used Vista so far). There is a menu at the top of your screen by default, called Places, which is very neat and easy-to-use, and has links to your computer's all drives, to you home folder, etc. Anyway, just by taking a look around the screen you should be able to get around.
since i can not boot in ubuntu, i need to access some files from window.
how can i do that.

since this installation was done 'within windows', it was done in the biggest/ largest space available in d drive. so i find that there are files which were there like media files and all with an additional folder belonging to 'ubuntu'.

i need to access the files on ubuntu from within windows.
pl. help.

---

### Post by Elfy on 2008-07-03
I've never had much to do with wubi tbh - but you mmight need to try to access it like this from within a booted ubuntu livecd.

[https://wiki.ubuntu.com/WubiGuide#head-d08dd29d8d72682732b0bdb835cef9e81cd675b7](https://wiki.ubuntu.com/WubiGuide#head-d08dd29d8d72682732b0bdb835cef9e81cd675b7)

---

### Post by natirips on 2008-07-03
> **copperco2 said:**
> since i can not boot in ubuntu, i need to access some files from window.
how can i do that.

since this installation was done 'within windows', it was done in the biggest/ largest space available in d drive. so i find that there are files which were there like media files and all with an additional folder belonging to 'ubuntu'.

i need to access the files on ubuntu from within windows.
pl. help.

Sorry, I got you wrong. That went for clean Ubuntu installation. The post above from forestpixie seems to be the info you're looking for. Sorry.

---

### Post by copperco2 on 2008-07-03
not possible to access it from a live cd.

pl. help.

---

### Post by Elfy on 2008-07-03
What happens when you run the command in the link I gave you?

---

### Post by jingo811 on 2008-07-03
> **copperco2 said:**
> not possible to access it from a live cd.

pl. help.

The link forestpixie recommended earlier.
[https://wiki.ubuntu.com/WubiGuide#head-d08dd29d....]("https://wiki.ubuntu.com/WubiGuide#head-d08dd29d8d72682732b0bdb835cef9e81cd675b7")

[CENTER][SIZE="3"][COLOR="Sienna"]How can I access my Wubi install and repair my install if it won't boot?[/COLOR][/SIZE][/CENTER]

In terminal type these CLI commands (miss typing occurs 70% of all previous newbie cases, so be accurate):
```
sudo mkdir /win
```
```
sudo mount /dev/sda5 /win
```
```
sudo mkdir /vdisk
```
```
sudo mount -o loop /win/ubuntu/disks/root.disk /vdisk
```
```
cd /vdisk
```
```
ls -l
```

Can you see your files if yes then you could use the GUI file browser Nautilus and copy & paste the files like in Windows.


If you don't have permission to copy files from this folder then do this on the Desktop area.
[LIST]
[*]*press* Alt+F2
[*]```
gksudo nautilus
```
[*]*double click* File system 
[*]*press* Ctrl+2
[*]Then find your **vdisk** folder.
[/LIST]

---

### Post by copperco2 on 2008-07-04
thanks for all the help. i will soon get back to you.

Regards.

---

### Post by areskz on 2008-07-05
Guys, I have the problem close to author's one. 

Yesterday I have reinstalled my Gutsy. During the installation I have chosen to format my sda5 partition (**fdisk -l **output is attached), and set (as it was before) sda7 as home patition. sda6 was left as a swap. 

```

Disk /dev/sda: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x06902fba

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1         896     7194624   27  Unknown
Partition 1 does not end on cylinder boundary.
/dev/sda2   *         896        3507    20971520+   7  HPFS/NTFS
/dev/sda3            3508        9409    47407815    5  Extended
/dev/sda4            9410       24322   119781376    7  HPFS/NTFS
/dev/sda5            3508        6546    24410736   83  Linux
/dev/sda6            6547        6919     2996091   82  Linux swap / Solaris
/dev/sda7            6920        9409    20000893+  83  Linux

```

Everything went okay until the finishing of installation: when it started installing GRUB. It just hung. I've killed the process, started installation again, and now ticked off "Install GRUB" in options. (I just though that I already have GRUB, and I don't even change "\" partition number).

Installation went okay, and when I rebooted my laptop GRUB said to me: "**Error 15**". And there is no even a possibility to press 'e' to correct menu.lst, or something. It just hungs and the only option is to reboot by CTRL+ALT+DEL.

By the way, I have not only one OS installed now, also (along with Kubuntu) I have my pre-installed Vista, and before reinstall it also was in GRUB. Now I can't access nor Vista either Kubuntu. 

How can I, maybe, reinstall GRUB, and let him detect what OS I have installed and create menu.lst items for them? Or maybe I can somehow correct extisting version?

The only way I can access my laptop is via LiveCD.

---

### Post by Elfy on 2008-07-05
You might be better of with thread of your own, you can use the livecd to sort grub, but if this is a wubi install problem I have never done it.

[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

try that - if not trry and get a copy of the supergrub disc, you would need to downlaod and burn it on another pc/laptop though.

[http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)

---

### Post by jingo811 on 2008-07-05
> **areskz said:**
> guys, I Have The Problem Close To Author's One. 

Yesterday I Have Reinstalled My Gutsy. **[color="red"](1.)[/color] During The Installation I Have Chosen To Format My Sda5 Partition **(**fdisk -l **output Is Attached), And Set (as It Was Before) Sda7 As Home Patition. Sda6 Was Left As A Swap. 

**[color="red"](2.)[/color] Everything Went Okay Until The Finishing Of Installation: When It Started Installing Grub. It Just Hung.** I've Killed The Process, Started Installation Again, **[color="red"](3.)[/color]and Now Ticked Off "install Grub" In Options. (i Just Though That I Already Have Grub, And I Don't Even Change "\" Partition Number).**
...
...

**[color="red"](4.)[/color]by The Way, I Have Not Only One Os Installed Now, Also** (along With Kubuntu) I Have My Pre-installed Vista, And Before Reinstall It Also Was In Grub. Now I Can't Access Nor Vista Either Kubuntu. 

**[color="red"](5.)[/color]how Can I, Maybe, Reinstall Grub, And Let Him Detect What Os I Have Installed** And Create Menu.lst Items For Them? Or Maybe I Can Somehow Correct Extisting Version?

...


[COLOR="Red"](1.)[/COLOR] The minute you chose to format your old Gutsy / partition then your old **/boot/grub/menu.lst** also got erased.

[COLOR="Red"](2.)[/COLOR] Might be a case of poorly burnt or damaged CD.[https://...Installation/CDIntegrityCheck.../]("https://help.ubuntu.com/community/Installation/CDIntegrityCheck?action=show&redirect=CDIntegrityCheck/")

[COLOR="Red"](3.)[/COLOR] GRUB depends on **/boot/grub/menu.lst** to work which you erased when you did the /sda5 format.  Don't untick GRUB install during  Gutsy installation!

[COLOR="Red"](4.)[/COLOR] Follow the advice on [COLOR="Red"](3.)[/COLOR] and all your other operating systems will show up on GRUB menu again.

[COLOR="Red"](5.)[/COLOR] Such a simple solution doesn't seem to exist, just re-install Gutsy without unticking GRUB and everything should be fine again.

Supergrubdisk is probably your best bet if you still want to find that solution but that requires more reading/learning maybe not much still I don't like extra reading.  Just re-install Gutsy with GRUB again.

---

