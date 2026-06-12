---
title: "f77 compiling error"
date: 2006-11-11
forum: Programming Talk
---

### Post by dopewalker on 2006-11-11
i'm having a problem with my f77 compiler. everytime i run the command
f77 -o hrs hrsdeg-sci.f
i get the following error:

/usr/bin/ld: crt1.o: No such file: No such file or directory
collect2: ld returned 1 exit status

i know this means i have an error in my input file from my open statement, but these are my statements:

      open(1,file='SCI.dat',status='old')
      open(8,file='SCI.test.dat',status='new')

I have no idea what could be causing this problem but I'm sure it's trivial. Please let me know! I have below my program, but the spacing you see between the numbers and lines is probably different from what it is... i believe the spacing is correct:

      program hrsdg1
      implicit real(a-h,o-z)
      character*13 name1
      character*1 JSIGN

 50   format(a14,3x,f8.4,2x,f8.4,2x,i3)
 51   format(a17,2(i2),f4.1,1x,a1,3(i2),20x,i3)

      open(1,file='SCI.dat',status='old')
      open(8,file='SCI.test.dat',status='new')

 10   read(1,51,end=99) name1, Irah, Iram, ras, jsign, Idecd, Idecm, 
     &   Idecs, w
      rat=RAF(Irah, Iram, ras, Idecd, Idecm, Idecs)
      dect=DECF(Irah, Iram, ras, Idecd, Idecm, Idecs)
C      print *, agc, name, Irah, Idecd, vhel
      if (jsign.eq.'-') dect=-dect
      write(8,50) name1, rat, dect, w
      goto 10
 99   close(1)
      close(8)
      end

      FUNCTION RAF(IHOUR,IMIN,SEC,IDEG,IARCMN,IARCSC)

      implicit real(a-h,o-z)
      dM=2.2354759*10**(-4)
      dN=9.7156662*10**(-5)
      rh=IHOUR*15.0+IMIN*0.25+(SEC*0.25)/60.0
      dd=IDEG*1.0+IARCMN/60.+IARCSC/3600.
      RArad=rh/57.29577951
      DECrad=dd/57.29577951
      dRA=dM+dN*sin(RArad)*tan(DECrad)
      RAF=57.29577951*(RArad+dRA)*50
      return
      end

      FUNCTION DECF(IHOUR,IMIN,SEC,IDEG,IARCMN,IARCSC)

      implicit real(a-h,o-z)
      dM=2.2354759*10**(-4)
      dN=9.7156662*10**(-5)
      rh=IHOUR*15.0+IMIN*0.25+(SEC*0.25)/60.0
      dd=IDEG*1.0+IARCMN/60.+IARCSC/3600.
      RArad=rh/57.29577951
      DECrad=dd/57.29577951
      dRA=dM+dN*sin(RArad)*tan(DECrad)
      dDEC=dN*cos(RArad)
      DECF=57.29577951*(DECrad+dDEC)*50
      return
      end

---

### Post by jpkotta on 2006-11-11
I don't know much about fortran, but I do know this:
```
[jpkotta@euler w](0)$ locate crt1.o
/usr/lib/crt1.o
/usr/lib/gcrt1.o
/usr/lib/Mcrt1.o
/usr/lib/Scrt1.o
```

```
[jpkotta@euler w](0)$ dpkg -S crt1.o
libc6-dev: /usr/lib/Scrt1.o
libc6-dev: /usr/lib/Mcrt1.o
libc6-dev: /usr/lib/gcrt1.o
libc6-dev: /usr/lib/crt1.o
```

So probably all you have to do is get libc6-dev, and possibly point the compiler to the file by hand.

---

### Post by junglepeanut on 2006-11-12
I have not had this issue on my linux laptop...

but I know exactly what that has to do with for Intel Fortran Compiler on Mac OS X

Apparently the compiler expects there to be a libcrt0 and a subroutine crt0.o

Ooh I just realized it is crt0 for Mac OS X, although ithis is off my head it may have been crt1 in both cases. If this doesn't work and you need me to ........

never mind I am going to ssh into the server figure out the name of the files exactly and comment back. I will even post the exact code I wrote for each dummy file.

brb

---

### Post by junglepeanut on 2006-11-12
Power must be off on campus as I can't log on and that would be the only reason unless the server crashed...not likely for the later.

OK in libcrt0 maybe libcrt0.so 

I wrote 
```

bbb

```

in crt0.f90 I wrote (and compiled with my first makefile then left it in place where it is always in the path for different programs)

```

Subroutine Sosillytohavetodothis
End Subroutine Sosillytohavetodothis

```

I would double check that those files for yourself dont actually have something in them before you change them if you have them, if you don't have them, just put them in the same place as wherever you compile or in a nice place where they won't be missed.

Note this was a fix for Intel Fortran on Mac OS X. I suspect it is somewhat along the same lines if you have installed all of the development files and have everything else this would be the next resort. 

If this is not working post again I will try the server again in the morning to see if I wrote anything else in the files.

---

### Post by junglepeanut on 2006-11-12
Eww, looks like an astronomy program, jk.

---

