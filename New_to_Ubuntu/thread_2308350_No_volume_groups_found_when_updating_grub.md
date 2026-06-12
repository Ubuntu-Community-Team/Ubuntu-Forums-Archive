---
title: "No volume groups found when updating grub"
date: 2016-01-02
forum: New to Ubuntu
---

### Post by noname9 on 2016-01-02
Hello! I am totally new to ubuntu. When I run 
```
sudo update-grub 
``` 
it says
```

Found linux image: /boot/vmlinuz-3.19.0-32-generic
Found initrd image: /boot/initrd.img-3.19.0-32-generic
  No volume groups found
done

``` 
Thanks for your attention.

---

### Post by grahammechanical on 2016-01-02
It should also find this

> Found memtest86+ image: /boot/memtest86+.elf
Found memtest86+ image: /boot/memtest86+.bin


Unless you have edited certain Grub configuration files. Do you have LVM? I do not. So I cannot say if "No volume groups found" is a message to worry about. It is not appearing on my system which is running the latest version of Grub as it is Ubuntu Xenial Xerus (16.10). These are the important questions:

Is update-grub detecting all the operating systems on the computer? Is the Grub boot menu presenting options to load all the OS present on the machine? Does each OS load when selected?

Regards.

---

### Post by noname9 on 2016-01-03
It didn't give me such output. How to check that I have LVM? I thing that it is problem because I can not update grub. I have only one OS - Mint 17.3. Thank you!

---

