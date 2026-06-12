---
title: "libdb.so.2 on Hardy 64bit"
date: 2008-06-12
forum: New to Ubuntu
---

### Post by julesverhoeven on 2008-06-12
Environment : 64bit Ubuntu Hardy server with no desktop
Some oracle soft need use libdb.so.2
I found that the libdb1-compat should install this.
But is does not.
I also read somewhere that it could be a 64 bit problem?

I tryed also to install by installing a gnome-libs-1.4.2-9.fc8.src.rpm with alien

Also this does not work.

Can anybody help me with this problem.

Thanks a lot !

---

### Post by Bachstelze on 2008-06-12
> **julesverhoeven said:**
> E
Some oracle soft need use libdb.so.2
I found that the libdb1-compat should install this.
But is does not.


It does indeed. What makes you think it does not?

---

### Post by Cappy on 2008-06-12
You probably need the 32-bit library, download and install getlibs:
[http://ubuntuforums.org/showthread.php?t=474790](http://ubuntuforums.org/showthread.php?t=474790)
and run
```
sudo getlibs -p libdb1-compat
```
or
```
sudo getlibs /path/to/your/program
```
if it is missing more libraries than just that.

---

### Post by julesverhoeven on 2008-06-12
Hi Cappy,

Thanks a lot for this wonderful solution.
After 18 hours of searching, I maybe don't need to switch over to another OS.

Many many thanks =D>=D>=D>=D>=D>

---

### Post by pshashanka on 2010-06-03
Thanks a lot. It helped me complete installation of Oracle SOA suite 10g on Lucid.

---

