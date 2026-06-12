---
title: "Grub not booting windows 11 when selecting boot manager"
date: 2023-10-19
forum: New to Ubuntu
---

### Post by techcoarse on 2023-10-19
Hello,


Been trying to fix this issue for a few days now, being very new to this all I'm not sure even were to begin but I did some googling and after trying a few things (Cant remember as I've had a day or so off from trying to sort this out so I didn't burn my self out on Linux before I even got to using it properly) so I don't know if they didn't work or if its because I didn't know what I was looking for or what they were even asking me to do.




Anyway, I installed Ubuntu 22.04.3 LTS a few days back got that all going and then tried restarting the pc to see if dual booting worked, so the pc loaded into grub fine but when I go down to Windows boot manager and hit enter I get this:


> error: no such device: 18FE-92BE.
error: file '/efi/Microsoft/Boot/bootmgfw.efi' not found.


press any key to continue...


So after hitting any key I get returned back to grub, I can boot in the boot select of the bios into windows no problem and it even boots into windows after hitting escape and then typing in exit in the console for grub (And it seems typing is quite delayed in grub but I don't know if that's the same issue or a completely unrelated issue), but after doing that twice it seems to just restart the pc into windows.


Any help with this problem would be greatly appreciated!.


Thanks for taking the time to read!

---

### Post by yancek on 2023-10-19
If windows 11 was preinstalled on the computer, it would be an EFI install and there should be a file with the name referred to in the output you posted.  Boot Ubuntu and run these command to get information;

```
sudo parted -l
blkid

```

The first command should output information on your hard drives connected, the partitions on each and their mount points.  There should be an EFI partition.  One of these should be a partition labelled  EFI system partition.  From a file manager or terminal, loot at the /boot/efi/EFI location to see if there is a folder named Microsoft. Also check if there is a folder named ubuntu,  There should be folders named Microsoft and ubuntu if both are UEFI installs.  The   second command will output the UUIDs for each partition and you need to check to see if there is one named:  18FE-92BE.  If not check to see what the UUID is for the EFI partition and if you don't resolve this, post that information here.

That would be the EFI partition.  Does it have another UUID?  Are windows and Ubuntu on the same physical hard drive?

---

### Post by techcoarse on 2023-10-19
Thanks for the reply, the operating systems are on two separate drives, im a little lost with some of the information given but from what i did understand is that both windows drive and ubuntu driver are both EFI System Partitions i couldn't find a UUID matching the one in the output i posted (Maybe im missing it?). I also went to the location you asked for and i found only: 

BOOT
ubuntu

There was no windows folder in the location i looked [here's a screenshot]("https://ibb.co/HPJZHzC") in case i looked in the wrong place.

Here is the output from the commands you asked me to do:

```
techcoarse@CoarseSystems:~$ sudo parted -l
Model: ATA Samsung SSD 860 (scsi)
Disk /dev/sda: 1024GB
Sector size (logical/physical): 512B/512B
Partition Table: gpt
Disk Flags: 

Number  Start   End     Size    File system  Name                          Flags
 1      17.4kB  134MB   134MB                Microsoft reserved partition  msftres
 2      135MB   1024GB  1024GB  ntfs         Basic data partition          msftdata


Model: ATA Samsung SSD 860 (scsi)
Disk /dev/sdb: 1024GB
Sector size (logical/physical): 512B/512B
Partition Table: gpt
Disk Flags: 

Number  Start   End     Size    File system  Name                          Flags
 1      17.4kB  16.8MB  16.8MB               Microsoft reserved partition  msftres
 2      16.8MB  1024GB  1024GB  ntfs         Basic data partition          msftdata


Model: ATA ST2000LX001-1RG1 (scsi)
Disk /dev/sdc: 2000GB
Sector size (logical/physical): 512B/4096B
Partition Table: gpt
Disk Flags: 

Number  Start   End     Size    File system  Name                          Flags
 1      17.4kB  16.8MB  16.8MB               Microsoft reserved partition  msftres
 2      16.8MB  2000GB  2000GB  ntfs         Basic data partition          msftdata


Model: ATA ST2000DM001-1CH1 (scsi)
Disk /dev/sdd: 2000GB
Sector size (logical/physical): 512B/4096B
Partition Table: msdos
Disk Flags: 

Number  Start   End     Size    Type     File system  Flags
 1      1049kB  2000GB  2000GB  primary  ntfs


Model: Samsung SSD 970 PRO 512GB (nvme)
Disk /dev/nvme0n1: 512GB
Sector size (logical/physical): 512B/512B
Partition Table: gpt
Disk Flags: 

Number  Start   End    Size   File system  Name                  Flags
 1      1049kB  538MB  537MB  fat32        EFI System Partition  boot, esp
 2      538MB   512GB  512GB  ext4


Model: CT1000P3PSSD8 (nvme)
Disk /dev/nvme1n1: 1000GB
Sector size (logical/physical): 512B/512B
Partition Table: gpt
Disk Flags: 

Number  Start   End     Size    File system  Name                          Flags
 1      1049kB  106MB   105MB   fat32        EFI system partition          boot, esp
 2      106MB   123MB   16.8MB               Microsoft reserved partition  msftres
 3      123MB   999GB   999GB   ntfs         Basic data partition          msftdata
 4      999GB   1000GB  715MB   ntfs                                       hidden, diag


techcoarse@CoarseSystems:~$ blkid
/dev/nvme0n1p2: UUID="c4bfc7e0-3172-4a95-8957-01170f5e995e" BLOCK_SIZE="4096" TYPE="ext4" PARTUUID="6de15e76-3e4c-4a72-bebe-57131764843b"

```

CT1000P3PSSD8 is windows
Samsung SSD 970 PRO is ubuntu

---

### Post by ajgreeny on 2023-10-19
See **Boot-Repair** in my signature below and follow the instructions there to run the Boot-Info-Script which you can do either from your installed Ubuntu or from the live USB system.

**Do not run any default repair just yet** but simply copy back here the pastebin link you get which will show us a lot more about your system.

---

### Post by techcoarse on 2023-10-19
Here you go as requested 

[https://paste.ubuntu.com/p/XftTpqHZVW/](https://paste.ubuntu.com/p/XftTpqHZVW/)

---

### Post by tea for one on 2023-10-19
I can't see anything drastically wrong in the boot-repair report.
Perhaps Grub was confused by the presence of 5 other drives and did not find/install the Windows Boot Manager correctly?

Anyway, try this first:-
Remove or isolate the non-os storage drives (sda, sdb, sdc and sdd)
Leave both the nvme disks attached
Make sure Windows 10/11 is not hibernating.
Boot into the installed Ubuntu 22.04
Open a terminal and enter:-
```
sudo update-grub
```
Please post the output within code tags (via Adv Reply)

If no errors are reported, see if Windows boots via Grub.
Fingers crossed................

---

### Post by techcoarse on 2023-10-19
Here is the output when i tested, didnt know how to make sure windows 11 wasnt hibernating so i just went past that step to see if this will work.

Here is the output requested on my first run of update.
```
techcoarse@CoarseSystems:~$ sudo update-grub
[sudo] password for techcoarse: 
Sourcing file `/etc/default/grub'
Sourcing file `/etc/default/grub.d/init-select.cfg'
Generating grub configuration file ...
Found linux image: /boot/vmlinuz-6.2.0-34-generic
Found initrd image: /boot/initrd.img-6.2.0-34-generic
Found linux image: /boot/vmlinuz-6.2.0-26-generic
Found initrd image: /boot/initrd.img-6.2.0-26-generic
Memtest86+ needs a 16-bit boot, that is not available on EFI, exiting
Warning: os-prober will be executed to detect other bootable partitions.
Its output will be used to detect bootable binaries on them and create new boot entries.
Found Windows Boot Manager on /dev/nvme1n1p1@/efi/Microsoft/Boot/bootmgfw.efi
Adding boot menu entry for UEFI Firmware Settings ...
done
techcoarse@CoarseSystems:~$ 

```

Will report back here once ive tested to see if it boots into windows

---

### Post by techcoarse on 2023-10-19
Hope the double post is fine as it has been a few minutes but i just wanted to post an update, everything seem to have worked grub is now booting windows! (even now with all the drives plugged back in!) i wanted to say thanks to everyone involved!

---

### Post by tea for one on 2023-10-19
> **techcoarse said:**
> Hope the double post is fine as it has been a few minutes but i just wanted to post an update, everything seem to have worked grub is now booting windows! (even now with all the drives plugged back in!) i wanted to say thanks to everyone involved!That's good news.
A second post with a successful result is more than welcome.

---

### Post by techcoarse on 2023-10-20
Well, i didn't want to re-open this so to speak but I just restarted ubuntu to boot into windows and grub is doing that error again, I know how to fix it but I don't know if this is going to be a repeated thing or not (and to be able to see what im doing id have to move some furniture to be able to unplug all the drives again every time is a lil much lol.

Thanks again and sorry that I reopened this topic so to speak (If this isn't what i was suppose to do I'm sorry I didn't know where else to go)

---

### Post by tea for one on 2023-10-20
It's OK to revisit a thread if the original problem persists.

I noticed in the boot-repair report that:-
Line 135 - SecureBoot enabled according to mokutil 

Can you access your UEFI firmware, disable Secure Boot and then update-grub again.

---

### Post by techcoarse on 2023-10-20
Is there a way to get grub to not scan the drives without disconnecting all the drives again?

---

### Post by oldfred on 2023-10-20
I copy boot stanza from grub first run (or my records) into 40_custom. And then turn off os-prober in grub settings.
That speeds the grub update as I have lots of partitions that os-prober has to look at.

cat /etc/default/grub
I add this or change from false to true
[FONT=monospace][COLOR=#000000]GRUB_DISABLE_OS_PROBER=true

Very first thing I do is this, to have a copy of the original grub.
[/COLOR][/FONT]sudo cp -a /boot/grub/grub.cfg /boot/grub/grub.cfg.backup

I then add any other boot stanzas into 40_custom.
Using 40_custom & Custom menu
[https://help.ubuntu.com/community/MaintenanceFreeCustomGrub2Screen](https://help.ubuntu.com/community/MaintenanceFreeCustomGrub2Screen)
[https://help.ubuntu.com/community/Grub2/CustomMenus](https://help.ubuntu.com/community/Grub2/CustomMenus)
[https://askubuntu.com/questions/1425637/how-can-i-add-windows-11-to-grub-menu](https://askubuntu.com/questions/1425637/how-can-i-add-windows-11-to-grub-menu) &

---

### Post by techcoarse on 2023-10-21
Hey,

So i booted up since i took a break from my pc since ive been working on it alot recently so i needed to take a night off. 
Anyway i booted up today and on the off chance that it just decided to work well....ive done nothing to my pc and it decided to boot windows again @_@

---

### Post by tea for one on 2023-10-21
I think it was Einstein who said "Keep trying the same thing and expecting a different result is insanity"?
He also said "Dual booting, that's tricky business" ;)

In the meantime, have a look at your UEFI settings and see if you can disable Fast Boot.

---

### Post by techcoarse on 2023-10-21
alright i have done that and it seems to have sorted it so im going to tentatively set this as resolved and see where einstein takes me ;-) thanks alot for the help

---

