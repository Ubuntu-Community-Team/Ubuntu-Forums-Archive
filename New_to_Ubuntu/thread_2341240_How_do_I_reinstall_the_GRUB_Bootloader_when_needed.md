---
title: "How do I reinstall the GRUB Bootloader when needed?"
date: 2016-10-26
forum: New to Ubuntu
---

### Post by OctaVive on 2016-10-26
So I heard, when Windows releases a new big update, you have to reinstall the grub bootloader because the update can overwrite the bootloader.


If this happens, how can I reinstall the grub bootloader?

---

### Post by ajgreeny on 2016-10-26
You can do it from a live DVD/USB of any of the same version *ubuntu OSs, either by mounting the installed Ubuntu partitions and running command ```
sudo grub-install /dev/sda
```assuming sda is your Ubuntu disk, or you can also do it with Boot-Repair in my signature below and follow the instructions there to repair or reinstall grub.

---

### Post by TheFu on 2016-10-26
It is a little trial and error, since every machine is a little different, but ..... normally, it is **sudo update-grub**. This can be run from a live-booted Ubuntu. It should find the existing grub install and successfully search for AND find all known OSes on the connected HDDs.  That is the theory. I've seen it be confused with a USB Flash drive being deemed "the first disk" and updating that rather than the grub on the disk I intended.  The tool can't read our minds, so sometimes it needs a little help when disk order gets screwed up. 

I don't have any UEFI systems dual booting here, so that might cause slight changes to be necessary.  In theory, it should make it easier.

Of course, if you use whole disk encryption, things can be a little more complicated.  I don't dual boot any of my encrypted systems either.

At that point, I'd have to RTFM ... check the manpages for grub and update-grub and **grub-install**.  BTW, running **sudo update-grub** multiple times should be safe. For example, just ran it:
```
$ sudo update-grub
Generating grub configuration file ...
Warning: Setting GRUB_TIMEOUT to a non-zero value when GRUB_HIDDEN_TIMEOUT is set is no longer supported.
Found linux image: /boot/vmlinuz-4.4.0-45-generic
Found initrd image: /boot/initrd.img-4.4.0-45-generic
Found linux image: /boot/vmlinuz-4.4.0-38-generic
Found initrd image: /boot/initrd.img-4.4.0-38-generic
Found memtest86+ image: /memtest86+.elf
Found memtest86+ image: /memtest86+.bin
done
```  This is a legacy boot system with whole disk encryption (using LVM and dm-crypt/LUKS) - no efi partition.

Make sense?

---

### Post by valereguerin on 2016-10-26
you can also run "Bootrepair" on live cd or USB key....

---

### Post by yancek on 2016-10-26
> it is **sudo update-grub**. This can be run from a live-booted Ubuntu

I don't think that will work without chrooting to the boot drive. grub-install from a DVD or flash drive will work.  The boot repair disk is probably be easiest but can be a problem if you have a number of different hard drives as you will have to tell which drive you want Grub installed to.

---

### Post by TheFu on 2016-10-26
> **yancek said:**
> I don't think that will work without chrooting to the boot drive. grub-install from a DVD or flash drive will work.  The boot repair disk is probably be easiest but can be a problem if you have a number of different hard drives as you will have to tell which drive you want Grub installed to.

You might be correct. Haven't tested this on a dual boot in some time.  Vaguely remember there was a howtogeek article about this ... found it. [http://www.howtogeek.com/114884/how-to-repair-grub2-when-ubuntu-wont-boot/](http://www.howtogeek.com/114884/how-to-repair-grub2-when-ubuntu-wont-boot/) - it is from 2012, so things might have changed slightly.  It doesn't show using a chroot.

---

### Post by oldfred on 2016-10-26
With UEFI Windows does not overwrite the /EFI/ubuntu folder in the ESP - efi system partition. But does change boot order making it first. Full install of grub makes Ubuntu entry first in UEFI, so boot order has to be changed if desired. 

But I also suggest to backup the entire ESP, it is not large and all you have to do is restore it, no install required. 
You may have to cold boot several times to get UEFI to see if a totally reformatted partition as it then has new GUID.

Also with UEFI, you should be able to use UEFI (which is also a boot manager with menu) to choose which system to boot even if not new default.
Then when in Ubuntu you can use efibootmgr to reset boot order.
see:
man efibootmgr
#Shows list of entries in UEFI boot menu:
sudo efibootmgr -v
       #Change boot order with efibootmgr, some require all 4 hex char others 1 is ok. This makes entry 2 first boot option and 1 second.
sudo efibootmgr -o 2,1 

 How to restore the Ubuntu/XP/Vista/7/8/10 BIOS bootloader 
[https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader](https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader)
[https://help.ubuntu.com/community/Grub2/Installing#Fixing_a_Broken_System](https://help.ubuntu.com/community/Grub2/Installing#Fixing_a_Broken_System) 

For BIOS, from live installer you must first mount partition (and /boot if separate partition) then install. 
      sudo mount /dev/sda5 /mnt
sudo grub-install --root-directory=/mnt/ /dev/sda
#  The above command should work but they now suggest this command for grub 1.99 with Natty 11.04 or later - uses boot not root.:
sudo grub-install --boot-directory=/mnt/boot /dev/sda 
    
If inside working install you can just specify which MBR to install into.
#if it's "/dev/sdb"  then just run:
sudo grub-install /dev/sdb 

 Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

I also have Super Grub to boot into system or its Rescatux. 
[http://www.supergrubdisk.org/](http://www.supergrubdisk.org/) 

And it does not hurt to have Knoppix, Parted Magic, gparted and other repair tools in tool box. I used to burn many CDs, but now have flash drives, but put many tools on one flash drive and use grub2's loopmount to directly boot ISO, so many fit even on smaller flash drives.

---

