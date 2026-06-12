---
title: "Retaining Ubuntu after installing Windows 8"
date: 2012-11-17
forum: New to Ubuntu
---

### Post by pras8421 on 2012-11-17
Hi, . . .

My friend wants to install windows 8 replacing windows 7, but he does't want his Ubuntu (grub loader) to be altered. What he just needs is all the packages installed inside it.

Can you suggest us a solution?

---

### Post by carl4926 on 2012-11-17
You will have to repair the Grub bootloader because windows will blugger it up.
Install win8 (it's rubbish IMO)

To repair grub
For that you need the Ubuntu CD you used to install Ubuntu.

Then it's:

> Boot the Ubuntu CD to the Live desktop
* Open a terminal and type

$ sudo fdisk -l

    * Now, you need to remember which device listed is your linux distribution, for reference, /dev/sda1 will be used. Now we need to mount the filesystem to /mnt

$ sudo mount /dev/sda1 /mnt

    * Now mount the rest of your devices

$ sudo mount --bind /dev /mnt/dev

    * Now chroot into your system

$ sudo chroot /mnt

    *

      When that is done you need to run update-grub to create the configuration file.

$ update-grub

    *

      To install GRUB 2 to the MBR, next you need to run grub-install /dev/sda

$ grub-install /dev/sda

And your done


---

### Post by pras8421 on 2012-11-18
Do you assure that no previous data and packages are lost?

---

### Post by carl4926 on 2012-11-18
> **pras8421 said:**
> Do you assure that no previous data and packages are lost?

The Linux data will be safe...
Assuming the windows 8 install is assigned to the correct partition.. Yes.

I do this stuff day in day out, it's a doddle

---

### Post by pras8421 on 2012-11-18
Thanks:)

---

### Post by 681ankit on 2012-11-18
That means ur windows is loading then try to fix it with windows ...Download and install BOOT US . exe ...It will guide you ..very easy way..

---

### Post by Mark Phelps on 2012-11-18
I'd recommend AGAINST installing Boot-US.  It's yet ANOTHER boot manager -- and given that it has not been updated since Feb 2012, it's VERY unlikely to work with Windows8.

---

