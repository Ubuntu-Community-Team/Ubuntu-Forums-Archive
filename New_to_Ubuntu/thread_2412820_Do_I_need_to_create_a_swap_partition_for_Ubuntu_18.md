---
title: "Do I need to create a swap partition for Ubuntu 18.04 minimal(mini.iso) ?"
date: 2019-02-17
forum: New to Ubuntu
---

### Post by automate-stuff on 2019-02-17
I am installing Ubuntu 18.04 minimal( [https://help.ubuntu.com/community/Installation/MinimalCD](https://help.ubuntu.com/community/Installation/MinimalCD) )


If I do not create a swap partition during installation, Will a swap file be created by default ?

---

### Post by automate-stuff on 2019-02-17
Should I create a swap partition if I want to hibernate ?

---

### Post by Dennis N on 2019-02-17
Swap files are used in 18.04 by default IF there is no swap partition already on the disk when you install. Both have the same purpose.

---

### Post by automate-stuff on 2019-02-17
but by default, the swap file is 2 GB and If I want to hibernate I am going to need 6GB of swap space ... Should I just create a swap partition ? that way I can easily specify the size.


Another question, Should I create the swap as primary or logical partition ?

---

### Post by Dennis N on 2019-02-17
If you are concerned, then set up a swap partition of the desired size. Better safe than sorry. My current system has a swap partition used by 18.04, since it also has older 16.04 installed which needed swap partition when installed. It's a multiboot system.

Another thought: Several OS on the disk can share one swap partition. But I don't think they can share one swap file!

---

### Post by Dennis N on 2019-02-17
> Should I create the swap as primary or logical partition ? 

Sorry, missed this part.

You should be using GPT partition table on the disk. There are no logical partitions - all partitions are the same kind. 
If you used MSDOS, I believe it can be either primary or logical. Whatever the selector in the installer allows. I haven't used MSDOS partitions when installing for years so my recollection is a bit hazy.

---

### Post by oldfred on 2019-02-17
All systems since Windows 8 released in 2012 are UEFI.
But the mini installer does not support UEFI. If you want UEFI, you can install the server version, but not select to install any software. About only difference is the few extra drivers.

[https://help.ubuntu.com/community/Installation/MinimalCD#mini_system_in_UEFI_mode](https://help.ubuntu.com/community/Installation/MinimalCD#mini_system_in_UEFI_mode)

---

