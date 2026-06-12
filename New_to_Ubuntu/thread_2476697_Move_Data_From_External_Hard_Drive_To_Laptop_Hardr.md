---
title: "Move Data From External Hard Drive To Laptop Hardrive"
date: 2022-07-03
forum: New to Ubuntu
---

### Post by president-6 on 2022-07-03
Gateway NE56R (I already know it is as old as my first son) ;) Operating System: Ubuntu 22.04 LTS with all updates current as of 03JUL22. Fresh install and no exotic add ons.

So, my old laptop finally quit in that I cannot get power or a light in the screen. I purchased a hard drive enclosure as the old system stopped working (screen, lights, etc.) and it connects to my current laptop without issue. To that point, the USB which connects my hard drive (from the old system) enclosure mounts the data such as initrd, vmlinuz, grub folder, config, etc. What both the external hard drive and the local hard drive in the laptop have in common is Ubuntu 22.04. It should be noted that I have Disk Encryption installed on the hard drive seated as the external source. The laptop hard drive IS NOT encrypted. When I load it it has two USB symbols and I click the one locked and enter my password and it opens it up.

I attempted to move all the files to a folder on the laptop and then execute the initrd.img but it states that I cannot transfer some of the files and thus they are missing. Not sure if that is even the right thing to do, but did try. When I click the initrd.img it opens Restore Disk Image which lists my external hard drive, the laptop drive and the CD drive. This is the picture (and attached as file): [https://imgur.com/a/k3EjNEC](https://imgur.com/a/k3EjNEC)[IMG]https://imgur.com/a/k3EjNEC[/IMG]

I presume that the external hard drive via USB is mounted as I get:

 /boot/efi                          /dev/sda1        vfat    rw,relatime,fmask=&#9492;&#9472;/media/ghost/ad3acb64-303f-42e4-8729-7f217327ef8f
                                     /dev/sdb1        ext4    rw,nosuid,nodev,re

My only interest are the files I had on there. A lot were on folders and some were simply saved and stored on Desktop. After getting those files I simply want to use the external hard drive for storage.

The below are the files listed in the external hard drive when I execute "dir" and many of these files have a Red X as I guess they are simply old versions:


[LIST]
[*]grub
[*]config-5.15.0-39-generic
[*]config-5.15.0-40-generic
[/LIST]


[LIST]
[*]initrd.img.old
[*]initrd.img
[*]initrd.img-5.15.0-39-generic
[*]initrd.img-5.15.0-40-generic
[*]lost+found
[*]memtest86+.bin
[*]memtest86+_multiboot.bin
[*]memtest86+.elf
[*]System.map-5.15.0-39-generic
[*]System.map-5.15.0-40-generic

[*]vmlinuz		
[*]vmlinuz.old
[*]vmlinuz-5.15.0-39-generic
[/LIST]


[LIST]
[*]vmlinuz-5.15.0-40-generic
[/LIST]

Not sure if the next set of info is needed, but including it anyway ...

lshw -short

H/W path                   Device      Class          Description
=================================================================
                                       system         NE56R (NE56R_0649_V2.15)
/0                                     bus            EG50_HC_HR
/0/0                                   memory         128KiB BIOS
/0/4                                   processor      Intel(R) Pentium(R) CPU B9
/0/4/b                                 memory         32KiB L1 cache
/0/4/c                                 memory         256KiB L2 cache
/0/4/d                                 memory         2MiB L3 cache
/0/a                                   memory         32KiB L1 cache
/0/1a                                  memory         4GiB System Memory
/0/1a/0                                memory         DIMM [empty]
/0/1a/1                                memory         DIMM [empty]
/0/1a/2                                memory         4GiB SODIMM DDR3 Synchrono
/0/1a/3                                memory         DIMM [empty]
/0/100                                 bridge         2nd Generation Core Proces
/0/100/2                   /dev/fb0    display        2nd Generation Core Proces
/0/100/16                              communication  7 Series/C216 Chipset Fami
/0/100/1a                              bus            7 Series/C216 Chipset Fami
/0/100/1a/1                usb1        bus            EHCI Host Controller
/0/100/1a/1/1                          bus            Integrated Rate Matching H
/0/100/1a/1/1/3            input24     multimedia     HD WebCam: HD WebCam
/0/100/1b                  card0       multimedia     7 Series/C216 Chipset Fami
/0/100/1b/0                input25     input          HDA Intel PCH Mic
/0/100/1b/1                input26     input          HDA Intel PCH Headphone
/0/100/1b/2                input27     input          HDA Intel PCH HDMI/DP,pcm=
/0/100/1c                              bridge         7 Series/C216 Chipset Fami
/0/100/1c/0                enp2s0f0    network        NetLink BCM57785 Gigabit E
/0/100/1c/0.1              mmc0        bus            BCM57765/57785 SDXC/MMC Ca
/0/100/1c/0.2                          generic        BCM57765/57785 MS Card Rea
/0/100/1c/0.3                          generic        BCM57765/57785 xD-Picture 
/0/100/1c.1                            bridge         7 Series/C210 Series Chips
/0/100/1c.1/0              wlp3s0      network        AR9485 Wireless Network Ad
/0/100/1d                              bus            7 Series/C216 Chipset Fami
/0/100/1d/1                usb2        bus            EHCI Host Controller
/0/100/1d/1/1                          bus            Integrated Rate Matching H
/0/100/1d/1/1/1            scsi4       storage        NS1068
/0/100/1d/1/1/1/0.0.0      /dev/sdb    disk           500GB ST500LT012-1DG14
/0/100/1d/1/1/1/0.0.0/1    /dev/sdb1   volume         731MiB EXT4 volume
/0/100/1d/1/1/1/0.0.0/2    /dev/sdb2   volume         465GiB Extended partition
/0/100/1d/1/1/1/0.0.0/2/5  /dev/sdb5   volume         465GiB Linux filesystem pa
/0/100/1d/1/1/3                        input          USB Receiver
/0/100/1d/1/1/3/0          input20     input          Logitech M325
/0/100/1d/1/1/3/1          input21     input          Logitech M525
/0/100/1f                              bridge         HM70 Express Chipset LPC C
/0/100/1f/0                            generic        PnP device MSF0001
/0/100/1f/1                            generic        PnP device ETD0500
/0/100/1f/2                            system         PnP device PNP0c02
/0/100/1f/3                            system         PnP device PNP0b00
/0/100/1f/4                            generic        PnP device INT3f0d
/0/100/1f/5                            system         PnP device PNP0c02
/0/100/1f/6                            system         PnP device PNP0c01
/0/100/1f.2                scsi0       storage        7 Series Chipset Family 6-
/0/100/1f.2/0              /dev/sda    disk           500GB WDC WD5000LPVX-2
/0/100/1f.2/0/1                        volume         511MiB Windows FAT volume
/0/100/1f.2/0/2            /dev/sda2   volume         465GiB EXT4 volume
/0/100/1f.2/1              /dev/cdrom  disk           DVD-RAM UJ8E1
/0/100/1f.3                            bus            7 Series/C216 Chipset Fami
/1                         input0      input          Power Button
/2                         input1      input          Lid Switch
/3                         input2      input          Sleep Button
/4                         input22     input          Acer WMI hotkeys
/5                         input23     input          Video Bus
/6                         input3      input          Power Button
/7                         input4      input          AT Translated Set 2 keyboa
/8                         input6      input          ETPS/2 Elantech Touchpad






Any help appreciated!



[INDENT][/INDENT]

---

### Post by tea for one on 2022-07-03
I can't quite follow what you are trying to do?
It seems that you wish to recover personal data from your broken laptop.

You have successfully popped the drive from the broken laptop into an enclosure and mounted it on your working PC,
Can you not navigate to /home/user/Desktop or /home/user/Documents etc and copy the folders you need?

---

### Post by oldfred on 2022-07-03
I would not try to copy anything system related that is in / other than what is in /home or other data partition(s).
Even if install is same version, it may be different since different hardware.

If you had system settings in /etc, you may want to review those, but I would not try to copy those either. I do copy my /etc/grub.d/40_custom but manually edit /etc/default/grub.

---

### Post by Holger_Gehrke on 2022-07-03
My experience with drive encryption is limited to what I read here and in other places around the net, but it looks to me like what you're accessing is the unencrypted partition that used to be mounted as '/boot'. It basically contains the kernel and needs to be unencrypted (the code to decrypt the encrypted part of the disk isn't loaded at the point when this stuff gets loaded). The initrd.img is a filesystem image that gets loaded into a ram-disk as a temporary root file system as part of the boot process and doesn't hold any files that you might want.

The output of 'lsblk --exclude 7' (list block devices excluding major device number 7, loop devices used for mounting snaps) will probably be helpful for people with deeper knowledge of the topic willing to help.

Holger

---

### Post by Impavidus on 2022-07-03
> **president-6 said:**
> 
The below are the files listed in the external hard drive when I execute "dir" and many of these files have a Red X as I guess they are simply old versions:


[LIST]
[*]grub 
[*]config-5.15.0-39-generic 
[*]config-5.15.0-40-generic 
[/LIST]


[LIST]
[*]initrd.img.old 
[*]initrd.img 
[*]initrd.img-5.15.0-39-generic 
[*]initrd.img-5.15.0-40-generic 
[*]lost+found 
[*]memtest86+.bin 
[*]memtest86+_multiboot.bin 
[*]memtest86+.elf 
[*]System.map-5.15.0-39-generic 
[*]System.map-5.15.0-40-generic 
[*]vmlinuz 
[*]vmlinuz.old 
[*]vmlinuz-5.15.0-39-generic 
[/LIST]


[LIST]
[*]vmlinuz-5.15.0-40-generic 
[/LIST]

That looks like a /boot partition. When you have an encrypted system, you also need a /boot partition that's not encrypted, so it looks like you mounted that one. There must be another partition, which is encrypted, where you can find your documents, provided you have the password and the filesystem isn't damaged. Having never used encrypted harddrives, I don't know about that.

Those red Xes are for files where you have no read access.

---

### Post by grahammechanical on 2022-07-03
> When I click the initrd.img it opens Restore Disk Image

Of course it would do that. You are clicking on an image file. But why are you clicking on initrd.img? Are you trying to load the OS on the drive that is in the external drive enclosure?

I have a dead desktop machine and a new laptop. I have purchased a USB external drive enclosure and I am going to put the drive from the desktop into the enclosure. Then I can copy my personal files from the old drive onto the new laptop. If I wanted to load the OS on the old drive I would run this command:

```
sudo update-grub
```

Then I would reboot and at the Grub menu select the version of Ubuntu on the old drive. I am not sure that you want to do that. But that is the way I would do it.

Regards





Regards

---

### Post by president-6 on 2022-07-04
I appreciate all the replies. So, for me the solution was pretty much locating this article:  [https://dev-notes.eu/2016/09/mount-and-transfer-data-from-an-encrypted-filesystem-in-ubuntu/](https://dev-notes.eu/2016/09/mount-and-transfer-data-from-an-encrypted-filesystem-in-ubuntu/)

To that point, I did not proceed past moving the User Home Directory. I was able to pull up the files in the normal file viewer and then simply cut and paste them across. In hindsight, I should have done a few things like thinned out the files from cache, but it is what it is. IMHO there should be a simple page on this as I am pretty sure it is more common than folks let on about --- using a hard drive enclosure via a USB to pull a drive from a dead computer and salvage the files. My added issue was the encryption, but still ... And hindsight also has me setting up the data transfer from my laptop to the cloud. To that point, I wish everyone a safe and happy 4th of July. This thread is closed; however, I do not know how to close it.

---

### Post by Impavidus on 2022-07-04
You marked the thread as solved; that's enough.

Encryption really made this harder. Without that, you just plug it in and it works.

Have a nice day. Nothing to celebrate here; the next official holiday in my country will be Christmas.

---

