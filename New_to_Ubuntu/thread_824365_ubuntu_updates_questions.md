---
title: "ubuntu updates questions"
date: 2008-06-10
forum: New to Ubuntu
---

### Post by alicelou85 on 2008-06-10
Hello, 
I have been constantly downloading updates for my ubuntu, and now I have 3 versions/kernels of it. I believe they are just slightly different from each other. However, every time when I start my computer, I will need to choose the one I want to boot my computer from out of the 3 ubuntu versions, plus the recovery version and windows longhorn. I wonder if there is any way to hide/delete the older versions from that list. 
Thank you. 
Alice

---

### Post by wannadumpwindows on 2008-06-10
When you boot up, take note of the old ones version numbers. Then use the synaptic package manager to remove them. It's also not a bad idea to leave the last working one that you used on there, just in case you ever run into any problems with a future update.

---

### Post by iaculallad on 2008-06-10
> **alicelou85 said:**
> Hello, 
I have been constantly downloading updates for my ubuntu, and now I have 3 versions/kernels of it. I believe they are just slightly different from each other. However, every time when I start my computer, I will need to choose the one I want to boot my computer from out of the 3 ubuntu versions, plus the recovery version and windows longhorn. I wonder if there is any way to hide/delete the older versions from that list. 
Thank you. 
Alice

You can remove it by editing your /boot/grub/menu.lst file and removing the old kernel entries. If you want it permanently removed, you can delete it using Synaptics.

Create a backup first:

```
sudo cp /boot/grub/menu.lst /boot/grub/menu.lst.original
```

And open it for edit:

```
sudo gedit /boot/grub/menu.lst
```

---

### Post by aquavitae on 2008-06-10
You can also just remove them from the list:
```
gksu gedit /boot/grub/menu.lst
```
Then find the sections relating to the ones you want to remove and simply delete them. Be careful not to delete the ones you do need though or you might have difficulties booting up.

---

### Post by SteveNorman on 2008-06-10
is it better to comment out the old one or is it ok to just delete?

mine is below
```
## ## End Default Options ##

title		Ubuntu 8.04, kernel 2.6.24-18-generic
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.24-18-generic root=UUID=bcff3fcd-a60d-4931-ab38-00802d3ada03 ro quiet splash
initrd		/boot/initrd.img-2.6.24-18-generic
quiet

title		Ubuntu 8.04, kernel 2.6.24-18-generic (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.24-18-generic root=UUID=bcff3fcd-a60d-4931-ab38-00802d3ada03 ro single
initrd		/boot/initrd.img-2.6.24-18-generic

title		Ubuntu 8.04, kernel 2.6.24-17-generic
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.24-17-generic root=UUID=bcff3fcd-a60d-4931-ab38-00802d3ada03 ro quiet splash
initrd		/boot/initrd.img-2.6.24-17-generic
quiet

title		Ubuntu 8.04, kernel 2.6.24-17-generic (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.24-17-generic root=UUID=bcff3fcd-a60d-4931-ab38-00802d3ada03 ro single
initrd		/boot/initrd.img-2.6.24-17-generic

title		Ubuntu 8.04, kernel 2.6.22-14-generic
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=bcff3fcd-a60d-4931-ab38-00802d3ada03 ro quiet splash
initrd		/boot/initrd.img-2.6.22-14-generic
quiet

title		Ubuntu 8.04, kernel 2.6.22-14-generic (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=bcff3fcd-a60d-4931-ab38-00802d3ada03 ro single
initrd		/boot/initrd.img-2.6.22-14-generic

title		Ubuntu 8.04, memtest86+
root		(hd0,1)
kernel		/boot/memtest86+.bin
quiet

```

deleting it in gedit doesnt remove it from the hard drive though does it?

---

### Post by Kronie on 2008-06-10
the easiest way to do this is to get startup manager. 
its GUI software than allows u to customize splash, and grub.. very easy to use. to get it in terminal type
```
sudo apt-get startupmanager
```
then when u finish downloading and installing go to System->Administration->Startup Manager.in Boot Options tab make sure that default operating system is set to latest kernel version(8.04 kernel 2.6.24-19-generic is the latest one ATM) 
 then move on to Advanced tab and in Number of kernels section, put a check onto 'Limit number of kernels in boot menu' and in 'Number of kernels to keep' select 1. This will make grub show up only latest kernel, recovery mode, sumting else and windows. :D

---

### Post by iaculallad on 2008-06-10
> **SteveNorman said:**
> is it better to comment out the old one or is it ok to just delete?

mine is below
```
## ## End Default Options ##

title		Ubuntu 8.04, kernel 2.6.24-18-generic
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.24-18-generic root=UUID=bcff3fcd-a60d-4931-ab38-00802d3ada03 ro quiet splash
initrd		/boot/initrd.img-2.6.24-18-generic
quiet

title		Ubuntu 8.04, kernel 2.6.24-18-generic (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.24-18-generic root=UUID=bcff3fcd-a60d-4931-ab38-00802d3ada03 ro single
initrd		/boot/initrd.img-2.6.24-18-generic

title		Ubuntu 8.04, kernel 2.6.24-17-generic
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.24-17-generic root=UUID=bcff3fcd-a60d-4931-ab38-00802d3ada03 ro quiet splash
initrd		/boot/initrd.img-2.6.24-17-generic
quiet

title		Ubuntu 8.04, kernel 2.6.24-17-generic (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.24-17-generic root=UUID=bcff3fcd-a60d-4931-ab38-00802d3ada03 ro single
initrd		/boot/initrd.img-2.6.24-17-generic

title		Ubuntu 8.04, kernel 2.6.22-14-generic
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=bcff3fcd-a60d-4931-ab38-00802d3ada03 ro quiet splash
initrd		/boot/initrd.img-2.6.22-14-generic
quiet

title		Ubuntu 8.04, kernel 2.6.22-14-generic (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=bcff3fcd-a60d-4931-ab38-00802d3ada03 ro single
initrd		/boot/initrd.img-2.6.22-14-generic

title		Ubuntu 8.04, memtest86+
root		(hd0,1)
kernel		/boot/memtest86+.bin
quiet

```

deleting it in gedit doesnt remove it from the hard drive though does it?

That's you're choice (comment it or delete it). Just to be sure, create a backup of the file first before deleting any entries in your /boot/grub/menu.lst

sudo cp /boot/grub/menu.lst /boot/grub/menu.lst.original

---

### Post by Kronie on 2008-06-10
uh, u might wanna consider marking this thread as [SOLVED] since it explains all the ways u can edit grub..

---

### Post by beercz on 2008-06-10
> **Kronie said:**
> the easiest way to do this is to get startup manager. 
its GUI software than allows u to customize splash, and grub.. very easy to use. to get it in terminal type
```
sudo apt-get startupmanager
```then when u finish downloading and installing go to System->Administration->Startup Manager.in Boot Options tab make sure that default operating system is set to latest kernel version(8.04 kernel 2.6.24-19-generic is the latest one ATM) 
 then move on to Advanced tab and in Number of kernels section, put a check onto 'Limit number of kernels in boot menu' and in 'Number of kernels to keep' select 1. This will make grub show up only latest kernel, recovery mode, sumting else and windows. :D
Thanks for the tip regarding start up manager, I've previously edited grub by hand, so now I can be lazy and use startupamanger.

I installed it via synaptic.

---

