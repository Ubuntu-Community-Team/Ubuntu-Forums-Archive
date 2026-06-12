---
title: "Need help booting on ibm a31"
date: 2008-11-23
forum: New to Ubuntu
---

### Post by holybratwurst on 2008-11-23
I'm new to ubuntu and I installed ubuntu 8.10 onto an older IBM A31 from the alternative cd after trying with the desktop cd. I had to change the boot parameters by deleting 'quiet' and adding 'acpi=off' for it to work.  It seemed to install ok cause It told me that installation was complete and that it needed to reboot. however it will not finish booting now. I read on [https://help.ubuntu.com/community/BootParameters](https://help.ubuntu.com/community/BootParameters) that i need to to make permanent changes in the file /boot/grub/menu.lst after the installation has completed, however I do not know how to do this. I don't know if that is what is wrong or not.

---

### Post by spiderbatdad on 2008-11-23
get the grub menu by pressing esc, if necessary, during start up to see the grub menu. When you see a list of kernels, quickly press e, you only have several seconds...unless you move the arrow key. Anyway...pressing e puts you into an edit mode. You will now see a new screen with 'kernel' on the second line. Use the arrow key to move to that line. Press e again. Go to the end of the line and make your change. Hit enter and then b to boot.

This is only a one time change. Once your system boots. Open a terminal Applications>>Accessories>>Terminal
Run the command ```
gksu gedit /boot/grub/menu.lst
```scroll to the section:

```
## ## End Default Options ##

title		Ubuntu 8.10, kernel 2.6.27-7-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=XXXX ro **lapic hpet=force**
initrd		/boot/initrd.img-2.6.27-7-generic
quiet

``` make your changes where I have highlighted above, then save the file.

---

### Post by holybratwurst on 2008-11-23
Thanks so much spiderbatdad it worked.

---

### Post by holybratwurst on 2008-11-23
Now I got it to boot up but it keeps freezing a few minutes after I log on. Its always about the same amount of time from when I log on and it freezes. I've been doing differnt things each time so I don't think it is a program I am running.

---

### Post by ximhot on 2009-11-28
My A31 doesn't work under 9.10. The display is very very slow. I tried GNOME safe mode and it works, just no internet connection. I should have searched the internet before I upgrade. 

> **holybratwurst said:**
> Now I got it to boot up but it keeps freezing a few minutes after I log on. Its always about the same amount of time from when I log on and it freezes. I've been doing differnt things each time so I don't think it is a program I am running.

---

