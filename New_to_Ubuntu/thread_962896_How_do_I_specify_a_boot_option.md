---
title: "How do I specify a boot option?"
date: 2008-10-29
forum: New to Ubuntu
---

### Post by ginestre on 2008-10-29
How do I specify a boot option, both on a one-off and a permanent basis?

---

### Post by aeiah on 2008-10-29
you could mean something else, but im going to assume you mean changing what operating system you boot into at the grub menu. you can just use the arrow keys to select a different one. if you want to permanently set a default, then you need to edit your /boot/grub/menu.lst file
```
sudo gedit /boot/grub/menu.lst
```

like i said, you could mean something else though and ive misunderstood

---

### Post by drs305 on 2008-10-29
Assuming you mean grub options, I highly recommend using StartUp-Manager, a gui-based app that let's you set the default OS, kernel, menu timeout, how many kernels to display, and more. It doesn't require opening and editing /boot/grub/menu.lst but makes the changes via a simple interface that is hard to mess up.

Install:
```
sudo apt-get install startupmanager
```

Run:
System, Administration, StartUp-Manager

See the link in my signature for a tutorial with lots of information about how to use this program.

---

### Post by kansasnoob on 2008-10-29
> **drs305 said:**
> Assuming you mean grub options, I highly recommend using StartUp-Manager, a gui-based app that let's you set the default OS, kernel, menu timeout, how many kernels to display, and more. It doesn't require opening and editing /boot/grub/menu.lst but makes the changes via a simple interface that is hard to mess up.

Install:
```
sudo apt-get install startupmanager
```

Run:
System, Administration, StartUp-Manager

See the link in my signature for a tutorial with lots of information about how to use this program.

+1!

Startup Manager makes life great!

I'm a GUI guy.

---

