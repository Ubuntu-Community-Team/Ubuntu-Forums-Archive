---
title: "GRUB Error 15"
date: 2008-05-04
forum: New to Ubuntu
---

### Post by dorsetmark on 2008-05-04
Hi there,

Apologies firstly if I have posted this in the wrong forum.

I have an old Dell Optiplex GX150 that has no CD drive.
It originally had Windows 2000. I installed Ubuntu 7.10 on a partition and everything worked OK until I started fiddling about with it.

Today, I inserted the hard drive into another PC as the Primary IDE slave, deleted everything from the drive and installed Ubuntu 8.04 on it, hoping I could put the hard drive back into the GX150 and everything would be OK.

Of course (presumably and guestimating!) GRUB or the MBR cannot find Ubuntu on the hard drive. I've got a GRUB startup floppy but just cannot get everything configured OK.

I'd but gratefully of any help and advice,

Regards,
Mark (who always ignores the phrase "If it ain't broke, don't fix it!)

---

### Post by njparton on 2008-05-06
That's not a good idea as your other PC will likely have lots of different hardware such as motherboard, CPU etc etc?

---

### Post by mlentink on 2008-05-06
> **njparton said:**
> That's not a good idea as your other PC will likely have lots of different hardware such as motherboard, CPU etc etc?

I agree. And also, and that's what's causing your GRUB error 15, you installed it on a secondary drive, which GRUB obviously doesn't find on your Dell...
You could edit your GRUB to have Ubuntu boot from hd0, but I doubt if that will do you much good. In view of all the different hardware, I wouldn't be surprised if you ended up in cli...

---

### Post by bumanie on 2008-05-06
Boot with the live cd and in terminal > sudo fdisk -l and post the output (if any). Hardware issues are quite likely going to be a problem as you are already aware, but you may be able do something by editing /boot/grub/menu.lst and /etc/fstab and not use uuid's in fstab - not very confident that things will work though.

---

### Post by dorsetmark on 2008-05-25
Thanks for your advice.
I've bought a CD drive for the machine now and have re-installed ubuntu.
It works like a dream now.

---

