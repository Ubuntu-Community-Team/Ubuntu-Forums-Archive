---
title: "Fortran77 on ubuntu for scientific computing"
date: 2007-01-10
forum: Programming Talk
---

### Post by euler_fan on 2007-01-10
The only version of the software he has had any success with to do the kinds of work we want to do is several releases old and mostly written in fortran77. The rest is written in C. The plan is to go into the source, modify it, build our version, and compare it to the vanilla version.

We have a unix desktop in the lab with fortran77 capability, but don't want to be tied to it while we work on the project (we intend to use it mostly for large runs and it is shared with other projects in the department).

I looked at the gcc, but their site says they no longer are supporting g77 or including it in the gcc, and I couldn't get a definate picture of whether or not the current fortran support in the gcc is back compatable (I somehow doubt it). Maybe I missed it in the documentation, but can't be sure.

I was also thinking about just going and getting the most recent version of g77 I could and installing it on my machine (running edgy). Not sure how that would affect building the ARPS software on my machine.

Any advice about how to (1) ensure I can make and install software written in f77 or (2) get that capability would be greatly appreciated. I am running edgy and my advisor runs either openSUSE or Fedora Core depending on his mood that day.

It would be running on  a Compaq v5000 with an AMD turion64 ml-40 with 512 RAM.

Thanks in advance,

Euler_fan

---

### Post by xtacocorex on 2007-01-11
Intel has a non-supported FORTRAN 90 compiler that will compile F77 files. You have to register on their site though, but it is a free download and use.

I've used the Intel FORTRAN compiler to compile PMARC-12 (3D Potential Flow Code), which is written in F77 and everything runs fine. I have .deb's I made for Breezy that work on Dapper, but haven't put them on my Edgy VM yet, but I'm sure the ones I made might work.

Here is the thread link: [http://ubuntuforums.org/showthread.php?t=89571](http://ubuntuforums.org/showthread.php?t=89571)
Chickenmonger and I both attended the same university, so I know him personally.

---

### Post by euler_fan on 2007-01-11
Thanks! I think I should have said I am running an AMD 64. I put the tech specs up as the last line in my first post. I looked at the Intel website and it says they support Intel 32- & 64-bit, (of course) but as much as I'm willing to try it, have you (or anyone else for that matter) had success with that compiler working on a non-Intel platform? 

Thanks again,

Euler_fan

---

### Post by xtacocorex on 2007-01-11
I've only ever had Intel machines, so I haven't tested it on AMD, sorry. The gfortran compiler under gcc should work with F77 files and I know that is current and should support non-Intel processors.

---

### Post by euler_fan on 2007-01-11
Well, I think I have gfortran installed, and will go ahead and try to compile and install the software in question and see what happens. I'll post whatever I do and get.

Thanks again,

Euler_fan

---

### Post by junglepeanut on 2007-01-11
gFortran and G95 should compile it, but give warnings if anything from it is obsolete. Intel's as well.

---

### Post by euler_fan on 2007-01-14
Sorry for not getting back here for so long. Thanks so much for the help. It is really appreciated.

Thanks again,

Euler_fan

---

