---
title: "Shutdown/Restart after installation"
date: 2011-09-10
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by _d_ on 2011-09-10
I'm not sure how many other people have experienced this, but I've noticed that after a fresh installation of 11.10 (x86_64), the installer won't shutdown or restart by it's self as one of the shutdown procedures hangs forever:

```
nm-dispatcher.action: Caught signal 15, shutting down . . .
```

That is where it hangs indefinitely, and is only an issue with 11.10 (Beta1).

Anyone else experience this at all?

---

### Post by kyleabaker on 2011-09-11
Are you still seeing this issue? If so, please list your hardward configuration.

---

### Post by effenberg0x0 on 2011-09-11
It's hard to guess. I'd like to see a little more information because I think it might be a common acpi or driver issue. At the very least it would help us to see some information like:

cat /etc/default/grub
lspci | grep -i vga
lspci | grep -i ethernet
lspci | grep -i wireless[FONT=monospace]

[/FONT]Regards,
Effenberg

---

### Post by kyleabaker on 2011-09-11
> **effenberg0x0 said:**
> At the very least it would help us to see some information like:

cat /etc/default/grub
lspci | grep -i vga
lspci | grep -i ethernet
lspci | grep -i wireless[FONT=monospace]

[/FONT]Regards,
Effenberg
That's what I'm saying. Some config options will help us diagnose the problem. Thanks effenberg0x0. ;)

Without some logs or debug statements you're asking for us to solve this blindly.

---

### Post by mrcoolinux on 2011-09-11
Hi. Do a check sum. Chances are you might have a faulty cd or a bad download.

---

### Post by _d_ on 2011-09-11
Sorry, I wasn't really asking for support. :P

I was just asking if anyone else experienced this same thing.

---

