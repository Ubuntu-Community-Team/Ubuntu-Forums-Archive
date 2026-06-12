---
title: "Please, help with Fortran 77/90"
date: 2006-07-05
forum: Packaging and Compiling Programs
---

### Post by fossilsking on 2006-07-05
Hi guys, I'm quite new in programming and I need to compile and install one program for doing some theoretical calculations. I have installed the Fortran 77 from aptitute (g77-3.4 3.4.4-6ubuntu8.1). The source of the program I have is a "filename_f77.f" (or filename_f90.f). When I try to run f77 -o filename filename_f77.f (g77 -o filename filename_f77.f ) I get the following error:

bash: f77: command not found or
bash: g77: command not found

Please, let me know how to solve this problem. Many thanks in advance. Cheers, Emil

---

### Post by aev on 2006-07-11
I have my fortran g77/f77 installed through Synaptic - search "fortran" . If you search "f77" most probably won't find it.

Install the package - g77 4.3.4.6-1

Most probably this will fix the problem:-k . Also, you may want to install "ddd" - Data Display Debugger. Cool for debuging when compiling with the -g option.

---

### Post by xtacocorex on 2006-07-22
The FORTRAN 90 compilers are in a package gfortran.

You could always get the Intel FORTRAN compilers for Linux. They are free for non-commercial use. There are a couple of How-To's to get the rpm's to convert to .deb files.

I have an older version and I find it far superior to the GNU FORTRAN compilers.

---

### Post by fossilsking on 2006-08-03
Many thanks for the suggestions. The installation of the compiler was OK. It just does not want to start. I used the same procedure to install it on my desktop machine and then everything ran flawless. On my laptop, it seems to me that after the installation it is not in the bash, for some reason.

---

### Post by sfp100 on 2010-05-25
I had compile FORTRAN 77 code (barotropic model) with command
```
gfortran -o baro baro.for
```and it works.
I'm not sure if it will work with all F77 codes or not, but in my case was good.
May be some special features can broke this simple method (now I have problem with code written with features from Fortran 90 ANSI/ISO and warnings from gfortran, but it's other story), but in several cases should work.

---

