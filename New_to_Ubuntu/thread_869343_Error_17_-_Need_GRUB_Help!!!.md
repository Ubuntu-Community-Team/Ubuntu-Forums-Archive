---
title: "Error 17 - Need GRUB Help!!!"
date: 2008-07-24
forum: New to Ubuntu
---

### Post by discmaster on 2008-07-24
I can't seem to get past this error. 

This is my setup;

ASRock 775Twins-HDTV mainboard

hda1 ntfs 80gb --------previous Win XP install, still in place
hdb1 ntfs  80 gb -------storage

sda1 ext3 15gb root (ubuntu)
sda2 swap 2 gb
sda6 ext3 50gb (home)
sda5 ext3 180gb (storage)

sdb5 ntfs - 250 gb (storage)

I have tried several installs, all seem to go well. Installation completes, tells me to remove disc & reboot. I do that, and after the startup screen I.D.'s the SATA drives, I then get the following error.

GRUB Loading stage1.5.
GRUB Loading, please wait...
Error 17


I have been all through the BIOS, searched all over the forums, nothing I try seems to work! No sense in doing another install, I need to find out what to do at this point. 

Please help! :confused:

---

### Post by paul101 on 2008-07-24
this is what i used when i got an error 17:


[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

---

### Post by discmaster on 2008-07-24
Ok, I followed that guide, & for locations it returned - 

(hd2,0)

I don't understand what I am supposed to enter for root & setup?

---

### Post by caljohnsmith on 2008-07-24
> **discmaster said:**
> Ok, I followed that guide, & for locations it returned - 

(hd2,0)

I don't understand what I am supposed to enter for root & setup?
In the grub prompt (use "sudo grub" to get there), just type:
```
grub> root (hd2,0)
grub> setup (hd0)
```
If that doesn't solve your problem we can go from there.

---

### Post by discmaster on 2008-07-24
Ok, I did that, when I reboot I get -
Error 17: Cannot mount selected partition.

It does give me the selection menu though. I can choose ubuntu or XP, but it won't boot into either one, just gives me the error.

---

### Post by caljohnsmith on 2008-07-24
> **discmaster said:**
> Ok, I did that, when I reboot I get -
Error 17: Cannot mount selected partition.

It does give me the selection menu though. I can choose ubuntu or XP, but it won't boot into either one, just gives me the error.
That's a good sign. How about posting /boot/grub/device.map? That will give us an idea how to set up your menu.lst so you can boot your drives/partitions properly.

---

### Post by discmaster on 2008-07-24
> /boot/grub/device.map type it in like that? When I do, I get "No such file or directory."

---

### Post by gerbalblaste on 2008-07-24
Mount the partition while in the livecd (as simple as double clicking on it) and navigate to /boot/grub/device.map

---

### Post by caljohnsmith on 2008-07-24
> **discmaster said:**
> type it in like that? When I do, I get "No such file or directory."
OK, first boot up a Live CD, open a terminal window, and do the following:
```
sudo mount /dev/sda1 /mnt
cat /mnt/boot/grub/device.map
cat /mnt/boot/grub/menu.lst
```
Then copy and paste the output back here.

---

### Post by discmaster on 2008-07-24
Here is what I have from the boot/grub/device.map -
> (hd0)  /dev/hda
(hd1)  /dev/hdb
(hd2)  /dev/sda
(hd3)  /dev/sdb

EDIT - when I run "sudo gedit /boot/grub/menu.lst" the menu.lst comes up blank.

---

### Post by caljohnsmith on 2008-07-24
OK, you need to open up your menu.lst file from your sda1 Ubuntu partition as root. There are many ways to do so, but can do it like so:
```
sudo mount /dev/sda1 /mnt
gksudo gedit /mnt/boot/grub/menu.lst &
```
Or if your Live CD does not have gedit, you can use another editor, or even use "nano" in the terminal (replace gedit with nano in the command above).

Once you get menu.lst open, change your Windows entry to the following:
```
title		Windows XP
root		(hd0,0)
makeactive
chainloader	+1

```
To get Ubuntu to boot, add the following to your menu:
```
title		Ubuntu 8.04
root		(hd2,0)
kernel		/boot/vmlinuz-2.6.24-19-generic root=/dev/sda1 ro quiet splash
initrd		/boot/initrd.img-2.6.24-19-generic
quiet
```
Except you'll need to change those kernel numbers to whatever you have installed. In other words, just do a "ls /mnt/boot/" and see which kernel versions you have.

---

### Post by discmaster on 2008-07-24
Here is the menu.lst Is this not correct as it is?


> ## ## End Default Options ##

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic
root		(hd2,0)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=812cea6c-6384-471e-8540-04012073d28f ro quiet splash
initrd		/boot/initrd.img-2.6.24-19-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic (recovery mode)
root		(hd2,0)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=812cea6c-6384-471e-8540-04012073d28f ro single
initrd		/boot/initrd.img-2.6.24-19-generic

title		Ubuntu 8.04.1, memtest86+
root		(hd2,0)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title		Microsoft Windows XP Home Edition
root		(hd0,0)
savedefault
makeactive
chainloader	+1


---

### Post by discmaster on 2008-07-24
Well, I don't know what is going on with this system; I have been using Linux for quite some time, but I have never had it give me this much problem with booting before.

I changed the menu.lst to what *caljohnsmith* posted, & I am still getting Error 17: Cannot mount selected partition

What the heck?!?!:confused: :confused: :confused:

---

### Post by sharks on 2008-07-24
[http://ubuntuforums.org/showthread.php?t=804696](http://ubuntuforums.org/showthread.php?t=804696)

---

### Post by caljohnsmith on 2008-07-24
Yes, your menu.lst appears to be correct. To make sure your Ubuntu entries are correct, try:
```
sudo blkid
```
And where it lists sda1, check that its UUID is the same as your menu.lst entries for Ubuntu, i.e. "812cea6c-6384-471e-8540-04012073d28f". And also make sure you have "vmlinuz-2.6.24-19-generic" and "initrd.img-2.6.24-19-generic" files in the /boot directory of the Ubuntu partition.

So what exactly happens on start up now? Do you still get the error 17, or does that occur after you choose Windows/Ubuntu from the grub menu? Please give as many details as possible.

---

### Post by discmaster on 2008-07-24
> So what exactly happens on start up now? Do you still get the error 17, or does that occur after you choose Windows/Ubuntu from the grub menu? Please give as many details as possible. I am getting the selection screen, and after I choose Ubuntu from the list, I get the error 17. Is the entry (hd2,0) correct? That is what I have in the root listing.

---

### Post by sharks on 2008-07-24
> I am getting the selection screen, and after I choose Ubuntu from the list, I get the error 17. Is the entry (hd2,0) correct? That is what I have in the root listing.

just move the slider to ubuntu and press "e" then there will be a option callled "root  (hd2,0)" press e at it. then change it to root  (hd0,5)
or root  (hd0,1) then press b to boot.

---

### Post by bumanie on 2008-07-24
Post output of > sudo fdisk -lThat's a lower case L

---

### Post by discmaster on 2008-07-24
> just move the slider to ubuntu and press "e" then there will be a option callled "root (hd2,0)" press e at it. then change it to root (hd0,5)
or root (hd0,1) then press b to boot. Sorry sharks; I tried both of those with the same result. Error 17: Cannot mount selected partition.

---

### Post by sharks on 2008-07-24
try this root  (hd0,2)

---

### Post by discmaster on 2008-07-24
To run a command as administrator (user "root"), use "sudo <command>".
See "man sudo_root" for details.

ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x81a381a3

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        1909    15334011   83  Linux
/dev/sda2            1910        2176     2144677+  82  Linux swap / Solaris
/dev/sda4            2177       30401   226717312+   5  Extended
/dev/sda5            8258       30401   177871648+  83  Linux
/dev/sda6            2177        8257    48845569+  83  Linux

Partition table entries are not in disk order

Disk /dev/sdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x7be4becb

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               2       30401   244188000    f  W95 Ext'd (LBA)
/dev/sdb5               2       30401   244187968+   7  HPFS/NTFS

Disk /dev/hda: 81.9 GB, 81964302336 bytes
60 heads, 63 sectors/track, 42350 cylinders
Units = cylinders of 3780 * 512 = 1935360 bytes
Disk identifier: 0xcee8cee8

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1       42349    80039578+   7  HPFS/NTFS

Disk /dev/hdb: 80.0 GB, 80026361856 bytes
16 heads, 63 sectors/track, 155061 cylinders
Units = cylinders of 1008 * 512 = 516096 bytes
Disk identifier: 0x83d6f963

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *           1      155056    78148161    7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/hdb2               1           1           0   83  Linux
Partition 2 does not end on cylinder boundary.

Partition table entries are not in disk order
ubuntu@ubuntu:~$ 
ubuntu@ubuntu:~$

---

### Post by discmaster on 2008-07-24
Any more ideas, guys? I can't figure this one out on my own, that's for sure! ](*,)

---

### Post by caljohnsmith on 2008-07-24
You should see whether your sda1 partition is really the Ubuntu partition you are trying to boot:
```
sudo mount /dev/sda1 /mnt
ls /mnt/boot/
```
Do you see "vmlinuz-2.6.24-19-generic" and also "initrd.img-2.6.24-19-generic" listed?

---

### Post by discmaster on 2008-07-24
> Do you see "vmlinuz-2.6.24-19-generic" and also "initrd.img-2.6.24-19-generic" listed? yes, they are both there.

---

### Post by discmaster on 2008-07-24
> ubuntu@ubuntu:~$ sudo mount /dev/sda1 /mnt
mount: /dev/sda1 already mounted or /mnt busy
mount: According to mtab, /dev/sda1 is already mounted on /mnt
ubuntu@ubuntu:~$ ls /mnt/boot/
abi-2.6.24-19-generic         memtest86+.bin
config-2.6.24-19-generic      system.map-2.6.24-19-generic
grub                          vmlinuz-2.6.24-19-generic
initrd.img-2.6.24-19-generic
ubuntu@ubuntu:~$ 

1

---

### Post by kansasnoob on 2008-07-24
> **discmaster said:**
> Well, I don't know what is going on with this system; I have been using Linux for quite some time, but I have never had it give me this much problem with booting before.

I changed the menu.lst to what *caljohnsmith* posted, & I am still getting Error 17: Cannot mount selected partition

What the heck?!?!:confused: :confused: :confused:

I'm far too tired to go into detail but I've run into situations like this before and every time I bring it up I catch hell. I have seen instances where GRUB does NOT recognize things properly! Especially with two or more drives!

And it's always happened when I installed a new distro. Not new to the world, but new to my system! And it's usually when I used "manual install" to install that *buntu distro.

And if I just delete the new unusable distro and it is the "only" true vacant space on any drive, then just reinstall Ubuntu selecting "Guided - use the largest continuous free space"! (Now, it will do just what you say! So be sure of yourself!)

Nine times out of ten that gets me bootable and then I have to deal with what I broke fiddling around.

NOTE: I must also say that I've seen GRUB recognize partitions as separate drives, and large drives can be extremely perplexing.

---

### Post by caljohnsmith on 2008-07-24
I've got to get going now and won't be back until tomorrow, so in case nobody else can continue helping you, I thought I would mention that I have heard of similar problems as yours with people who use both IDE and SATA drives on the same computer. You might want to do some searching in the forums for that. Also, with such large HDDs, you might possibly be running into some sort of BIOS limitation. Anyway, I might be around tomorrow to help you. Good luck. :)

---

### Post by discmaster on 2008-07-24
Thanks for the info. guys. This is a new system I am working with, Motherboard & CPU. Everything else is out of my old mobo/cpu system that went south. It worked fine in the old system, with just some minor boot tweaking.

It just seems so odd that with the "correct" menu.lst / GRUB settings that I am still getting this error. I am wondering if it might be a good idea to just unplug all drives except for the ubuntu drive & reinstall. 

From there I could add the other drives afterwards & possibly configure the dual boot. Just a thought... Good idea?

---

### Post by Bucky Ball on 2008-07-24
[http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)

Download and make a copy, boot from that and see how you go. Should identify your two OSs regardless where they are and guide you through from there.

Incidentally, I have the ASRock ConroeXfire board with SATA and IDE drives, XP and Ubuntu no probs ...

Good luck ... :)

---

### Post by discmaster on 2008-07-24
Isn't supurgrub only for Windows? I downloaded it and it was an .exe file.

---

### Post by Bucky Ball on 2008-07-24
Make a bootable cd out of that file. Make sure you are downloading the right one for a disk (not usb stick, floppy - unless that is what you are using). And no, Windows does not natively use Grub Boot at all.

---

### Post by unutbu on 2008-07-24
discmaster, I believe the BIOS is not seeing the drives in the same order as the linux kernel. When you run "sudo grub" from the liveCD, GRUB relies on the linux kernel to tell it the order of the drives. When GRUB is installed on the MBR, at boot time GRUB relies on the BIOS to tell it the order of the drives. The liveCD linux kernel says that the linux partition is (hd2,0) but when you actually boot, the BIOS sees the linux partition as something other than the 1st partition on the 3rd drive, i.e. (hd2,0).

Try the following: Power up. Press ESC to get to the GRUB menu. Press 'e' to edit a selection. Press 'e' to edit the "root" line. Change (hd2,0) to one of the following
```

(hd0,0)
(hd1,0)
(hd3,0)
```

Press return to finish editing the root line. Press 'b' to attempt to boot.

You only have four drives, you know the Ubuntu partition is the first on its drive, so there are just four possibilities for "root (hdx,0)". We know x does not equal 2. Let's see if x=0,1 or 3.

If you get some success with this, then we'll know we are on the right path.

You then will have at least 3 options:

(1) This is the simplest. It is crude, but it should work. 
Boot from the LiveCD. Open a terminal
```
sudo mount /dev/sda1 /mnt
gksu gedit /mnt/boot/grub/menu.lst
```

Edit all the "root (hdx,0)" lines in your Linux boot stanzas with the correct value for x.

Then to get Windows booting, edit the Windows boot stanza to
```

title  Windows XP
root (hd1,0)
makeactive
map (hd0) (hd1)
map (hd1) (hd0)
chainloader +1
```

Again you'll need to experiment (using the method described above) to find out the right 'y' to put in '(hdy,0)'. There is a little wrinkle here: Windows insists on finding itself on the first drive. So you have to use map commands to swap the order of the drives. When you edit the Windows boot stanza (either temporarily through the GRUB boot menu, or through menu.lst) you need to change 'y' in three places:
```

title  Windows XP
root (hdy,0)
makeactive
map (hd0) (hdy)
map (hdy) (hd0)
chainloader +1

```
Try y=0,1,2,3. (Though I think you've already eliminated y=0).


(2) Use mbwardle's solution: [http://ubuntuforums.org/showpost.php?p=3518911&postcount=9](http://ubuntuforums.org/showpost.php?p=3518911&postcount=9). You'll have to modify your device.map a bit differently, since he only had 3 drives and you have 4. This solution is perhaps the most elegant because it gets the order of the drives from within Linux to agree with the order of the drives at boot time. 

If you choose to go this route: Note the following:

you have a 250GB disk with 3 linux partitions and a Linux swap partition (/dev/sda),
you have a 250GB disk with 1 HPFS/NTFS partition (/dev/sdb)
you have a 82GB disk with 1 HPFS/NTFS partition (/dev/hda)
you have a 80GB disk with 1 HPFS/NTFS partition and 1 Linux partition (/dev/hdb)

Power up. Press ESC to get to the GRUB menu. Press 'c' to get to the GRUB command line.
type

```
geometry (hd0)
geometry (hd1)
geometry (hd2)
geometry (hd3)
```

For each of the geometry commands, you will see output that looks somewhat like this:
```

drive 0x80: C/H/S = 38913/255/63, The number of sectors = 488281250, /dev/sda
   Partition num: 0,  Filesystem type unknown, partition type 0xde
   Partition num: 1,  Filesystem type is fat, partition type 0xb
   Partition num: 2,  Filesystem type is ext2fs, partition type 0x83
   Partition num: 4,  Filesystem type unknown, partition type 0x82

```
Notice that it tells you the number of sectors (i.e. the size of the disk), and also the number of partitions and the partition type. A sector is 512 bytes. So a 250GB disk is 488281250 sectors, for example. Using these pieces of information, you will be able write down the device map:

Something like

```
(hd0) /dev/sda 
(hd1) /dev/sdb
(hd2) /dev/hda
(hd3) /dev/hdb
```

Once you know this information you will be ready to follow mbwardle's solution: [http://ubuntuforums.org/showpost.php?p=3518911&postcount=9](http://ubuntuforums.org/showpost.php?p=3518911&postcount=9).

(3) Swap the order in which your drives are connected to the machine. This will change the BIOS order. This seems messy to me. I wouldn't recommend this in this case.


If any of this is unclear, post.

---

### Post by kansasnoob on 2008-07-24
> **discmaster said:**
> Thanks for the info. guys. This is a new system I am working with, Motherboard & CPU. Everything else is out of my old mobo/cpu system that went south. It worked fine in the old system, with just some minor boot tweaking.

It just seems so odd that with the "correct" menu.lst / GRUB settings that I am still getting this error. I am wondering if it might be a good idea to just unplug all drives except for the ubuntu drive & reinstall. 

From there I could add the other drives afterwards & possibly configure the dual boot. Just a thought... Good idea?

So you take how many operating systems with whatever configuration from system A to system B:confused:

If you're a do at your-selfer as I am, and you need to replace a Mobo & CPU just pull out some old small hard drive and do a fresh install of your favorite distro. Keep notes! Well, I'm old enough I need notes:(

Then you can build upwards! You CAN NOT just change a MOBO & CPU and expect everything to auto configure.

It sounds to me like you also have Win on that machine. Did it just auto-config? Or do you have a clock ticking?

---

### Post by kansasnoob on 2008-07-24
> **unutbu said:**
> discmaster, what you have is a case of the BIOS not seeing the drives in the same order as GRUB. When you run "sudo grub" from the liveCD, it says that the linux partition is (hd2,0) but that's obviously not working for you during the boot process.

Try the following: Power up. Press ESC to get to the GRUB menu. Press 'e' to edit a selection. Press 'e' to edit the "root" line. Change (hd2,0) to one of the following
```

(hd0,0)
(hd1,0)
(hd3,0)
```

Press return to finish editing the root line. Press 'b' to attempt to boot.

You only have four drives, you know the Ubuntu partition is the first on its drive, so there are just four possibilities for "root (hdx,0)". We know x does not equal 2. Let's see if x=0,1 or 3.

If you get some success with this, we can then discuss what's the best way to make this permanent.

+1

That happens!

But take note that it sounds like we're transferring existing hard drive configs to a new system!

---

### Post by Bucky Ball on 2008-07-25
> [http://www.supergrubdisk.org/index.php?pid=5](http://www.supergrubdisk.org/index.php?pid=5)

Make a cd, go to bios, select to boot from cd, insert Grub boot you just made, exit saving changes and see how you go.

---

### Post by discmaster on 2008-07-25
I was able to change menu.lst to (hd0,0), and I am able to at least boot into ubuntu now. I haven't tried to boot to xp yet. One issue at a time! Right now I seem to be dealing with instability issues, such as;

* FF 3.0 is crashing at random times - browser window will close on its' own. I have disabled all visual effects, didn't seem to help.

* After FF crashes, it seems that the system itself is in an unstable state, because I cannot get other pgms. to open, even synaptic won't open at that point.

This is a completely fresh install of ubuntu. I can't see that the system is corrupt, although I guess the install could be. I know ff3 is buggy, but I was running it on my previous system without major issues like this.

I figure after I get all the ubuntu problems ironed out I will reinstall xp on the other drive. Any ideas on all the instability?

---

### Post by discmaster on 2008-07-25
Update:

I have disconnected all drives except the SATA 1 that I have installed ubuntu on. Install went fairly well. BIOS on this mainboard wasn't properly recognizing mt RAM as ddr 400, it had it set at 333. 

After I corrected that, I am able to boot into ubuntu without a hitch. I have to disable all visual effects for openoffice to run, or that pgm. will crash. 

I am still getting random firefox crashes. Right now, when I click on synaptic to open it, it won't open. There is also "hdc status error" when I view the system log.

Bottom line, this system is unstable, and I can't use it like this. Problem is, I don't know where to begin looking.

A couple of years ago, with another system, I had cpu identity issues which were resolved with a BIOS update. I am wondering if a BIOS update would be a fix here with this ubuntu problem.

Anyone experience anything similar? I need to head in a direction to resolve this, but I just don't really know where to start, without going down alot of dead end roads...
:confused:   :confused:  :confused: 

Open to ideas...

---

### Post by Bucky Ball on 2008-07-25
The plot thickens. One thing - when you boot from the Ubuntu Installation disk, the first screen you get gives you a few options. One is to install ubuntu, the next is to check the disk for defects before you install (or words to that effect). Did you check the disk for defects before the install? If not, I suggest you do that now. If there is a problem with the disk, that could be your problem because, as you say, this is a clean, fresh, brand new install of Ubuntu. I can't for the life of me work out why you are having so many problems.

---

### Post by hogwartsnigel on 2008-07-25
Hi,
Speed reading so forgive this if already mentioned but you could simply use a downloaded super grub disc and follow its gui (very informative) to correct the grub loader and indeed activate the appropriate partition.

Hope that helps

Nigel

---

### Post by Bucky Ball on 2008-07-25
Been saying that since the get go, hogwartsnigel! :)

---

### Post by hogwartsnigel on 2008-07-26
Sorry Bucky Ball,
Blushing, i read it this time.:)
SGD got me out of many "where the hell is my install moments...lol"

Nigel

---

### Post by discmaster on 2008-07-30
> as you say, this is a clean, fresh, brand new install of Ubuntu. I can't for the life of me work out why you are having so many problems.Just wanted to give an update here. This is unbelievable - the problem is always in the last place that you look, I guess. I have narrowed down one (hopefully all) of my problems to a bad memory stick.

I decided top try an XP install w/ just 1 HD connected & I ran into several errors upon that attempt. At that point I knew there must be some type of hardware issue, because I have done XP installs many times without a hitch.

I started pulling memory/swapping slots, & my problem went away. Haven't had a chance to attempt the Ubuntu install yet, that will be my next venture. As it stands now, I do have a stable running system. I have XP installed on a PATA drive on IDE 1, the Ubuntu install will go on a SATA drive. 

I guess after that install I will probably have to configure menu.lst so I get the dual boot to work correctly, as I have never had it (dual boot) seem to be configured right when I did installs previously.

I will give super grub a shot, since it seems to be a well liked program.

Many thanks to all who contributed to this thread - sorry for "wasting" so much time, when it turned out to be a bum piece of hardware...

---

### Post by sharks on 2008-07-30
> sorry for "wasting" so much time, when it turned out to be a bum piece of hardware...

Its ok.> As it stands now, I do have a stable running system. I have XP 

When u have XP , then how u can have a stable running system?:lolflag:

---

### Post by unutbu on 2008-07-30
Thank you for the update. Next time we see symptoms like this maybe we'll remember to suggest a memtest.

---

### Post by discmaster on 2008-07-30
> Thank you for the update. Next time we see symptoms like this maybe we'll remember to suggest a memtest.Now that is the funny part of this situation. When my previous system was giving me problems, a couple of weeks ago, I ran memtest with this RAM (Corsair, good stuff). I let it run for quite a long time, & no errors were reported.

It turned out that my previous system had bulged/bad capacitors on the mobo, that is why I put together this new system. It is odd that the memory stick went bad between then & now. While I was waiting for the new mobo/cpu to arrive, I pulled everything from my old system & stored the hardware in their original boxes/packaging so they would not get damaged.

Guess it was just time for that stick to go - so now I am computing with 512 for the time being.

> When u have XP , then how u can have a stable running system? LOL

---

### Post by Bucky Ball on 2008-07-30
> 
I will give super grub a shot, since it seems to be a well liked program.

You should find that Hardy (8.04) will do this for you and when install is finished and you reboot you should be faced with a fully operational grub (not necessarily the case in previous versions). If this doesn't happen, SuperGrubDisk will certainly fix the problem for you (or should), as long as you have a think and take it slow through the menu. I suspected hardware but was looking at the optical drive (mentioned in my post of awhile ago).

You are getting somewhere! Yay! Have fun and keep us informed. :)

---

