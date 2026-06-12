---
title: "Using grub-pc for booting existing LVM ('/' on LV) installation"
date: 2009-06-27
forum: Outdated Tutorials &amp; Tips
---

### Post by Linux_oid on 2009-06-27
The posting describe how to boot existing LVM installation using grub-pc (also known as GRUB2). 

*** Install grub2 

$ sudo aptitude install grub2

By default, Ubuntu 9.04 doesn't install GRUB2 but creates entry in existing GRUB (GRUB Legacy) to test it. Grub-pc is using menu.lst existing entries and os-prober package to create /boot/grub/grub.cfg file responsible for booting.
Finall grub.cfg here contains 32 menuentries.



*** Create core.img with LVM support

$ sudo grub-mkimage --output=/boot/grub/core.img ext2 _chain pc gpt biosdisk lvm 

*** Create an entry in existing grub. 

***** GRUB entry 
title Ubuntu 9.04 core.img on /dev/sda10
root (hd0,9)
kernel (hd0,9)/boot/grub/core.img
***** The end of GRUB entry

*** Adding custom entry to GRUB2 menu.

My posting in Debian forum [http://forums.debian.net/viewtopic.php?f=17&t=36716](http://forums.debian.net/viewtopic.php?f=17&t=36716) gives some ideas about creating it.

$ sudo gedit /etc/grub.d/40_custom

It opens file with three lines only

***** Original 40_custom file
#!/bin/sh
exec tail -n +3 $0 
# This file is an example on how to add custom entries
***** The end of original 40_custom file

Modify it like an example below

***** Custom entries to grub-pc sample file

#!/bin/sh
# exec tail -n +3 $0 
# This file is an example on how to add custom entries

echo "Adding Mandriva 2009.1 (speedboot) on /stable-testing" >&2
cat << EOF
menuentry "Mandriva 2009.1 (speedboot) on stable-testing" {
linux (stable-testing)/boot/vmlinuz root=/dev/mapper/stable-testing ro silent speedboot
initrd (stable-testing)/boot/initrd.img
}
EOF

echo "Adding Ubuntu 8.04.2 on /stable-main" >&2
cat << EOF
menuentry "Ubuntu 8.04.2 on /stable-main" {
linux (stable-main)/vmlinuz root=/dev/mapper/stable-main ro silent 
initrd (stable-main)/initrd.img
}
EOF

***** The end of custom entries to grub-pc sample file

Save the file and issue

$ sudo /usr/sbin/update-grub

*** Booting custom entry by default

$ sudo gedit /etc/default/grub

There is a line GRUB_DEFAULT=0 that should be modified to something like this GRUB_DEFAULT=<the_line_number_you_want_to_boot>. 
The simplest way to find out what menuentry GRUB2 should boot:

Open grub.cfg file

$ gedit /boot/grub/grub.cfg 

and count existing menuentries. 

Modify /etc/default/grub file, save it, and issue

$ sudo /usr/sbin/update-grub

Reboot.

---

