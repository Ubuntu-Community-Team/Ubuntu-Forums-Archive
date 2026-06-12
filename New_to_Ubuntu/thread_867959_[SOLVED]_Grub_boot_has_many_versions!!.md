---
title: "[SOLVED] Grub boot has many versions!!"
date: 2008-07-23
forum: New to Ubuntu
---

### Post by koba101 on 2008-07-23
Hi,

This is how my GRUB looks when  I start the system...I've got so many Ubutu's do I need all of those?  Can I delete some of them? Whey do i need all the different kernels for?


```

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=21449a34-e36b-4254-8932-e68e8c1353db ro quiet splash
initrd		/boot/initrd.img-2.6.24-19-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=21449a34-e36b-4254-8932-e68e8c1353db ro single
initrd		/boot/initrd.img-2.6.24-19-generic

title		Ubuntu 8.04.1, kernel 2.6.24-18-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-18-generic root=UUID=21449a34-e36b-4254-8932-e68e8c1353db ro quiet splash
initrd		/boot/initrd.img-2.6.24-18-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-18-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-18-generic root=UUID=21449a34-e36b-4254-8932-e68e8c1353db ro single
initrd		/boot/initrd.img-2.6.24-18-generic

title		Ubuntu 8.04.1, kernel 2.6.24-17-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-17-generic root=UUID=21449a34-e36b-4254-8932-e68e8c1353db ro quiet splash
initrd		/boot/initrd.img-2.6.24-17-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-17-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-17-generic root=UUID=21449a34-e36b-4254-8932-e68e8c1353db ro single
initrd		/boot/initrd.img-2.6.24-17-generic

title		Ubuntu 8.04.1, kernel 2.6.24-16-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=21449a34-e36b-4254-8932-e68e8c1353db ro quiet splash
initrd		/boot/initrd.img-2.6.24-16-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-16-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=21449a34-e36b-4254-8932-e68e8c1353db ro single
initrd		/boot/initrd.img-2.6.24-16-generic

title		Ubuntu 8.04.1, kernel 2.6.22-14-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=21449a34-e36b-4254-8932-e68e8c1353db ro quiet splash
initrd		/boot/initrd.img-2.6.22-14-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.22-14-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=21449a34-e36b-4254-8932-e68e8c1353db ro single
initrd		/boot/initrd.img-2.6.22-14-generic

title		Ubuntu 8.04.1, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST
```

---

### Post by match002001 on 2008-07-23
Hello,

You shouldn't NEED all those versions, but it would be a good to have if you are troubleshooting an issue with that kernal version. If you would like to remove them check this out and change the GRUB menu.lst 

Hope that helps.

-Match

---

### Post by drs305 on 2008-07-23
Each time a new kernel is downloaded it is included in the grub menu. The easiest way to control the grub display is through StartUp-Manager.

```
sudo aptitude install startupmanager
```

To run: System, Administration, StartUp-Manager

To learn more about it, read this tutorial:
[HOWTO: Grub Menu Kernel Display Options & StartUp-Manager]("http://ubuntuforums.org/showthread.php?t=818177")

You can either limit the number visible in the boot menu via Startup-Manager, or for a cleaner system, remove old kernels via Synaptic. Look for "linux-image..." and uninstall older ones but keep at least two - the current one and one older one that works. As you remove the kernels with synaptic they will be removed from the grub menu.

---

### Post by northern lights on 2008-07-23
Certainly. Might as well get rid of the older kernel versions.

I leave the latest two. That would be ```
title		Ubuntu 8.04.1, kernel 2.6.24-19-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=21449a34-e36b-4254-8932-e68e8c1353db ro quiet splash
initrd		/boot/initrd.img-2.6.24-19-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=21449a34-e36b-4254-8932-e68e8c1353db ro single
initrd		/boot/initrd.img-2.6.24-19-generic

title		Ubuntu 8.04.1, kernel 2.6.24-18-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-18-generic root=UUID=21449a34-e36b-4254-8932-e68e8c1353db ro quiet splash
initrd		/boot/initrd.img-2.6.24-18-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-18-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-18-generic root=UUID=21449a34-e36b-4254-8932-e68e8c1353db ro single
initrd		/boot/initrd.img-2.6.24-18-generic

```

The rest is pretty much superfluous.
(If these two are stable, that is)

---

### Post by Zorael on 2008-07-23
If you're not afraid of some text editing, pop up your **/boot/grub/menu.lst** file in an editor with superuser permissions and find the line that defines how many kernels should actually be offered.

Alt+F2 to spawn the run box. Gnome command:
```
gksu gedit /boot/grub/menu.lst
```
KDE command:
```
kdesu "kate /boot/grub/menu.lst"
```

```
## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
##      howmany=7
# howmany=all
```
Set **all** to something else. Save.

---

### Post by billgoldberg on 2008-07-23
I only keep 1 extra kernel in the grub *(a stable one to fall back on if there should be some sort of problem)*.

---

### Post by koba101 on 2008-07-25
yeah i set the limit to 1... that makes a difference.  Looks good now

---

### Post by SunnyRabbiera on 2008-07-25
Yeh this happns though the kernel updates and such, but its nothing to worry about and takes up no real space.

---

