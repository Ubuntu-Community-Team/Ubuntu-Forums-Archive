---
title: "HOWTO : keep boot screen after reinstalling windows"
date: 2005-09-04
forum: Outdated Tutorials &amp; Tips
---

### Post by dkmxbe on 2005-09-04
Hi

i'm runnig windows and on my second hard drive: ubuntu.
windows is running slowly; so i will format it and reinstall it

but i know from the last time i formated windows, i olso lost my bootscreen

so question, how can i hold my boot screen ? after installing windows ?

mx

---

### Post by BlueEagle on 2005-09-06
What you need to do is to install grub on the MBR again. What I do is boot from the install-CD, press ALT+F2 and Enter to open a console.
Then mkdir /installed
mount /dev/XdaY/installed
mount /dev/XdaY/installed/boot
mount /dev/XdaY/installed/usr
..and so on until you've got all your partitions.
chroot /install /bin/bash
grub
Now, in the grub setup prompt write
root (hd0,Y)
setup (hd0)

Note that /dev/XdaY is the type and partition number like /dev/hda5 or /dev/sda7
Note that root (hd0,Y) Y should be the partition number of your /boot partition (or / partition if you have got no /boot). Also note that grub counts from 0 while as /dev/XdaY counts from 1, so you need to subtract one from the number your /boot partition has in /dev/XdaY

Now it should be a matter of rebooting.

To be honest I haven't tried this with the Ubuntu install CD, but rather with the gentoo live-CD. You can grab the minimal image from gentoo.org if this does not work with the ubuntu install CD.

---

