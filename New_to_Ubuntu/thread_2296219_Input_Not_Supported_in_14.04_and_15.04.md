---
title: "Input Not Supported in 14.04 and 15.04"
date: 2015-09-24
forum: New to Ubuntu
---

### Post by Loina on 2015-09-24
Two quick things:

I'm running an Nvidia graphics card (GTX 970)
This is happening on both Xubuntu and Ubuntu, haven't tested it on any others as of yet.

So on a fresh install of Ubuntu (Wiped hard drive so it has no previous OS etc.. etc..) using a USB stick to boot from, I get to the first menu (The Try ubuntu, install Ubuntu, advanced options etc...) I can select anything from here, but when I go to install or try Ubuntu I get the Ubuntu loading screen (the four dots lighting up underneath the ubuntu logo) and then the screen goes black and flashes "input not support" around the screen.

I can load the ctrl, alt, f1 menu and that's it, I've tried changing the grub menu resolution through the cfg so it reads like so:

```


if loadfont /boot/grub/font.pf2 ; then
	set gfxmode=1024x768	insmod efi_gop
	insmod efi_uga
	insmod gfxterm
	terminal_output gfxterm
fi


set menu_color_normal=white/black
set menu_color_highlight=black/light-gray


menuentry "Try Ubuntu without installing" {
	set gfxpayload=keep
	linux	/casper/vmlinuz.efi  file=/cdrom/preseed/ubuntu.seed cdrom-detect/try-usb=true noprompt floppy.allowed_drive_mask=0 ignore_uuid boot=casper quiet splash --
	initrd	/casper/initrd.lz
}
menuentry "Install Ubuntu" {
	set gfxpayload=keep
	linux	/casper/vmlinuz.efi  file=/cdrom/preseed/ubuntu.seed cdrom-detect/try-usb=true noprompt floppy.allowed_drive_mask=0 ignore_uuid boot=casper only-ubiquity quiet splash --
	initrd	/casper/initrd.lz
}
menuentry "OEM install (for manufacturers)" {
	set gfxpayload=keep
	linux	/casper/vmlinuz.efi  file=/cdrom/preseed/ubuntu.seed cdrom-detect/try-usb=true noprompt floppy.allowed_drive_mask=0 ignore_uuid boot=casper only-ubiquity quiet splash oem-config/enable=true --
	initrd	/casper/initrd.lz
}
menuentry "Check disc for defects" {
	set gfxpayload=keep
	linux	/casper/vmlinuz.efi  cdrom-detect/try-usb=true noprompt floppy.allowed_drive_mask=0 ignore_uuid boot=casper integrity-check quiet splash --
	initrd	/casper/initrd.lz
}



```

to no avail, googling gave no results so for someone migrating off Windows, any pointers as to how to fix this?

---

### Post by yancek on 2015-09-24
You indicate "a fresh install of Ubuntu" but the rest of your comments seem to indicate you are still trying to install from a flash drive.  Is it installed or not?  I had this several versions back on an installed system and had to boot a Live CD, mount the Ubuntu partition then chroot into it and modify the /etc/default/grub file by removing the hash mark (#) at the beginning of the line, specifically the line below.  After doing that, run sudo update-grub.

> [COLOR=red]#GRUB_GFXMODE=640x480[/COLOR]

If you are getting this on the isntallation medium post back.

---

### Post by uninvolved on 2015-09-24
I'm assuming you have another computer that you're using to type this into here - hopefully it isn't a cell phone or the likes. As the above poster implied, try using it as a live disk instead of doing the install from GRUB. However, before doing that, get yourself a fresh image (I'm assuming this is possible) and download it. Install an application called 'unetbootin' and follow the directions - in your case you'll want it to use the .iso image that you downloaded. You can check the MD5/checksum on your freshly downloaded .iso and make sure that it matches the sum at the download site and do that before making your live USB disk.

Then, as the above person mentioned, you'll probably want to boot to the live state and do the install from there - I've had MUCH better luck doing it from inside the live OS than I have from the GRUB menu. I have no idea what causes this of if it an error on my part. However, I've had this happen a few times and so now I just do so by default. I've tried every flavor of Ubuntu that I know of, and a number of forks. This happened with some regularity so I simply boot to the live state and install from there.

It will load very slowly at first. Once everything is loaded into RAM you will be all set. Just be aware that it takes a minute. Or three.

---

### Post by deadflowr on 2015-09-24
Probably need to set nomodeset at the grub menu.
When you start it and get that menu screen, try pressing F6, then select the option nomodeset.
Then hit the esc key to return to normal screen.
Then try booting.

---

### Post by Loina on 2015-09-24
> **deadflowr said:**
> Probably need to set nomodeset at the grub menu.
When you start it and get that menu screen, try pressing F6, then select the option nomodeset.
Then hit the esc key to return to normal screen.
Then try booting.
I get to the menu screen that looks like so: [http://imgur.com/n71yf46](http://imgur.com/n71yf46) (sorry for the crappy screenshot, best I could do)

Hitting F6 does nothing but make the screen flash black for a quarter of a second.


Also:
I'm using the live CD on a USB stick (as the comment above suggest I should)

---

### Post by yancek on 2015-09-24
You're using unetbootin so you might try the suggestion above to add "nomodeset" to the kernel line.  With either the default or Try Ubuntu menu options highlighted, hit the Tab key on your keyboard and the menu should change.   It should show the standard kernel/linux line so use the right arrow key to go to boot=casper and after that leave a space and enter nomodeset.  This is only good for a one time boot.  Hit the enter key and it should eventually boot.  Took about 15 seconds on my machine.  There might be another 'magic key' but I don't know what it is.  If that doesn't work, try the same process and try adding nomodeset to the end of the line.

---

### Post by Loina on 2015-09-24
> **yancek said:**
> You're using unetbootin so you might try the suggestion above to add "nomodeset" to the kernel line.  With either the default or Try Ubuntu menu options highlighted, hit the Tab key on your keyboard and the menu should change.   It should show the standard kernel/linux line so use the right arrow key to go to boot=casper and after that leave a space and enter nomodeset.  This is only good for a one time boot.  Hit the enter key and it should eventually boot.  Took about 15 seconds on my machine.  There might be another 'magic key' but I don't know what it is.  If that doesn't work, try the same process and try adding nomodeset to the end of the line.
This did it! Thank you for compensating for my newbieness!

---

### Post by Geoffrey_Arndt on 2015-09-24
I also think "nomodeset" is your best option . . . Ubuntu requires 3d hw-acceleration, and the default open-source driver doesn't handle that well.    Nomodeset will put you into a lower resolution screen (typically 800 by 600) so it's clunky and slow, but will allow you to get to the place to use Ubuntu's software repositories to load/install the Ubuntu modified nvidia driver.

"System Settings>Software & Updates>Additional Drivers (Tab)"

For me (on a couple HP machines) the trick was _to display the actual "grub boot parameter" screen_ and add the text "nomodeset" in exactly the right place.

See below for additional links I've saved in my zim-wiki database:

................................................................................................................

**Nomodeset**

   Created Wednesday 05 August 2015 
   To  boot with the 'nomodeset' boot parameter. 
   1).   For a PC with no other operating system - the Grub2 menu will NOT be displayed by default, so:
>     Hold down (right) SHIFT to display the menu during boot. In certain cases, pressing the ESC key may also display the menu.  
   If you are able to boot with this parameter, you can install a graphics driver from the "Additional Drivers" utility in the actual install. 
   [http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132) <- How to set NOMODESET and other kernel boot options in grub2 
   [https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions) <-nomodeset option in detail 
   let us know how it goes
THE current(cy) in Documentation: 
[https://help.ubuntu.com/community/PopularPages](https://help.ubuntu.com/community/PopularPages) 
   ................................................................................................................. 
   Another rendition of above: 
   Boot the machine and at the grub menu highlight the kernel you want to use and click 'e' to edit.


   Find the line that ends in 'quiet splash' and after a space, add 'nomodeset'. The end of the line should look like this: 

   _quiet splash nomodeset_

Follow the instructions at the bottom of that screen to save changes and continue

---

