---
title: "Purple Screen of death, framed in black"
date: 2012-07-15
forum: New to Ubuntu
---

### Post by Draexo on 2012-07-15
I am dual-boot Windows 7 64 bit and Ubuntu, 64 bit.  I am only able to successfully boot into Ubuntu about half the time.  The other half, I select Ubuntu, and select the normal mode and I get a purple screen framed in black that lasts for hours.  When I then hit CTRL-ALT-DEL, sometimes the computer reboots and I get into Ubuntu successfully, and other times, the login screen suddenly appears.

---

### Post by techvish81 on 2012-07-15
provide details about your installation. ( how you installed)

---

### Post by Draexo on 2012-07-15
> **techvish81 said:**
> provide details about your installation. ( how you installed)
I burned the 64 bit Ubuntu ISO in Windows 7 and ran Wubi.exe.  It then installed as a dual-boot, with Ubuntu as secondary option.
When I selected Ubuntu from the boot menu, I am presented with a SECOND boot menu, that appears to be an Ubuntu boot menu as it is in purple and I can either pick Linux kernal (normal) or Linux kernal (recovery).  If I do not select something it defaults to the normal build.  Sometimes this works, and sometimes it does not - as I presented in my first post.

---

### Post by techvish81 on 2012-07-15
> **Draexo said:**
> I burned the 64 bit Ubuntu ISO in Windows 7 and ran Wubi.exe.  It then installed as a dual-boot, with Ubuntu as secondary option.
When I selected Ubuntu from the boot menu, I am presented with a SECOND boot menu, that appears to be an Ubuntu boot menu as it is in purple and I can either pick Linux kernal (normal) or Linux kernal (recovery).  If I do not select something it defaults to the normal build.  Sometimes this works, and sometimes it does not - as I presented in my first post.

you can go to the "wubi mega thread" for wubi related problems,  which is in the general help section.  wubi can sometimes be very problematic. i would advise you to install it as real dual boot ( install it on your hdd as a separate operating system. you can easily dual boot without hassles, ) wubi install of ubuntu is dependent on windows, so if there is a problem in your windows,  wubi will not work as expected.

---

### Post by Draexo on 2012-07-16
> **techvish81 said:**
> you can go to the "wubi mega thread" for wubi related problems,  which is in the general help section.  wubi can sometimes be very problematic. i would advise you to install it as real dual boot ( install it on your hdd as a separate operating system. you can easily dual boot without hassles, ) wubi install of ubuntu is dependent on windows, so if there is a problem in your windows,  wubi will not work as expected.

I thought what I did was a real install, even though I used Wubi.  There is another install method without using Wubi?  It seems like a real install to me.  I get the Windows boot screen and then a Ubuntu boot screen (where I must pick between normal and recovery).

---

### Post by techvish81 on 2012-07-16
in wubi install, ubuntu is installed just as an application inside windows, it remains only inside a folder. by real install i meant installing it on a separate partition.  you can do that by booting from the cd and following the default install process. it will allow you to keep windows 7 and ubuntu as dual boot.

---

### Post by Draexo on 2012-07-17
> **techvish81 said:**
> in wubi install, ubuntu is installed just as an application inside windows, it remains only inside a folder. by real install i meant installing it on a separate partition.  you can do that by booting from the cd and following the default install process. it will allow you to keep windows 7 and ubuntu as dual boot.

I see now!
Thanks.
I will uninstall what I have an just let the DVD do its thing.  It sure looks like a real install to me.
I see how the DVD install is a bit different...

---

### Post by Draexo on 2012-07-19
> **techvish81 said:**
> in wubi install, ubuntu is installed just as an application inside windows, it remains only inside a folder. by real install i meant installing it on a separate partition.  you can do that by booting from the cd and following the default install process. it will allow you to keep windows 7 and ubuntu as dual boot.

I have tried this many times and the Ubuntu CD makes a new partition and seems to copy files to it and then when I reboot there is no dual boot option.  I just go directly into Windows.

---

### Post by techvish81 on 2012-07-19
press and hold right "shift "  while booting and see if grub options come or not.

---

