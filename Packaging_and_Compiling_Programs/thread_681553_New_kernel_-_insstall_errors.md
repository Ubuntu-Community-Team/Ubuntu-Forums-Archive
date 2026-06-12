---
title: "New kernel - insstall errors"
date: 2008-01-29
forum: Packaging and Compiling Programs
---

### Post by linuxonbute on 2008-01-29
Sorry if this is the wrong forum for this, just not sure which is the right one.

I have Gutsy kernel 2.6.22-14-generic on my Zepto laptop.

The touchpad is an elantech touchpad but is not recognized so i am using a usb mouse which is fine.

There is a driver for this pad in development and i am trying to help in testing it out.

I have been using the instructions here :
[http://www.howtoforge.com/kernel_compilation_ubuntu](http://www.howtoforge.com/kernel_compilation_ubuntu)

First with version 2 of the patch and now with version 3.

Everything goes well until the stage where I follow this part:

```

dpkg -i linux-image-2.6.18.1-custom_2.6.18.1-custom-10.00.Custom_i386.deb

```

when I get this error:
```


Setting up linux-image-2.6.24-custom (2.6.24-custom-10.00.Custom) ...
Running depmod.
Finding valid ramdisk creators.
Using mkinitramfs-kpkg to build the ramdisk.
find: /lib/firmware/2.6.24-custom: No such file or directory
find: /lib/firmware/2.6.24-custom: No such file or directory
find: /lib/firmware/2.6.24-custom: No such file or directory
find: /lib/firmware/2.6.24-custom: No such file or directory
find: /lib/firmware/2.6.24-custom: No such file or directory
find: /lib/firmware/2.6.24-custom: No such file or directory

```

This is the case with builds from 2.6.22,  2.6.22.14, 2.6.24
so I find that my wireless card is unusable as it's module iwlwifi_mac80211 not available.

What am I doing wrong?
Is there a Ubuntu modified kernel i need to patch so I can get both wireless and touchpad?

---

### Post by linuxonbute on 2008-01-29
> **linuxonbute said:**
> Sorry if this is the wrong forum for this, just not sure which is the right one.

I have Gutsy kernel 2.6.22-14-generic on my Zepto laptop.

The touchpad is an elantech touchpad but is not recognized so i am using a usb mouse which is fine.

There is a driver for this pad in development and i am trying to help in testing it out.

I have been using the instructions here :
[http://www.howtoforge.com/kernel_compilation_ubuntu](http://www.howtoforge.com/kernel_compilation_ubuntu)

First with version 2 of the patch and now with version 3.

Everything goes well until the stage where I follow this part:

```

dpkg -i linux-image-2.6.18.1-custom_2.6.18.1-custom-10.00.Custom_i386.deb

```

when I get this error:
```


Setting up linux-image-2.6.24-custom (2.6.24-custom-10.00.Custom) ...
Running depmod.
Finding valid ramdisk creators.
Using mkinitramfs-kpkg to build the ramdisk.
find: /lib/firmware/2.6.24-custom: No such file or directory
find: /lib/firmware/2.6.24-custom: No such file or directory
find: /lib/firmware/2.6.24-custom: No such file or directory
find: /lib/firmware/2.6.24-custom: No such file or directory
find: /lib/firmware/2.6.24-custom: No such file or directory
find: /lib/firmware/2.6.24-custom: No such file or directory

```

This is the case with builds from 2.6.22,  2.6.22.14, 2.6.24
so I find that my wireless card is unusable as it's module iwlwifi_mac80211 not available.

What am I doing wrong?
Is there a Ubuntu modified kernel i need to patch so I can get both wireless and touchpad?

Can anyone tell me how or where I can download the kernel source for 
kernel 2.6.22-14-generic which is the one installed with Gutsy please?

---

### Post by JamesUser on 2008-02-02
Just in case, you havent managed to find it so far...

[http://www.us.kernel.org/pub/linux/kernel/v2.6/]("http://www.us.kernel.org/pub/linux/kernel/v2.6/")

Go halfway down the page for the version of your choice.

---

