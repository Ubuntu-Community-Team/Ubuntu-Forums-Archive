---
title: "boot windows installation iso without flash drive/DVD on GRUB"
date: 2021-03-17
forum: New to Ubuntu
---

### Post by zaciars on 2021-03-17
I use dualboot linux and windows, however my windows is broken and I can't access it(shutdown every time i try to start) 
I don't have any usb or dvd so I couldn't boot it normal ways...

i read in here [https://help.ubuntu.com/community/Grub2/ISOBoot#:~:text=Once%20the%20menuentry%20has%20been,and%20press%20ENTER%20or%20F10.](https://help.ubuntu.com/community/Grub2/ISOBoot#:~:text=Once%20the%20menuentry%20has%20been,and%20press%20ENTER%20or%20F10.)
that you can boot an ISO with GRUB
,but my /boot/images is to small to fit windows iso so i couldn't use grub-imageboot

sorry if this is not really an Ubuntu questions

---

### Post by C.S.Cameron on 2021-03-17
I have shown the method that worked for me here: [https://askubuntu.com/questions/1321750/how-to-erase-ubuntu-and-reinstall-windows-10-on-a-single-booted-system/1321763#1321763](https://askubuntu.com/questions/1321750/how-to-erase-ubuntu-and-reinstall-windows-10-on-a-single-booted-system/1321763#1321763)
Let me know if you need additional explanation.

---

### Post by zaciars on 2021-03-17
sorry, page not found

---

### Post by C.S.Cameron on 2021-03-17
That page was just deleted. The guys at Ask Ubuntu seem to not want users reinstalling Windows, Here is the solution.

**Installing Windows 10 without USB using Ubuntu GRUB**

- Backup the Target drive.

- Create a 6GB NTFS partition on the hard drive and extract the Windows ISO to it.

- Create a 20GB, or larger, NTFS partition on the hard drive for the Windows Installation.

- Open Disks, (Gnome-Disks), and note Device, (/dev/sdx), and UUID of the Windows ISO extract partition.

- For msdos partition table, copy the following menuentry to `/etc/grub.d/40-custom/`*:

```
```
menuentry 'Windows Recovery Environment (on /dev/sda4)' --class windows --class os $menuentry_id_option 'osprober-chain-592C85254E2CD0B7' {
	insmod part_msdos
	insmod ntfs
	set root='hd0,msdos4'
	if [ x$feature_platform_search_hint = xy ]; then
	  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos4 --hint-efi=hd0,msdos4 --hint-baremetal=ahci0,msdos4  592C85254E2CD0B7
	else
	  search --no-floppy --fs-uuid --set=root 592C85254E2CD0B7
	fi
	parttool ${root} hidden-
	drivemap -s (hd0) ${root}
	chainloader +1
    ntldr /bootmgr
}
```
```

- Edit menuentry, changing `sda4 to sdax`, `msdos4` to `msdosx` (4 places), and 592C85254E2CD0B7 to UUID, (3 places), to suit step 4 above.

- Run `sudo update grub` confirm that `ntldr /bootmgr` appears in grub.cfg.

- Boot the computer into the newly created Windows menuentry and install Windows into it's new partition.

- Reinstall Ubuntu if desired, the GRUB bootloader will have been replaced with the Windows bootloader.

*For gpt partition table, copy the following menuentry to `/etc/grub.d/40-custom/`:

```
    menuentry 'Windows Recovery Environment (on /dev/sdc1)' --class windows --class os $menuentry_id_option 'osprober-chain-5642BC722509341F' {
    	insmod part_gpt
    	insmod ntfs
    	set root='hd0,gpt1'
    	if [ x$feature_platform_search_hint = xy ]; then
    	  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,gpt1 --hint-efi=hd0,gpt1 --hint-baremetal=ahci0,gpt1  5642BC722509341F
    	else
    	  search --no-floppy --fs-uuid --set=root 5642BC722509341F
    	fi
    	drivemap -s (hd0) ${root}
    	chainloader +1
    	ntldr /bootmgr
    }
```

**Boot selecting Windows from the GRUB menu and follow the instructions.**

---

### Post by zaciars on 2021-03-17
because I can't access windows, which apps should I use to create NTFS partition and extract windows iso to it?

---

### Post by zaciars on 2021-03-17
also should I just replace it with sdax and msdosx or i need to find what is the 'x'?
edit(my partition is GPT, is the step still mandatory?)

---

### Post by C.S.Cameron on 2021-03-18
I use GParted. Disks will also work.

The menuentry above has "set root='hd0,gpt1'"

Disks would call that partition sda1

So if Disks lists the partition as sdb2, you would use 'hd1,gpt2'.

If you have Ubuntu installed on the HDD and have extracted the ISO, you can run "sudo update-grub" and that will add most of the menu entry, but you would need to add the line: "ntldr /bootmgr" manually.

---

### Post by zaciars on 2021-03-18
Edit:
Nvm working after removing theme

---

