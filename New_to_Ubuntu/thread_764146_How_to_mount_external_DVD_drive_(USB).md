---
title: "How to mount external DVD drive (USB)"
date: 2008-04-23
forum: New to Ubuntu
---

### Post by iwannalearn on 2008-04-23
Hi, how do i connect my external DVD drive (USB)? I have inserted a disk in the drive and i get a window which says "Medium type Unmounted CD Writer"

What do i do to mount it?

Would it be something like this?

mkdir /mnt/dvdr

mount /dev/usb /mnt/dvdr

Thanks

---

### Post by wolfen69 on 2008-04-23
> **iwannalearn said:**
> Hi, how do i connect my external DVD drive (USB)? I have inserted a disk in the drive and i get a window which says "Medium type Unmounted CD Writer"

What do i do to mount it?

Would it be something like this?

mkdir /mnt/dvdr

mount /dev/usb /mnt/dvdr

Thanks

that's about it, except that you will have to edit your /etc/fstab also.

---

### Post by iwannalearn on 2008-04-23
> **wolfen69 said:**
> that's about it, except that you will have to edit your /etc/fstab also.


This i am not sure of, can you tell me how?

I am sorry linux still new to me!

---

### Post by twright on 2008-04-23
you don't need to do that yet

you should just be able to mount it, if not you might need to install some extra packages or format the hard drive

/etc/fstab just contains the default options for mounting drives, editing it (sudo gedit /etc/fstab) will change how drives are automatically handled and if the drive is in /etc/fstab you can mount it just by typing mount /dev/**whatever. **don't worry, it may seem confusing now but once you do not need to understand all this stuff just to use the system :)

---

### Post by aparigraha on 2008-04-23
have a look here:
[How to fstab]("http://ubuntuforums.org/showthread.php?t=283131")

---

### Post by ajmix2 on 2010-05-16
Honestly,  didn't understand a thing to do...I'm lost....

---

