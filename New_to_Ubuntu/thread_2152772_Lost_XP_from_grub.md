---
title: "Lost XP from grub"
date: 2013-06-08
forum: New to Ubuntu
---

### Post by katalla on 2013-06-08
Hi im new to ubuntu and have been using it for 4 months now. i have been having sound problems recently so i got a command online that reinstalled grub and some other stuff oops.
so now windows is gone from the boot menu. i did the update grub and get this
{Generating grub.cfg ...
Found linux image: /boot/vmlinuz-3.2.0-45-generic-pae
Found initrd image: /boot/initrd.img-3.2.0-45-generic-pae
Found linux image: /boot/vmlinuz-3.2.0-41-generic-pae
Found initrd image: /boot/initrd.img-3.2.0-41-generic-pae
Found linux image: /boot/vmlinuz-3.2.0-40-generic-pae
Found initrd image: /boot/initrd.img-3.2.0-40-generic-pae
Found linux image: /boot/vmlinuz-3.2.0-39-generic-pae
Found initrd image: /boot/initrd.img-3.2.0-39-generic-pae
Found linux image: /boot/vmlinuz-3.2.0-38-generic-pae
Found initrd image: /boot/initrd.img-3.2.0-38-generic-pae
Found linux image: /boot/vmlinuz-3.2.0-37-generic-pae
Found initrd image: /boot/initrd.img-3.2.0-37-generic-pae
Found linux image: /boot/vmlinuz-3.2.0-36-generic-pae
Found initrd image: /boot/initrd.img-3.2.0-36-generic-pae
Found linux image: /boot/vmlinuz-3.2.0-35-generic-pae
Found initrd image: /boot/initrd.img-3.2.0-35-generic-pae
Found linux image: /boot/vmlinuz-3.2.0-29-generic-pae
Found initrd image: /boot/initrd.img-3.2.0-29-generic-pae
Found memtest86+ image: /boot/memtest86+.bin
done}

when i enter sudo fdisk -lu
{Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x4b36bdea

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *     7598745   156280319    74340787+   7  HPFS/NTFS/exFAT
/dev/sda2              63     7598744     3799341    b  W95 FAT32

Partition table entries are not in disk order

Disk /dev/sdb: 30.8 GB, 30750031872 bytes
255 heads, 63 sectors/track, 3738 cylinders, total 60058656 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x9dc96e9e

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *          63    37075404    18537671    7  HPFS/NTFS/exFAT
/dev/sdb2        37076990    60057599    11490305    5  Extended
/dev/sdb5        55902208    60057599     2077696   82  Linux swap / Solaris
/dev/sdb6        37076992    55902207     9412608   83  Linux

Partition table entries are not in disk order}

i tried adding this to the grub.cfg file
 menuentry "Windows xp " {
set root=(hd0,1)
chainloader (hd0,1)+1}

this puts windows on the boot menu but then it says the NTLDR is missing and press ctrl alt del to restart.
any help would be great i dont know what else to try and would like to get my windows back .
Thanks

---

### Post by varunendra on 2013-06-09
> **katalla said:**
> this puts windows on the boot menu but then it says the **NTLDR is missing** and press ctrl alt del to restart.

So did you check if NTLDR is really missing? In order for grub to recognize a win XP installation, I believe these three files are necessary to be on its boot partition -
[LIST]
[*]NTLDR
[*]ntdetect.com
[*]boot.ini
[/LIST]
If the file is really missing, you can simply copy it from another computer that has XP running. The harder way is to boot with XP installation CD, choose to go into repair mode, and run "fixboot" command from there. But then you'll have to reinstall Grub.


Oh, and Welcome to the forums katalla ! :)

**PS:**
By the way, you have a lot of unnecessary older kernels installed. If your current Ubuntu installation is working fine, it is recommended to delete all but one last older kernel. This will free a lot of space on your drive which is quite valuable for you since they are only 80 and 30 GB in size.

---

### Post by katalla on 2013-06-09
Hi Varun, Im not sure i don't know exactly how to check if its missing. i do have a back up restore copy on my hd so i have the file but dont know how to view the windows partition through ubuntu. Im reading the mounting procedure and will try it

---

### Post by varunendra on 2013-06-09
Are you using default Ubuntu or Xubuntu?

In default Ubuntu, if you open the file browser (the folder icon in the left side launcher), it should show all your drives/partitions in the left pane. Clicking on any of it should automatically mount and open it.

The NTLDR file should be located at the root (means right in the partition, not in any folder in it) of the partition where XP is installed. This partition can be easily identified by its contents. It must have Windows, Documents and Settings, Program Files, etc. folders. And besides these folders, there must be the three files (among a few others) that I mentioned above.

---

### Post by katalla on 2013-06-09
Ntldr is there so is ntdetect but i cannot find boot.ini , can i download this file somewhere ?
thanks about the old kernals ill look up how to get rid of the old ones :)

---

### Post by varunendra on 2013-06-09
> **katalla said:**
> Ntldr is there so is ntdetect but i cannot find boot.ini , can i download this file somewhere ?
thanks about the old kernals ill look up how to get rid of the old ones :)
You can manually create one using any simple text editor (not advanced ones like libre office writer).

However, it is quite possible that your XP was actually booting from the other hard disk, and as such, it is possible that these files are (should be) also located in the boot partition of the other drive. Please double-check it.

I am suspecting that because the error message was about NTLDR, not boot.ini. So it is possible that the other hard disk's boot partition has the boot.ini file but not the NTLDR. If so, you can just copy the found copy of ntldr there and retry update-grub.

Accordingly, please check the other partitions as well to see if any of them have any of the three files (ntdetect.com, ntldr, boot.ini). If found, post back and forget what is suggested below.


**ONLY IF THE ABOVE CHECK FAILS (no copies of any of the three files are found on any other partition) :**

If you are absolutely sure that the other partitions don't have any of the three files, ONLY THEN follow what is suggested below -

The contents of a typical boot.ini file, for example, are -
> [boot loader]
timeout=30
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect

[LIST]
[*]The first line should be exactly same as above.
[*]The second line's value can be changed but leave it as it is above. It's value doesn't matter in your setup.
[*]The third line is important and can be different depending on your setup. It should be exactly same as what is in the left of the equal sign in the last line.
[*]The fourth line should be exactly same as above.
[*]The fifth line is the only one which may take some experiment to be successful. The values in the braces may change depending on the location of your XP installation. You may just copy the above to begin with. If it returned error, we can try changes.
[/LIST]


Just copy the above lines in an empty text file, and save the file as "boot.ini".
**[COLOR="#FF0000"]IMPORTANT :[/COLOR]** Since you will be using Ubuntu to save the file, make sure the "Line Ending" is set to "Windows" (this setting is located at the bottom of the "Save" dialogue box in Gedit)

---

### Post by katalla on 2013-06-09
Wow thats crazy, grub now sees windows when updated. i made the boot.ini file using gedit, now when i launch windows it goes into recovery mode and wants to reformat the drives. should i do that then reinstall ubuntu? or is there something else we can try.
Thanks for all the help btw :)

---

### Post by varunendra on 2013-06-09
> **katalla said:**
> now when i launch windows it goes into recovery mode and wants to reformat the drives. should i do that then reinstall ubuntu? or is there something else we can try.

Depends on which drives does it want to format, or if you have anything to save. Regardless, it sounds like the XP installation has corrupted, and I don't think formatting 'other' drives can fix xp itself.

While you are in XP, try doing a disk scan on the partition on which xp itself is installed. Use the "disk scan" utility or "chkdisk /f" command to do so. It will be done at reboot > booting into XP.

Then try booting into XP in normal mode. If you can, then you may try whatever suits you best. If however, you can't boot into normal mode even after the disk scan, then I'm afraid re-installing XP can be the only proper fix.

In any case, backup your important data on an external drive first. You never know what these actions can eventually lead to ;)


**EDIT:**
Oh wait !!
Is it "Recovery Mode" or "Safe Mode" of XP?
Looks like you actually booted the "Recovery Partition" of the drive. :-o

---

### Post by katalla on 2013-06-09
Thank Varun, it doesnt give me any choices other than an ok to format the drives. Sounds like it is toast, it had a good 8 year run haha. i will back up my stuff then wipe everything and use Ubuntu only since i dont have the windows CD plus my CD drive is dead anyway :)
Thank You
Karim

---

### Post by varunendra on 2013-06-09
> **katalla said:**
> Thank Varun, it doesnt give me any choices other than an ok to format the drives.

Please take a look at my Edit in my previous post. I confused "Recovery Mode" with "Safe Mode" (although immediately realized the mistake).

So indeed it looks like you are booting the wrong partition (Recovery Partition created by the OEM), and XP is on another one. While proceeding with the Recovery prompt *should* work (it will restore the laptop to its original state when you bought it), I hope that simply booting the correct partition should be as easier and should save you the hassle of re-installing/updating the applications and OS.

Let me know if you need help with that. :)


**PS:**
Oh, by the way, if the lappy is 8 years old, then the default Ubuntu with Unity may not be a good choice considering performance. Take a look at [Xubuntu]("http://xubuntu.org/getxubuntu/") or [Lubuntu]("https://help.ubuntu.com/community/Lubuntu/GetLubuntu") instead and see if they suffice your needs.

Also, I'd recommend to keep this "Recovery" partition in case you need your XP back for some reason. After all, you have 'paid' for this OS :D

---

