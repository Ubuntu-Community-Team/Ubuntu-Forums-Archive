---
title: "GCC-4.0 Fortran error"
date: 2005-08-12
forum: Programming Talk
---

### Post by ubuntme on 2005-08-12
Hi Guys,

This is my first post here, and I have only been using ubuntu for a couple of days, and am very much new to linux so be easy on me....

Anyway, I am trying to compile and run some fortran90 programs, So I want to get gcc-4.0 working.

btw I am downloading Intel'f fortran compiler as we speak, but I would think that gcc should work.

I need it to work for fortran 90, but first a basic hello world program:

```
c
c   Hello, world.
c
      Program Hello

      implicit none
      logical DONE

      DO while (.NOT. DONE)
        write(*,10)
      END DO
   10 format('Hello, world.')
      END
``` 

This is how I am trying to compile:

matt@ubuntu:~$ gcc helloworld.f
gcc: installation problem, cannot exec `f771': No such file or directory
matt@ubuntu:~$ gcc -f77 helloworld.f
gcc: installation problem, cannot exec `f771': No such file or directory
matt@ubuntu:~$ gcc-4.0 helloworld.f
gcc-4.0: installation problem, cannot exec 'f951': No such file or directory

so f77 and f95 is not working for some reason....

Is there something obvious I am missing or need to do?  I am not sure how to play with things in ubuntu, I am just trying it on a new box, I am used to gentoo....

Thanks

---

### Post by mo_x on 2005-08-12
Looks like you don't have installed the fortran compilers. Use synaptic and search for g77 and g95.

---

### Post by ubuntme on 2005-08-16
Ah thanks,

I didn't think of that... :)

g77 works now, but gcc - x f77 doesn't still... oh well.

I can't find g95 on the other hand (I'm using fortran 90).  I have added extra repositories as per [http://ubuntuguide.org/#extrarepositories](http://ubuntuguide.org/#extrarepositories)

and I get:

matt@ubuntu:~$ sudo apt-get install g95
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package g95
matt@ubuntu:~$


any ideas?

thanks

---

### Post by gte258v on 2005-08-16
To get Fortran 95 support in gcc, I believe you need to install the package "gfortran" from the universe repositories.

-Eric

---

### Post by ubuntme on 2005-08-16
Ah, the package is called gfortran-4.0

thanks :)

Program won't run though :( I wonder if that is because it is fortran90.

Oh well, At least I have the compiler.  Thanks All.

---

