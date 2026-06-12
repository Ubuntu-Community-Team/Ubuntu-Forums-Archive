---
title: "how  to get my windows open"
date: 2018-06-26
forum: New to Ubuntu
---

### Post by idarwin2 on 2018-06-26
guys, i have installed Ubuntu 18.04 LTS on my usb device and i choose the boot on the usb.
 the question is, when i reboot my computer, it can only boot on the usb, the grub on ubuntu don't have windows.
i have tried to update gurb2, but it didn't work.
now, who can help me fix this&#65311;

```
this is fdisk -l:
Disk /dev/loop0&#65306;1.6 MiB&#65292;1691648 &#23383;&#33410;&#65292;3304 &#20010;&#25159;&#21306;
&#21333;&#20803;&#65306;&#25159;&#21306; / 1 * 512 = 512 &#23383;&#33410;
&#25159;&#21306;&#22823;&#23567;(&#36923;&#36753;/&#29289;&#29702;)&#65306;512 &#23383;&#33410; / 512 &#23383;&#33410;
I/O &#22823;&#23567;(&#26368;&#23567;/&#26368;&#20339;)&#65306;512 &#23383;&#33410; / 512 &#23383;&#33410;


Disk /dev/loop1&#65306;12.2 MiB&#65292;12804096 &#23383;&#33410;&#65292;25008 &#20010;&#25159;&#21306;
&#21333;&#20803;&#65306;&#25159;&#21306; / 1 * 512 = 512 &#23383;&#33410;
&#25159;&#21306;&#22823;&#23567;(&#36923;&#36753;/&#29289;&#29702;)&#65306;512 &#23383;&#33410; / 512 &#23383;&#33410;
I/O &#22823;&#23567;(&#26368;&#23567;/&#26368;&#20339;)&#65306;512 &#23383;&#33410; / 512 &#23383;&#33410;


Disk /dev/loop2&#65306;21 MiB&#65292;22003712 &#23383;&#33410;&#65292;42976 &#20010;&#25159;&#21306;
&#21333;&#20803;&#65306;&#25159;&#21306; / 1 * 512 = 512 &#23383;&#33410;
&#25159;&#21306;&#22823;&#23567;(&#36923;&#36753;/&#29289;&#29702;)&#65306;512 &#23383;&#33410; / 512 &#23383;&#33410;
I/O &#22823;&#23567;(&#26368;&#23567;/&#26368;&#20339;)&#65306;512 &#23383;&#33410; / 512 &#23383;&#33410;


Disk /dev/loop3&#65306;140 MiB&#65292;146841600 &#23383;&#33410;&#65292;286800 &#20010;&#25159;&#21306;
&#21333;&#20803;&#65306;&#25159;&#21306; / 1 * 512 = 512 &#23383;&#33410;
&#25159;&#21306;&#22823;&#23567;(&#36923;&#36753;/&#29289;&#29702;)&#65306;512 &#23383;&#33410; / 512 &#23383;&#33410;
I/O &#22823;&#23567;(&#26368;&#23567;/&#26368;&#20339;)&#65306;512 &#23383;&#33410; / 512 &#23383;&#33410;


Disk /dev/loop4&#65306;3.3 MiB&#65292;3411968 &#23383;&#33410;&#65292;6664 &#20010;&#25159;&#21306;
&#21333;&#20803;&#65306;&#25159;&#21306; / 1 * 512 = 512 &#23383;&#33410;
&#25159;&#21306;&#22823;&#23567;(&#36923;&#36753;/&#29289;&#29702;)&#65306;512 &#23383;&#33410; / 512 &#23383;&#33410;
I/O &#22823;&#23567;(&#26368;&#23567;/&#26368;&#20339;)&#65306;512 &#23383;&#33410; / 512 &#23383;&#33410;


Disk /dev/loop5&#65306;86.6 MiB&#65292;90759168 &#23383;&#33410;&#65292;177264 &#20010;&#25159;&#21306;
&#21333;&#20803;&#65306;&#25159;&#21306; / 1 * 512 = 512 &#23383;&#33410;
&#25159;&#21306;&#22823;&#23567;(&#36923;&#36753;/&#29289;&#29702;)&#65306;512 &#23383;&#33410; / 512 &#23383;&#33410;
I/O &#22823;&#23567;(&#26368;&#23567;/&#26368;&#20339;)&#65306;512 &#23383;&#33410; / 512 &#23383;&#33410;


Disk /dev/sda&#65306;232.9 GiB&#65292;250059350016 &#23383;&#33410;&#65292;488397168 &#20010;&#25159;&#21306;
&#21333;&#20803;&#65306;&#25159;&#21306; / 1 * 512 = 512 &#23383;&#33410;
&#25159;&#21306;&#22823;&#23567;(&#36923;&#36753;/&#29289;&#29702;)&#65306;512 &#23383;&#33410; / 512 &#23383;&#33410;
I/O &#22823;&#23567;(&#26368;&#23567;/&#26368;&#20339;)&#65306;512 &#23383;&#33410; / 512 &#23383;&#33410;
&#30913;&#30424;&#26631;&#31614;&#31867;&#22411;&#65306;dos
&#30913;&#30424;&#26631;&#35782;&#31526;&#65306;0xdbf6dbf6

&#35774;&#22791;       &#21551;&#21160;      &#36215;&#28857;      &#26411;&#23614;      &#25159;&#21306;   &#22823;&#23567; Id &#31867;&#22411;
/dev/sda1  *         2048 161399548 161397501    77G  7 HPFS/NTFS/exFAT
/dev/sda2       161399549 488397167 326997619 155.9G  f W95 &#25193;&#23637; (LBA)
/dev/sda5       161399616 224314168  62914553    30G  7 HPFS/NTFS/exFAT
/dev/sda6       224314232 236897136  12582905     6G  7 HPFS/NTFS/exFAT
/dev/sda7       236897200 249183151  12285952   5.9G  7 HPFS/NTFS/exFAT
/dev/sda8       249185200 377113519 127928320    61G  7 HPFS/NTFS/exFAT
/dev/sda9       377113584 488397167 111283584  53.1G  7 HPFS/NTFS/exFAT




Disk /dev/sdb&#65306;14.9 GiB&#65292;16005464064 &#23383;&#33410;&#65292;31260672 &#20010;&#25159;&#21306;
&#21333;&#20803;&#65306;&#25159;&#21306; / 1 * 512 = 512 &#23383;&#33410;
&#25159;&#21306;&#22823;&#23567;(&#36923;&#36753;/&#29289;&#29702;)&#65306;512 &#23383;&#33410; / 512 &#23383;&#33410;
I/O &#22823;&#23567;(&#26368;&#23567;/&#26368;&#20339;)&#65306;512 &#23383;&#33410; / 512 &#23383;&#33410;
&#30913;&#30424;&#26631;&#31614;&#31867;&#22411;&#65306;dos
&#30913;&#30424;&#26631;&#35782;&#31526;&#65306;0x558dbfe3

&#35774;&#22791;       &#21551;&#21160;     &#36215;&#28857;     &#26411;&#23614;     &#25159;&#21306;  &#22823;&#23567; Id &#31867;&#22411;
/dev/sdb1  *        2048  4196351  4194304    2G  6 FAT16
/dev/sdb2        4196352  4587519   391168  191M 83 Linux
/dev/sdb3        4589566 28024831 23435266 11.2G  5 &#25193;&#23637;
/dev/sdb5        4589568 24119295 19529728  9.3G 83 Linux
/dev/sdb6       24121344 28024831  3903488  1.9G 83 Linux

when i tried to grub-install /dev/sdb
it turns out:
Installing for x86_64-efi platform.
GUID Partition Table Header signature is wrong: 8e7c00bcd08ec033 != 5452415020494645
GUID Partition Table Header signature is wrong: 0 != 5452415020494645
GUID Partition Table Header signature is wrong: 8e7c00bcd08ec033 != 5452415020494645
GUID Partition Table Header signature is wrong: 0 != 5452415020494645
GUID Partition Table Header signature is wrong: 8e7c00bcd08ec033 != 5452415020494645
GUID Partition Table Header signature is wrong: 0 != 5452415020494645
```
Installation finished. No error reported.

now, who can help me fix this&#65311;

---

### Post by wildmanne39 on 2018-06-26
Please use the default font color and properties unless you need to highlight or draw attention to a part of your post.

Please use code tags - if you are using New Reply button - highlight text and use the # button in the text box header. 
 
If using Quick Reply then [noparse]```
[/noparse] at the beginning and [noparse]
```[/noparse] at the end.

To get the help you need you should translate all the output of the commands to English since you have posted in an English only sub-forum and not sure anyone here will understand what the output says.

Thanks

---

### Post by ajgreeny on 2018-06-26
And this is fdisk -l output quickly put through google-translate:
```
Disk /dev/loop0: 1.6 MiB, 1691648 bytes, 3304 sectors
Unit: Sector / 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (min/best): 512 bytes / 512 bytes


Disk /dev/loop1:12.2 MiB,12804096 bytes, 25008 sectors
Unit: Sector / 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (min/best): 512 bytes / 512 bytes


Disk /dev/loop2: 21 MiB, 22003712 bytes, 42976 sectors
Unit: Sector / 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (min/best): 512 bytes / 512 bytes


Disk /dev/loop3: 140 MiB, 146841600 bytes, 286800 sectors
Unit: Sector / 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (min/best): 512 bytes / 512 bytes


Disk /dev/loop4:3.3 MiB, 3411968 bytes, 6664 sectors
Unit: Sector / 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (min/best): 512 bytes / 512 bytes


Disk /dev/loop5: 86.6 MiB, 90759168 bytes, 177264 sectors
Unit: Sector / 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (min/best): 512 bytes / 512 bytes


Disk /dev/sda:232.9 GiB, 250059350016 bytes, 488397168 sectors
Unit: Sector / 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (min/best): 512 bytes / 512 bytes
Disk label type: dos
Disk identifier: 0xdbf6dbf6

Device Start Start End Sector Size Id Type
/dev/sda1 * 2048 161399548 161397501 77G 7 HPFS/NTFS/exFAT
/dev/sda2 161399549 488397167 326997619 155.9G f W95 Extension (LBA)
/dev/sda5 161399616 224314168 62914553 30G 7 HPFS/NTFS/exFAT
/dev/sda6 224314232 236897136 12582905 6G 7 HPFS/NTFS/exFAT
/dev/sda7 236897200 249183151 12285952 5.9G 7 HPFS/NTFS/exFAT
/dev/sda8 249185200 377113519 127928320 61G 7 HPFS/NTFS/exFAT
/dev/sda9 377113584 488397167 111283584 53.1G 7 HPFS/NTFS/exFAT




Disk /dev/sdb:14.9 GiB,16005464064 bytes, 31260672 sectors
Unit: Sector / 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (min/best): 512 bytes / 512 bytes
Disk label type: dos
Disk identifier: 0x558dbfe3

Device Start Start End Sector Size Id Type
/dev/sdb1 * 2048 4196351 4194304 2G 6 FAT16
/dev/sdb2 4196352 4587519 391168 191M 83 Linux
/dev/sdb3 4589566 28024831 23435266 11.2G 5 Extensions
/dev/sdb5 4589568 24119295 19529728 9.3G 83 Linux
/dev/sdb6 24121344 28024831 3903488 1.9G 83 Linux

When i tried to grub-install /dev/sdb
It turns out:
Installing for x86_64-efi platform.
The GUID Partition Table Header signature is wrong: 8e7c00bcd08ec033 != 5452415020494645
GUID Partition Table Header signature is wrong: 0 != 5452415020494645
The GUID Partition Table Header signature is wrong: 8e7c00bcd08ec033 != 5452415020494645
GUID Partition Table Header signature is wrong: 0 != 5452415020494645
The GUID Partition Table Header signature is wrong: 8e7c00bcd08ec033 != 5452415020494645
GUID Partition Table Header signature is wrong: 0 != 5452415020494645
```

---

### Post by ajgreeny on 2018-06-26
See **Boot-Repair** in my signature below and follow the instructions there to run the Boot-Info-Script.	 **Do not run the default repair just yet** but simply copy back here the pastebin link you get which will show us a lot more about your system. 

I suspect you have grub in the internal hard disk but all the files grub needs are on the USB.
If the USB is not attached at boot you will get to a grub command line only; the output of boot-repair will help us figure out if this is correct.

---

