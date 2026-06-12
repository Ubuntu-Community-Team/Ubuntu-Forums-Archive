---
title: "Dynamic librairies linking"
date: 2012-02-09
forum: Programming Talk
---

### Post by mogeb on 2012-02-09
Hi,
I would like to know against wich librairies a running program is linking. Is it looking for the file /proc/THEPID/maps?
The thing is that I have two shared librairies of the same name, one that is in /usr/lib/ure/lib and the other one in /opt/libreoffice3.4/ure/lib. While having the same name, the librairies are different. If I delete the file in /usr/lib/ure/lib, my program works fine. But when I restore it, it stops working.

Thanks

---

### Post by SevenMachines on 2012-02-09
Use ldd
```
$  ldd /usr/bin/hello
    linux-vdso.so.1 (0x00007fff486f5000)
    libc.so.6 => /lib/x86_64-linux-gnu/libc.so.6 (0x00007f70abfe6000)
    /lib64/ld-linux-x86-64.so.2 (0x00007f70ac3d6000)
```Note you can alter the ld search path by adding a LD_LIBRARY_PATH environment variable, for example, note the difference in the following

```

$ ldd /usr/bin/hello
    linux-vdso.so.1 (0x00007fff239ff000)
    libc.so.6 => /lib/x86_64-linux-gnu/libc.so.6 (0x00007fe3dd809000)
    /lib64/ld-linux-x86-64.so.2 (0x00007fe3ddbf9000)
$ sudo cp /lib/x86_64-linux-gnu/libc.so.6  /opt/
$ LD_LIBRARY_PATH=/opt ldd /usr/bin/hello
    linux-vdso.so.1 (0x00007fff2c3ff000)
    libc.so.6 => /opt/libc.so.6 (0x00007fcc63a5b000)
    /lib64/ld-linux-x86-64.so.2 (0x00007fcc63e18000)

```

---

### Post by mogeb on 2012-02-09
Thank you for your reply. I already tried LD_LIBRARY_PATH but it didn't work. 
And ldd doesn't show the librairies at run-time therefore it wouldn't help me.

---

### Post by MadCow108 on 2012-02-09
you can run the program with ltrace -e dlopen to get runtime loaded libraries.

---

### Post by mogeb on 2012-02-10
> **MadCow108 said:**
> you can run the program with ltrace -e dlopen to get runtime loaded libraries.

I tried it but it doesn't work..

---

### Post by nvteighen on 2012-02-10
> **mogeb said:**
> I tried it but it doesn't work..

Send us whatever appears on your terminal when doing this. If you only tell us "it doesn't work" without providing more information, it's very difficult for us to help you.

---

