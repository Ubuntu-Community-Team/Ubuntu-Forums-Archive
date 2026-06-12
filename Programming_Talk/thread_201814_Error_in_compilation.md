---
title: "Error in compilation"
date: 2006-06-22
forum: Programming Talk
---

### Post by cardogar on 2006-06-22
Hi,

I'm trying to compile a program in my breezy but the compilation crashes when the linking process is starting:

carlos@meteoro:~/ECARE/SimEarthCARE/src$ make plot_3d
ifort -assume nobscc -g -O0 -traceback -fpe0 -CB plot_3d.o col_plot_label.o pgxtal.o  -lifport /home/carlos/ECARE/Pgplot/work/libpgplot.a -L/usr/lib/gcc-lib/i386-linux/2.95.4/ -lgcc -lm -lc -lg2c -L /usr/X11R6/lib/  -o ../bin/plot_3d -lX11
ld: cannot find -lgcc
make: *** [plot_3d] Error 1

I think that lgcc corresponds to the libgcc library, I've looked for in the package repository and I've found the libgcc1 library, but I have already the libgcc1 library installed, so I don't understand what is the problem...

Any idea?

Thanks in advance.

Cheers.

---

### Post by hod139 on 2006-06-22
have you installed the build-essential package?

---

### Post by cardogar on 2006-06-23
Yes I have it.

---

### Post by hod139 on 2006-06-23
Looking more closely at your error message, it seems you are trying to link against libgcc.  
```
-L/usr/lib/gcc-lib/i386-linux/2.95.4/ -lgcc
```

I would remove those lines from the Makefile and see what happens.

---

