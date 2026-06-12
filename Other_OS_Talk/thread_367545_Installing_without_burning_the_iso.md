---
title: "Installing without burning the iso?"
date: 2007-02-22
forum: Other OS Talk
---

### Post by Minyaliel on 2007-02-22
I've run out of cd's... Well, I know it's possible to install directly from the iso file without burning it to a cd first, but I'm not entirely sure how to do it. Could someone please explain this to me? I'd be eternally grateful.

---

### Post by renzokuken on 2007-02-22
i think you can do it with something called a "Network Install", not sure how though, never tried it myself

---

### Post by mips on 2007-02-22
You should me able to install from the iso or the net. you will have to mount the iso.

I have never done this but there are guides out there if you search.

---

### Post by Minyaliel on 2007-02-22
Well, I did find [http://www.paulisageek.com/wordpress/2006/03/22/install-linux-without-burning-a-cd-dvd/](http://www.paulisageek.com/wordpress/2006/03/22/install-linux-without-burning-a-cd-dvd/), but I don't understand a thing :P

---

### Post by fuscia on 2007-02-22
unless you're really interested in learning how to do this, i say drop the other shoe and go buy some cds.

---

### Post by steven8 on 2007-02-23
> **fuscia said:**
> unless you're really interested in learning how to do this, i say drop the other shoe and go buy some cds.

What do shoes have to do with it? :popcorn:

---

### Post by M_the_C on 2007-02-23
> **Minyaliel said:**
> Well, I did find [http://www.paulisageek.com/wordpress/2006/03/22/install-linux-without-burning-a-cd-dvd/](http://www.paulisageek.com/wordpress/2006/03/22/install-linux-without-burning-a-cd-dvd/), but I don't understand a thing :P
This only works if you have a Linux OS already installed.

I think it works like this:

Create a directory on a hard drive.
Type:
```
mount -o loop nameofiso.iso /mnt/cdrom
```
to mount the .iso so it appears as a CD\DVD.

Then copy these files:
```
cp -a /mnt/cdrom/isolinux/vmlinuz /boot/FC2-install
cp -a /mnt/cdrom/isolinux/initrd.img /boot/FC2-install.img
```
this way copies it to the /boot/ folder, I'm not so sure this is such a good idea.  Fortunately you can just put it anywhere.  Simply substitute /boot/ for another folder.

Then unmount the .iso:
```
umount /mnt/cdrom
```

Open grub.conf which is found at /etc/grub.conf in a text editor.

Go down to where you see a similar entry to below, with the title of the distro. (i.e. ubuntu 6.10)  Then add the following lines:

```
title justpickaname
root (hd0,0)
kernel /boot/FC2-install
initrd /boot/FC2-install.img
```
You shouldn't need to but you may need to change 'root' to whichever drive you are installing from.

Change the 'kernel' and 'initrd' to the location of the files you copied earlier.

Then reboot your computer and install.

This should work, but post back if it doesn't.

---

### Post by Minyaliel on 2007-02-23
Thanks! *hug for M_the_C*

So which folder would you suggest instead of the boot folder, and why? (I'm really doing this to force myself to use the command line and to learn a bit about Linux, apart from the cd problem, so please bear with my questions...)

---

### Post by fuscia on 2007-02-24
> **steven8 said:**
> What do shoes have to do with it? :popcorn:

that's a little like asking "what would a snowball be doing in hell? :confused: "

---

### Post by steven8 on 2007-02-27
> **fuscia said:**
> that's a little like asking "what would a snowball be doing in hell? :confused: "

But. . .a snowball would melt in hell.  :popcorn:

---

### Post by fdrake on 2007-02-27
to mount your iso image :
sudo apt-get install mount
mount  /isopath/isoname.iso /media/cdrom

isopath=the location of your isofile
isoname=the name
after you mount the iso you shuld see a cd loaded on the desktop.

---

