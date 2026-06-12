---
title: "Blurry text on boot after kernel recompile"
date: 2005-12-18
forum: Outdated Tutorials &amp; Tips
---

### Post by WhiteHorse on 2005-12-18
Hope this saves someone else some trouble:
After compiling a custom kernel, the boot screen is all blurry... but then after X loads all is back to normal. This is caused by adding framebuffer support into the kernel. Anyway, the fix is as follows: Tell Grub to use the framebuffer corectly. In my situation, I added the Nvidia framebuffer(nvidiafb), and I prefer 1024x768 resolution so I modified the file /boot/grub/menu.lst as follows:
title		Ubuntu, kernel 2.6.12-custom2 
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.12-custom2 root=/dev/hda2 ro quiet splash video=nvidiafb:mtrr,ywrap vga=0x318
initrd		/boot/initrd.img-2.6.12-custom2
savedefault
boot

All I did was append the following to the line which says "kernel":
video=nvidiafb:mtrr,ywrap vga=0x318

---

