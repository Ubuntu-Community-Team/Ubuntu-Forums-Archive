---
title: "update-grub not updating menu.lst"
date: 2008-08-26
forum: New to Ubuntu
---

### Post by ace007 on 2008-08-26
Can someone help me with this?

I noticed menu.lst is not updating the kernel when I install a new update.  I have run "sudo update-grub" and the new kernels are found, but menu.lst is not modified.  From what I understand this is because I choose keep local menu.lst when I installed a new kernel for the first time. I should have selected update menu.lst.  

Evidently update-grub loads the options from that first time I installed, can someone tell me how to change it so that I can re-run update-grub and have the option to update the menu.lst file?


Here is the bug:
[https://bugs.launchpad.net/ubuntu/+source/grub/+bug/202009](https://bugs.launchpad.net/ubuntu/+source/grub/+bug/202009)

---

### Post by philinux on 2008-08-26
This is a long shot.

Install startupmanager from synaptic.

But run it from a terminal using

sudo startupmanager 

Yes I know it should be gksudo. but use sudo for this.

It should correct the issue.

---

### Post by nicedude on 2008-08-26
I don't see an easy answer, I just read all the posts on that bug report and no one had an answer for those who were so afflicted. You could always try just modifying it by hand as it is pretty simple ( for starters ou could copy the working kernel load settings and paste it anew and then change the kernel to reflect the one you want to boot into. That way if you goof it would only be a goof of the one that you added and old ones should work.

sudo gedit /boot/grub/menu.lst  -  to edit it


here are some outputs from mine, as you can see the only thing different between my -20 and -21 kernels is the -2? part which if for example I had installed -22 but it didn't show up I could just copy and paste the -21 one and change -21 to -22 and the number in the initrd line as well.

title        Ubuntu 8.04.1, kernel 2.6.24-21-generic
root        (hd0,2)
kernel        /boot/vmlinuz-2.6.24-21-generic root=UUID=761f2c18-7ace-4955-a05b-599ad9bf942a ro quiet splash
initrd        /boot/initrd.img-2.6.24-21-generic
quiet

title        Ubuntu 8.04.1, kernel 2.6.24-21-generic (recovery mode)
root        (hd0,2)
kernel        /boot/vmlinuz-2.6.24-21-generic root=UUID=761f2c18-7ace-4955-a05b-599ad9bf942a ro single
initrd        /boot/initrd.img-2.6.24-21-generic

title        Ubuntu 8.04.1, kernel 2.6.24-20-generic
root        (hd0,2)
kernel        /boot/vmlinuz-2.6.24-20-generic root=UUID=761f2c18-7ace-4955-a05b-599ad9bf942a ro quiet splash
initrd        /boot/initrd.img-2.6.24-20-generic
quiet

Hope this info helps and sorry you are in a bad spot, but on the good side I would just learn allot more about GRUB and count this as a learning experience. The kernel doesn't update that often and you will just be good at fixing your own Grub file :-)

---

### Post by chrisccoulson on 2008-08-26
To fix this, edit your /etc/kernel-img.conf file and add the following two lines to it:
```
postinst_hook = update-grub
postrm_hook = update-grub
```

Should do the trick:)

*Edit: Sorry, I misread your post. It seems your problem is not that update-grub isn't running*

---

