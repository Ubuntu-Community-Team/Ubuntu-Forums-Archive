---
title: "Whats the difference between &quot;Bookmarking&quot; and &quot;Auto-mounting&quot; a network drive?"
date: 2014-07-06
forum: New to Ubuntu
---

### Post by Herbon on 2014-07-06
I was looking to write a BASH script to move older .avi folders to a Network Array Storage (NAS) device once the NAS was on-line. And after watching a few youtube videos, this subjects was never clarified.

---

### Post by Vladlenin5000 on 2014-07-06
Bookmarking, as in creating a bookmark for a local or network location in a file manager (Nautilus, Thunar, etc.), doesn't mount it unless you click it.

---

### Post by Herbon on 2014-07-07
> **Vladlenin5000 said:**
> Bookmarking, as in creating a bookmark for a local or network location in a file manager (Nautilus, Thunar, etc.), **doesn't mount it unless you click it.**

It there a way to change this??

---

### Post by Vladlenin5000 on 2014-07-07
Change what? What are you trying to achieve?

---

### Post by Herbon on 2014-07-07
> **Vladlenin5000 said:**
> Change what? What are you trying to achieve?

I trying to create a persistent link/map to a NAS folder without editing the "fstab" file.  

So I was wondering if its possible to have the "Bookmarked" drive be available without *"clicking*" it

Later I was planning to write a script that moves old folders to the NAS.

---

### Post by Vladlenin5000 on 2014-07-08
If the network drive is a "Windows share" (or something that emulates that) then the following should help: [https://wiki.ubuntu.com/MountWindowsSharesPermanently](https://wiki.ubuntu.com/MountWindowsSharesPermanently)

---

### Post by Herbon on 2014-07-09
> **Vladlenin5000 said:**
> If the network drive is a "Windows share" (or something that emulates that) then the following should help: [https://wiki.ubuntu.com/MountWindowsSharesPermanently](https://wiki.ubuntu.com/MountWindowsSharesPermanently)

Thanks!

---

