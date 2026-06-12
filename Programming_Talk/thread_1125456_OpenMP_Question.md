---
title: "OpenMP Question"
date: 2009-04-14
forum: Programming Talk
---

### Post by par123 on 2009-04-14
Hi all,

I have a basic question on running OpenMP on core 2 duo architecture. I am learning parallel programming on real
64-core machine developed at university of maryland where
I can log into the machine and use power of 64-core machine.
The language we use to program this computer is variant of C.
Now I want to learn OpenMP so any one can suggest how should 
I start installing OpenMP on Ubuntu?

Thanks so much
parin

---

### Post by unutbu on 2009-04-14
For 64-bit machines, it appears the package you should install is lib64gomp1:
```

sudo apt-get install lib64gomp1
```

To find other packages related to openmp, type
```

apt-cache search openmp
```

---

### Post by slavik on 2009-04-14
i thought openmp was part of stock gcc since 4.2 or somewhere around that ...

---

### Post by jdrodrig on 2009-04-15
My experience with OpenMP is through Fortran. I learned the basics of OpenMP using SunStudio 12 (free for Linux). It is easy to install in Ubuntu (just unpack the software).

It might be a stupid question; but do you mean you want to learn how to use the OpenMP API through a compiler? or actually, getting into how the API works and interacts with the kernel, scheduler, etc?

---

### Post by rplantz on 2009-04-16
I have libgomp1 installed on my machine (running 64-bit), and I use the -fopenmp switch.

Make sure to run System Monitor. It's cool watching both cores run. I played around with one of my instructor's examples so that one core ran about twice as long as the other, which is easy to see in System Monitor.

---

### Post by monkeyking on 2009-04-16
> **par123 said:**
> Hi all,

I have a basic question on running OpenMP on core 2 duo architecture. I am learning parallel programming on real
64-core machine developed at university of maryland where
I can log into the machine and use power of 64-core machine.
The language we use to program this computer is variant of C.
Now I want to learn OpenMP so any one can suggest how should 
I start installing OpenMP on Ubuntu?

Thanks so much
parin

What variant is this c? Just out of curiosity

---

