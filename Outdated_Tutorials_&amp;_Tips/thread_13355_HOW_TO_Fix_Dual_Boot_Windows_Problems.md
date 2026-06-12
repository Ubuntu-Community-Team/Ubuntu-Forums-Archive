---
title: "HOW TO: Fix Dual Boot Windows Problems"
date: 2005-01-30
forum: Outdated Tutorials &amp; Tips
---

### Post by rafarossi on 2005-01-30
Thanks to a lot of research and effort from a variety of sources (too many to mention here) I finally put together a way of fixing your dual boot problems with windows. the final solution was found in the LWN page located at [http://lwn.net/Articles/86835/](http://lwn.net/Articles/86835/) .
The problem is caused because the Geometry of the Hard Drive is being reported wrong to the Windows system, which makes it hang. 
If you have your Windows installation on your Primary Master HD, it then should be located at /dev/hda. The command should be then as follows:

sudo sfdisk -d /dev/hda | sudo sfdisk --no-reread -H255 /dev/hda

Change it accordingly to fit yours. Try your boot menu and see if it works now.

PS: This isn't by any means extensive and technically based. It was made solely on research and messages posted on the forums throughout the Web. Your problem might be different. Use it at your own risk.

---

### Post by lilpac on 2005-02-05
Well im having trouble with installing windows next 2 my ubuntu installation,
i tryd the command above, but since ive installed ubuntu, my windows cd can't boot :).

lilpac

---

### Post by crane on 2005-02-05
[QUOTE=lilpac]Well im having trouble with installing windows next 2 my ubuntu installation,
i tryd the command above, but since ive installed ubuntu, my windows cd can't boot :).

lilpac[/QUOTE]


look at this file
/boot/grub/menu.lst

post what this file says about windows.
It should be towards the bottums of the list.

---

### Post by lilpac on 2005-02-05
*edit*
title		Ubuntu, kernel 2.6.8.1-4-686 
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.8.1-4-686 root=/dev/hda1 ro quiet splash
initrd		/boot/initrd.img-2.6.8.1-4-686
savedefault
boot

title		Ubuntu, kernel 2.6.8.1-4-686 (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.8.1-4-686 root=/dev/hda1 ro single
initrd		/boot/initrd.img-2.6.8.1-4-686
savedefault
boot

title		Ubuntu, kernel 2.6.8.1-3-386 
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.8.1-3-386 root=/dev/hda1 ro quiet splash
initrd		/boot/initrd.img-2.6.8.1-3-386
savedefault
boot

title		Ubuntu, kernel 2.6.8.1-3-386 (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.8.1-3-386 root=/dev/hda1 ro single
initrd		/boot/initrd.img-2.6.8.1-3-386
savedefault
boot

title		Memory test
root		(hd0,0)
kernel		/boot/memtest86+.bin

### END DEBIAN AUTOMAGIC KERNELS LIST

:) this is it

---

### Post by uberlinux on 2005-02-05
If you get a message from sfdisk saying"I dont like this geometry, nothing was changed", then finish it off with the switch  "--force"  Worked for me!
P.S.   Is this the same command to fix the same issue in FedoraCore2... anyone?

---

### Post by jerome bettis on 2005-02-07
i just went through the same thing.  i installed ubuntu, got it setup the way i like it, and then found out this class i'm taking uses a windows only CD for some homework problems.  so i had to bite the bullet and scar my laptop with microsoft crap.

anyway, i tried doing what you're doing and it wouldn't work for me.  after some reading, the most comprehensive article i found on this issue [here](http://www.ibiblio.org/pub/Linux/docs/HOWTO/Linux+Win9x+Grub-HOWTO) didn't work.

basically it uses grub to trick winblows into thinking it's actually using sector 0 of the drive, but it's actually using a logical partition.  this would probably work great if you can get windoze installed.

but i had to install it from cd, and i could not for the life of me get grub to recognize my cd rom drive.  it's /dev/hdc and according to the way grub maps it should be (hd1,0) or maybe (hd2,0).  i tried putting so many things in /boot/grub/device.map and tried all sorts of commands in the menu but no matter what it always said specified device does not exist.  maybe installing from a floppy would work, but i don't have one.  i also tried setting up a dos partition, swapped the mapping in grub, and copied the xp cd on there, but that didn't work either - same thing happened.

anyway, i said the hell with it, put the xp cd in, wiped out my hard drive and gave windoze a 2.5 gb primary partition, and left the rest unpartitioned.  i booted into windows once, remembered how much it sucked, and put the ubuntu cd back in.  i left the windows partition alone, and pieced up the rest of my drive like i always do.  i installed grub on the MBR and now i can boot ubuntu and windows fine.

so the basic answer to your question is windows thinks it's the center of the universe and it's much easier just to let it have the primary partition.  install windoze first and then linux.  unless someone knows how to do it the other way???

but as much as i hate microsoft, i have to say, it's nice to have it there as something to fall back on.  i'm always experimenting with linux (6 kernel panics in 2 days) so it's good to know i can still get something done if i screw up.  plus if i get bored i can see how much spyware i can get on there.

---

### Post by Tichondrius on 2005-02-07
[QUOTE=jerome bettis]i just went through the same thing.  i installed ubuntu, got it setup the way i like it, and then found out this class i'm taking uses a windows only CD for some homework problems.  so i had to bite the bullet and scar my laptop with microsoft crap.

anyway, i tried doing what you're doing and it wouldn't work for me.  after some reading, the most comprehensive article i found on this issue [here](http://www.ibiblio.org/pub/Linux/docs/HOWTO/Linux+Win9x+Grub-HOWTO) didn't work.

basically it uses grub to trick winblows into thinking it's actually using sector 0 of the drive, but it's actually using a logical partition.  this would probably work great if you can get windoze installed.

but i had to install it from cd, and i could not for the life of me get grub to recognize my cd rom drive.  it's /dev/hdc and according to the way grub maps it should be (hd1,0) or maybe (hd2,0).  i tried putting so many things in /boot/grub/device.map and tried all sorts of commands in the menu but no matter what it always said specified device does not exist.  maybe installing from a floppy would work, but i don't have one.  i also tried setting up a dos partition, swapped the mapping in grub, and copied the xp cd on there, but that didn't work either - same thing happened.

anyway, i said the hell with it, put the xp cd in, wiped out my hard drive and gave windoze a 2.5 gb primary partition, and left the rest unpartitioned.  i booted into windows once, remembered how much it sucked, and put the ubuntu cd back in.  i left the windows partition alone, and pieced up the rest of my drive like i always do.  i installed grub on the MBR and now i can boot ubuntu and windows fine.

so the basic answer to your question is windows thinks it's the center of the universe and it's much easier just to let it have the primary partition.  install windoze first and then linux.  unless someone knows how to do it the other way???

but as much as i hate microsoft, i have to say, it's nice to have it there as something to fall back on.  i'm always experimenting with linux (6 kernel panics in 2 days) so it's good to know i can still get something done if i screw up.  plus if i get bored i can see how much spyware i can get on there.[/QUOTE]
 To avoid these problems, it's better to install windows in the first primary partition. If current;y your first primary partition is used by something else, you should use a partition editor to resize and/or move the first partition, and then create a new first partition, so you'll be able to install any version windows (some of them are more touchy than others) in that partition. After installing windows, you will need to reinstall grub, because windows will overwrite the master boot record of the hardisk with its own boot loader which only boots the windows partition. 

The best tool to use for this process is a linux live CD, such as knoppix, which has a partition editor (qtparted), as well as grub-install. Also you can always boot from the CD in case something gets messed up with the boot loader on the hardisk, and fix it manually. So the first step is to download the knoppix live CD image file, and burn it onto a blanck CD.   Then boot knoppix, and use qtparted to move and/or resize partitions, so that there is free space in the beginning of the disk. Then create a new partition in that space. Now you should be able to install windows in that partition. Afterwards, boot the knoppix cd again, and reinstall grub, by mounting your linux root partition (and boot partition under it, if you have one), then do "grub-install" and use the "--root-directory=" option to specify the directory where you mounted your root linux partition (e.g. /mnt/tmp). Also make sure to add an entry to boot windows in grubs menu.lst file, and use the "makeactive" instruction there, as some versions of windows will only boot if their partition is marked active. 


Regarding your linked article, it seems very strange that it recommends to try to run the windows installation using grub - that's just doesn't make sense. Grub is a boot loader which let's you choose among partitions of a single hard-drive. It is usually a very bad idea to try to let grub manage partition in more than one drive. So grub should be installed in the MBR of a hard disk, and only manage the partitions on that hardisk ! If you want to boot a partition in a different drive, you can tell the bios to boot that device. So for installing windows, just boot the windows install CD, and let it install normally - into the first partition you prepared for it. As I mentioned, windows will overwrite the MBR (and grub), but you will be able to restore grub easily, by booting knoppix, and re-installing grub. That is the standard procedure after installing windows.
And btw, /dev/hdc which refers to an entire drive is equivalent to (hd2) in grub, not (hd2,0) which refers to a single partition (e.g. /dev/hdc1).

---

### Post by lilpac on 2005-02-07
[QUOTE=jerome bettis]

so the basic answer to your question is windows thinks it's the center of the universe and it's much easier just to let it have the primary partition.  install windoze first and then linux.  unless someone knows how to do it the other way???
.[/QUOTE]

yes , i C
but i can't install windows xp,
the cd woulnd boot :)
Can you help me with that? ( someone)  :confused: 


greetz lilpac

---

### Post by Tichondrius on 2005-02-07
[QUOTE=lilpac]yes , i C
but i can't install windows xp,
the cd woulnd boot :)
Can you help me with that? ( someone)  :confused: 


greetz lilpac[/QUOTE]

just choose the CDROM as the first boot device in the bios, insert your windows install CD in it, and reboot. Presto! it will boot just fine.   (forget about booting a CD from grub, if that's what you're trying to do - it's just silly).

---

