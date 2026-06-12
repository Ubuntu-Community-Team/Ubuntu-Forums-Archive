---
title: "Inconsisten file structure message"
date: 2008-11-07
forum: New to Ubuntu
---

### Post by jivabill on 2008-11-07
Well been running 8.04 on my Compaq machine no problem, worked good.  Today out of the clear blue when I try to start it I get this message, "Error 16 Inconsistent File Structue"

I searched all the forums and found a thread where the remedy was described like this:
Boot up on the Live CD
Start a Terminal Window
type sudo fsck.ext3 -f /dev/sda1 (on my machine)

I ran this it went thru a number of passes and no error messages.

BUT

Still can not boot from the latest kernel in the menu.  I can go back to 19 and system boots fine.

My question then, is there a backup of kernel 21 somewhere on my machine?  Can I use it to boot and get this fixed.  Do I have to do a whole fresh install?

Frankly, this is beginning to seem a lot like Windows :-)

Help appreciated.
Thanks in advance
bill

---

### Post by Yuki_Nagato on 2008-11-07
If all you want to do is roll back to a previous kernel, then YES, this is easy to do.

All of the kernels that have been used at some point are stored in the "/boot" directory.

Get to a terminal.  This can be done from the "19" kernel.

We are going to edit the GRUB menu.lst file to point to a different kernel.

```

cd /boot/grub/
cp menu.lst menu.lst.backup
gedit menu.lst

```

We "cd" into the grub directory, backup the previous file, and then begin to edit.  If it asks for sudo, give it the password.

In the menu.lst file, there should be entries that look something like this (Or very similar.  This was not taken from an Ubuntu machine.):

```
title Linux kernel 2.6.22
root (hd0,0) 
kernel /boot/vmlinuz-2.6.22 root=/dev/hda1 ro 3
initrd /boot/initrd.img 

```

Find the one that points to the broken kernel.  Then edit the number of the kernel.  The, "vmlinuz-2.6.XX" part.  That is critical, but changing the number in the "title" is nice too.  Do not bother the "19" kernel entries you booted into with in case this does not work.

After changing these numbers, save the file and reboot.  It might work.

If you want to double check that there is a kernel to point to, and double check the name, "cd /boot"

The available kernels should be in there.  Do not worry about most of the name.  The number is what is most important.  If you just edit the number in menu.lst, you should be fine.

---

### Post by jivabill on 2008-11-07
Hi Yuki, thank you for the good suggestion and code.  I'll give it a try.  

I noted in another thread in the install/upgrade forum someone said there was a "backup" they could go to from the live CD session.  Hence my question.

Sounds like your remedy may do the trick.  Still a mystery how my kernel 21 got corrupted.  Looks like it is a common occurence though.

thanks again
bill

---

