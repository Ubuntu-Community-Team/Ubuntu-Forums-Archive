---
title: "Lubuntu does not boot"
date: 2014-11-02
forum: New to Ubuntu
---

### Post by Umut_Tundemir on 2014-11-02
I have one old pc that Windows XP even got performance problems in time that caused me to give one lite linux distro try to make this pc useful for web surfing mainly.

I dont want dual boot, or need any NT base operating system together with Linux.I want only one lite single Linux distro running on the pc.

I got formatted, partitioned the disk and installed Lubuntu many times, however for a week long already i couldn't manage to get Lubuntu boots which is only installed operating system on the disk.

After the installation is completed, i immediately got the following command line instead lubuntu is booted;

```

Entering rescue mode... 
grub rescue>
```

I have two disk on the pc, one is primary and has 7.5 gb capacity which has Lubuntu installed on it, and one 40gb which is totally free with one partition that is only used for storing data.

What i have tried so far to make it working but no luck;

i get terminal run from the live lubuntu and executed the following commands;

```

sudo apt-get install lilo
sudo lilo -M /dev/sda mbr

```

It`s said that the MBR has been successfully updated.However it didnt fix the booting problem.

After that i have tried;


```

sudo update-grub 
sudo grub-install /dev/sda
```


and get the following error;

```

error: failed to get canonical path of `/cow`.
```


And lastly when i execute 'sudo parted /dev/sda print all' then i get the following;

```
> Model: ATA QUANTUM FIREBALL (scsi) Disk /dev/sda: 7510MB Sector size
> (logical/physical): 512B/512B Partition Table: msdos Disk Flags: 
> 
> Number  Start   End     Size    Type      File system     Flags  1    
> 1049kB  6988MB  6987MB  primary   ext4            boot  2      6989MB 
> 7510MB  521MB   extended  5      6989MB  7510MB  521MB   logical  
> linux-swap(v1)
> 
> 
> Model: ATA MAXTOR 6L040J2 (scsi) Disk /dev/sdb: 40.0GB Sector size
> (logical/physical): 512B/512B Partition Table: msdos Disk Flags: 
> 
> Number  Start   End     Size    Type     File system  Flags  1     
> 32.3kB  40.0GB  40.0GB  primary  ntfs         boot
> 
> 
> Model: Ut163 USB2FlashStorage (scsi) Disk /dev/sdc: 1011MB Sector size
> (logical/physical): 512B/512B Partition Table: msdos Disk Flags: 
> 
> Number  Start   End     Size    Type     File system  Flags  1     
> 1049kB  1011MB  1010MB  primary  fat32        boot, lba
> 
> 
> Warning: Unable to open /dev/sr0 read-write (Read-only file system). 
> /dev/sr0 has been opened read-only.
```

Any help will be appreciated for me to make this Lubuntu bootable.Thank you very much.

---

### Post by ajgreeny on 2014-11-02
Which of the two disks is first device in the boot priority?
It is possible that for some reason grub is installed in the other disk to that to which you are trying to boot so try changing the boot order to use the other disk as first priority device in the BIOS to see if that helps.

---

### Post by Umut_Tundemir on 2014-11-02
> **ajgreeny said:**
> Which of the two disks is first device in the boot priority?
It is possible that for some reason grub is installed in the other disk to that to which you are trying to boot so try changing the boot order to use the other disk as first priority device in the BIOS to see if that helps.

Thank you very much for your answer.

The disk which has 7.5gb capacity and primary  is the first device in the boot priority which Lubuntu is installed on.
In the BIOS it is not possible to make the disk bootable which is attached as secondary to the motherboard.In the options there are only floppy,cd rom and primary disk, the other disk 40gb not even available as option to set in boot priority list which is secondary disk.The secondary disk which is 40gb has just formatted and has only one NTFS partition that is totally empty.

I don't have any personal data at all on both of the disks.So any solution i can try without any risk.

---

### Post by Umut_Tundemir on 2014-11-02
Here how my drives current look:

[IMG]http://i.hizliresim.com/kYyj17.png[/IMG]

---

### Post by mörgæs on 2014-11-03
The 40 GB is likely to be much faster than the 7,5 GB one. Running on the small disk gives a bad performance, and 7.5 GB is hardly useful these days.

I suggest that you remove the small disk, keeping only the new one (remember to set as master) and install here.

---

### Post by Umut_Tundemir on 2014-11-03
> **mörgæs said:**
> The 40 GB is likely to be much faster than the 7,5 GB one. Running on the small disk gives a bad performance, and 7.5 GB is hardly useful these days.

I suggest that you remove the small disk, keeping only the new one (remember to set as master) and install here.

thank you for the answer.unfortunately the 40gb disk has bad sector in it so its not best way of using any operating system on it but only use it for store data as second disk.Thus i have to make this Lubuntu working in the last disk i have that is working without any problem which has 7.5gb capacity.What i expect from Lubuntu is only running web browser for surfing and that's all, dont have big expectations neither from the Lubuntu or this PC itself.

---

### Post by mörgæs on 2014-11-04
If the 40 GB disk has a bad sector (which many old disks have, and that does not cause problems) I am even more convinced that this one should run Lubuntu. The small but more reliable 7,5 disk could then be used for data.

---

### Post by Umut_Tundemir on 2014-11-04
I run the boot-repair utility and unfortunately it didnt help too. Here its log:

[http://paste.ubuntu.com/8818796/](http://paste.ubuntu.com/8818796/)

Also after reboot, in the welcome screen of Lubuntu where we  choose either install,try lubuntu etc, i choosed the option called "boot  from first harddisk" and i got the following result in the command  line:

  [INDENT]   isolinux: Found something at drive = F0
      isolinux: Extremely broken BIOS detected, last attempt with drive = EF
      isolinux: See [http://syslinux.zytor.com/sbm](http://syslinux.zytor.com/sbm) for more information.
      isolinux: Diskerror 01, AX = 4222, drive EF

 [/INDENT]

---

