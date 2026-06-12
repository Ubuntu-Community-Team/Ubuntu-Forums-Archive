---
title: "bios fails cut off  pci=force required"
date: 2008-05-05
forum: New to Ubuntu
---

### Post by hazman on 2008-05-05
hi,
when ubuntu starts up i get bios fails cut off[1999] and something about needing pci=force.what does this mean and how can i resolve it.although everything go ok and ubuntu loads as normal.

---

### Post by jboy012000 on 2008-05-05
[http://ph.ubuntuforums.com/showthread.php?t=759438](http://ph.ubuntuforums.com/showthread.php?t=759438)

go to the link above and take a look at some of the replies he got, they may be the answer to your problem.

Cheers

---

### Post by eriqjaffe on 2008-05-05
If everything works, you don't need to do anything.

---

### Post by hazman on 2008-05-05
but does it mean pci slots not working as i havn't got my belkin wireless g notebook card to work or my external cdrom

---

### Post by philinux on 2008-05-05
It's apci=force, it's power management. My guess is you have to button the pc after telling it to shutdown. My old pc was the same.

1. you can try to update the bios.
2. live with it.
3. Add acpi=force to the end of the kernel line in grub. But if a new kernel comes along you'll have to add it back again.

---

### Post by hazman on 2008-05-05
thanks phil,so it has no bearing on my pci slots then they should work when i can figure them out.i am struggling to get on net or get my external cdrom going

---

### Post by wolfen69 on 2008-05-05
i had the same thing with my old laptop. it would not completely shutdown and had to hold the power button to do it. not wanting to wear out the power button, i updated the bios and it was fixed.

---

### Post by eriqjaffe on 2008-05-05
You might want to try adding

```
acpi=force pci=noacpi
```

To the kernel line in Grub...

---

### Post by hazman on 2008-05-05
what will this do and how do i do it

---

### Post by eriqjaffe on 2008-05-05
> **hazman said:**
> what will this do and how do i do itacpi=force will, well, force the ACPI system to work despite the old BIOS.  My old laptop doesn't power off without this.

pci=noacpi disables PCI IRQ routing, which **may** allow your cardbus stuff to work.

There are a couple ways to apply this...

1) At boot time get into the GRUB menu.  Select the kernel you wish to boot (usually the first one) and add it manually.  Off-hand, I can't remember what to type to do that, but search around and you'll find it.  That sets it for that boot only.

2) For a permanent change, edit the /boot/grub/menu.lst file, adding the parameter(s) to the appropriate kernel line(s).  You need to be root to save changes to that file, so you have to run it as sudo:

```
sudo gedit /boot/grub/menu.lst
```

Not a bad idea to make a backup copy of the menu.lst file before you dig around in it, btw.

---

### Post by spiderbatdad on 2008-05-05
```
## ## End Default Options ##

title		Ubuntu 8.04, kernel 2.6.24-16-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=xxxxxxxxxxx ro **lapic pci=routeirq**
initrd		/boot/initrd.img-2.6.24-16-generic
quiet
savedefault
```

See **highlighted** end of line beginning with the word 'kernel.'

---

