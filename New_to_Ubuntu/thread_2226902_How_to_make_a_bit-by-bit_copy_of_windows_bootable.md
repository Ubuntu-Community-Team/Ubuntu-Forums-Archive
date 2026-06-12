---
title: "How to make a bit-by-bit copy of windows bootable?"
date: 2014-05-29
forum: New to Ubuntu
---

### Post by peysun1 on 2014-05-29
Hi,

I made a copy of my old windows system, bit-by-bit using dd, and then I copied the file (again bit by bit using dd) to a new parition in my hard drive. I later made (as far as I can say) appropriate changes to the file /etc/fstab by adding the UUID of the new parition. Now my old windows appears in nautilus as a device, but it is not bootable. Is there any way to make it bootable?

Thanks

PS: I followed the instruction in [https://help.ubuntu.com/community/DriveImaging](https://help.ubuntu.com/community/DriveImaging). I however couldn't manage to find the file /boot/grub/menu.lst.

---

### Post by LastDino on 2014-05-29
I think it is not getting booted because there is no MBR/Windows boot loader as you only copied installed drive. You can try os probing and then upgrading grub, but I'm not entirly sure if it will work or not. So, I'll wait for someone else to see what can be done.

Anyway, I'm posting to tell you that; that link is giving 404 error, saying it has been removed.

---

### Post by sudodus on 2014-05-29
You can clone your whole drive, not only a partition, from the source drive to a target drive of the same size or bigger. This is possible to do with ***dd***, but risky. It is safer and more efficient to use ***Clonezilla***. Get an iso file to create a CD/DVD/USB boot drive from

[http://clonezilla.org/](http://clonezilla.org/)

I know, because I have done it many times.

---

### Post by peysun1 on 2014-05-29
@LastDino: True, I edited the link.

---

### Post by sudodus on 2014-05-29
This command line is old (relevant for old systems)

```
dd if=/dev/hda of=/dev/hdx conv=noerror,sync bs=1024
```

Today the corresponding command line (in Ubuntu) is

```
dd if=/dev/sda of=/dev/sdx conv=noerror,sync bs=4096
```

I put **x** for the output drive letter to avoid unwanted surprises from the 'disk destroyer'. dd is a very powerful tool, but also very risky and slow compared to Clonezilla.

If you want to use dd anyway, have ***no*** partition on the source and target drives mounted. Boot from a third drive (e.g. CD/DVD/USB drive). Double check and triple check that if and of and the drive letters are correct!

---

### Post by peysun1 on 2014-05-29
Thanks sudodus for the quick reply!

What I did for sure: I actually used bs=4096 (I stumbled upon a link which recommended it). I did boot from a third drive (USB drive), and "if" and "of" were definitely correct.
What I didn't do: I think I didn't use "conv=noerror" nor sync options. I had my source drive mounted, but it was an external drive and the link I mentioned above didn't require it to be unmounted.
As I said, I can see every single file of my old windows partition as a device, the problem is that it is not bootable.

---

### Post by sudodus on 2014-05-29
Well, it you be so simple that you must install the bootloader. Try according to this link

[https://help.ubuntu.com/community/Grub2/Installing#Fixing_a_Broken_System](https://help.ubuntu.com/community/Grub2/Installing#Fixing_a_Broken_System)

But it could be some other error too, which might be very hard to find. Then the best option is to do it again, this time cloning the whole drive, not only a partition. Doing so, you will also copy the bootloader, and everything will be be in the correct place.

By the way, it works for me without 'conv=noerror,sync', but I copied it from the wiki page you referred to.

-o-

There are easier ways to do it with linux, but you have Windows on the disk. Still, I would recommend Clonezilla, which understands the NTFS file system of Windows and can manage it in an efficient way without copying (only skipping) free space in the partitiions as well as unallocated space.

---

### Post by peysun1 on 2014-05-29
Thanks, I'll try to install the bootloader and see what happens.

All I have now is an old dual boot harddrive (and of course the dd of its windows partition, the PC itself is not functional any more). I have to check if I can use Clonezilla in this setting (or does it require a functional windows OS to work).

---

### Post by sudodus on 2014-05-29
You cannot expect Windows to work in another computer. You cannot expect Windows to work from USB. Windows is made so that it should be hard to move it (to make it harder to run without paying a licence fee for every computer). But you can mount the Windows partition from linux to read and copy the files (documents, pictures, video clips, music etc).

---

