---
title: "Linux support for HP-UX 9.0 system calls"
date: 2008-02-06
forum: Programming Talk
---

### Post by ksunix on 2008-02-06
Hi all,

I am very new to Linux programming. My company has an old C program that runs on a 1994 HP-UX server, running HP-UX 9.0. We want to port that application to Linux. I have three questions...

1.) Are the HP-UX and Linux system calls compatible? 
2.) We use the "System" and "Fork" commands in the old program, is this supported in Linux as well?
3.) Which distro of Linux do you suggest for this project?

Thanks in advance for the info!

Yours,
Ke

:qw!

---

### Post by lnostdal on 2008-02-06
> **ksunix said:**
> 
1.) Are the HP-UX and Linux system calls compatible? 


There will probably be some differences.

> **ksunix said:**
> 
2.) We use the "System" and "Fork" commands in the old program, is this supported in Linux as well?


Yes, but see my answer above. edit: try typing this in your Linux terminal: 
```
man fork
```

> **ksunix said:**
> 
3.) Which distro of Linux do you suggest for this project?


..anything based on Debian is nice. Ubuntu is very nice - it's easy and straightforward to maintain and has a huge community backing it. By the way .. I might be able to help you guys with this in a more direct fashion than via the forums if you are interested in that. See my signature.

---

### Post by stroyan on 2008-02-06
There are some HP-UX system calls and libraries that are not present in linux.
Your code may not be using any of those.
The port will be easier if the original developer tried to make it portable, or didn't know HP-UX _too_ well. ;-)

System and fork will be no trouble at all.
You might have more trouble matching the commands that the program starts with 'system'.
You may also have more fundamental code portability issues.
The C code may assume a big-endian memory arrangement.
It probably is not 64-bit clean, but you can use a 32-bit linux.

The distro selection is heavily influenced by what kind of support you want to have.
If you want professional support then you could look to support by HP (on redhat or novell or debian) or RedHat or Novell or Canonical.
If you want to just go with community support then your options of distro are _much_ broader.

---

### Post by ksunix on 2008-02-06
Thanks for the reply guys! I'll look into it for more info.

Best,
Ke

---

