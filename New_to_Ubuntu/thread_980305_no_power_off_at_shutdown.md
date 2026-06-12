---
title: "no power off at shutdown"
date: 2008-11-12
forum: New to Ubuntu
---

### Post by killerbyteeire on 2008-11-12
The computer hangs at the shutdown splash screen. The bar goes completely across but does not power off then. I have to physically switch the power off. Also during startup there is a screen that has text saying bios fails age cutoff 1997 i think. Can anybody tell me how to fix this so that it shuts down and powers off?

thank you
brendan

---

### Post by stephanvaningen on 2008-11-12
When the shutdown-bar is then almost empty and then it seems to 'hang': can you change to a terminal-screen with i.e. Ctrl-Alt-F2? If so, can you sign in? If so, what does...:
 dmesg | tail
...tell you?

---

### Post by jimmy the saint on 2008-11-12
how old is that machine?  it may be an issue of the bios not accepting the kill signal.  perhaps if you can find the make/model of the mobo, you can find a bios upgrade?

---

### Post by killerbyteeire on 2008-11-12
stephanvaningen, no i cant change to a terminal screen with ctrl alt and any f number button then. sudo shutdown now doesnt work either

jimmy the saint, the mobo is from sometime around 99 2000 i think. it did shutdown before the last reformat.

---

### Post by tgalati4 on 2008-11-12
Depending on your BIOS, you can set a kernel boot code (acpi=force or apm=force noacpi) and see if the behavior changes.

Look out the output in the beginning of dmesg:

>dmesg | more

Pay attention to the lines concerning acpi and apm.

---

### Post by desperado665 on 2008-11-12
My old athlon xp used to do the exact same thing, and it was resolved by using the kernel boot code acpi=force

---

### Post by alienexplorers on 2008-11-12
you can setup your /boot/grub/menu.lst file to read like this for each kernel:
> title		Ubuntu 8.04.1, kernel 2.6.24-21-generic (on /dev/sdb1)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.24-21-generic root=UUID=11e5a808-45f5-41fb-8b43-5f2a8af9016d ro quiet splash [COLOR="Red"]acpi=force[/COLOR] 
initrd		/boot/initrd.img-2.6.24-21-generic
savedefault
boot


---

