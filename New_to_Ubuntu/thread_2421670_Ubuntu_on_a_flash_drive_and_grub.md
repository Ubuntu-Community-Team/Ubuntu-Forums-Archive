---
title: "Ubuntu on a flash drive and grub"
date: 2019-06-25
forum: New to Ubuntu
---

### Post by joelore on 2019-06-25
I've been following instruction on running Ubuntu from a flash drive but grub keeps attaching itself to my Windows MBR. I know how to remove it but how do I prevent this from happening in the first place so I don't have to restore my MBR just to boot into Windows.

--dev

---

### Post by oldfred on 2019-06-25
If booting in the now old BIOS mode, you use Something Else and choose using combo box at bottom of partitioning screen where to install grub. 
[https://help.ubuntu.com/community/Grub2/Installing#Installing_Ubuntu_to_a_Specific_Partition_.28.22Something_Else.22.29](https://help.ubuntu.com/community/Grub2/Installing#Installing_Ubuntu_to_a_Specific_Partition_.28.22Something_Else.22.29)

With newer UEFI that selection of where to install grub boot loader does not work & you have to partition in advance with gpt and be sure to include an ESP - efi system partition on flash drive.

---

### Post by joelore on 2019-06-25
Thanks for the information

---

### Post by joelore on 2019-06-25
Is 32G enough for Ubuntu?

---

### Post by deadflowr on 2019-06-25
> **joelore said:**
> Is 32G enough for Ubuntu?

Yes.
Ubuntu needs less than 10Gb for the system, usually.
So that would leave you with around 20Gb for personal usage.

We are talkin' drive space and not RAM, right?

---

### Post by oldfred on 2019-06-25
Be sure to only use USB3 flash drive and best in USB3 port.
Writes to flash drives are very slow. You want to change any mounted partitions to use noatime.

One of my flash drives. My full install with added in apps uses 7GB, but all data normally in /home is in my data partition. Flash drive is basically a default install before adding anything. More for emergency boot for me.
```
fred@bionic-z97:~$ df -h
Filesystem      Size  Used Avail Use% Mounted on
/dev/sda7        29G  7.0G   20G  27% /
/dev/sda1       499M  7.7M  492M   2% /boot/efi
/dev/sdb4       385G   80G  286G  22% /mnt/data
/dev/sdd2        14G  4.8G  7.9G  38% /media/fred/USB_root
/dev/sdd3        15G   14G  659M  96% /media/fred/usb_data
```

Add noatime like this and if data partitions mounted use noatime also:
UUID=8c92557f-cc60-438b-b1ea-ffea0adf0a1a /    ext4    [COLOR=#ff0000]noatime,[/COLOR]errors=remount-ro


Flash drive will be slow, I can do a full install to SSD in less than 10 minutes, but install to flash drive is over 40 minutes as write is so slow. Reading is faster & once an app is in memory works just as fast, but better not to use full Ubuntu, but one of the lighterweight gui, as less to load.

       Light weight flavors
Lubuntu, xubuntu, Ubuntu mate, Budgie
[https://wiki.ubuntu.com/UbuntuFlavors](https://wiki.ubuntu.com/UbuntuFlavors) 
    
There are others settings/changes to consider:
       Slow Boot --------------------------------
[https://ubuntuforums.org/showthread.php?t=2417453](https://ubuntuforums.org/showthread.php?t=2417453)
[https://www.dedoimedo.com/computers/ubuntu-beaver-slow-boot.html](https://www.dedoimedo.com/computers/ubuntu-beaver-slow-boot.html)

---

