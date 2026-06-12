---
title: "Windows starts from GRUB... sometimes"
date: 2008-10-19
forum: New to Ubuntu
---

### Post by neil6412 on 2008-10-19
Hi,

After a lot of struggling, I managed to adapt menu.lst so that I could load Windows Vista, and it worked!  However a few days later when I tried to use the Windows boot, it started but then after a few seconds the screen goes blank and then restarts and I go back to my Grub menu.  Since then there has been one time when it has worked but the rest not. I'm assuming that some of my menu.lst settings could be more robust... Has anyone experienced anything like this? 

Thanks
Neil

Here is an extract from my menu.lst file.  

> title		Ubuntu intrepid (development branch), kernel 2.6.27-6-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.27-6-generic root=UUID=72e04ce4-8689-4674-a0a0-88a3044ad2ef ro quiet splash 
initrd		/boot/initrd.img-2.6.27-6-generic
quiet

title		Ubuntu intrepid (development branch), kernel 2.6.27-6-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.27-6-generic root=UUID=72e04ce4-8689-4674-a0a0-88a3044ad2ef ro  single
initrd		/boot/initrd.img-2.6.27-6-generic

title		Ubuntu intrepid (development branch), kernel Last successful boot
root		(hd0,0)
kernel		/boot/last-good-boot/vmlinuz root=UUID=72e04ce4-8689-4674-a0a0-88a3044ad2ef ro quiet splash  last-good-boot
initrd		/boot/last-good-boot/initrd.img
quiet

title		Ubuntu intrepid (development branch), kernel 2.6.27-4-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.27-4-generic root=UUID=72e04ce4-8689-4674-a0a0-88a3044ad2ef ro quiet splash 
initrd		/boot/initrd.img-2.6.27-4-generic
quiet

title		Ubuntu intrepid (development branch), kernel 2.6.27-4-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.27-4-generic root=UUID=72e04ce4-8689-4674-a0a0-88a3044ad2ef ro  single
initrd		/boot/initrd.img-2.6.27-4-generic

title		Ubuntu intrepid (development branch), kernel 2.6.24-19-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=72e04ce4-8689-4674-a0a0-88a3044ad2ef ro quiet splash 
initrd		/boot/initrd.img-2.6.24-19-generic
quiet

title		Ubuntu intrepid (development branch), kernel 2.6.24-19-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=72e04ce4-8689-4674-a0a0-88a3044ad2ef ro  single
initrd		/boot/initrd.img-2.6.24-19-generic

title		Ubuntu intrepid (development branch), memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin
quiet

title           Windows Vista
root		(hd0,1)
chainloader 	+1
quiet


---

### Post by Bucky Ball on 2008-10-19
Try this, change title to what you want but everything else the same:

```
title           Windoze Vista - Longhorn (loader)
root            (hd0,1)
savedefault
makeactive
chainloader     +1
```It looks like you installed Ubuntu first, which can be problematic. If still no joy, try this:

```
title           Windows Vista
root            (hd0,1)
savedefault
makeactive
chainloader     +1
map (hd0) (hd1)
map (hd1) (hd0)
```A stab, someone else may be able to correct me or add to the thread on this ... You might want to experiment referencing this page here:

[https://help.ubuntu.com/community/How_to_dual-boot_Ubuntu_and_XP_after_installing_them_separately_on_two_HDs](https://help.ubuntu.com/community/How_to_dual-boot_Ubuntu_and_XP_after_installing_them_separately_on_two_HDs)

:)

---

### Post by northern lights on 2008-10-19
> **Bucky Ball said:**
> Try this, change title to what you want but everything else the same:
```
title           Windoze Vista - Longhorn (loader)
root            (hd0,1)
savedefault
makeactive
chainloader     +1
```
This would have been my initial suggestion also. Might not suffice, though.

> **Bucky Ball said:**
> It looks like you installed Ubuntu first, which can be problematic. If still no joy, try this:

```
title           Windows Vista
root            (hd0,1)
savedefault
makeactive
chainloader     +1
map (hd0) (hd1)
map (hd1) (hd0)
```A stab, someone else may be able to correct me or add to the thread on this
While it's not relevant which OS was installed first chronologically, Windows wants to reside on the first partition of the first drive - (hd0,0) in GRUB syntax. The map function in GRUB can make the Windows bootloader (ntldr) believe that it's booting from the first hdd when it really isn't. As in the above, map will perform a virtual swap of the first and second hdd. In the OPs configuration however, Windows is on the second *partition* of the first *drive*.

If the initial suggestion does not suffice, try to make it this:```
title           Windows Vista
rootnoverify    (hd0,1)
savedefault
makeactive
chainloader     +1
```

---

### Post by Bucky Ball on 2008-10-19
northern lights, is there a map command to trick Windoze from one *partition* to the other, as is the case here, or the map command only applies to physical drives?

---

### Post by northern lights on 2008-10-19
'map' itsself is designed only for drive mapping, it can't handle partitions.

Windows should hopefully be happy with any primary (of which you can have a maximum of 4, the extended partition being one of them) partition of the first drive. As dual booting two different Windows releases on the same machine also is possible.

Theoretically you can hide partitions, which is helpful in the above case of more than one Windows, as ntldr will otherwise get confused. In this case it shouldn't be necessary.

Let's see how far the OP gets...

---

### Post by neil6412 on 2008-10-19
> title           Windows Vista
rootnoverify	(hd0,1)
savedefault
makeactive
chainloader 	+1
quiet

Thanks, but still no luck! Most recently it seemed to get quite far before restarting... perhaps it is a windows problem rather than a Grub problem?

---

### Post by northern lights on 2008-10-19
> **neil6412 said:**
> perhaps it is a windows problem rather than a Grub problem?Very well could be. I'd also get rid of the "quiet" option, but nonetheless, this sounds like an issue with the windows installation. Any quotable error messages?

---

### Post by caljohnsmith on 2008-10-19
I agree with Northern Lights, I think you almost for sure have a Windows problem and not a Grub problem at this point. You can use the original entry in your Grub menu, but I would get rid of the "quiet" option like Northern Lights suggested:
```
title Windows Vista
root (hd0,1)
chainloader +1
```
Do you have a Windows Vista Install/Recovery CD? If not, you can download one from [here]("http://neosmart.net/blog/2008/download-windows-vista-x64-recovery-disc/"). I would boot that up and simply do the "Vista Repair" option. If that doesn't work to get Vista booting OK, there are some commands we can try from the Vista Recovery CD; but you could also have a HDD problem since the behavior you observe with Vista is inconsistent. Anyway, give the Recovery CD a shot and let us know how it goes. :)

---

