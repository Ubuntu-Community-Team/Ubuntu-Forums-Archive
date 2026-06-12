---
title: "Need help getting grub menu item back"
date: 2012-05-02
forum: New to Ubuntu
---

### Post by oldgeezer1 on 2012-05-02
Using a Acer Aspire 3690 laptop with clean install of Windows XP Professional on formatted hard drive.  Installed Linux 10.04 LTS in dual boot configuration.  Restarted the system a couple times and all was well.  Got some updated files in Ubuntu and now Grub does not list Windows XP on the boot menu.  Even worse, I can't even find menu.lst.  Could someone kindly walk me through getting Windows XP back as a boot option?

---

### Post by westie457 on 2012-05-02
Hi first option is boot into Ubuntu and in a terminal run ```
sudo update-grub
```

Post back here any error messages you may get.

---

### Post by oldgeezer1 on 2012-05-02
> **westie457 said:**
> Hi first option is boot into Ubuntu and in a terminal run ```
sudo update-grub
```

Post back here any error messages you may get.
Thank you.  Here is what I get:

Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.32-41-generic
Found initrd image: /boot/initrd.img-2.6.32-41-generic
Found linux image: /boot/vmlinuz-2.6.32-28-generic
Found initrd image: /boot/initrd.img-2.6.32-28-generic
Found memtest86+ image: /boot/memtest86+.bin
done

---

### Post by westie457 on 2012-05-02
Looks like Windows has disappeared. One further check please.

Go to here for Bootinfoscript, full instructions are provided.

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

Pleases post the RESULTS.txt file inside {code} tags.

---

### Post by oldgeezer1 on 2012-05-02
Okay .... I think this is what you asked for:

### BEGIN /etc/grub.d/10_linux ###
menuentry 'Ubuntu, with Linux 2.6.32-41-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set 8dc3267e-af45-4d2e-b5db-087b72071c42
	linux	/boot/vmlinuz-2.6.32-41-generic root=UUID=8dc3267e-af45-4d2e-b5db-087b72071c42 ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-41-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-41-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set 8dc3267e-af45-4d2e-b5db-087b72071c42
	echo	'Loading Linux 2.6.32-41-generic ...'
	linux	/boot/vmlinuz-2.6.32-41-generic root=UUID=8dc3267e-af45-4d2e-b5db-087b72071c42 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-41-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-28-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set 8dc3267e-af45-4d2e-b5db-087b72071c42
	linux	/boot/vmlinuz-2.6.32-28-generic root=UUID=8dc3267e-af45-4d2e-b5db-087b72071c42 ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-28-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-28-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set 8dc3267e-af45-4d2e-b5db-087b72071c42
	echo	'Loading Linux 2.6.32-28-generic ...'
	linux	/boot/vmlinuz-2.6.32-28-generic root=UUID=8dc3267e-af45-4d2e-b5db-087b72071c42 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-28-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod ext2
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set 8dc3267e-af45-4d2e-b5db-087b72071c42
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod ext2
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set 8dc3267e-af45-4d2e-b5db-087b72071c42
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}


No rush getting back to me right now as I have a Bible study class at my church so won't be back for about four hours.  Thanks for your help.

---

### Post by oldgeezer1 on 2012-05-03
I was able to boot a DOS copy of Norton Partition Magic and discovered that there was an allocation error on the partition table.  With that in mind I dediced to try Grub's repair menu selection.  I had to run it twice but the second time Windows XP Pro reappeared on the menu.  I am happy to say that I once again have a dual-boot system up and running. Hopefully it will stay that way.

My sincere thanks to westie457 for his diagnostic guidance.  I learned a thing or two from that.

---

### Post by westie457 on 2012-05-03
Glad you got it sorted. When you have a few moments could you mark as solved please.

---

### Post by oldgeezer1 on 2012-05-03
> **westie457 said:**
> Glad you got it sorted. When you have a few moments could you mark as solved please.

I realize that is the courteous thing to do but for the life of me I can't seem to figure out how to change the category from Ubuntu to Solved.

---

### Post by BlinkinCat on 2012-05-03
> **oldgeezer1 said:**
> I realize that is the courteous thing to do but for the life of me I can't seem to figure out how to change the category from Ubuntu to Solved.

Hi,

At the top of the page you will see a choice of "Thread tools"
One of the items you may select is "Mark this thread as Solved"

Cheers - :p

---

