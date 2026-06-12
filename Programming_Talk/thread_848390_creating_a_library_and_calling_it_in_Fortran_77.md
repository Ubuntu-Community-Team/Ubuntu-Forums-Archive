---
title: "creating a library and calling it in Fortran 77"
date: 2008-07-03
forum: Programming Talk
---

### Post by gusanto on 2008-07-03
Hi all,
In my office, when I want to generate random number deviates, I just compile the program by calling the library. So I don't need to write the code in  the main program.
For example:
[COLOR="Red"]g77 test.f -lrando -o test[/COLOR]
to compile the program and call a library named rando.
I want to create a library for random number deviates (I have the code writen in f77, say [COLOR="Red"]rnd.f[/COLOR]). If I want to do the same thing like in my office, what should I do to make [COLOR="Red"]rnd.f[/COLOR] callable when I compile my main program that will use [COLOR="Red"]rnd.f[/COLOR].
I know the fortran language but never learn how to do such things such as creating library, etc. So please show me the way by giving me example.
Thanks.

Cheers,
gusanto

---

### Post by WW on 2008-07-19
You may have figured out how to do this by now, but just in case you (or someone else) is still interested, here is an example.  I will use g77, but gfortran would also work.

mylib.f
```

C
C     squareit(x)  returns x**2
C
      function squareit(x)
      implicit none
      real squareit
      real x

      squareit = x**2

      return
      end

C
C     cubeit(x)  returns x**3
C
      function cubeit(x)
      implicit none
      real cubeit
      real x
      
      cubeit = x**3

      return
      end

```

Here is one way to convert this into a library:
```

$ g77 -c mylib.f                     # Compile the code
$ ar -rcs libmylib.a mylib.o         # Create the archive containing the code
$ sudo cp libmylib.a /usr/local/lib  # Copy it to /usr/local/lib

```
Now you can link this library with the option **-lmylib**.
For example, here is a test program:

maintest.f
```


      program maintest
      implicit none
      real x,y,z
      real squareit
      real cubeit

      x = 12.0
      y = squareit(x)
      z = cubeit(x)
      print *, x, y, z
      stop
      end

```

These commands compile and run it:
```

$ g77 maintest.f -o maintest -lmylib
$ ./maintest 
  12.  144.  1728.
$ 

```

---

### Post by gusanto on 2008-07-23
That's what I want to know, thanks a lot. I'll try it.

---

### Post by gusanto on 2008-11-06
Hi WW,
I found many routines and functions from NETLIB website [http://www.netlib.org/random/]("http://www.netlib.org/random/") for generating some random numbers from different type of distribution from UNIFORM, NORMAL, POISSON, CHISQUARE, etc. I downloaded this file ranlib.f.tar.gz.
I want to make them available in my machine. I have read the README file but still have no idea how to do it.
Could you please show me step by step. (Attached is the README file)
Many thanks.

---

### Post by gusanto on 2008-11-06
Sory, I forgot the source file in the previous post. Please find the file in the attachment.

---

### Post by skorpio11 on 2010-07-03
Came across this thread in search of same solution... Anyone??

---

### Post by skorpio11 on 2010-07-03
Found this solution for creating library file from ranlib.f

Unpack ranlib.f.tar source.  Compile all to unlinked objective files. I am using gfortran so:

gfortran -c *.f
Next create archive of resulting .o files like so:

ar r ranlib.a *.o
Place in library path and link at compile with your program:

gfortran myFortran90.f90 -o myFortran90 ranlib.a
Should create myFortran90 executable

---

