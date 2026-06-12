---
title: "Make floppy disk grub/bootloader"
date: 2011-11-22
forum: New to Ubuntu
---

### Post by Septuagenarian on 2011-11-22
The CD drive on my old laptop has failed and it wont boot from USB , so I was wondering if it is possible to make a boot disk floppy for emergencies. Am using Ubuntu 11.10 . Is it possible to use a DD command?

---

### Post by plucky on 2011-11-22
> **Septuagenarian said:**
> The CD drive on my old laptop has failed and it wont boot from USB , so I was wondering if it is possible to make a boot disk floppy for emergencies. Am using Ubuntu 11.10 . Is it possible to use a DD command?

Go [Here](http://www.mediafire.com/?bfst8cygs4tbc6t) and download super_grub_disk_hybrid-1.98s1.iso and use the command

 ```
sudo dd if=super_grub_disk_hybrid-1.98s1.iso of=/dev/fd0
```

Does your laptop have a floppy?

---

### Post by Septuagenarian on 2011-11-23
Many thanks plucky , I will give this a try . Yes my old laptop has a floppy drive , but only usb 1 ports , I may have to raid my piggy bank and get a new one ! Thanks again.

---

### Post by Septuagenarian on 2011-11-23
Hi , I tried this then booted from the FDD and got "welcome to grub" then error "invalid arch" , then "grub rescue" Now for some reason my floppy drive has become read only. Apart from this everything seems to work , so I think I will just use it till it breaks and if the grub gets corrupted or it becomes unbootable I will get another . Thanks again,

---

