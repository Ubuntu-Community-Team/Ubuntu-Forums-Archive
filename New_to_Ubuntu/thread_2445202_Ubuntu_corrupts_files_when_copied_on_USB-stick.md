---
title: "Ubuntu corrupts files when copied on USB-stick"
date: 2020-06-10
forum: New to Ubuntu
---

### Post by ivan422 on 2020-06-10
Greetings everyone,

I started using Ubuntu on my old laptop (2007) in february 2020 in order to do basic things such as getting my emails and writing for my projects.

I have the following issue:
Whenever I copy a file on my USB-stick, the files can be accessed until I eject the USB-stick or shutdown my laptop. Afterward, it gives me an error message such as the following whenever I try to open it:
"Impossible d&#8217;ouvrir le document « file:///media/benjamin/ClefUSB256GB/imprimer/retouretiket(1).pdf ».
Le type de fichier modèle (binaire) STL 3D (model/x.stl-binary) n&#8217;est pas pris en charge"
My computer is set in french so I will translate the error message:
"Unable to open the file « file:///media/benjamin/ClefUSB256GB/imprimer/retouretiket(1).pdf ».
The model type file (binary) STL 3D (model/x.stl-binary) is not handled"

The issue does not appear when I use the USB-stick on a Windows computer. I sent the original files through emails and my reciever was able to open them. The issue appears also when I work on a file directly on the USB-stick using Ubuntu.

I would like to be able to fully use Ubuntu and my USB-stick. The problematic files are often ".doc", ".docx", and ".pdf" type. I use libreoffice (openoffice) native from Ubuntu.

According to the general guidelines, the following information could be helpful:
I installed Ubuntu using a boot USB-stick. At the time, it was Ubuntu LTS 16.0.4 (32bits). Later, Ubuntu offered to update itself to 18.04.4 LTS (32bits), which I accepted.

The USB-stick was formated using Ubuntu. When I check its type it says "fuse".

The USB-stick contains various types of files and a VeraCrypt partition for work files. I have not yet had issues with the VeraCrypt partition.

Would anyone have ideas on how to fix this issue, please?

PS: I do not know if it is important but Ubuntu usually asks me to empty the recycle bin before ejecting the USB-stick. I tried to accept and to refuse and it did not seem to change anything.

Regards,
ivan42.

---

### Post by ActionParsnip on 2020-06-10
What file system is used by the USB stick please?
Does it get used in Windows systems as well as Linux?
Do you use the safe remove feature in the OS before you physically unplug the device?

---

### Post by ivan422 on 2020-06-10
> **ActionParsnip said:**
> What file system is used by the USB stick please?
Does it get used in Windows systems as well as Linux?
Do you use the safe remove feature in the OS before you physically unplug the device?

Hello,
Here are answers:

What file system is used by the USB stick please?
-> Would you explain to me how to get that information, please?

Does it get used in Windows systems as well as Linux?
-> Yes. And I never had issues on Windows computers.

Do you use the safe remove feature in the OS before you physically unplug the device?
-> Yes. Except for a few accidental crashes from my laptop (it is old and freezes once in a while).

Regards,
ivan422.

---

### Post by ActionParsnip on 2020-06-12
If you use it in Windows then right click the disk and click properties. You will see "File System". Is it NTFS? FAT32? exFAT? Something else?
If you run a ckdsk on the file system in Windows (Or use the "tools" tab in the above dialogue then "Check drive for file system errors") does it come back as OK?

---

### Post by ivan422 on 2020-06-12
> **ActionParsnip said:**
> If you use it in Windows then right click the disk and click properties. You will see "File System". Is it NTFS? FAT32? exFAT? Something else?
If you run a ckdsk on the file system in Windows (Or use the "tools" tab in the above dialogue then "Check drive for file system errors") does it come back as OK?

If you use it in Windows then right click the disk and click properties. You will see "File System". Is it NTFS? FAT32? exFAT? Something else?
-> I checked and it is NTFS on windows.
-> According to "disc" from Ubuntu, it is: NTFS/exFAT/HPFS.

If you run a ckdsk on the file system in Windows (Or use the "tools" tab in the above dialogue then "Check drive for file system errors") does it come back as OK?
-> I do not have access to a windows computer today. I will try as soon as possible to use the Check Disc you mentionned. However, I used "Disc" from Ubuntu and it said that the USB-stick is corrupted. I used "Disc" from Ubuntu to repair it and it said that all was well but the problem is not solved.

I ran several tests the other day:
Using windows
-> if I create a .doc file or copy a .doc file on the USB-stick, when I open it on Ubuntu, the content is changed to full "#########".
-> if I copy a .png file on the USB-stick, 2/3 of the time it works without corruption, the rest of the time I get the same "unable to access file" error message than for .pdf files.

---

### Post by CelticWarrior on 2020-06-12
You need a Windows OS to repair NTFS.

---

### Post by ActionParsnip on 2020-06-13
As CelticWarrior says, use the Windows OS to run a check on the storage. Ubuntu can access NTFS but it is a proprietary file system and only Microsoft knows how it works. The NTFS access you enjoy in Ubuntu is the result of a lot of trial and error and is a best effort attempt at getting it right. If the NTFS is not quite right then Ubuntu may have issues with it.
If you want to use a USB stick between Windows and Ubuntu and the files are smaller than 4Gb then FAT32 will hie you an easier ride as FAT32 is understood by both systems. Unfortunately Windows cannot access many file systems without extra tools.

---

### Post by lvm on 2020-06-13
> **ivan422 said:**
> "Unable to open the file « file:///media/benjamin/ClefUSB256GB/imprimer/retouretiket(1).pdf ».
The model type file (binary) STL 3D (model/x.stl-binary) is not handled"


I think you are on the wrong track: unless something is lost in translation this message doesn't indicate any sort file or filesystem corruption, it means that your application/pdf file type is misconfigured ant the system doesn't know how to handle it. To check open pdf viewer program e.g. Okular and open this file via file-open (^O) menu.

---

### Post by ivan422 on 2020-06-13
> **CelticWarrior said:**
> You need a Windows OS to repair NTFS.
Thank you for this information.

"ActionParsnip                   [INDENT]                              Re: Ubuntu corrupts files when copied on USB-stick
                          As CelticWarrior says, use the Windows OS to run a check on the  storage. Ubuntu can access NTFS but it is a proprietary file system and  only Microsoft knows how it works. The NTFS access you enjoy in Ubuntu  is the result of a lot of trial and error and is a best effort attempt  at getting it right. If the NTFS is not quite right then Ubuntu may have  issues with it.
If you want to use a USB stick between Windows and Ubuntu and the files  are smaller than 4Gb then FAT32 will hie you an easier ride as FAT32 is  understood by both systems. Unfortunately Windows cannot access many  file systems without extra tools.         "

-> Would it be a good idea to format the USB-stick to FAT32 using Ubuntu? With "Disc", I have several choices:
"W95 FAT32 (0x0b)"
"W95 FAT32 (LBA) (0x0c)"

Or, maybe the best would be to format is on a Windows computer to exFAT? I use Windows 10 on the other computer.

"lvm                   [INDENT]                              Re: Ubuntu corrupts files when copied on USB-stick
                                                                                                        [IMG]https://ubuntuforums.org/images/ubuntu-VB4/misc/quote_icon.png[/IMG] Originally Posted by **ivan422**                     [[IMG]https://ubuntuforums.org/images/ubuntu-VB4/buttons/viewpost-right.png[/IMG]]("https://ubuntuforums.org/showthread.php?p=13964296#post13964296")                 
                 "Unable to open the file « file:///media/benjamin/ClefUSB256GB/imprimer/retouretiket(1).pdf ».
The model type file (binary) STL 3D (model/x.stl-binary) is not handled"
                      
     
 
I think you are on the wrong track: unless something is lost in  translation this message doesn't indicate any sort file or filesystem  corruption, it means that your application/pdf file type is  misconfigured ant the system doesn't know how to handle it. To check  open pdf viewer program e.g. Okular and open this file via file-open  (^O) menu.         "

-> I installed Okular and tried every test files I had. Nothing works. It says "unable to open file" every time. Also, I cannot open the files on Windows.
[/INDENT]
    



[/INDENT]

---

### Post by The Cog on 2020-06-13
> "Unable to open the file « file:///media/benjamin/ClefUSB256GB/imprimer/retouretiket(1).pdf ».
The model type file (binary) STL 3D (model/x.stl-binary) is not handled"
This may well be file corruption. Linux identifies file types by looking at the start of the file, looking for "magic numbers". It seems to be mistaking the type of file (pdf) as an STL 3D file. 
It would be very informative to run this command on a file that you have just written to the stick, both before and after you eject and re-insert the stick. The command prints the binary values of the first 160 bytes of the file:
```
hd /media/benjamin/ClefUSB256GB/imprimer/retouretiket(1).pdf | head
```
They *should* both be the same, but I think they will probably be different.
Bear in mind that the output before you eject will just show the contents of your disk cache in RAM. This is not what is actually on the stick, but is what the OS thinks it wrote to the stick. After ejecting and re-inserting, you should see what is *really* on the stick.

It may be worth running the command **sync** before ejecting the stick and **wait for the command to finish before ejecting**. Just in case the eject is not doing its sync properly. It might make a difference.

---

### Post by ivan422 on 2020-06-13
> **The Cog said:**
> This may well be file corruption. Linux identifies file types by looking at the start of the file, looking for "magic numbers". It seems to be mistaking the type of file (pdf) as an STL 3D file. 
It would be very informative to run this command on a file that you have just written to the stick, both before and after you eject and re-insert the stick. The command prints the binary values of the first 160 bytes of the file:
```
hd /media/benjamin/ClefUSB256GB/imprimer/retouretiket(1).pdf | head
```
They *should* both be the same, but I think they will probably be different.
Bear in mind that the output before you eject will just show the contents of your disk cache in RAM. This is not what is actually on the stick, but is what the OS thinks it wrote to the stick. After ejecting and re-inserting, you should see what is *really* on the stick.

It may be worth running the command **sync** before ejecting the stick and **wait for the command to finish before ejecting**. Just in case the eject is not doing its sync properly. It might make a difference.

Here is the first without sync:
benjamin@benjamin-Satellite-A110:~$ hd /media/benjamin/ClefUSB256GB/test3.odt | head
00000000  50 4b 03 04 14 00 00 08  00 00 c8 63 cd 50 5e c6  |PK.........c.P^.|
00000010  32 0c 27 00 00 00 27 00  00 00 08 00 00 00 6d 69  |2.'...'.......mi|
00000020  6d 65 74 79 70 65 61 70  70 6c 69 63 61 74 69 6f  |metypeapplicatio|
00000030  6e 2f 76 6e 64 2e 6f 61  73 69 73 2e 6f 70 65 6e  |n/vnd.oasis.open|
00000040  64 6f 63 75 6d 65 6e 74  2e 74 65 78 74 50 4b 03  |document.textPK.|
00000050  04 14 00 00 08 00 00 c8  63 cd 50 bf 9f 2b dd 6a  |........c.P..+.j|
00000060  01 00 00 6a 01 00 00 18  00 00 00 54 68 75 6d 62  |...j.......Thumb|
00000070  6e 61 69 6c 73 2f 74 68  75 6d 62 6e 61 69 6c 2e  |nails/thumbnail.|
00000080  70 6e 67 89 50 4e 47 0d  0a 1a 0a 00 00 00 0d 49  |png.PNG........I|
00000090  48 44 52 00 00 00 b5 00  00 01 00 08 03 00 00 00  |HDR.............|

Here is the second without sync:
benjamin@benjamin-Satellite-A110:~$ hd /media/benjamin/ClefUSB256GB/test3.odt | head
00000000  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
00001f6f

Here is the first with sync:
benjamin@benjamin-Satellite-A110:~$ hd /media/benjamin/ClefUSB256GB/test4.odt | head
00000000  50 4b 03 04 14 00 00 08  00 00 95 64 cd 50 5e c6  |PK.........d.P^.|
00000010  32 0c 27 00 00 00 27 00  00 00 08 00 00 00 6d 69  |2.'...'.......mi|
00000020  6d 65 74 79 70 65 61 70  70 6c 69 63 61 74 69 6f  |metypeapplicatio|
00000030  6e 2f 76 6e 64 2e 6f 61  73 69 73 2e 6f 70 65 6e  |n/vnd.oasis.open|
00000040  64 6f 63 75 6d 65 6e 74  2e 74 65 78 74 50 4b 03  |document.textPK.|
00000050  04 14 00 00 08 00 00 95  64 cd 50 ca c7 30 68 7d  |........d.P..0h}|
00000060  01 00 00 7d 01 00 00 18  00 00 00 54 68 75 6d 62  |...}.......Thumb|
00000070  6e 61 69 6c 73 2f 74 68  75 6d 62 6e 61 69 6c 2e  |nails/thumbnail.|
00000080  70 6e 67 89 50 4e 47 0d  0a 1a 0a 00 00 00 0d 49  |png.PNG........I|
00000090  48 44 52 00 00 00 b5 00  00 01 00 08 03 00 00 00  |HDR.............|

Here is the second with sync (before ejecting):
benjamin@benjamin-Satellite-A110:~$ sync
benjamin@benjamin-Satellite-A110:~$ hd /media/benjamin/ClefUSB256GB/test4.odt | head
00000000  50 4b 03 04 14 00 00 08  00 00 95 64 cd 50 5e c6  |PK.........d.P^.|
00000010  32 0c 27 00 00 00 27 00  00 00 08 00 00 00 6d 69  |2.'...'.......mi|
00000020  6d 65 74 79 70 65 61 70  70 6c 69 63 61 74 69 6f  |metypeapplicatio|
00000030  6e 2f 76 6e 64 2e 6f 61  73 69 73 2e 6f 70 65 6e  |n/vnd.oasis.open|
00000040  64 6f 63 75 6d 65 6e 74  2e 74 65 78 74 50 4b 03  |document.textPK.|
00000050  04 14 00 00 08 00 00 95  64 cd 50 ca c7 30 68 7d  |........d.P..0h}|
00000060  01 00 00 7d 01 00 00 18  00 00 00 54 68 75 6d 62  |...}.......Thumb|
00000070  6e 61 69 6c 73 2f 74 68  75 6d 62 6e 61 69 6c 2e  |nails/thumbnail.|
00000080  70 6e 67 89 50 4e 47 0d  0a 1a 0a 00 00 00 0d 49  |png.PNG........I|
00000090  48 44 52 00 00 00 b5 00  00 01 00 08 03 00 00 00  |HDR.............|
 
Here is the third with sync (after ejecting):
benjamin@benjamin-Satellite-A110:~$ sync
benjamin@benjamin-Satellite-A110:~$ hd /media/benjamin/ClefUSB256GB/test4.odt | head
00000000  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
00001f80


-> If I understood what you said, it means you are right.
Is formating on FAT32 or exFAT a solution, then? Must I do it on a windows computer?

---

### Post by The Cog on 2020-06-13
They're coming back full of zeros. I suspect that the stick may be faulty. Clearly the stick can hold some data because the directory entry exists. But the file contents are full of zeros. So I suspect that maybe half of the stick's memory has died (or somehow the format is indicating the stick is bigger than it really is). I have read of some disreputable web sellers selling small sticks that are formatted to look bigger than they are - people only find out when they try to fill the stick beyond its actual size, but it may just be a faulty stick.

You could try to reformat it and see what happens - it might help. Either ntfs or fat32 - exfat is not well supported on Linux until very recently due to Microsoft patent threats. Probably best to format on windows, and unless you want to use files over 4G then fat32 would be preferred.

---

### Post by TheFu on 2020-06-13
> **ivan422 said:**
>  
Is formating on FAT32 or exFAT a solution, then? Must I do it on a windows computer?

No.  The problem is that the drive is being pulled before the data finishes writing.  Unix systems work differently than Windows.  in theory, the "eject" should flush all data to the storage. That has always worked here.  Lacking that, use sync.

BTW, PDF files have different versions.  Adobe and Adobe tools can be told to make specific versions of PDF standard files.  F/LOSS PDF libraries used to end with PDF v1.6 so any tools built on those will have trouble with newer PDF file versions.  Don't know whether that is still the situation or not.  The **file** command will show the specific version of most file formats. it uses the "magic number" signature.  So 
```
$ file *f
st_for_webs.pdf:             PDF document, version 1.5
ia-journal_vol.__2_no_2.pdf: PDF document, version 1.4
tooth_Keyboard-Manual.pdf:   PDF document, version 1.6
cond_Edition.pdf:            PDF document, version 1.4
al.pdf:                      PDF document, version 1.4
es-ref.pdf:                  PDF document, version 1.4
ight.pdf:                    PDF document, version 1.4
```

Be aware that file extensions are just guides for programs and handy for humans.  it is the signature for each file that matters.

So, whatever you are doing to properly flush to disk hasn't been working.  This could be a PBKAC, a bug in the code for those programs, a bug in the supporting libraries, or a bug in the file system implementation.

The NTFS implementation for simple needs is fairly good.  Same for vFAT (FAT32).  The exFAT is much newer and i've never used it.  For storage that isn't shared w/ Windows, there are much better choices for file systems.  Windows doesn't provide the number of choices that Linux does.  We have 50+ different file systems, each for a specific purpose.  i use 2 in general.  ext4 for SSD and spinning HDDs. f2fs for flash media.  if i had to deal with Windows at all, i'd add NTFS and probably exFAT.  NTFS for SSDs and HDDs.  exFAT is something i'd never consider before MSFT decided to give the patents away to the world. Think that happened about a year ago.  Before then, FAT32 was the only choice for flash storage even with the technical issue for 64G and larger sizes.  Some of my cameras and android devices still only support FAT32 so we don't always have a choice.

---

### Post by ivan422 on 2020-06-14
I formatted the USB-stick.
I opted for FAT32 so I now have two partitions: 32GB (created with Windows 10) and 218GB (created with "Disc" from Ubuntu 18.04 LTS).

It seems to have solved the issue (so far). I think I can live without NTFS and >4GB files.

However, I am unable to write any file in the 218GB partition created with Ubuntu...
Did I make any mistep when creating these partitions that would explain why the second one does not seem to be writable? Specificaly: I can write files on it but when I eject and insert back the USB-stick, it says that the second partition does not hold any file.

---

### Post by ivan422 on 2020-06-23
Hello,

The good news is that the 32GB FAT32 partition seems to work on both OS.

The bad news is that I paid for a 256GB USB-stick so I am still looking for a solution to use the remaining 218GB. Anyone would have a lead, please?

Regards,

---

### Post by sudodus on 2020-06-23
It might be that you have a ***fake 256 GB*** stick. Maybe it is really only 32 GB or 64 GB.

You could start over and create a new partition table with gparted

```

sudo apt update
sudo apt install gparted

```

Start gparted.

1. Select the correct device (in the top right corner)
2. Select 'Device' --> 'Create Partition Table' and select GPT
3. Next create several 32 GB partitions with FAT32 until you have used all of the drive space
4. Then test if all of the partitions work (that you can write a file and read the file after unmounting (ejecting) and replugging
5. Tell us the result.

Depending of the result we can decide what is the next step.

---

### Post by ivan422 on 2020-07-14
> **sudodus said:**
> It might be that you have a ***fake 256 GB*** stick. Maybe it is really only 32 GB or 64 GB.

You could start over and create a new partition table with gparted

```

sudo apt update
sudo apt install gparted

```

Start gparted.

1. Select the correct device (in the top right corner)
2. Select 'Device' --> 'Create Partition Table' and select GPT
3. Next create several 32 GB partitions with FAT32 until you have used all of the drive space
4. Then test if all of the partitions work (that you can write a file and read the file after unmounting (ejecting) and replugging
5. Tell us the result.

Depending of the result we can decide what is the next step.

Hello,

I installed gparted (seems great, by the way).

I recieved an error message stating:
"Assertion (ped_partition_is_active (part)) à ../../
libparted/disk.c : échec de 1417 dans la fonction ped_partition_is_flag_available()"

Then gparted crashed.

It does say I have 218gb free to create a partition, though. I created a 218gb ntfs partition and formated to ext4 for testing and apparently it does not work. I will try again on a windows OS when I visit my brother.

---

### Post by sudodus on 2020-07-14
When gparted fails, you can try to wipe the first mibibyte with [**mkusb**](https://help.ubuntu.com/community/mkusb), but please try also the other tips from the following link,

[**Analysis of the problem**](https://askubuntu.com/questions/144852/cant-format-my-usb-drive-i-have-already-tried-with-mkdosfs-and-gparted/933035#933035).

It is possible that the drive is damaged beyond repair, or that it has a fake size (as described earlier), but there might also be 'confusion'. Let us hope that there is 'only' confusion. In this case it should help to wipe the first mibibyte, where the information about parttion table and boot structure is stored.

---

### Post by TheFu on 2020-07-14
it has been 4 weeks.  That is usually the legal return period for getting a replacement from the vendor who sold the faulty device. Hope you already returned it.

---

### Post by ivan422 on 2020-09-04
Hi there, sorry for the delay. I finally got back to home town for a while and tried several things.

I used mkusb to wipe the first bytes. Then, used gparted to make partitions. As soon as the stick was plugged into my Windows computer, I recieved the message "This disk needs to be formatted before you can use it.".

I tried several composition: 
Partition 1 -> 32GB FAT32 / Partition 2 -> 218GB NTFS
Partition 1 -> 218GB NTFS / Partition 2 -> 32GB FAT32

I kind of get the feeling it is not possible to have both FAT32 and NTFS on the same USB stick.

I used GPARTED to format all for my USB stick to one big FAT32 partition and so far it seems to work on both OS.

I think I will continue with this configuration because it seems to work. Too bad for NTFS and its >4GB files...

In any case, thank you all for your help and assistance!

---

### Post by TheFu on 2020-09-04
> **ivan422 said:**
>  

I kind of get the feeling it is not possible to have both FAT32 and NTFS on the same USB stick.

I think I will continue with this configuration because it seems to work. Too bad for NTFS and its >4GB files...

In any case, thank you all for your help and assistance!

Not true.  You can have 1-100+ partitions, each with different file systems on the same storage device.  

FAT32 is about the worst file system available today. The only reason to use it would be if you have specific devices that only work with that file system.  Some devices still get confused when there are multiple partitions on a storage device. That is a problem for the device, not the storage and not the file system.

Hang on, I've made a claim. Let me see if it is actually true. Ok, here's a 64G flash drive I have lying around.

```
$ sudo smartctl -d scsi  -x  /dev/sdd
smartctl 6.5 2016-01-24 r4214 [x86_64-linux-4.15.0-112-generic] (local build)
Copyright (C) 2002-16, Bruce Allen, Christian Franke, www.smartmontools.org

=== START OF INFORMATION SECTION ===
Vendor:               Corsair
Product:              **Voyager VEGA**
Revision:             000A
Compliance:           SPC-4
User Capacity:        61,958,258,688 bytes [61.9 GB]
Logical block size:   512 bytes
```

It is a **Corsair Voyager VEGA** flash device. [https://www.amazon.com/Corsair-Flash-Voyager-Compact-Profile/dp/B00NAWEFGU](https://www.amazon.com/Corsair-Flash-Voyager-Compact-Profile/dp/B00NAWEFGU) is the device. It is tiny (about pinky-nail sized) and gets very hot. When new, it was fast.

```
$ sudo fdisk -l /dev/sdd
Disk /dev/sdd: 57.7 GiB, 61958258688 bytes, 121012224 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: gpt
Disk identifier: D9235A67-3F4F-47D6-92EA-928D3B9E2F88

Device         Start       End   Sectors   Size Type
/dev/sdd1  109312000 121010175  11698176   5.6G Microsoft basic data
/dev/sdd2       1953      3906      1954   977K BIOS boot
/dev/sdd3       3907    503906    500000 244.1M EFI System
/dev/sdd4     503907   4021484   3517578   1.7G Linux filesystem
/dev/sdd5    4022272 109311999 105289728  50.2G Linux filesystem

Partition table entries are not in disk order.
```

EFI is always FAT32. Microsoft basic is NTFS.  Heck, let's just mount each of these:
```
$ df -Th
Filesystem                        Type     Size  Used Avail Use% Mounted on
/dev/sdd1                         fuseblk  5.6G   30M  5.6G   1% /mnt/1
/dev/sdd3                         vfat     241M   15M  226M   7% /mnt/3
/dev/sdd4                         iso9660  1.7G  1.7G     0 100% /mnt/4
/dev/sdd5                         ext4      50G  3.5G   44G   8% /mnt/5

```
d1 = NTFS
d3 = FAT32
d4 = ISO9660 - a CDROM/ISO. It is mounted read-only, as all ISO are.
d5 = ext4, normal Linux file system

It has been a few months since I created this. It was handled using mkusb with an Ubuntu release ISO. During the mkusb session, I was asked about data storage for Linux (50G) and Windows (5.6G).  You can see my choices.  

Let's check the labels on the partitions:

```
$ ll /dev/disk/by-label/
total 0
drwxr-xr-x 2 root root 140 Sep  4 07:53 ./
drwxr-xr-x 8 root root 160 Sep  4 07:53 ../
lrwxrwxrwx 1 root root  10 Sep  4 07:53 casper-rw -> ../../sdd5
lrwxrwxrwx 1 root root  10 Sep  4 07:53 Ubuntu-MATE\x2016.04.6\x20LTS\x20amd64 -> ../../sdd4
lrwxrwxrwx 1 root root  10 Sep  4 07:53 usbboot -> ../../sdd3
lrwxrwxrwx 1 root root  10 Sep  4 07:53 usbdata -> ../../sdd1

```
So, *casper-rw* is a special name used by Ubuntu to to have a read-write overlay file system.  It is an ubuntu-mate 16.04 installation flash setup.  usbdata is the NTFS "data" partition and usbboot is the UEFI boot area, fat32.

Pretty interesting stuff for a tiny usb3 flash drive.  Note that it uses a GPT partition table to get passed the 4 primary partition limit, though it wouldn't matter on Linux. Windows BIOS might care and refuse to boot UEFI without GPT.

---

### Post by ivan422 on 2020-09-04
Hi again,

Apparently, I talked too fast...

Back to my place I tried to work on a .odt file and now it tells me that I don't own the privileges needed in order to modify files in the USB stick.

I read your post, TheFu, and I did not follow. Sorry about that... I did not understand well enough.

When I use your code I get these results:
"$ sudo fdisk -l /dev/sdb1
Disque /dev/sdb1 : 250 GiB, 268434407424 octets, 524285952 secteurs
Unités : secteur de 1 × 512 = 512 octets
Taille de secteur (logique / physique) : 512 octets / 512 octets
taille d'E/S (minimale / optimale) : 512 octets / 512 octets
Type d'étiquette de disque : dos
Identifiant de disque : 0x00000000"

"$ df -Th
Sys. de fichiers        Type     Taille Utilisé Dispo Uti% Monté sur
udev                    devtmpfs   943M       0  943M   0% /dev
tmpfs                   tmpfs      194M    1,8M  193M   1% /run
/dev/sda1               ext4       293G    136G  143G  49% /
tmpfs                   tmpfs      969M     34M  936M   4% /dev/shm
tmpfs                   tmpfs      5,0M    4,0K  5,0M   1% /run/lock
tmpfs                   tmpfs      969M       0  969M   0% /sys/fs/cgroup
/dev/loop0              squashfs    53M     53M     0 100% /snap/core18/1878
/dev/loop1              squashfs    55M     55M     0 100% /snap/gtk-common-themes/1502
/dev/loop2              squashfs    53M     53M     0 100% /snap/core18/1887
/dev/loop3              squashfs   165M    165M     0 100% /snap/gnome-3-28-1804/127
/dev/loop4              squashfs    27M     27M     0 100% /snap/snapd/8540
/dev/loop5              squashfs   162M    162M     0 100% /snap/chromium/1243
/dev/loop6              squashfs    63M     63M     0 100% /snap/gtk-common-themes/1506
/dev/loop7              squashfs    92M     92M     0 100% /snap/core/9803
/dev/loop8              squashfs    93M     93M     0 100% /snap/core/9669
/dev/loop9              squashfs    27M     27M     0 100% /snap/snapd/8788
/dev/loop10             squashfs   163M    163M     0 100% /snap/chromium/1261
tmpfs                   tmpfs      194M     28K  194M   1% /run/user/123
tmpfs                   tmpfs      194M     40K  194M   1% /run/user/1000
/home/benjamin/.Private ecryptfs   293G    136G  143G  49% /home/benjamin
/dev/sdb1               vfat       250G     32K  250G   1% /media/benjamin/FAT32"

I checked into mkusb but I did not find the option to make one partition FAT32 and another NTFS. All I was able to do was to make a FAT32 partition while wiping everything out.

I tried to use gparted to make the two partitions instead but maybe I do not use it adequately.

---

### Post by ivan422 on 2020-10-07
Hi again,

The problem is still troublesome.

If I write something on the usb-stick with WINDOWS OS, I can read it on a WINDOWS OS and a UBUNTU OS.
If I write something on the usb-stick with UBUNTU OS, I can read it on UBUNTU OS but not on a WINDOWS OS.

Anyone would still have ideas to troubleshoot this situation, please?

---

