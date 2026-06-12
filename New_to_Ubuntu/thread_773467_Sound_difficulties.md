---
title: "Sound difficulties"
date: 2008-04-28
forum: New to Ubuntu
---

### Post by jeremycollins08 on 2008-04-28
Hi!

I have Ubuntu Hardy installed, and I have been having some sound issues. Here is my situation.

I bought a set of surround speakers by logitech just a while ago, and also bought an Audigy Sound Blaster sound card for my computer. Both work well in xp, but not in linux. See, sometimes I can turn on my computer, and the sound works perfectly. However, other times when I turn on my computer and log into ubuntu, I cannot get any type of sound what so ever. I tried to restart my computer (this usually brings the sound back) but has failed to do so now. Any help? I am clueless here. It's like it has a mind of its own.

Thanks,
Jeremy

---

### Post by spiderbatdad on 2008-04-28
you might try adding pci=routeirq to the kernel line in /boot/gub/menu.lst if that makes any sense. Reading dmesg run in a terminal might help...It may look like a lot of nonsense, but in the output are human-readable suggestions like "try pci=routeirq if a device is not working properly."

---

### Post by jeremycollins08 on 2008-04-28
Thanks.

um...sorry but i am new and still do not understand what to do here. I opened menu.lst, but where do i put it?

---

### Post by spiderbatdad on 2008-04-29
use ```
gksu gedit /boot/grub/menu.lst
```

scroll way down to the section: ###END DEFAULT OPTIONS####
like this:
```
## ## End Default Options ##

title		Ubuntu 8.04, kernel 2.6.24-16-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=604f2b74-7f64-424f-a8bf-1160a71d9ea3 ro lapic **pci=routeirq**
initrd		/boot/initrd.img-2.6.24-16-generic
quiet
savedefault

title		Ubuntu 8.04, kernel 2.6.24-16-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=604f2b74-7f64-424f-a8bf-1160a71d9ea3 ro single
initrd		/boot/initrd.img-2.6.24-16-generic

title		Ubuntu 8.04, kernel 2.6.22-14-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=604f2b74-7f64-424f-a8bf-1160a71d9ea3 ro lapic pci=routeirq
initrd		/boot/initrd.img-2.6.22-14-generic
quiet
savedefault
```

See where I have highlighted the end of the line that begins with the word kernel in the default boot option? Default is the first one in the list.

I usually remove --quiet splash.

---

