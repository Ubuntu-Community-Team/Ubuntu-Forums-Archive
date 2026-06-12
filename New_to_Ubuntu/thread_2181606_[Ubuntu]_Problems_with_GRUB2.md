---
title: "[Ubuntu] Problems with GRUB2"
date: 2013-10-18
forum: New to Ubuntu
---

### Post by Fabio_Valentino on 2013-10-18
Hello, i am new to the forum and i decided to post because searching a lot didn't help me.

I have a problem with GRUB2 about Windows and Ubuntu installed in two different HDD, initially the grub2 wasn't available at all, after installing ubuntu 13.10 there was no way to boot the ubuntu partition.
So i rebotted with live CD and reinstalled GRUB2, all went fine but now my pc doesn't recognize the windows partition... i tried adding entries to 40_custom like that:

```

menuentry "Windows " {
    insmod ntfs
    set root='(hd0,2)'
    chainloader +1
}

```

but it didn't work.

The result of sudo fdisk -l is:

```

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 testine, 63 settori/tracce, 121601 cilindri, totale 1953525168 settori
Unità = settori di 1 * 512 = 512 byte
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Identificativo disco: 0x8f9b01e4

Dispositivo Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048      206847      102400    7  HPFS/NTFS/exFAT
/dev/sda2          206848  1953521663   976657408    7  HPFS/NTFS/exFAT

WARNING: GPT (GUID Partition Table) detected on '/dev/sdb'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sdb: 640.1 GB, 640135028736 bytes
255 testine, 63 settori/tracce, 77825 cilindri, totale 1250263728 settori
Unità = settori di 1 * 512 = 512 byte
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Identificativo disco: 0x38241e88

Dispositivo Boot      Start         End      Blocks   Id  System
/dev/sdb1               1  1250263727   625131863+  ee  GPT

Disk /dev/sdc: 320.1 GB, 320072933376 bytes
255 testine, 63 settori/tracce, 38913 cilindri, totale 625142448 settori
Unità = settori di 1 * 512 = 512 byte
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Identificativo disco: 0x03c78889

Dispositivo Boot      Start         End      Blocks   Id  System
/dev/sdc1   *       16065   625137344   312560640    f  W95 Esteso (LBA)
/dev/sdc5           16128   625137344   312560608+   7  HPFS/NTFS/exFAT


```

[SIZE=3]**Windows is installed in /dev/sda2 and ubuntu is installed in /dev/sdb1.**[/SIZE]
How can i add WIndows to my boot menu ?

Thanks in advance

---

### Post by fantab on 2013-10-18
Is this Windows 8? Does it boot from UEFI?
Post the output of:
```
sudo parted -l
```

---

### Post by Fabio_Valentino on 2013-10-18
Nope, it is windows 7, output of sudo parted -l

```

blast@blast-Z87-HD3:~$ sudo parted -l
[sudo] password for blast: 
Modello: ATA WDC WD10EZEX-00K (scsi)
Disco /dev/sda: 1000GB
Dimensione del settore (logica/fisica): 512B/4096B
Tabella delle partizioni: msdos

Numero  Inizio  Fine    Dimensione  Tipo     File system  Flag
 1      1049kB  106MB   105MB       primary  ntfs         avvio
 2      106MB   1000GB  1000GB      primary  ntfs


Modello: ATA WDC WD6400AAKS-2 (scsi)
Disco /dev/sdb: 640GB
Dimensione del settore (logica/fisica): 512B/512B
Tabella delle partizioni: gpt

Numero  Inizio  Fine   Dimensione  File system     Nome  Flag
 1      1049kB  512MB  511MB       fat32                 avvio
 2      512MB   632GB  631GB       ext4
 3      632GB   640GB  8472MB      linux-swap(v1)


Modello: Seagate Portable (scsi)
Disco /dev/sdc: 320GB
Dimensione del settore (logica/fisica): 512B/512B
Tabella delle partizioni: msdos

Numero  Inizio  Fine   Dimensione  Tipo      File system  Flag
 1      8225kB  320GB  320GB       extended               avvio, lba
 5      8258kB  320GB  320GB       logical   ntfs



```

---

### Post by grahammechanical on 2013-10-18
You have Windows on sda and Ubuntu on sdb. You should be able to use the BIOS to select which hard drive to boot. It is a way to load windows. Not so elegant a method but a method none the less.

Also, you can use something called Linux boot repair. It is based on Ubuntu. Just be careful when it offers to re-install Grub. Do not let it install Grub into the MBR of both hard disks. Just the MBR of sdb. This way if the problem is not fixed you cans till access Windows.

[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

Regards.

---

### Post by Jonathan Precise on 2013-10-18
Attach a screenshot of gparted of all disk drives.

---

### Post by Fabio_Valentino on 2013-10-19
I am already using BIOS boot by switching HDD to boot up at the moment, but it's not elegant.. i want to be able to boot windows from grub

Here are the two screenshot of gparted /sda and /sdb.
sdc is just an usb HDD, i have removed it.

Sorry, attachment is not working, it is saying "an error occurred" when i try to add pics and the size is less than 1024x768.... i use image button, sorry about that


[IMG]http://imageshack.us/a/img189/3603/t1fx.png[/IMG]

[IMG]http://imageshack.us/a/img692/5166/gda3.png[/IMG]

---

### Post by oldfred on 2013-10-19
While Windows main install is in sda2, your boot files are in sda1.

Grub should easily find your Windows install.
sudo update-grub

Your manual entry in first post would have worked if you used sda1 (hd0,1)

Windows 7 typically installs to a (hidden in Windows) 100GB Boot partition and then the main install. That primarily is so you could encrypt the main install as you cannot encrypt the boot files. Also sda1 has the Windows recovery (repair) files, so f8 only works from that. Best to have separate Windows 7 repair CD or flash drive anyway.

---

### Post by Jonathan Precise on 2013-10-20
> **Fabio_Valentino said:**
> I am already using BIOS boot by switching HDD to boot up at the moment, but it's not elegant.. i want to be able to boot windows from grub

Here are the two screenshot of gparted /sda and /sdb.
sdc is just an usb HDD, i have removed it.

Sorry, attachment is not working, it is saying "an error occurred" when i try to add pics and the size is less than 1024x768.... i use image button, sorry about that 

Don't worry! I've had that happen to me before!


> **Fabio_Valentino said:**
> [IMG]http://imageshack.us/a/img189/3603/t1fx.png[/IMG]

Typical BIOS.

> **Fabio_Valentino said:**
> [IMG]http://imageshack.us/a/img692/5166/gda3.png[/IMG]

Huh??????????????????????????????????????????????????????????????????????????????????????????????????

Typical UEFI???

Looks like you have to convert your Ubuntu install to BIOS mode. Luckily, that is (or should not be) too complicated.

> **Yannubuntu]**Converting Ubuntu into Legacy mode**




[LIST]
[*=left][FONT=inherit]Boot an Ubuntu Live CD/DVD. Mount the fat32 partition on /dev/sda2. **BACKUP EVERYTHING IN THE PARTITION!!!**. **I'M SERIOUS. BACKUP EVERYTHING THERE!!!!!**. Use [/FONT][GParted]("https://help.ubuntu.com/community/Gparted")[FONT=inherit] to re-size the Fat32 partition (1MiB less to its left so there is 1 MiB free space at the [/FONT]beginning[FONT=inherit] of the disk) and to create a BIOS-Boot partition (1MB, unformatted filesystem, bios_grub flag) at the start of its disk.[/FONT]
[*=left][FONT=inherit]Start [Boot-Repair]("https://help.ubuntu.com/community/Boot-Repair"), click on "Advanced options", go to the "GRUB location" tab.[/FONT]
[*=left]Untick the "Separate /boot/efi partition" option
[*=left]Click the "Apply" button.
[*=left][FONT=inherit]Set up your BIOS so that it boots the HDD in Legacy mode (see the "[Set up the BIOS in EFI or Legacy mode]("https://help.ubuntu.com/community/UEFI#Set_up_the_BIOS_in_EFI_or_Legacy_mode")" paragraph).[/FONT]
[/LIST]
[LEFT][FONT=inherit]&#8203 said:**
> 
[/LEFT]



Original website [here]("https://help.ubuntu.com/community/UEFI#Converting_Ubuntu_into_Legacy_mode").

---

### Post by oldfred on 2013-10-20
I missed that Windows is in BIOS mode and Ubuntu is in UEFI mode. Once you start booting you cannot switch as UEFI and BIOS are not really compatible. As installed you have to use UEFI to boot Ubuntu and from UEFI change to BIOS to boot Windows.
You can reinstall Ubuntu in BIOS boot mode even on gpt partitioned drive if you add a tiny 1MB unformatted partition for part of grub. Boot-Repair can convert install if you add bios_grub partition first, or else just reinstall.

---

