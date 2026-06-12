---
title: "Grub 2 expert required - apply within!"
date: 2012-01-22
forum: New to Ubuntu
---

### Post by davidc60 on 2012-01-22
[FONT=Lucida Console][SIZE=3]I have recently tried to add entries for other operating systems to the Grub2 menu by adding entries to the 40_custom file in /etc/grub.d/ in Lubuntu. As it happens, this was not successful so I restored the 40_custom file to the way it was before I changed it. This in itself is not the issue I am now concerned about. [/SIZE][/FONT]

[FONT=Lucida Console][SIZE=3]The real problem is that since trying to add those new entries I have not been able to boot into the HDD of my computer in the normal way (ie. by simply pressing the power-on button); when I try to do so I get the message:[/SIZE][/FONT]
[FONT=Lucida Console][SIZE=3]error: file not found[/SIZE][/FONT]
[FONT=Lucida Console][SIZE=3]grub rescue>[/SIZE][/FONT]

[FONT=Lucida Console][SIZE=3]I can boot into the computer via an USB which contains a backup of one of my operating systems and this enables me to access both the backup operating system on the USB and also all of the other operating systems that are on the HDD. [/SIZE][/FONT]

[FONT=Lucida Console][SIZE=3]From the OS that is on the USB I have tried running sudo grub-install /dev/sda and this returns the message:[/SIZE][/FONT]
[FONT=Lucida Console][SIZE=3]/usr/sbin/grub-setup: warn: no signature.[/SIZE][/FONT]
[SIZE=3][FONT=Lucida Console]/usr/sbin/grub-setup: error: embedding is not possible, but this is required for cross-disk install.[/FONT][/SIZE]

[SIZE=3][FONT=Lucida Console]I have also tried running sudo grub-install /dev/sda from one of the Linux OS's on the HDD itself and this returns the message:[/FONT][/SIZE]
[FONT=Lucida Console][SIZE=3]/usr/sbin/grub-setup: warn: no signature.[/SIZE][/FONT]
[FONT=Lucida Console][SIZE=3]/usr/sbin/grub-setup: warn: Embedding is not possible. GRUB can only be installed in this setup by using blocklists. However, blocklists are UNRELIABLE and their use is discouraged.[/SIZE][/FONT]
[FONT=Lucida Console][SIZE=3]/usr/sbin/grub-setup: error: will not proceed with blocklists.[/SIZE][/FONT]
 
 
[SIZE=3][FONT=Lucida Console]The net effect is that my GRUB 2 bootloader is presently in a bad way and **my question is simply whether it can be repaired and, if so, how? **[/FONT][/SIZE]

[FONT=Lucida Console][SIZE=3](NB. I am not seeking advice about using a SuperGrub2 disk as I can already access the HDD (via a USB), I just simply cannot do so in the correct/normal way).[/SIZE][/FONT]

[FONT=Lucida Console][SIZE=3]Some other miscellaneous background information that may or may not assist in your deliberations about this problem:[/SIZE][/FONT]

[FONT=Lucida Console][SIZE=3]- I have tried to access /usr/sbin/grub-setup but cannot open the file.[/SIZE][/FONT]

[FONT=Lucida Console][SIZE=3]- when I open 'Gparted' it shows the whole of the HDD as 'unallocated' which is obviously nonsense as I can still access all of the operating systems on it (via a USB). [/SIZE][/FONT]

[FONT=Lucida Console][SIZE=3]- when I run 'Disk Utility' I can still view my operating systems on the HDD but it does not function correctly either. Having said that, I was able to use the Disk Utility to erase Lubuntu (where the trouble started) and then use Pudd drive/partition copier to 'dd' a fresh version of Lubuntu into the empty space left by the old Lubuntu.[/SIZE][/FONT]

[FONT=Lucida Console][SIZE=3]- After that I again tried running sudo grub-install /dev/sda from the brand new Lubuntu but again got the same error message about blocklists.[/SIZE][/FONT]

[FONT=Lucida Console][SIZE=3]- I could not install that new Lubuntu from the Live USB directly on to the HDD because the Lubuntu installer simply did not show any drives/partitions for /dev/sda as it usually does. [/SIZE][/FONT]

[FONT=Lucida Console][SIZE=3]- I have tried installing Lubuntu from a Live USB onto a second USB and, crucially for the purpose of this message, selecting to put the bootloader onto the HDD (ie. /dev/sda rather than /dev/sdb as usual for a second USB) but when it got to the 'grub-install' stage of the process it returned a 'fatal error' message and the process failed.[/SIZE][/FONT]

[FONT=Lucida Console][SIZE=3]- running 'sudo fdisk -l' returns the following:[/SIZE][/FONT]
[FONT=Lucida Console][SIZE=3]omitting empty partition (16)[/SIZE][/FONT]
 
[FONT=Lucida Console][SIZE=3]Disk /dev/sda: 250.1 GB, 250059350016 bytes[/SIZE][/FONT]
[FONT=Lucida Console][SIZE=3]255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors[/SIZE][/FONT]
[FONT=Lucida Console][SIZE=3]Units = sectors of 1 * 512 = 512 bytes[/SIZE][/FONT]
[FONT=Lucida Console][SIZE=3]Sector size (logical/physical): 512 bytes / 512 bytes[/SIZE][/FONT]
[FONT=Lucida Console][SIZE=3]I/O size (minimum/optimal): 512 bytes / 512 bytes[/SIZE][/FONT]
[FONT=Lucida Console][SIZE=3]Disk identifier: 0x2a7df72b[/SIZE][/FONT]
 
[FONT=Lucida Console][SIZE=3]**_Device Boot Start End Blocks Id System_**[/SIZE][/FONT]
[FONT=Lucida Console][SIZE=3]/dev/sda1 2048 81922047 40960000 7 HPFS/NTFS/exFAT[/SIZE][/FONT]
[FONT=Lucida Console][SIZE=3]/dev/sda2 488353792 488395439 20824 ef EFI (FAT-12/16/32)[/SIZE][/FONT]
[FONT=Lucida Console][SIZE=3]/dev/sda3 * 81924094 488353791 203214849 5 Extended[/SIZE][/FONT]
[FONT=Lucida Console][SIZE=3]/dev/sda5 81924096 87781375 2928640 82 Linux swap / Solaris[/SIZE][/FONT]
[FONT=Lucida Console][SIZE=3]/dev/sda6 87783424 97546239 4881408 83 Linux[/SIZE][/FONT]
[FONT=Lucida Console][SIZE=3]/dev/sda7 97548288 107311103 4881408 83 Linux[/SIZE][/FONT]
[FONT=Lucida Console][SIZE=3]/dev/sda8 153727039 162996480 4634721 83 Linux[/SIZE][/FONT]
[FONT=Lucida Console][SIZE=3]/dev/sda9 486305792 488353791 1024000 82 Linux swap / Solaris[/SIZE][/FONT]
[FONT=Lucida Console][SIZE=3]/dev/sda10 107313152 123697151 8192000 83 Linux[/SIZE][/FONT]
[FONT=Lucida Console][SIZE=3]/dev/sda11 123699200 133462015 4881408 83 Linux[/SIZE][/FONT]
[FONT=Lucida Console][SIZE=3]/dev/sda12 133464064 143226879 4881408 83 Linux[/SIZE][/FONT]
[FONT=Lucida Console][SIZE=3]/dev/sda13 143228928 153726975 5249024 83 Linux[/SIZE][/FONT]
[FONT=Lucida Console][SIZE=3]/dev/sda14 162998272 174714879 5858304 83 Linux[/SIZE][/FONT]
[FONT=Lucida Console][SIZE=3]/dev/sda15 174716928 186433535 5858304 83 Linux[/SIZE][/FONT]
 
[FONT=Lucida Console][SIZE=3]Partition table entries are not in disk order[/SIZE][/FONT]
 
[FONT=Lucida Console][SIZE=3]Disk /dev/sdb: 4030 MB, 4030726144 bytes[/SIZE][/FONT]
[FONT=Lucida Console][SIZE=3]233 heads, 63 sectors/track, 536 cylinders, total 7872512 sectors[/SIZE][/FONT]
[FONT=Lucida Console][SIZE=3]Units = sectors of 1 * 512 = 512 bytes[/SIZE][/FONT]
[FONT=Lucida Console][SIZE=3]Sector size (logical/physical): 512 bytes / 512 bytes[/SIZE][/FONT]
[FONT=Lucida Console][SIZE=3]I/O size (minimum/optimal): 512 bytes / 512 bytes[/SIZE][/FONT]
[FONT=Lucida Console][SIZE=3]Disk identifier: 0x00034ef0[/SIZE][/FONT]
 
[FONT=Lucida Console][SIZE=3]Device Boot Start End Blocks Id System[/SIZE][/FONT]
[FONT=Lucida Console][SIZE=3]/dev/sdb1 * 2048 7870463 3934208 83 Linux[/SIZE][/FONT]
 
[FONT=Lucida Console][SIZE=3]For the record, the HDD has Windows 7 Starter on the first (primary) partition and the rest is essentially taken up by an Extended partition containing several Linux-related disros on logical drives). Everything was working perfectly until I started trying to amend the '40_custom' file in Lubuntu. [/SIZE][/FONT]

---

### Post by westie457 on 2012-01-22
[http://ubuntuforums.org/showthread.php?t=1581099](http://ubuntuforums.org/showthread.php?t=1581099)

Take a look at the above link, it might be what you are looking for.

---

### Post by ankspo71 on 2012-01-22
I'm not an expert on the subject but...

If the above guide doesn't work then you might need to reconfigure grub 2 from your Live CD/USB as seen in this next guide (which has saved me several times already). This does not say how to add additional entries though (see other links below).
[http://www.webupd8.org/2010/05/fix-symbol-grubputs-not-found-when.html](http://www.webupd8.org/2010/05/fix-symbol-grubputs-not-found-when.html) .

Adding OS Entries to Grub Legacy (not Grub2):
[http://www.dedoimedo.com/computers/grub.html#mozTocId286308](http://www.dedoimedo.com/computers/grub.html#mozTocId286308)

Using a 'Grub 2' and 'Grub Legacy' multiboot/multigrub setup:
[http://www.dedoimedo.com/computers/grub-2.html#mozTocId982259](http://www.dedoimedo.com/computers/grub-2.html#mozTocId982259)

PS. Sometimes it's better to have your favorite distro installed to the hard drive, then install the additional distros individually in a virtual machine such as virtualbox, since updates can break grub setups, and it can prevent other mishaps from happening too.

Hope this helps

---

### Post by oldfred on 2012-01-24
I would prefer to see a boot info script and use the beta version as it has some fixes. You show an efi partition but it is not first. UEFI requires efi to be first, so you are still BIOS.

Boot Repair:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or post the link to a run of boot info script so we can see your exact configuration. May be better to run the git/beta version of boot script as it has some fixes.

or you  can directly down load the test version of boot info script:

```
wget -O bootinfoscript 'http://bootinfoscript.git.sourceforge.net/git/gitweb.cgi?p=bootinfoscript/bootinfoscript;a=blob_plain;f=bootinfoscript;hb=HEAD'
chmod a+x bootinfoscript
sudo bash bootinfoscript

```

I have edited 40_custom a lot. The new version does not accept typos. I had a typo for a long time in my 40_custom but with grub2 1.99 it stopped working.

---

### Post by davidc60 on 2012-01-28
Hi, thanks to everyone for your excellent replies. I managed to fix the booting-up problem by running: **sudo dpkg-reconfigure grub-pc **as described in one of the articles referred to above. I did run the 'boot info script' before and after doing this but as the booting problem is resolved I won't now post this. Thanks again,
davidc

---

### Post by oldfred on 2012-01-29
Glad you got it resolved.

I also like to keep a recent copy of boot script's results.txt, just so I have the details of how my system is configured. I even went back and added it to the rsync script I run for backup.

---

### Post by davidc60 on 2012-01-30
[LEFT]Hi, 
thanks to 'oldfred' for your further reply. I was going to ask you about EFI/BIOS (see your previous comments) but I have just found one of your earlier posts which was very helpful in this regard.
thanks,
davidc
[/LEFT]

---

