---
title: "Can't mount Vista after...."
date: 2008-08-18
forum: New to Ubuntu
---

### Post by detroit/zero on 2008-08-18
(accidentally [posted to]("http://ubuntuforums.org/showthread.php?t=893380") Hardware & Laptops.)

I screwed up.

I have a Vista partition on my laptop. I was just screwing around and gave it a fancy windows icon, and I got to looking around in the Properties dialog, and I saw the option to specify a mount point. I thought, "Yeah, cool - why have it come up as 'SQ004286V02' when I can label it 'Vista'?"

So I set the mount point to /media/Vista, unmounted the drive, and when I try to remount it I get an error message saying that "the mount point cannot contain the following characters: newline_G_DIR_SEPARATOR (usually /)".

Since I can't mount this drive now, where can I go to erase that change I made and let the drive mount again?

---

### Post by billgoldberg on 2008-08-18
> **detroit/zero said:**
> (accidentally [posted to]("http://ubuntuforums.org/showthread.php?t=893380") Hardware & Laptops.)

I screwed up.

I have a Vista partition on my laptop. I was just screwing around and gave it a fancy windows icon, and I got to looking around in the Properties dialog, and I saw the option to specify a mount point. I thought, "Yeah, cool - why have it come up as 'SQ004286V02' when I can label it 'Vista'?"

So I set the mount point to /media/Vista, unmounted the drive, and when I try to remount it I get an error message saying that "the mount point cannot contain the following characters: newline_G_DIR_SEPARATOR (usually /)".

Since I can't mount this drive now, where can I go to erase that change I made and let the drive mount again?

you can use gparted to set mousepoints.

But I'm sure there are better ways.

---

### Post by detroit/zero on 2008-08-18
Actually, I didn't see anything in gparted that would help. It gave me error messages saying that the device was unreadable.

At any rate, I figured it had to be simple. I did a sudo mkdir /media/SQ40286V02, and then sudo mount /dev/sda2 /media/SQ4286V02.

The drive mounted and I was able to delete the command in the properties dialog.

---

### Post by prshah on 2008-08-18
> **detroit/zero said:**
> 
So I set the mount point to /media/Vista,

This is a very common error, made by most users; the mount point you specify should not include "/media/", it should be just the name of the directory you want it to mount to.

---

