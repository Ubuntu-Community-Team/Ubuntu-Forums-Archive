---
title: "Help needed on USB driver modification"
date: 2008-10-29
forum: Programming Talk
---

### Post by gskr on 2008-10-29
I have the source for Ubuntu. I am thinking of modifying the usb device driver to support an added functionality. I basically wanted to en/decrypt the data written to the USB disk. I want to know if I can do this by modifying the ubuntu kernel source. If so which file should I modify. I am planning to do this in C++ and I am new to linux. I would be grateful to get any help on device drivers programming.

---

### Post by LaRoza on 2008-10-29
> **gskr said:**
> I have the source for Ubuntu. I am thinking of modifying the usb device driver to support an added functionality. I basically wanted to en/decrypt the data written to the USB disk. I want to know if I can do this by modifying the ubuntu kernel source. If so which file should I modify. I am planning to do this in C++ and I am new to linux. I would be grateful to get any help on device drivers programming.
A few issues ;)

This isn't the job for the driver first of all. Second, the kernel is written in C, not C++. Third, isn't this a bit ambitious?

---

### Post by gskr on 2008-10-29
Yeah. I thought of modifying the existing driver code(the method) that sends the data for read/write and override its functionality by introducing the en/decryption engine here. But I am not sure where that happens. Also I heard that there is a lot of C++ source available for USB drivers but I could not find any. I wand to know if it is possible and can I venture on it further.

---

### Post by PmDematagoda on 2008-10-29
> **gskr said:**
> Yeah. I thought of modifying the existing driver code(the method) that sends the data for read/write and override its functionality by introducing the en/decryption engine here. But I am not sure where that happens. Also I heard that there is a lot of C++ source available for USB drivers but I could not find any. I wand to know if it is possible and can I venture on it further.

If you want to do this the proper way(if any), and also want it to be accepted, then the best place to do this would be at the Linux Kernel Mailing Lists, which can be joined by following the instructions found [here]("http://www.tux.org/lkml/").

But on the topic, I am with LaRoza, you may want to use a user-space application to do the encryption since the driver would be the wrong place for stuff like on-the-fly encryption and decryption. And forgive me if I'm wrong, but isn't TrueCrypt something like what you are trying to achieve here?

---

### Post by jespdj on 2008-10-29
The new Ubuntu 8.10 which is released tomorrow contains a new feature: you can create an [encrypted private directory](http://tombuntu.com/index.php/2008/09/23/encrypted-private-directory-in-ubuntu-810/).

It uses [ecryptfs](http://ecryptfs.sourceforge.net/) to do this. Probably you can set it up to do this on an USB stick instead of in a private directory on your harddisk.

Before starting hacking on the USB driver, you should learn more about the architecture of the Linux kernel and the different kinds of drivers that it contains. Encryption and decryption is most likely not something that you should add to the USB driver, but to a file system driver - and that's exactly what ecryptfs is already doing.

---

