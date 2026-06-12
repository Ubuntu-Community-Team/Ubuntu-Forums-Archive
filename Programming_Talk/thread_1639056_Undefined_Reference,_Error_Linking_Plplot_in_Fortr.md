---
title: "Undefined Reference, Error Linking Plplot in Fortran Program"
date: 2010-12-06
forum: Programming Talk
---

### Post by rmtatum on 2010-12-06
I tried to compile the following Fortran code found at 
[http://techlogbook.wordpress.com/2009/09/18/using-plplot-from-fortran-in-kubuntu-8-04/](http://techlogbook.wordpress.com/2009/09/18/using-plplot-from-fortran-in-kubuntu-8-04/)

```
program testplplot2d
use plplot
implicit none
real(plflt),dimension(6) :: x,y
real(plflt)::xmin,xmax,ymin,ymax
x=(/1,2,3,4,5,6/)
y=x**2
write(*,*) y
call plinit()
xmin=1.0
xmax=6.0
ymin=1.0
ymax=40.0
call plcol0(1)
call plenv(xmin,xmax,ymin,ymax,0,0)
call pllab('X','Y','Test 1D plot')
call plpoin(x,y,9)
call plline(x,y)
y=x**3
call plpoin(x,y,9)
call plline(x,y)
call plend()

end program testplplot2d
```

I used the following command in my attempt to compile the program:

```
gfortran -I/usr/lib/fortran/modules/plplot testplot2d.f90 -o testplot2d

```

However I received the a linking error message detailed below:

```
/tmp/cckSqEg4.o: In function `MAIN__':
testplot2d.f90:(.text+0x10c): undefined reference to `plinit_'
testplot2d.f90:(.text+0x154): undefined reference to `plcol0_'
testplot2d.f90:(.text+0x181): undefined reference to `plenv_'
testplot2d.f90:(.text+0x1a6): undefined reference to `__plplotp_MOD_pllab'
testplot2d.f90:(.text+0x248): undefined reference to `__plplot_MOD_plpoin'
testplot2d.f90:(.text+0x2e5): undefined reference to `__plplot_MOD_plline'
testplot2d.f90:(.text+0x3c6): undefined reference to `__plplot_MOD_plpoin'
testplot2d.f90:(.text+0x463): undefined reference to `__plplot_MOD_plline'
testplot2d.f90:(.text+0x46d): undefined reference to `plend_'
collect2: ld returned 1 exit status

```

---

### Post by dwhitney67 on 2010-12-06
Try sprinkling a -L and -l options in with your gfortran statement so that you can indicate where the "plplot" library resides, and also the library itself.

Personally I am not familiar with Fortran, much less with Plplot, but I believe you require something along the lines of:
```

gfortran -I/usr/lib/fortran/modules/plplot testplot2d.f90 -o testplot2d -L/usr/lib/fortran/modules/plplot -lplplot

```
Of course, insert the correct path and/or library name (sans the "lib" and file name extension).

Edit:  It seems that gfortran does not support the -l option; maybe it is not required?

---

### Post by rmtatum on 2010-12-06
Thanks for the suggestion dwhitney67.  gmargo's solution works.

---

### Post by gmargo on 2010-12-06
Install the **libplplot-dev** package and then compile with this command line:
```

gfortran testplot2d.f90 -o testplot2d $(pkg-config --cflags --libs plplotd-f95)

```

---

### Post by rmtatum on 2010-12-07
Thanks gmargo!  Your solution works.

---

### Post by dwhitney67 on 2010-12-07
> **rmtatum said:**
> Thanks gmargo!  Your solution works.

Out of curiosity, can you please post the results returned by running this command?
```

pkg-config --cflags --libs plplotd-f95

```

---

### Post by gmargo on 2010-12-07
On 64-bit 10.10 Maverick:
```

$ pkg-config --cflags --libs plplotd-f95
-I/usr/include/plplot -I/usr/lib/fortran/modules/plplot  -lplplotf95d -lplplotf95cd -lplplotd -lltdl -ldl -lm -lcsirocsa -lcsironn -lqhull -lqsastime -lfreetype  

```

---

### Post by dwhitney67 on 2010-12-08
> **rmtatum said:**
> Thanks for the effort but gfortran doesn't use the same linking options as gcc.
And it seems in the end, it does.  :p

---

