---
title: "Fortran 77 question"
date: 2009-12-09
forum: Programming Talk
---

### Post by DanSandbergUCONN on 2009-12-09
I apologize for this semi-unrelated question.  I added this code to a program:

        call getarg(1, filename)

to read the first command line argument into the character*200 variable.  Here is what the compiler spit back:

Undefined symbols:
  "_GETARG", referenced from:
      _MAIN__ in mndoci50_v4.7.o
ld: symbol(s) not found
collect2: ld returned 1 exit status
link failed.


Does anyone know what is going on here?  The manual I'm following (I really don't know fortran like I know other languages) says that getarg is an available subroutine for reading command line arguments.

---

### Post by DanSandbergUCONN on 2009-12-09
Note getarg is orange, indicating it is recognized by AbsoftEditor.  I compiled with command line:

f90 -s -w -W132 -C MYFILE.f -lV77

---

### Post by DanSandbergUCONN on 2009-12-10
Thanks to anyone who looked at this thread.  I'm sorry to post about fortran 77 in this ubuntu forum.  I don't really know what ubuntu is but it comes up when I google fortran forum. :D Hopefully maybe someone knows how to rectify my problem?  Thanks

---

### Post by DanSandbergUCONN on 2009-12-11
bump for any feedback - please!!

---

### Post by cholericfun on 2009-12-11
hi
should move this to "programming talk"
fortran questions are not too exotic there

i honestly have no idea about calling external functions.
did you try compiling with f77 though?

maybe some more parts of the program to read will help people help you

btw. i'd have used the "read*" command to read a command line string.
maybe that can be used?

---

### Post by Claus7 on 2009-12-11
Hello,

I have to say that I did not understand your problem very well:

1)what is f90 command? Which type of fortran are you using? I have not heard a compiler with the name f90. I would advice you to use gfortran  compilers. Also I would advice you to abandon fortran 77 and focus on fortran 90 onwards.

2)from where you want to read and what do you want to read exactly?

3)I have never run across getarg before...

It would not be a bad idea to see your entire code. Maybe me or someone else could give you some more insight on the issue.

Regards!

---

### Post by lavinog on 2009-12-11
> **Claus7 said:**
> 
1)what is f90 command? Which type of fortran are you using? I have not heard a compiler with the name f90. I would advice you to use gfortran  compilers. Also I would advice you to abandon fortran 77 and focus on fortran 90 onwards.

It looks like the OP is using windows.

They also might be required to maintain f77 compatibility.

to OP:
See if it works in linux.
Download a live cd.
open a terminal and type
```

sudo apt-get install gfortran

```

---

### Post by raineater on 2009-12-12
> **DanSandbergUCONN said:**
> I apologize for this semi-unrelated question.  I added this code to a program:

        call getarg(1, filename)

to read the first command line argument into the character*200 variable.  Here is what the compiler spit back:

Undefined symbols:
  "_GETARG", referenced from:
      _MAIN__ in mndoci50_v4.7.o
ld: symbol(s) not found
collect2: ld returned 1 exit status
link failed.


Does anyone know what is going on here?  The manual I'm following (I really don't know fortran like I know other languages) says that getarg is an available subroutine for reading command line arguments.
==
The diagnostic ending with:
ld: symbols not found

... is from the loader complaining that "GETARG" can't be found.  What does the manual for getarg() say about which libraries to use when compiling/linking/loading?

Haven't used fortan in decades; I used to hack a vector processor and C was/is much better ;)

---

### Post by Nubicles on 2010-04-21
I hit a similar problem today using the Sun Studio 12 compiler on a sparc machine.  I was linking a Fortran program with some C code, so I used the "-ext_names=plain" flag.  Unfortunately this messed up calls to the getarg and iargc intrinsic routines.  Adding underscores solved my problem (getarg_ and iargc_).  Perhaps there's a better way.

---

