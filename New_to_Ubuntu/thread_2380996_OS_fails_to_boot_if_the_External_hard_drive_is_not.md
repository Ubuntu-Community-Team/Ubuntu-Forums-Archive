---
title: "OS fails to boot if the External hard drive is not dismounted"
date: 2017-12-24
forum: New to Ubuntu
---

### Post by wrongusername2 on 2017-12-24
Hi,
    
I had manually mounted the an External hard drive and did not dismount. Next time machine did not boot. I ran Boot-repair, no use. I removed the hard drive and connected it to a different machine so that I can check /ect/fstab. It had a unmounted entry.

```
    #windows ext drive
    UUID=9A8C91E08C91B76B  /media/extsun  ntfs-3g  defaults,windows_names,locale=en_US.utf8  0 0
```

I commented out the above line in etc/fstab and loaded the drive back to original machine. This time machine booted well.

This means an unmounted external hard drive can make the machine not boot. Is this normal to Linux/Ubuntu? (Note I have no experience with Linux ecosystem.)
**I request someone clarify this point.**

GRUB error while OS was failing to boot

```

GRUB> Ls
(hd0) (hd0, gpt3) (hd0, gpt2) (hd0, gpt1) (hd1, gpt1) (hd2) error: failure to read sector
```


Thanks

---

### Post by Autodave on 2017-12-25
Someone with more experience than myself will hopefully give you a better answer than me, but it is not normal.  I have several machines with external HDs mounted to them with no problems.

The only thing I can quickly think of is that the BIOS is finding that drive first and trying to use it.

Is this a dual boot system?  Is there an operating system installed on that external drive?

---

### Post by oldfred on 2017-12-25
You typically do not mount external devices with fstab. 
If you give a partition a label it will then automount with the label rather than the UUID.

It used to be when an error in fstab, the system would timeout and then let you boot (as long as not /).
But have recently seen others that could not boot with fstab entry for device that was not there anymore.

---

### Post by wrongusername2 on 2017-12-25
> **Autodave said:**
> 
The only thing I can quickly think of is that the BIOS is finding that drive first and trying to use it.
Is this a dual boot system?  Is there an operating system installed on that external drive?

Thanks for responding. 
This this not dual boot, no trace of windows here. Clean install.
I am aware of the bios issues.  HP laptops expect the bootloader name to be "Windows...". That got resolved after installing latest BIOS released in 2017. efibootmgr shows just ubuntu.

---

### Post by wrongusername2 on 2017-12-25
> **oldfred said:**
> You typically do not mount external devices with fstab. 
If you give a partition a label it will then automount with the label rather than the UUID..

Thanks for responding. 
Some external hard drive do not get automatically mounted if any one of the partition is in bad state, but other partitions could be perfectly fine. In such cases I do manual mounting. I have check how mounting with label works. Limitation of the approach is label name may not be unique. Windows uses 'New Volume' as default name. 

> 
It used to be when an error in fstab, the system would timeout and then let you boot (as long as not /).
But have recently seen others that could not boot with fstab entry for device that was not there anymore.
I think this will be a hard problem for non-computer people. I was recommending Ubuntu for my non-computer friends; now not sure.

---

### Post by wrongusername2 on 2017-12-25
Here is the output of boot-repair.   [https://paste.ubuntu.com/26248806/](https://paste.ubuntu.com/26248806/) It shows fstab having orphan entry at the bottom. 

```

=============================== sda2/etc/fstab: ================================ 
UUID=33e7832e-316e-4c56-a0c3-13aa4b0d2cd6 /               ext4    errors=remount-ro 0       1
# /boot/efi was on /dev/sda1 during installation
#UUID=823B-A11F  /boot/efi       vfat    umask=0077      0       1
# swap was on /dev/sda3 during installation
UUID=7c8a7556-c64e-4ce9-b347-c7e16d39fe52 none            swap    sw              0       0
UUID=823B-A11F    /boot/efi    vfat    defaults    0    1

#windows ext drive
UUID=9A8C91E08C91B76B  /media/extsun  ntfs-3g  defaults,windows_names,locale=en_US.utf8  0 0
--------------------------------------------------------------------------------
```
Fstab has only entries for root-partitions. I had 3 internal-physical hard drives. Two of them had NTFS. 
It  means entry for mounting external hard drive and non-root partitions may have to go to some  other file. May be I have to create mount-point in /tmp  folder. Not sure.

---

### Post by oldfred on 2017-12-25
I do not have any NTFS partitions any more.

But only mount my internal partitions with fstab, and not all of them.
Some I manually mount with Naulitus which shows them by label. 
Or for instance my backup from sda to sdb has a manual mount in the script.

If using Linux best to not use spaces as that can confuse things. You have to use quotes or escape the space.
I use CamelCase, under_score or justaname for just about everything. 

I normally label partitions when I create them with gparted, but when I forget I use Disks to change labels. With gpt there are two labels.
```

fred@Asusz97:~$ lsblk -o NAME,LABEL,PARTLABEL,SIZE,UUID,MOUNTPOINT
NAME    LABEL   PARTLABEL   SIZE UUID                                 MOUNTPOINT
sda                       119.2G                                      
&#9500;&#9472;sda1  EFI     efi         500M FD76-E33D                            /boot/efi
&#9500;&#9472;sda2                        2M                                      
&#9500;&#9472;sda3  trusty  trusty     24.4G 45de38c8-6748-4634-b207-628d9aa8b42b 
&#9500;&#9472;sda4                      1.9G 3af6a910-59f8-4719-b58c-2e7484d435f0 [SWAP]
&#9500;&#9472;sda5  iso_ssd iso_ssd    10.7G 695d18b5-16f8-4e9c-bf66-675a12da5a26 
&#9500;&#9472;sda6  xenial  xenial     24.4G 255a2800-b871-4fdf-a809-16987e64b8b3 /
&#9492;&#9472;sda7  bionic  bionic     28.7G ca42543c-3a2e-4465-99b9-b9159d96ae7d 
sdb                       931.5G                                      
&#9500;&#9472;sdb1  ESP_B   ESP_b     499.7M 68CD-3368                            
&#9500;&#9472;sdb2                        2M                                      
&#9500;&#9472;sdb3  xenial_b
&#9474;               xenial_b   24.4G 52bfbc7e-a973-4b9b-bb1f-f5569aab60d0 /media/fre
&#9500;&#9472;sdb4  data    data      390.6G a0c1c99f-0f09-4787-a7cc-9e15bb3b4aa5 /mnt/data
&#9500;&#9472;sdb5  backup  backup     27.9G 084de40f-8ffd-4af1-97b1-8a60cdd9aab4 
&#9500;&#9472;sdb6  iso_hdd iso_hdd    12.6G 7f360ddc-d9fb-4a40-b17a-f2d5af6b61ed 
&#9500;&#9472;sdb7                      2.1G a7750d57-5381-421b-82fa-b53194ab45c2 [SWAP]
&#9500;&#9472;sdb8  debian  debian     25.4G cf713b4c-6d8d-4289-b152-fc54051213e8 
&#9500;&#9472;sdb9          artful     23.3G fabeeda1-ad36-4300-a7f8-73afba118f37 
&#9500;&#9472;sdb10         mate       24.4G edea2a89-8859-40b9-bf17-487695ae7a1e 
&#9492;&#9472;sdb11 test    test        9.8G 02FA0DAC185DDA7E                     
sr0                        1024M  
```

---

### Post by wrongusername2 on 2017-12-26
> **oldfred said:**
> I do not have any NTFS partitions any more.

But only mount my internal partitions with fstab, and not all of them.
Some I manually mount with Naulitus which shows them by label. 
Or for instance my backup from sda to sdb has a manual mount in the script.

If using Linux best to not use spaces as that can confuse things. You have to use quotes or escape the space.
I use CamelCase, under_score or justaname for just about everything. 

I normally label partitions when I create them with gparted, but when I forget I use Disks to change labels. With gpt there are two labels.


Thanks for the response. In few days i will be adding one more NTFS drive to my machine. I will post the Fstab then.

---

