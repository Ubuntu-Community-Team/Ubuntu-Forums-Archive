---
title: "Problem with libgnomeui.so.32"
date: 2006-04-03
forum: Programming Talk
---

### Post by Lalit1008 on 2006-04-03
Dear Freinds,

I am new to ubuntu. I installed Ubuntu 5.10 from ubuntu-5.10-install-i386.iso. I am trying to run an application on this and getting an error message ' Shared library libgnomeui.so.32 not found'


Please help me out. Its a little bit urgent.


Thanks in advance.

Regards,

Lalit

---

### Post by hod139 on 2006-04-03
```

sudo apt-get install libgnomeui32

```
should fix the problem.

What package are you trying to run, this is an old lib.

---

### Post by Lalit1008 on 2006-04-03
[QUOTE=hod139]```

sudo apt-get install libgnomeui32

```
should fix the problem.

What package are you trying to run, this is an old lib.[/QUOTE]

I tried this but it giving me some error.
I have 1 application compiled on Redhat with Gnome 1.14. I recompiled it with GNOME 2.12 on Debian/Ubuntu but still the errror comes.

I think there is a bug with apt-get. How can i remove this and install older stable apt-get.

---

