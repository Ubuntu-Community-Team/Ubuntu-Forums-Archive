---
title: "Duplicate items in grub"
date: 2008-07-06
forum: New to Ubuntu
---

### Post by quraid on 2008-07-06
Greetings
after some brutal tinkering i just caused another problem.

when i boot up i get duplicate entries in my grub (the linux boot manager is called grub, right?).
ie.

switch on, boot>>
----------------
[Windows boot manager]
Windows Vista
Ubuntu
[select Ubuntu]
----------------
>>Ubuntu Generic
>>Ubuntu safe mode
>>ubuntu memtest mode
>>Ubuntu Generic
>>Ubuntu safe mode
>>ubuntu memtest mode


i hope that gives the idea. the problem started when i disapproving of the grub bootup manger's ploy to be the default boot manager, instead recreated vista's master boot record. then i lost ubuntu's link in the windows bootloader. so i had to use a 3rd party app in windows to create a customized windows boot loader which had a link to grub. now in grub every option is repeated twice.

regards.

---

### Post by bapoumba on 2008-07-06
Please post the output to:
```
cat /boot/grub/menu.lst
```
You may just have several kernels. Are different numbers showing up somewhere ?

---

### Post by quraid on 2008-07-06
yep they are different kernels as you implied.
i have 24.19, 24.18 and 24.16 in the boot menu.
can i remove the 24.16 kernel altogether? will that save me some space or is it not worth it?

```
title		Ubuntu 8.04, kernel 2.6.24-19-generic
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=1c180a3b-0138-415b-997d-1883dd1df158 ro quiet splash
initrd		/boot/initrd.img-2.6.24-19-generic
quiet

title		Ubuntu 8.04, kernel 2.6.24-19-generic (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=1c180a3b-0138-415b-997d-1883dd1df158 ro single
initrd		/boot/initrd.img-2.6.24-19-generic

title		Ubuntu 8.04, kernel 2.6.24-18-generic
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.24-18-generic root=UUID=1c180a3b-0138-415b-997d-1883dd1df158 ro quiet splash
initrd		/boot/initrd.img-2.6.24-18-generic
quiet

title		Ubuntu 8.04, kernel 2.6.24-18-generic (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.24-18-generic root=UUID=1c180a3b-0138-415b-997d-1883dd1df158 ro single
initrd		/boot/initrd.img-2.6.24-18-generic

title		Ubuntu 8.04, kernel 2.6.24-16-generic
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=1c180a3b-0138-415b-997d-1883dd1df158 ro quiet splash
initrd		/boot/initrd.img-2.6.24-16-generic
quiet

title		Ubuntu 8.04, kernel 2.6.24-16-generic (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=1c180a3b-0138-415b-997d-1883dd1df158 ro single
initrd		/boot/initrd.img-2.6.24-16-generic

title		Ubuntu 8.04, memtest86+
root		(hd0,1)
kernel		/boot/memtest86+.bin
quiet


```

---

### Post by bapoumba on 2008-07-06
If .19 and .18 are working fine, you can safely remove .16 from synaptic. Search for the actual version number, 2.6.24-16 and remove the package, grub menu will be automagically edited, that's debian magic ;)

I usually keep the previous working kernel, just in case some unfortunate upgrade happens and a major bug comes in. Then you can always boot on the previous kernel. This situation is unlikely now, but has happened in the past, and many people were in serious trouble.

---

### Post by drs305 on 2008-07-06
Each time a new kernel is added/installed the grub menu includes it by default. There are various ways of hiding these extra kernels (or using them). The old way was to edit the grub menu.lst, but since Gutsy there has been a much safer and perhaps easier method - using StartUp-Manager. 

You can select which kernel to use (and set a default action for future updates), how many kernels to display and for how long, what colors to use, etc.

To install StartUp-Manager:
```
sudo apt-get install startupmanager
```

To run: System, Adminsitration, StartUp-Manager

I've written a tutorial about some of StartUp-Manager's options:
[HOWTO: Grub Menu Kernel Display Options & StartUp-Manager]("http://ubuntuforums.org/showthread.php?t=818177")

---

### Post by quraid on 2008-07-06
thanks guys. you have been very helpful.

---

### Post by bumanie on 2008-07-06
The extra entries are updated kernel entries. Unless space is critical, they do no harm and can come in handy if there is a kernel update that doesn't work well with your particular setup ie you can boot with one of the older kernels that you know works. If you want to reduce the list, > gksudo gedit /boot/grub/menu.lst and go down the list of kernels and put a # in front of the kernels you don't want appearing in the list. This does not remove them, only stops them from being listed on the screen.

---

### Post by bapoumba on 2008-07-06
> **bumanie said:**
> The extra entries are updated kernel entries. Unless space is critical, they do no harm and can come in handy if there is a kernel update that doesn't work well with your particular setup ie you can boot with one of the older kernels that you know works. If you want to reduce the list,  and go down the list of kernels and put a # in front of the kernels you don't want appearing in the list. This does not remove them, only stops them from being listed on the screen.
That is correct, but when a new kernel will be available, the menu.lst will be automagically rewritten. Then you'll have to do it all over again, all the installed kernel packages will have an entry.

---

### Post by kathryn on 2009-02-18
I'm glad I found this thread before posting about this myself.  I was alerted  to the presence of duplicate items (with different kernel numbers) in the menu.lst file when, following installation of many Ubuntu updates, my system started booting to the memtest by default.

Thank you drs305 for suggesting the Startup-Manager.  (You can also install the Startup-Manager via the Synaptic Package Manager, in System > Admin.)

---

