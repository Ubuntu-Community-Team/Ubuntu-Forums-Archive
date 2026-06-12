---
title: "ld: cannot find crt1.o"
date: 2012-05-20
forum: Programming Talk
---

### Post by csurocket on 2012-05-20
I'm using make to install a software, but encounter an error.
   
g77 mdx.o  graphx_mdx.o rdf_reader_subs.o -o mdx 
/usr/bin/ld: cannot find crt1.o: No such file or directory
/usr/bin/ld: cannot find crti.o: No such file or directory
/usr/bin/ld: cannot find -lgcc_s
collect2: ld returned 1 exit status
make: *** [mdx] Error 1

I have installed  g77,gcc, g++, gfortran  g++-multbuild  gcc-essential  libc6-dev
I don't know if it's because some error in the path, like the virable FFLAGS. I'm don't know how to set them. 

Thanks

---

### Post by Heyayun on 2012-06-09
i have the same problem:

$ g77 helloworld.f -o helloworld
/usr/bin/ld: cannot find crt1.o: No such file or directory
/usr/bin/ld: cannot find crti.o: No such file or directory
/usr/bin/ld: cannot find -lgcc_s
collect2: ld returned 1 exit status

i am using Kubuntu 11.10 32bit with gcc 4.6.1. I installed gcc 3.4.6 by adding the sourses:
deb [http://hu.archive.Ubuntu.com/ubuntu/](http://hu.archive.Ubuntu.com/ubuntu/) hardy universe  
deb [http://hu.archive.Ubuntu.com/ubuntu/](http://hu.archive.Ubuntu.com/ubuntu/) hardy-updates universe 

Anyone helps?

---

### Post by roelforg on 2012-06-10
```

sudo apt-get install build-essential

```
Will install the packages that are missing.

---

### Post by Heyayun on 2012-06-11
> **roelforg said:**
> ```

sudo apt-get install build-essential

```
Will install the packages that are missing.

I have installed the build-essential, and now it is already the newest version.

---

### Post by roelforg on 2012-06-11
> **Heyayun said:**
> I have installed the build-essential, and now it is already the newest version.
 
Did it work?

---

### Post by jabl on 2012-06-11
Try using gfortran instead of g77; using g77 is only going to get more and more difficult as it's unmaintained and the rest of the toolchain keeps evolving.

---

### Post by Heyayun on 2012-06-11
> **roelforg said:**
> Did it work?

Sorry, i didn't describe it clearly. I mean i have installed build-essential before i installed g77. Now g77 echoes errors, but gfortran works well.
My teacher uses fortran 77, so i hope g77 could work well. Any help?

---

### Post by jabl on 2012-06-11
> **Heyayun said:**
>  Now g77 echoes errors, but gfortran works well.
My teacher uses fortran 77, so i hope g77 could work well. Any help?

GFortran supports Fortran 77 as well, thus limiting yourself to Fortran 77 (which I think is a very bad idea in general, but YMMV) does not prevent you from using GFortran to compile your code.

---

### Post by Heyayun on 2012-06-11
> **jabl said:**
> GFortran supports Fortran 77 as well, thus limiting yourself to Fortran 77 (which I think is a very bad idea in general, but YMMV) does not prevent you from using GFortran to compile your code.

I think gfortran is much more flexible than g77, maybe i should learn both.

---

