---
title: "sudo nautilus error"
date: 2008-06-01
forum: New to Ubuntu
---

### Post by jtclicker on 2008-06-01
I can't launch sudo nautilus as I get a 'segmentation error'

julian@julian-desktop:~$ sudo nautilus
[sudo] password for julian: 
seahorse nautilus module initialized
Initializing nautilus-share extension
Segmentation fault


Any ideas?

---

### Post by IHATEDLINK on 2008-06-01
> **jtclicker said:**
> I can't launch sudo nautilus as I get a 'segmentation error'

julian@julian-desktop:~$ sudo nautilus
[sudo] password for julian: 
seahorse nautilus module initialized
Initializing nautilus-share extension
Segmentation fault


Any ideas?

NEVER EVER DO SUDO ANYTHING FOR LAUNCHING A GRAPHICAL APPLICATION!

```
gksudo nautilus
```
Safer ;)

---

### Post by Joeb454 on 2008-06-01
Try ```
gksudo nautilus
```

---

### Post by autocrosser on 2008-06-01
You might try sudo killall nautilus--nautilus will restart after the command....Or just reboot & try it again.

---

### Post by NilsE on 2008-06-01
> **jtclicker said:**
> I can't launch sudo nautilus as I get a 'segmentation error'

julian@julian-desktop:~$ sudo nautilus
[sudo] password for julian: 
seahorse nautilus module initialized
Initializing nautilus-share extension
Segmentation fault


Any ideas?
I get the same thing with just sudo.  try

gksudo nautilus

gksudo is for graphic interfaces such as nautilus/ sudo is for command line root access

---

### Post by jtclicker on 2008-06-01
thanks guys, I've tried all the suggestions (i've always used sudo, so I guess I've been wrong!) gksudo doesn't show an error but also doesn't launch nautilus as root, or any form of nautilus, killall shows nothing to kill, and rebooting doesn't help...

---

### Post by Joeb454 on 2008-06-01
gksudo doesn't launch nautilus at all?

---

### Post by jtclicker on 2008-06-01
nope...

julian@julian-desktop:~$ gksudo nautilus
Initializing nautilus-share extension
julian@julian-desktop:~$ 

but nautilus doesn't launch.

Under Gutsy I always - incorrectly - used sudo nautilus and it popped straight up. There was a fairly big upgrade yesterday which I think included some nautilus references, can't remember exactly...

---

### Post by jtclicker on 2008-06-01
I forgot to add, after the gksudo nautilus command, I get the splash screen asking for the password for nautlius, and telling me what nautilus does, but after I input the password it closes, and the nautilus doesn't appear

---

### Post by ibutho on 2008-06-01
Uninstall nautilus-share and see if you can then run nautilus as root by doing ALT-F2 and entering the command "gksu nautilus".

---

### Post by jtclicker on 2008-06-01
thanks, tried that. It still didn't launch

---

### Post by jtclicker on 2008-06-01
running dmesg shows this error

[  103.417975] nautilus[5934]: segfault at 00000000 eip 00000000 esp b63b725c error 4

---

