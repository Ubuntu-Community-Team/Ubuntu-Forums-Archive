---
title: "Kernel update caused these problems ... Sound, Video"
date: 2008-10-19
forum: New to Ubuntu
---

### Post by cwmoser on 2008-10-19
I noted some problems with Sound and Video associated with my Hardy version of Ubuntu.

Finally I observed in /boot a new version of the Kernel -- *server.

I currently have these:
vmlinuz-2.6.24-21-rt
vmlinuz-2.6.24-21-generic
vmlinuz-2.6.24-21-server


*server was the default in the grub menu.  I edited /boot/grub/menu.lst and changed the "default" value from 0 to 2 so that *rt was the default boot kernel.

Why did this *server kernel get built?

Carl

---

### Post by bpowell2005 on 2008-10-19
> **cwmoser said:**
> I noted some problems with Sound and Video associated with my Hardy version of Ubuntu.

Finally I observed in /boot a new version of the Kernel -- *server.

I currently have these:
vmlinuz-2.6.24-21-rt
vmlinuz-2.6.24-21-generic
vmlinuz-2.6.24-21-server


*server was the default in the grub menu.  I edited /boot/grub/menu.lst and changed the "default" value from 0 to 2 so that *rt was the default boot kernel.

Why did this *server kernel get built?

Carl

Was this an automatic update, or did you go into the package manager and select the Kernel for updating? My computer has gone through 2 Kernel updates no with no problems.

It sounds like you have solved the problem by selecting the correct kernel as the default, if you really don't need the Server kernel (which I don't have installed) you might want to go into the package manager and mark it for removal.

---

