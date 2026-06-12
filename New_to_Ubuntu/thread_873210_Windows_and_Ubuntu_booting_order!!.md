---
title: "Windows and Ubuntu booting order!!"
date: 2008-07-28
forum: New to Ubuntu
---

### Post by JnMrno on 2008-07-28
Hi, I just installed Ubuntu on a second hard-drive. I want to have it as second choice boot, but, when I turn on the pc, even though it asks me which OS I want to login in, after several seconds if I don't move the arrow down it logs into Ubuntu automatically since it is first in the list. How can I change orders, and make Windows the one to login automatically? (my dad won't know how to use Ubuntu or choose between OS) (I have to share this PC)

Thnks

---

### Post by iaculallad on 2008-07-28
> **JnMrno said:**
> Hi, I just installed Ubuntu on a second hard-drive. I want to have it as second choice boot, but, when I turn on the pc, even though it asks me which OS I want to login in, after several seconds if I don't move the arrow down it logs into Ubuntu automatically since it is first in the list. How can I change orders, and make Windows the one to login automatically? (my dad won't know how to use Ubuntu or choose between OS) (I have to share this PC)

Thnks

Open your /boot/grub/menu.lst and edit it. Change the value of **default** to point at windoze boot option number:

```
gksudo gedit /boot/grub/menu.lst
```

```
## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not use 'savedefault' or your
# array will desync and will not let you boot your system.
**[COLOR="Blue"]default         0[/COLOR]**

```

For the Sample below: The value of Ubuntu 7.10, memtest86+ is 2:

```
title           Ubuntu 7.10, kernel 2.6.22-15-generic
root            (hd0,2)
kernel          /boot/vmlinuz-2.6.22-15-generic root=UUID=6d422661-145e-4c07-9cbb-8428c17a2b1f ro quiet vga=792 splash
initrd          /boot/initrd.img-2.6.22-15-generic
quiet

title           Ubuntu 7.10, kernel 2.6.22-15-generic (recovery mode)
root            (hd0,2)
kernel          /boot/vmlinuz-2.6.22-15-generic root=UUID=6d422661-145e-4c07-9cbb-8428c17a2b1f ro single
initrd          /boot/initrd.img-2.6.22-15-generic

title           [COLOR="Blue"]**Ubuntu 7.10, memtest86+**[/COLOR]
root            (hd0,2)
kernel          /boot/memtest86+.bin
quiet

```

Start counting with 0 until you reach for the windoze boot option, usually it is 4 with no other boot kernel installed.

---

### Post by +Eric on 2008-07-28
Editing the grub file itself is a fine option. I do believe you need to open it as root though.

Another option is to install startup-manager.

```
sudo apt-get install startupmanager
```

---

### Post by rbc on 2008-07-28
If you prefer a GUI method, install Startup-Manager from Synaptic. Otherwise, follow iaculallad's instructions. It's really one of the least complicated things to do from terminal

---

### Post by iaculallad on 2008-07-28
> **+Eric said:**
> Editing the grub file itself is a fine option. I do believe you need to open it as root though.

You don't have to be a root to edit the /boot/grub/menu.lst file. As long as you have a privilege account, you too could edit it. The reason why you insert the gksudo command so it would ask for your authorize credentials.

```
gksudo gedit /boot/grub/menu.lst
```

---

### Post by kansasnoob on 2008-07-28
I'd go with installing startupmanager. It's also handy for dealing with how many kernels show up in the splash menu, and it's simply a great piece of art!

Anyone ever think how many hours go into creating our beloved guis?

---

