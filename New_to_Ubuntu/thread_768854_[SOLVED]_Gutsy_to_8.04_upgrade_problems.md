---
title: "[SOLVED] Gutsy to 8.04 upgrade problems"
date: 2008-04-26
forum: New to Ubuntu
---

### Post by okey666 on 2008-04-26
My upgrade from 7.10 to 8.04 has been an absolute disaster. When the upgrade finished, the PC booted back up but on the boot screen it did nothing and the bar just kept bouncing back and forth. After reading some threads I tried the .22 kernel which booted but then went into low-graphics mode saying that it could not detect the card, I have had no problems before.

Any ideas?

My Specs:
graphics - NVidia 8600GT
ram - 2G dual channel
motherboard - Abit AB9 quad GT

Please help, I need the PC to work.

---

### Post by okey666 on 2008-04-26
Fixed, if you want to know how just post.

---

### Post by hackle577 on 2008-04-26
Please mark this thread as solved by using the "Thread tools" menu at the top and clicking "Mark as solved".

---

### Post by okey666 on 2008-04-27
ok

---

### Post by okey666 on 2008-04-27
Um... the button on the thread tools menu is not there. I have done this before but it has gone.

---

### Post by Siegfried on 2008-04-29
> **okey666 said:**
> Fixed, if you want to know how just post.
How did you fix this problem?

---

### Post by okey666 on 2008-04-29
Ok....

I have always had a problem with my PC booting Linux. It was self built so I do not know about compatibility. What used to happen is that it would only boot 1 out of about 5 to 8 attempts. I just put up with it as it had never been a problem.

On 8.04 however it never booted. I fixed it by accessing the grub menu before boot, then selecting Ubuntu 8.04 (the kernel that ends in 26) and pressing e (edit). On the second option down press e again and add to the end of the line:
```
all_generic_ide
```
After editing this press enter and b to boot.

In Ubuntu you must then edit the Grub configuration file to make the changes perminant. Run the command:
```
sudo gedit /boot/grub/menu.lst
```
The text editor will appear. Scroll down until you find something that looks like:
> 
## ## End Default Options ##

title		Ubuntu 8.04, kernel 2.6.24-16-generic
root		(hd0,3)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=1d805b81-129f-4920-a8f7-595dd7b2e161 ro quiet splash vga=792 all_generic_ide
initrd		/boot/initrd.img-2.6.24-16-generic
quiet


This is my edited file. At the end of the line where it says kernel again write:
```
all_generic_ide
```
You can see it on my code. Then save the file.

I hope this fixes your problem.:)

---

