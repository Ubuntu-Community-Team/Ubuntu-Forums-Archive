---
title: "Why Do I have 4 versions of Ubuntu In Grub ?????"
date: 2008-07-14
forum: New to Ubuntu
---

### Post by YoB1U1N1T1U on 2008-07-14
Pretty mad here: For some reason I have 4 ubuntu options in Grub ! When I first installed ubuntu to my machine 12 hours ago. It only had 2 Ubuntu boot options, now it has 4!  2 are the same.

how do I get rid of this annoyance?!


Grub Menu.lst
```
## ## End Default Options ##

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=e67a942c-323f-479a-b7b6-a2574eb92884 ro quiet splash
initrd		/boot/initrd.img-2.6.24-19-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic (recovery mode)
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=e67a942c-323f-479a-b7b6-a2574eb92884 ro single
initrd		/boot/initrd.img-2.6.24-19-generic

title		Ubuntu 8.04.1, kernel 2.6.24-16-generic
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=e67a942c-323f-479a-b7b6-a2574eb92884 ro quiet splash
initrd		/boot/initrd.img-2.6.24-16-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-16-generic (recovery mode)
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=e67a942c-323f-479a-b7b6-a2574eb92884 ro single
initrd		/boot/initrd.img-2.6.24-16-generic

title		Ubuntu 8.04.1, memtest86+
root		(hd0,4)
kernel		/boot/memtest86+.bin
quiet

```


thanks!

---

### Post by Inxsible on 2008-07-14
When a new kernel is installed, it automatically gets an entry in the grub.

You can either :
1) Remove the older kernel from synaptic - which will also remove its entry from grub
2) Comment out the entries in grub manually

I find that its better to keep the new kernel PLUS 1 older working kernel just in case the new kernel has some issues with your hardware. I always remove anything older than 1 previous version from synaptic.

BTW...there aren't 4 versions of Ubuntu...same version but two kernels installed. If you see you need to have the normal login and a recovery login in case something goes wrong. So technically each kernel has 2 entries

---

### Post by brokenLockpick on 2008-07-14
I can't see a single character that is different, you can most likely safely delete the duplicates. Perhaps a more expirenced user should verify this, but from my understanding of what that file means to the system deleting the duplicates should work.

Edit I just noticed the kernel difference ignore my suggestion

---

### Post by Canis familiaris on 2008-07-14
Two of the enteries run the current version of kernel in your system. Out of this one is a recovery mode which is a sort of safe mode for Ubuntu.
The other two run the last working kernel in your system. It is used when the latest kernel has bugs and you are unable to use your computer It also has a recovery mode of it own.

---

### Post by overdrank on 2008-07-14
> **YoB1U1N1T1U said:**
> Pretty mad here: For some reason I have 4 ubuntu options in Grub ! When I first installed ubuntu to my machine 12 hours ago. It only had 2 Ubuntu boot options, now it has 4!  2 are the same.

how do I get rid of this annoyance?!


Grub Menu.lst
```
## ## End Default Options ##

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=e67a942c-323f-479a-b7b6-a2574eb92884 ro quiet splash
initrd		/boot/initrd.img-2.6.24-19-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic (recovery mode)
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=e67a942c-323f-479a-b7b6-a2574eb92884 ro single
initrd		/boot/initrd.img-2.6.24-19-generic

title		Ubuntu 8.04.1, kernel 2.6.24-16-generic
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=e67a942c-323f-479a-b7b6-a2574eb92884 ro quiet splash
initrd		/boot/initrd.img-2.6.24-16-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-16-generic (recovery mode)
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=e67a942c-323f-479a-b7b6-a2574eb92884 ro single
initrd		/boot/initrd.img-2.6.24-16-generic

title		Ubuntu 8.04.1, memtest86+
root		(hd0,4)
kernel		/boot/memtest86+.bin
quiet

```


thanks!

Hi and as you can see you have had a kernel update. This also helps as if the kernel update does not work well on your system you can still boot to a older kernel and rescue your system. If you do not want to see them at the grub then you can reduce the time for delay to like 3 or less and also place a # comment in front of the title to hide them. _But look at _the above reasons for not doing so.
Edit I type to slow :)

---

### Post by YaroMan86 on 2008-07-14
> **brokenLockpick said:**
> I can't see a single character that is different, you can most likely safely delete the duplicates. Perhaps a more expirenced user should verify this, but from my understanding of what that file means to the system deleting the duplicates should work.

Edit I just noticed the kernel difference ignore my suggestion

It is done this way mostly as a precaution. In case a kernel update goes south you can still revert to an older kernel and use Ubuntu. I usually comment these out as opposed to removing them, just in case.

---

### Post by kansasnoob on 2008-07-14
Another option is to install StartUp-Manager:

[http://www.ubuntugeek.com/how-to-change-settings-for-the-bootloader-and-splash-screen-in-ubuntu.html](http://www.ubuntugeek.com/how-to-change-settings-for-the-bootloader-and-splash-screen-in-ubuntu.html)

---

### Post by mikewhatever on 2008-07-14
Simply editing GRUB would just remove the lines from the menu, but the old kernel would still be installed and sit there unused and inaccessible. You should remove the 2.6.24-16-generic kernel using synaptic, which should also take care of GRUB's menu. To find the kernel, search for linux-image.

---

### Post by AnLGP on 2008-07-14
What I would do is just hide grub and have it enabled when you need it.  It'll say "press esc to see the menu" or something similar.  It sets a countdown.

---

### Post by kpkeerthi on 2008-07-14
Search for **linux-image** in Synaptic Package Manager and mark the older kernels for complete removal. This will auto-update your GRUB menu.

---

### Post by mastergunner on 2008-07-18
subscribe same issue here.

---

