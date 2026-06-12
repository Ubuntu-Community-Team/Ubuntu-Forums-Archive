---
title: "Custom kernel errors..."
date: 2008-01-20
forum: Packaging and Compiling Programs
---

### Post by Xavieran on 2008-01-20
I have compiled a custom kernel following a tutorial on the BitBender forums...there is nothing wrong with my compilation options GRUB boots to the kernel fine...
but I get this ```
not syncing : no cpio magic
```

And then the system stops loading...

I have figured out (thankyou google:D) that this has something to do with my initrd.img which I made with mkinitrd ...

Any ideas what went wrong?

---

### Post by stroyan on 2008-01-20
I would use update-initramfs rather than mkinitrd to regenerate an initrd image.
But for building and installing a custom kernel you can use the debian tools to create a .deb package that will generate a good initrd as part of the postinst scripts run when installing the package with "dpkg -i".
There is a how-to on the subject at
[https://help.ubuntu.com/community/Kernel/Compile](https://help.ubuntu.com/community/Kernel/Compile)

---

### Post by Xavieran on 2008-01-21
For the time being I am simply using one of ubuntu's stock initrd.img's along with my custom kernel...it gives me a few warning messages at bootup but works brilliantly...thanks for the link too,though it seems to be a bit negative about using anything but the ubuntu stock kernel...;)

---

