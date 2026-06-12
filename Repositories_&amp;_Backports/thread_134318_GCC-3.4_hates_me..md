---
title: "GCC-3.4 hates me."
date: 2006-02-21
forum: Repositories &amp; Backports
---

### Post by kaydot on 2006-02-21
```
kaydot@ubuntu:~$ sudo apt-get install gcc-3.4
Reading package lists... Done
Building dependency tree... Done
The following extra packages will be installed:
  cpp-3.4 gcc-3.4-base
Suggested packages:
  gcc-3.4-doc libc6-dev-amd64
The following NEW packages will be installed:
  cpp-3.4 gcc-3.4 gcc-3.4-base
0 upgraded, 3 newly installed, 0 to remove and 0 not upgraded.
Need to get 2355kB of archives.
After unpacking 8720kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 http://us.archive.ubuntu.com breezy/main gcc-3.4-base 3.4.4-6ubuntu8 [163kB]
Get:2 http://us.archive.ubuntu.com breezy/main cpp-3.4 3.4.4-6ubuntu8 [1707kB]
Get:3 http://us.archive.ubuntu.com breezy/main gcc-3.4 3.4.4-6ubuntu8 [484kB]
Fetched 719B in 0s (2969B/s)
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/g/gcc-3.4/gcc-3.4-base_3.4.4-6ubuntu8_i386.deb  Size mismatch
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/g/gcc-3.4/cpp-3.4_3.4.4-6ubuntu8_i386.deb  Size mismatch
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/g/gcc-3.4/gcc-3.4_3.4.4-6ubuntu8_i386.deb  Size mismatch
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?
```

Help? :(

---

### Post by gerbman on 2006-02-21
[QUOTE=kaydot]Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?[/QUOTE]

Did you try those commands? Any errors when you did? Does ```
sudo apt-get install gcc
```give you the same thing?

---

### Post by nwatson on 2006-02-21
I'm having this problem as well. Trying to compile a new kernel, which apparently wants gcc-3.4.

If you just apt-get install gcc, it'll give you the newest version, which apparently isn't 3.4. Tried the fix flag too...

---

### Post by kaydot on 2006-02-21
[QUOTE=nwatson]I'm having this problem as well. Trying to compile a new kernel, which apparently wants gcc-3.4.

If you just apt-get install gcc, it'll give you the newest version, which apparently isn't 3.4. Tried the fix flag too...[/QUOTE]
Yeah, it sounds like you and I are in the same league. =/

---

### Post by nwatson on 2006-02-23
[QUOTE=kaydot]Yeah, it sounds like you and I are in the same league. =/[/QUOTE]

If you're trying to compile a kernel as I am, I've found that the latest version of the kernel from kernel.org works just fine... just download it from there, stick it in /usr/src, and it works the same, it just likes gcc.

---

