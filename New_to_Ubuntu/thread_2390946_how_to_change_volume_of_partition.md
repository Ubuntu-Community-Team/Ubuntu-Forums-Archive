---
title: "how to change volume of partition"
date: 2018-05-04
forum: New to Ubuntu
---

### Post by hilario_ferreira on 2018-05-04
Hi all:

I have on my desktop a dual boot with ubuntu 17.10 and ubuntu mate 18.04.

When I created the partitions I was thinking to use mainly the 17.10 and so I made its partition a lot bigger.

Now that I'm really happy with mate 18.04 I would like to increase the volume of the partition.

Is there an easy way to do it using gparted ?? I know it can be shrunk using gparted but I don't see any option to increase the volume.

Is that possible or not ??

---

### Post by Dennis N on 2018-05-04
Since MATE 18.04 was probably the second installation, you could have some unallocated space after and adjacent to it. If that is the case, gparted can resize the partition using that unallocated space and that is relatively safe to do. If a partition is surrounded by other partitions, then it is a different story. Post output of:
**```
sudo parted -l
```** to see what the possibilites are here.

---

### Post by hilario_ferreira on 2018-05-04
Here it is:

Modelo: ATA TOSHIBA DT01ABA1 (scsi)
Disco /dev/sda: 1000GB
Tamanho de sector (lógico / físico): 512B/4096B
Tabela de Partições: msdos
Sinalizadores do Disco: 

Número  Início  Final   Tamanho  Tipo      Sistema de ficheiros  Sinalizadores
 1      1049kB  718GB   718GB    primary   ext4                  boot
 2      718GB   1000GB  282GB    extended
 5      718GB   1000GB  282GB    logical   ext4


Aviso: O descritor do driver informa que o tamanho físico de bloco é 2048 bytes,
mas o Linux informa que é 512 bytes.
Ignorar/Ignore/Cancelar/Cancel?

---

### Post by ajgreeny on 2018-05-04
I guess that **sda5** is your new Mate-18.04, a logical partition inside **sda2**, the extended partition.

The only way you can enlarge sda5 is by first shrinking sda1 (your 17.10?) then enlarging sda2, the extended partition into that fre space, and finally enlarging the Mate-18.04 partition into the space now free inside the extended partition.

This will take a long time but is safe enough as long as your machine does not lose power, so if this is a laptop make sure you have the power-cord plugged in and that the machine does not shutdown or suspend from what it thinks is inactivity.

---

### Post by oldfred on 2018-05-04
You used the older MBR partitioning with its primary, extended & logical partitions inside the extended partition.
So to expand sda5, you have to first make room inside the extended partition and moving partitions left requires all data to be copied. So if lots of data, it can take a very long time. And any interruption corrupts data. So be sure to have good backups.
So shrink, sda1, I think you can expand extended left, then move sda5 left, and then expand it right.

Generally I prefer smaller / (root) partition of 25 or 30GB and then large data partition. I have multiple installs, so mount same data into all installs.

If never installing Windows in BIOS boot mode, you can convert MBR to gpt. But need a 1 or 2MB unformatted bios_grub partition and would have to reinstall grub.
       GPT Advantages (older 2010 but still valid)  see post#2 by srs5694:
[http://ubuntuforums.org/showthread.php?t=1457901](http://ubuntuforums.org/showthread.php?t=1457901)
[URL="https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT"]https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT

      [/URL]
 Converting to or from GPT
[http://www.rodsbooks.com/gdisk/mbr2gpt.html](http://www.rodsbooks.com/gdisk/mbr2gpt.html) 
    [URL="https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT"]
[/URL]

---

### Post by hilario_ferreira on 2018-05-04
> **ajgreeny said:**
> I guess that **sda5** is your new Mate-18.04, a logical partition inside **sda2**, the extended partition.

The only way you can enlarge sda5 is by first shrinking sda1 (your 17.10?) then enlarging sda2, the extended partition into that fre space, and finally enlarging the Mate-18.04 partition into the space now free inside the extended partition.

This will take a long time but is safe enough as long as your machine does not lose power, so if this is a laptop make sure you have the power-cord plugged in and that the machine does not shutdown or suspend from what it thinks is inactivity.

Ok I will try that way.

I have only applications installed so far( installations were made a few days ago). No important data so far.

will be back if I have any problems.
thank you

---

### Post by hilario_ferreira on 2018-05-04
Ok first step no problem I drag it to the left untill I get the desired shrink.
The second step to enlarge sda2 I don't see how I can do it ( i  think that sd2 is the greyed area created when shrinking sda1, right ??).

It seems it's not possible to change that partition !!
Unless I have to do one step at the time !!! is that so??

---

### Post by hilario_ferreira on 2018-05-04
So I shrunk the sda1.
Now I have 3 partitions- SDA1 . the nom allocated area and the SDA5.
From this point I don't know what to do !! can you please tell me what to do next ??

---

### Post by ajgreeny on 2018-05-04
You should make those changes to sda2 and sda5 using a live system as you can not change partitions you are using, and I suspect you are using 18.04, while trying to make these changes to the 18.04 partitions.

If you can still boot into your newly size-reduced 17.10, and install gparted in that, you may be able to enlarge both sda2 and then sda5 by dragging the left hand end of sda2 first, then sda5.

It is safer, however, to always use a live system's gparted to make partition changes.

---

### Post by hilario_ferreira on 2018-05-04
Well , I'm afraid I can't boot into 17.10 anymore.
This is not a problem.
Is there any possibility to still enlarge sda5 ??

OK if I understood what you said I have to use a USB with ubuntu and use gparted from there to enlarge sda5.is that so ? and what about the shrunk partition sda2 , can I still use it to install another OS ?

---

### Post by oldfred on 2018-05-04
What other OS?
Windows has many rules. Like it must be a primary NTFS formatted partition with the boot flag.  It can only be a logical partition if you have another primary partition NTFS formatted with the boot files.

---

### Post by hilario_ferreira on 2018-05-04
> **oldfred said:**
> What other OS?
Windows has many rules. Like it must be a primary NTFS formatted partition with the boot flag.  It can only be a logical partition if you have another primary partition NTFS formatted with the boot files.

OK forget the installation of another OS.
Please confirm if I have to use the USB with ubuntu mate 18.04 to enlarge the sda5.
can I do it that way ?

---

### Post by yancek on 2018-05-04
YOu need to use a Live USB or DVD with some Linux on it which contains GParted.  Ubuntu would be one.  When you open GParted, the first thing you need to do is unmount the partitions you want to work on.  Once that is done, you can move the Extended partition to the left and then the logical partition.  It's not possible for us to give you specific information when you have only posted general information yourself.  Posting an image or a link to an image of the GParted screen would help.  The GParted Manual is available online so go to their site and scroll down to the resizing section.

 [https://gparted.org/display-doc.php%3Fname%3Dhelp-manual](https://gparted.org/display-doc.php%3Fname%3Dhelp-manual)

---

### Post by hilario_ferreira on 2018-05-05
> **yancek said:**
> YOu need to use a Live USB or DVD with some Linux on it which contains GParted.  Ubuntu would be one.  When you open GParted, the first thing you need to do is unmount the partitions you want to work on.  Once that is done, you can move the Extended partition to the left and then the logical partition.  It's not possible for us to give you specific information when you have only posted general information yourself.  Posting an image or a link to an image of the GParted screen would help.  The GParted Manual is available online so go to their site and scroll down to the resizing section.

 [https://gparted.org/display-doc.php%3Fname%3Dhelp-manual](https://gparted.org/display-doc.php%3Fname%3Dhelp-manual)

here you have the image of gparted screen

---

### Post by oldfred on 2018-05-05
The little key icons say the partitions are mounted. You cannot use the / on the hard drive you are working with.
You have to use the live installer and it still mounts swap if separate partition (and then the extended partition swap is in).

So reboot and use gparted from the Ubuntu live installer.
Then you should be able to move extended partition

---

### Post by hilario_ferreira on 2018-05-05
> **oldfred said:**
> The little key icons say the partitions are mounted. You cannot use the / on the hard drive you are working with.
You have to use the live installer and it still mounts swap if separate partition (and then the extended partition swap is in).

So reboot and use gparted from the Ubuntu live installer.
Then you should be able to move extended partition

it's done sucessfully.

Now I have plenty of space in my sda5 (more than 700 GB)

Now I have another question.

What can I do with partition sda1 (168 GB).Is it possible to install another linux distro without ruining my ubuntu mate on sda5 ??

---

### Post by oldfred on 2018-05-05
I only use 25GB for each install. I often install each release and maybe more than once to experiment with settings that I may not want permanently in my main working install.
I then have a large /mnt/data partition that I mount into every install, so same data in all installs, but not a shared /home as I do not want user settings shared.

But last install takes over boot or is the version installed in the MBR if BIOS or UEFI's ESP if UEFI.
You can easily reset that to use main install or just use the other install's grub.
Best to always have a working live installer, so you can make repairs or reset grub easily.

---

### Post by hilario_ferreira on 2018-05-05
ok thanks for your tips.

---

