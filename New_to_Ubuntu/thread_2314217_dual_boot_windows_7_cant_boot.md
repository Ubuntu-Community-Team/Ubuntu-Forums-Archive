---
title: "dual boot windows 7 cant boot"
date: 2016-02-19
forum: New to Ubuntu
---

### Post by d9867eb on 2016-02-19
hello,
i dual booted my  windows 7 school computer with ubuntu a few day a ago. both windows and ubuntu worked well but today in the morning i couldnt boot windows. i updated some stuff yesterday, could it be that? also i did start ubuntu while windows was in sleeping mode but i have done that before and that worked.
thanks

---

### Post by grahammechanical on 2016-02-19
Some more information would be useful. Version of Ubuntu? Do you get a Grub boot menu? If so, is there an option to load Windows 7? What happens when you select the Windows 7 option? It would also be useful to know the partition layout. That sort of stuff. We need to see what you are seeing and we can only do that from a description that you give. 

If you can load Ubuntu then open a terminal and run this

```
sudo update-grub
```

Watch the printout. Does the printout record a Windows 7 boot loader in its list? Having Windows in sleep mode should not prevent the Linux boot loader from detecting Windows when we run that update-grub command.

Regards

---

### Post by d9867eb on 2016-02-19
i think i have 14 lts or something. 
here is update-grub:
Generating grub configuration file ...
Found linux image: /boot/vmlinuz-3.19.0-50-generic
Found initrd image: /boot/initrd.img-3.19.0-50-generic
Found linux image: /boot/vmlinuz-3.19.0-49-generic
Found initrd image: /boot/initrd.img-3.19.0-49-generic
Found memtest86+ image: /boot/memtest86+.elf
Found memtest86+ image: /boot/memtest86+.bin
Found Windows 7 (loader) on /dev/sda1
done
when i boot can select between ubuntu, memorytest64 and windows 7 loader and something more.
and thanks for your reply! :)

---

### Post by yancek on 2016-02-19
In your initial post you indicate that you "updated some stuff" yesterday.  What did you update and on which system did you do the update, windows or Ubuntu?  Also, you indicate that you couldn't boot windows but give no details.  What happens when you select the windows option from the boot menu?  The output in your last post clearly shows a windows entry detected.

---

