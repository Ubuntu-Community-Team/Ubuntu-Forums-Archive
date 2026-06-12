---
title: "Jaunty Kernel upgrade!..."
date: 2009-08-28
forum: Philippine Team
---

### Post by killer_d76 on 2009-08-28
After reading a few forum i found a very interesting thread wherein they have upgraded their linux kernel to 2.6.30-020630 by doing this simple few steps...

> 1. Go to this page: [http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.30/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.30/)

2. Download the following files to any location:

[B]linux-headers-2.6.30-020630_2.6.30-020630_all.deb

linux-image-2.6.30-020630-generic_2.6.30-020630_i386.deb[/B]

3. Install the files by doubleclicking them or selecting them from the menu. Start with "linux-headers..."

4. Reboot and confirm update by typing "uname -a" in a terminal window. 2.6.30 should be visible in plain text.



tested it on my trusty old Jaunty and to my surprise!.. it did boost up the speed of my Jaunty!.. :guitar: ASTIG!!!!!!...

---

### Post by Nhatz on 2009-08-28
Good!!! hehehe :)

ASTIG!!! :guitar:

---

### Post by Script Warlock on 2009-08-28
so ibig sabihin pwede na skip 2.6.29..... but yeah i tried parang ok pa laptop ko with 9.04 and kernel 2.6.30..

---

### Post by killer_d76 on 2009-08-28
found a few issues.. webcam not working and just lost my wireless connection!.. hehehe.. i think forgot to mention that you **[COLOR="Red"]do this process at your own risk![/COLOR]** :eek:

but other than those issue.. everything seems to be working fine and pretty snappy!... :D

---

### Post by Script Warlock on 2009-08-28
still everything is fine here......

---

### Post by Script Warlock on 2009-08-29
bison webcam on my lappy is not working...... roll-back agad ako...

---

### Post by e30ernest on 2009-10-05
Hi supported ba dito PAE?  I have 4gigs of RAM kaso 3.2Gigs lang nakikita ng machine.  Di naman 64bit ang machine ko and di ko alam if ok magswitch to the server kernel.  Baka mas ok itong new kernel na nakita mo.  Salamat!

---

### Post by tacantara on 2009-10-05
I did the kernel upgrade.  The first time I opened Firefox, the system froze up.  I rebooted and opened up the Chrome browser.  I found that the flash-based games on Facebook ran much smoother in that browser.  I've also noticed an overall performance boost from my laptop.  No problems with my wi-fi card.  I have other hardware to test out yet (i.e. webcam), but so far, so good. Thanks for the tip, _*killer_d76*_ :)

---

### Post by renkinjutsu on 2009-10-05
2.6.31 is where it's at ;)

---

### Post by detorresrc on 2009-10-06
Mga idol baket nag error sakin?


[PHP]
rommel@rommel-desktop:~/Desktop$ sudo dpkg -i *.deb
[sudo] password for rommel: 
Selecting previously deselected package linux-headers-2.6.30-020630.
(Reading database ... 317994 files and directories currently installed.)
Unpacking linux-headers-2.6.30-020630 (from linux-headers-2.6.30-020630_2.6.30-020630_all.deb) ...
Selecting previously deselected package linux-image-2.6.30-020630-generic.
Unpacking linux-image-2.6.30-020630-generic (from linux-image-2.6.30-020630-generic_2.6.30-020630_i386.deb) ...
Done.
Setting up linux-headers-2.6.30-020630 (2.6.30-020630) ...
Setting up linux-image-2.6.30-020630-generic (2.6.30-020630) ...
Running depmod.
update-initramfs: Generating /boot/initrd.img-2.6.30-020630-generic
Running postinst hook script /sbin/update-grub.
Searching for GRUB installation directory ... found: /boot/grub
Searching for default file ... found: /boot/grub/default
Testing for an existing GRUB menu.lst file ... found: /boot/grub/menu.lst
Searching for splash image ... none found, skipping ...
Found kernel: /boot/vmlinuz-2.6.30-020630-generic
Found kernel: /boot/vmlinuz-2.6.28-15-generic
Found kernel: /boot/vmlinuz-2.6.28-13-generic
Found kernel: /boot/vmlinuz-2.6.28-11-generic
Found kernel: /boot/vmlinuz-2.6.27-11-generic
Found kernel: /boot/vmlinuz-2.6.27-9-generic
Found kernel: /boot/vmlinuz-2.6.27-7-generic
Found kernel: /boot/memtest86+.bin
Replacing config file /var/run/grub/menu.lst with new version
Updating /boot/grub/menu.lst ... done

Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/dkms
 * Running DKMS auto installation service for kernel 2.6.30-020630-generic                                                                                                                                
 *  nvidia (180.44)...                                                                                                                                                                                    nvidia (180.44): Installing module.
  Kernel headers for 2.6.30-020630-generic are not installed.  Cannot install this module.
  Try installing linux-headers-2.6.30-020630-generic or equivalent.
                                                                                                                                                                                                   [fail]
run-parts: executing /etc/kernel/postinst.d/nvidia-common
[/PHP]

---

