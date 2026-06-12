---
title: "Problem installing Ubuntu alongside Windows 7 (possibly UEFI/GPT-related)"
date: 2012-03-08
forum: New to Ubuntu
---

### Post by rilgoom on 2012-03-08
(Apologies if this should have gone in the Installation Support forum instead.)

So I've got two hard drives, A and B. Windows 7 64-bit is installed on hard drive A. I want to install Ubuntu 11.10 64-bit on hard drive B and be able to boot into either OS. Hard drive A's space is taken up entirely by Windows 7, but hard drive B's space is entirely unallocated, ready for Ubuntu to be installed on it.

When I reach the Installation type screen in the Ubuntu installation wizard, I am told that "This computer currently has no detected operating systems", even though it should detect Windows 7. See below.

[[IMG]http://i.imgur.com/okaqbl.png[/IMG]]("http://i.imgur.com/okaqb.png")

Now I don't know much about Ubuntu (or OSes in general), but I've got a hunch that the reason the Ubuntu installer doesn't detect Windows 7 is that because Windows 7 is on a GPT drive.

I'm pretty sure I can't just install Ubuntu with either option the installer gives me and expect to be able to dual-boot (or boot at all) after that. So what are my options? Note that my Windows 7 install is still rather fresh, so I *could* reinstall it if I have to, but I'm hoping there's another solution.

Oh, and in case you need it for troubleshooting, here's the fdisk -l output for both drives (gptfdisk in drive A's case):

```

Disk /dev/sda: 1250263728 sectors, 596.2 GiB
Logical sector size: 512 bytes
Disk identifier (GUID): 9BF0FF1B-4CCC-48DA-AE3E-4D07C2375125
Partition table holds up to 128 entries
First usable sector is 34, last usable sector is 1250263694
Partitions will be aligned on 2048-sector boundaries
Total free space is 2669 sectors (1.3 MiB)

Number  Start (sector)    End (sector)  Size       Code  Name
   1            2048          206847   100.0 MiB   EF00  EFI system partition
   2          206848          468991   128.0 MiB   0C01  Microsoft reserved part
   3          468992      1250263039   595.9 GiB   0700  Basic data partition



Disk /dev/sdb: 250.1 GB, 250058268160 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488395055 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000928d0

```

---

### Post by NikTh on 2012-03-08
Hi , 
I am curius to see how you will solve your problem. I never hear or read again about GTP problems on ubuntu. 
But i have something to suggest. Format your unlocated space (/dev/sdb) to some file system (Ext4 ,ntfs ...) and run again installer. Continue then with the option of  " Something Else" and install ubuntu to that drive. Of course i don't know if grub will be capable to see your windows installation. 

Good Luck.

---

### Post by theducksfan2010 on 2012-03-08
Click on the something else option, it will allow you to choose which hard drive you want to install Ubuntu on, just pick the one without Windows 7.

You would also be able to pick the drive with Windows on it to hold the Grub (assuming your Bios is set to load off of Primary Hard drive and that is the one you have Windows on).

---

### Post by rilgoom2 on 2012-03-08
> **theducksfan2010 said:**
> Click on the something else option, it will allow you to choose which hard drive you want to install Ubuntu on, just pick the one without Windows 7.
That would let me install Ubuntu, but would it not also overwrite the boot loader so that I wouldn't be able to boot into Windows 7 anymore? That's what I'm worried about.

And I don't know anything about configuring GRUB.

---

### Post by rilgoom2 on 2012-03-09
Alright, so I decided to try my luck and just install Ubuntu on drive B and see how that works out (using the scary "Erase disk" option in the installer).

Turns out that since I'm using a UEFI system, I don't actually need the Ubuntu installer (GRUB?) to see Windows 7. Apparently every EFI BIOS has its own boot loader that lets you select which boot loader to boot into (I think this is called chainloading?). I can simply change between Windows' and Ubuntu's boot loader in the EFI BIOS and boot into either OS without any problems. It's a little awkward, but it works.

If a mod sees this, please mark this thread as solved.

---

### Post by pootan on 2012-03-09
Just so you know if you installed the grub2 bootloader to the same disk as the Ubuntu install, let's say: dev/sdb for example, then you could set the second disk as the default boot and it will show you Ubuntu and Windows while keeping the MBR on the windows disk whole. Perhaps this is the way it turned out for you, so go ahead and try setting the second disk as the default boot option and see how you go.

---

### Post by NikTh on 2012-03-09
> **rilgoom2 said:**
> Alright, so I decided to try my luck and just install Ubuntu on drive B and see how that works out (using the scary "Erase disk" option in the installer).

Turns out that since I'm using a UEFI system, I don't actually need the Ubuntu installer (GRUB?) to see Windows 7. Apparently every EFI BIOS has its own boot loader that lets you select which boot loader to boot into (I think this is called chainloading?). I can simply change between Windows' and Ubuntu's boot loader in the EFI BIOS and boot into either OS without any problems. It's a little awkward, but it works.

If a mod sees this, please mark this thread as solved.

Those was good informations . 
Thank you. 

You can mark this thread as solved. (Thread tools). ;)

---

### Post by oldfred on 2012-03-11
We have a new test version of the boot info script and want to make sure it sees efi partitions correctly. 

Could you run this only your system and post the results.txt it creates.

```
wget -O bootinfoscript 'http://bootinfoscript.git.sourceforge.net/git/gitweb.cgi?p=bootinfoscript/bootinfoscript;a=blob_plain;f=bootinfoscript;hb=HEAD'
chmod a+x bootinfoscript
sudo bash bootinfoscript

```

If you need some instructions the old current version has some instructions:
Boot Info Script courtesy of forum members meierfra & Gert Hulselmans
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste contents of results.txt in a New Reply, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the New Reply Edit toolbar and then paste the contents between the generated [ code] paste here [ /code] tags.
V60 has improved formating and requires code tags to make it legible. New Version is a zip file that you have to extract to get .sh to run.
Install these before running script:
sudo apt-get install gawk
sudo apt-get install xz-utils

---

### Post by gaxi on 2012-06-06
I still cannot understand what is happening. Why can't I install Ubuntu alongside Windows, when UEFI/GPT is in use?
My Ubuntu-installation-window looks the same as in the first message of this thread. The destination disk is shown empty in the installer ("free space") - but fdisk and Ubuntu's disk utulity show the NTFS-partitions properly.

What is the difference between the disk-util and the installer?

I need to install Ubuntu on this disk alongside and I have no chance to reinstall Windows...

Is this impossible?

Thanks, GaXi

---

### Post by oldfred on 2012-06-06
@gaxi
If you have gpt partitions fdisk will not show the partitions, it just shows one large gpt partition.
Post this:
```
sudo parted /dev/sda unit s print
```

---

### Post by wiak on 2013-04-13
hey i have the same problem
trying to install xubuntu 12.10 x64 on a 256GB SSD with a Windows 8 x64 partition
i have even tried make sure u(x)buntu will find a linux partition by using easeus partition master in windows to make the ext3 partition 
i tried booting both as UEFI or standard via ASUS EFI BIOS boot options
the installer always sees the disk as empty 256gb disk same does gparted, but not fdisk it seems
will try to get more reports on this, its a annoying issue

> Disk /dev/sda: 256.1 GB, 256060514304 bytes
255 heads, 63 sectors/track, 31130 cylinders, total 500118192 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000217e3


   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048      718847      358400    7  HPFS/NTFS/exFAT
/dev/sda2          718848   450203240   224742196+   7  HPFS/NTFS/exFAT
/dev/sda3       450205560   500103449    24948945   83  Linux


system is
AMD FX-8350
Sabertooth 990FX R2.0
32GB Patriot 1600mhz CL9 DDR3
Samsung 840 PRO 256GB
Windows 8 Professional x64

---

### Post by oldfred on 2013-04-13
Do you have Windows hibernated?
Was drive every part of RAID or RAID set in BIOS?
Does NTFS need chkdsk? Even if it boots ok?

---

### Post by wiak on 2013-04-14
> **oldfred said:**
> Do you have Windows hibernated?
Was drive every part of RAID or RAID set in BIOS?
Does NTFS need chkdsk? Even if it boots ok?
found the issue, the drive was mbr but it also had some leftovers from gpt, i used fixparts to fix it
[http://www.rodsbooks.com/fixparts/](http://www.rodsbooks.com/fixparts/)

---

