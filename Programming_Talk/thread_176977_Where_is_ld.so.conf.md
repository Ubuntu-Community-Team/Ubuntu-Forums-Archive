---
title: "Where is ld.so.conf"
date: 2006-05-15
forum: Programming Talk
---

### Post by sparklehorse on 2006-05-15
Hi all,

I've just installed Ubuntu 5.10 (previously used Debian and then Gentoo). I can't seem to find what was /etc/ld.so.conf on my previous Linux systems. I'd like to do some programming and I need /usr/local/lib in my library path.

Thanks in advance for the help!

Matthias

---

### Post by moterpent on 2006-05-15
Someone can correct me if I'm wrong here but I think you can safely create and add whatever you need to /etc/ld.so.conf.  By default, ldconfig includes /lib and /usr/lib when run even if they aren't specified on the command line or in /etc/ld.so.conf.

Because Ubuntu packages put everything in either /lib or /usr/lib I suppose it doesn't, by default, need a /etc/ld.so.conf.  Or at least that's how it looks.  Maybe someone else has a better explanation.

---

### Post by hod139 on 2006-05-15
I ran into the same problem and simply created the file myself and added "/usr/local/lib" as the only line without any problems.  I also wondered why that file didn't exist?

---

### Post by sparklehorse on 2006-05-16
[QUOTE=hod139]I ran into the same problem and simply created the file myself and added "/usr/local/lib" as the only line without any problems.  I also wondered why that file didn't exist?[/QUOTE]

Hi all,

creating the file did it for me too, thanks! I thought that maybe it was someplace else instead of just ... well... missing.

---

