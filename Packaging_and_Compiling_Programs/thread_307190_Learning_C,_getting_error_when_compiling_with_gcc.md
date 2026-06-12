---
title: "Learning C, getting error when compiling with gcc"
date: 2006-11-26
forum: Packaging and Compiling Programs
---

### Post by oliviacond on 2006-11-26
I have installed gcc from synaptic.
This is the error :
> 
:~/prog/c/learn$ gcc code.c -o code
code.c:1:19: error: stdio.h: No such file or directory
code.c: In function 'main':
code.c:5: warning: incompatible implicit declaration of built-in function 'printf' 


---

### Post by meng on 2006-11-26
Try
sudo aptitude install build-essential

then recompile.

I'm no C expert, but the first line of the error code says that gcc can't find the header file (stdio.h) that you want to include. printf is a function of that header file, so the 2nd and 3rd lines follow logically, so to speak.

Hopefully the installation of build-essential will solve the problem.

---

### Post by srix on 2006-11-26
Looks like the development packages are not installed - you probably need libc6-dev, at the very least.

---

### Post by oliviacond on 2006-11-26
problem solved. :)

---

### Post by Ian0107 on 2006-11-28
I  encountered the same problem, but I couldn't install the so called "build-essential".who can tell me why?
$ sudo apt-get install build-essential
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package build-essential

---

### Post by hod139 on 2006-11-29
What if you do an update first?
```
sudo apt-get update
```

---

### Post by az on 2006-11-29
> **Ian0107 said:**
> I  encountered the same problem, but I couldn't install the so called "build-essential".who can tell me why?
$ sudo apt-get install build-essential
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package build-essential

If you are not connected to the internet, you need to get the packages from the install cd - they are there, seperate from the live session.  Just pop the cd into the drive once you have booted into Ubuntu and the packaga manager will come up.  Install build-essential then.

---

