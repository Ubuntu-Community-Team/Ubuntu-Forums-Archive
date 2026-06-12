---
title: "Knopperdisk On usb"
date: 2008-05-19
forum: Other OS Talk
---

### Post by reyhan on 2008-05-19
i want to use knopperdisk on usb 
but i confused to convert the syslinux.cfg to grub menu.lst
this is the syslinux.cfg
> default knopperdisk

timeout 100
prompt 1

display boot.msg

label knopperdisk
   kernel kernel
   append initrd=initrd:confused::confused:

---

### Post by meierfra. on 2008-05-19
Try this

title knopperdisk
root (hd1,0)
kernel /kernel
initrd /initrd

Of  course you need to adjust (hd1,0) according to the location of your knopperdisk partion.

---

