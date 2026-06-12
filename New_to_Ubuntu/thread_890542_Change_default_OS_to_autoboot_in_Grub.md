---
title: "Change default OS to autoboot in Grub"
date: 2008-08-15
forum: New to Ubuntu
---

### Post by wolfsigh on 2008-08-15
Hello.  I am new to Ubuntu and have set up a dual boot with Vista. I install Ubuntu on a separate HD and Grub installed on the MBR of the Vista drive.  I would like to make Grub autoload Vista if no OS is selected in the boot menu.  Can I do this?
Wolfsigh

---

### Post by ger_mulvey on 2008-08-15
You can do this by changing the default setting that boots Ubuntu in the menu.lst.
I would search for a guide on how to do this. You should find one. It's fairly easy to do and will achieve the desired effect.

---

### Post by iaculallad on 2008-08-15
> **wolfsigh said:**
> Hello.  I am new to Ubuntu and have set up a dual boot with Vista. I install Ubuntu on a separate HD and Grub installed on the MBR of the Vista drive.  I would like to make Grub autoload Vista if no OS is selected in the boot menu.  Can I do this?
Wolfsigh

On your terminal, open menu.lst for editing:

```
gksudo gedit /boot/grub/menu.lst
```

and look for the part in the file that says:

```
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not use 'savedefault' or your
# array will desync and will not let you boot your system.
**[COLOR="Blue"]default         0[/COLOR]**
```

Replace the **default** value with the number assigned for your vista. Start your counting with **0** upwards.

```
## ## End Default Options ##

title           Ubuntu 7.10, kernel 2.6.22-15-generic  [COLOR="Blue"]<-----This would be 0[/COLOR]
root            (hd0,2)
kernel          /boot/vmlinuz-2.6.22-15-generic root=UUID=16d722ac-565b-4d2d-9c6e-317b1ac253ff ro quiet splash
initrd          /boot/initrd.img-2.6.22-15-generic
quiet

title           Ubuntu 7.10, kernel 2.6.22-15-generic (recovery mode) [COLOR="Blue"]<-----This would be 1[/COLOR]
root            (hd0,2)
kernel          /boot/vmlinuz-2.6.22-15-generic root=UUID=16d722ac-565b-4d2d-9c6e-317b1ac253ff ro single
initrd          /boot/initrd.img-2.6.22-15-generic

title           Ubuntu 7.10, kernel 2.6.22-14-generic [COLOR="Blue"]<-----This would be 2[/COLOR]
root            (hd0,2)
kernel          /boot/vmlinuz-2.6.22-14-generic root=UUID=16d722ac-565b-4d2d-9c6e-317b1ac253ff ro quiet splash
initrd          /boot/initrd.img-2.6.22-14-generic
quiet

title           Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode) [COLOR="Blue"]<-----This would be 3[/COLOR]
root            (hd0,2)
kernel          /boot/vmlinuz-2.6.22-14-generic root=UUID=16d722ac-565b-4d2d-9c6e-317b1ac253ff ro single
initrd          /boot/initrd.img-2.6.22-14-generic

title           Ubuntu 7.10, memtest86+ [COLOR="Blue"]<-----This would be 4[/COLOR]
root            (hd0,2)
kernel          /boot/memtest86+.bin
quiet

```

When you're done editing/replacing the [COLOR="Blue"]**default**[/COLOR] value, save and close the file.

---

### Post by mcduck on 2008-08-15
In addition to that, find the line "# updatedefaultentry=false" and change it into "# updatedefaultentry=true".

If you don't do that, when the next kernel update comes it will add new kernels into the grub menu before the Windows entry, and your default setting won't worlk correctly any more.

---

### Post by Paqman on 2008-08-15
There's a good GUI tool called [Startup Manager](apt:startupmanager) that can do this for you without having to edit files manually. It does a lot of other handy stuff too.

---

### Post by ace007 on 2008-08-15
By setting the default value your just telling grub which entry to highlight while it counts down.  I believe the above will solve your question. Please find the solved button on the thread and click it.

Welcome to Ubuntu.

---

### Post by wolfsigh on 2008-08-15
Thanks to all who replied. I appreciate the detailed help.  Turned out to be an easy fix.  Opened menu.lst and changed "default" and "updateddefaultentry". Still have a lot to learn about Ubuntu (Linux). Thanks again.
wolfsigh

---

