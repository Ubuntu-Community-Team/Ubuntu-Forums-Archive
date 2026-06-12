---
title: "Cant access my external hard drive :/"
date: 2012-10-08
forum: New to Ubuntu
---

### Post by edgu on 2012-10-08
Im trying to retrieve files from my extternal hard drive. my sata to usb on my external hard drive busted. I don't have the money to buy an adapter but i had a sata cable i was able to borrow. so i disconnected the sata to usb and i connected the external hard drive with the sata cable directly to my computer. it comes up in gparted partion but it comes up as unallocated. also appears in disk utility but it says unpartitioned and disk healthy. Im not sure what do from here. i have pictures i dont want to lose. is there a way to get them??? thank you

---

### Post by NikTh on 2012-10-08
Hi , 

Please plug the HDD and then open a terminal and give the results***** of bellow commands

```
sudo fdisk -l 
sudo parted -l
``` 

*****Put the results between the brackets **[noparse]```
Here
```[/noparse]**

Thanks

---

### Post by edgu on 2012-10-08
[Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x8c8bb30c

Disk /dev/sdb doesn't contain a valid partition table

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xb8352b40

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   231576974   115788456   83  Linux
/dev/sda2       231576975   234436544     1429785    5  Extended
/dev/sda5       231577038   234436544     1429753+  82  Linux swap / Solaris
ebi@EBI:~$ sudo parted -l
Model: ATA ST3120813AS (scsi)
Disk /dev/sda: 120GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End    Size    Type      File system     Flags
 1      32.3kB  119GB  119GB   primary   ext3            boot
 2      119GB   120GB  1464MB  extended
 5      119GB   120GB  1464MB  logical   linux-swap(v1)]




not sure if this is wht you meant by the brackets. sorry.

as for sudo parted i got this

[Error: /dev/sdb: unrecognised disk label                                  

ebi@EBI:~$ sudo parted -l
Model: ATA ST3120813AS (scsi)
Disk /dev/sda: 120GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End    Size    Type      File system     Flags
 1      32.3kB  119GB  119GB   primary   ext3            boot
 2      119GB   120GB  1464MB  extended
 5      119GB   120GB  1464MB  logical   linux-swap(v1)]

---

### Post by Wim Sturkenboom on 2012-10-08
I have a feeling this is going to be a recovery exercise. The program 'testdisk / photorec' is in the repo (under testdisk).

---

### Post by Wim Sturkenboom on 2012-10-08
> 
not sure if this is wht you meant by the brackets. sorry.


This is what NikTh asked for
1)
Type **[noparse]```
[/noparse]** literally
2)
Paste the output of the commands after [noparse][code][/noparse]
3)
Type **[noparse]
```[/noparse]** literally after the pasted output.

```

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x8c8bb30c

Disk /dev/sdb doesn't contain a valid partition table

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xb8352b40

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   231576974   115788456   83  Linux
/dev/sda2       231576975   234436544     1429785    5  Extended
/dev/sda5       231577038   234436544     1429753+  82  Linux swap / Solaris

```

---

### Post by edgu on 2012-10-08
ebi@EBI:~$ ```
Disk /dev/sdb: 500.1 GB, 500107862016 bytes
[code]Disk: command not found
ebi@EBI:~$ 255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors255: command not found
ebi@EBI:~$ Units = sectors of 1 * 512 = 512 bytes
No command 'Units' found, did you mean:
 Command 'units' from package 'units' (universe)
Units: command not found
ebi@EBI:~$ Sector size (logical/physical): 512 bytes / 4096 bytes
bash: syntax error near unexpected token `('
ebi@EBI:~$ I/O size (minimum/optimal): 4096 bytes / 4096 bytes
bash: syntax error near unexpected token `('
ebi@EBI:~$ Disk identifier: 0x8c8bb30c
No command 'Disk' found, did you mean:
 Command 'risk' from package 'xfrisk' (universe)
Disk: command not found
ebi@EBI:~$ 
ebi@EBI:~$ Disk /dev/sdb doesn't contain a valid partition table
> 
> Disk /dev/sda: 120.0 GB, 120034123776 bytes
> 255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors
> Units = sectors of 1 * 512 = 512 bytes
> Sector size (logical/physical): 512 bytes / 512 bytes
> I/O size (minimum/optimal): 512 bytes / 512 bytes
> Disk identifier: 0xb8352b40
> 
>    Device Boot      Start         End      Blocks   Id  System
> /dev/sda1   *          63   231576974   115788456   83  Linux
> /dev/sda2       231576975   234436544     1429785    5  Extended
> /dev/sda5       231577038   234436544     1429753+  82  Linux swap / Solaris
```

after i typed ```
 i hit ctrl+shift+v and this happened. ebi@EBI:~$ [code]Disk /dev/sdb: 500.1 GB, 500107862016 bytes
[code]Disk: command not found
ebi@EBI:~$ 255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors255: command not found
ebi@EBI:~$ Units = sectors of 1 * 512 = 512 bytes
No command 'Units' found, did you mean:
 Command 'units' from package 'units' (universe)
Units: command not found
ebi@EBI:~$ Sector size (logical/physical): 512 bytes / 4096 bytes
bash: syntax error near unexpected token `('
ebi@EBI:~$ I/O size (minimum/optimal): 4096 bytes / 4096 bytes
bash: syntax error near unexpected token `('
ebi@EBI:~$ Disk identifier: 0x8c8bb30c
No command 'Disk' found, did you mean:
 Command 'risk' from package 'xfrisk' (universe)
Disk: command not found
ebi@EBI:~$ 
ebi@EBI:~$ Disk /dev/sdb doesn't contain a valid partition table
> 
> Disk /dev/sda: 120.0 GB, 120034123776 bytes
> 255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors
> Units = sectors of 1 * 512 = 512 bytes
> Sector size (logical/physical): 512 bytes / 512 bytes
> I/O size (minimum/optimal): 512 bytes / 512 bytes
> Disk identifier: 0xb8352b40
> 
>    Device Boot      Start         End      Blocks   Id  System
> /dev/sda1   *          63   231576974   115788456   83  Linux
> /dev/sda2       231576975   234436544     1429785    5  Extended
> /dev/sda5       231577038   234436544     1429753+  82  Linux swap / Solaris 

didn't give me time to add 
``` 
i still typed it but nothing happened

---

### Post by edgu on 2012-10-08
photorec worked well. Ill be able to extract my pictures. Thank you :]

---

### Post by Wim Sturkenboom on 2012-10-08
> **edgu said:**
> i still typed it but nothing happenedIt will only be visible once you have posted ;)

Glad you recovered your photos.

---

