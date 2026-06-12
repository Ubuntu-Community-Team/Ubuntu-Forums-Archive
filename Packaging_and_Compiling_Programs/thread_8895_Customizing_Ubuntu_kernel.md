---
title: "Customizing Ubuntu kernel"
date: 2004-12-22
forum: Packaging and Compiling Programs
---

### Post by S3rGy0 on 2004-12-22
Hi, i'm trying to install kernel 2.6.9 to customize my new Ubuntu. I configure it with the same options that i configured my Debian Woody (without any problem), but when i restart my computer and it starts booting, it shows the message: "Booting the kernel" and it doesn't load anything else.

I've installed grub in the mbr and the options to load with this are:

title         "Ubuntu kernel 2.6.9"
root        (hd1,2) #Hard disk 2, partition 3
kernel     /boot/vmlinuz-2.6.9

I don't know if with Ubuntu i have to do something special to load correctly a new kernel. When i load with ubuntu kernel, after it appears "Booting the kernel", it show: "Starting Ubuntu...", for this reason i think that i would have to do something else.  Can someone tell me what do i have to do??

Sergio.

---

### Post by cacofonix on 2004-12-22
Have you tried putting in the equal sign? Im not sure if they are needed but to me it looks like you need them.

```

title= "Ubuntu kernel 2.6.9"
root= (hd1,2) #Hard disk 2, partition 3
kernel= /boot/vmlinuz-2.6.9

```


If that doesn't work you might need an initrd image you can find out by typing this:
```

$>grep -sq initrd /etc/grub.conf && echo "Ram disk needed"
#make initrd image
$>sudo mkinitrd /boot/initrd-2.6.9 
``` 

Im not sure if the command to make an initrd image is right if anyone know the right command please correct :D

cheers
cacofonix

---

### Post by S3rGy0 on 2004-12-22
I don't find /etc/grub.conf in my system so i've made initrd with this command:

(as root): mkinitrd -o /boot/initrd-2.6.9 2.6.9

Then, i put initrd in the menu.lst file. i restarted, but the same problem.

I suposse this isn't the problem.

Thansk for help.

Sergio.

---

### Post by cacofonix on 2004-12-22
Did you try putting in the equal signs?

---

### Post by S3rGy0 on 2004-12-23
No, because the other entry in menu.lst (this entry works) don't have equals sign but works. I don't think this is the problem.

Thanks.

Sergio.

---

### Post by Xpop on 2005-01-03
Have u found out what the problem was? .. cause im having the same problem :???:

---

### Post by Danilo on 2005-01-10
Just a wild guess: try adding "root=/dev/hdb3" (with hdb3 being your root partition) to "kernel" command line.

For instance, I've added this entry since my root partition is on first partition of first/primary channel hard drive on second IDE interface ;-)

title           Ubuntu, kernel 2.6.7 proba 
root            (hd0,0)
kernel          /boot/proba-2.6.7 root=/dev/hdc1 ro quiet splash

---

