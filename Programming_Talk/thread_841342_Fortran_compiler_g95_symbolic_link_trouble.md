---
title: "Fortran compiler g95 symbolic link trouble"
date: 2008-06-26
forum: Programming Talk
---

### Post by lordhaworth on 2008-06-26
Hey all
This should hopefully be a quick one. 
Ive installed a fortran compiler 'g95' but i need to set a symbolic link before i start programming i.e. 

lordhaworth@the-fort:~$ ln -s /home/lordhaworth/Documents/g95/g95-install/bin/i686-suse-linux-gnu-g95 /bin/g95

however the above command gives me the following error message:

ln: creating symbolic link `/bin/g95': Permission denied


does anyone know how i can resolve this? 


Cheers

---

### Post by WW on 2008-06-26
By default, regular users do not have permission to copy files to /bin.  To do this, use **sudo** in front of the ln command.  By the way, it would be more appropriate to put the link in **/usr/bin** (or even better, **/usr/local/bin**) rather than **/bin**.

I also have to ask: why are you installing this version of fortran?  Does gfortran (provided by the Ubuntu package [gfortran](http://packages.ubuntu.com/hardy/gfortran)) not meet your needs?

---

### Post by lordhaworth on 2008-06-26
Hey thanks for the help im new to ubuntu and missed the sudo!
I m going to be working on code as part of a larger program which I believe (although not certain) is in g95--->would there be any compatability issues with using gfortran? If not then that may be the better option

Cheers

---

### Post by WW on 2008-06-26
From the **gfortran** package description (see the link I gave above):
> 
This is the GNU Fortran 95 compiler, which compiles Fortran 95 on platforms supported by the gcc compiler.

Looks like that is what you want.  There is no harm in trying it; you can have both gfortran and g95 installed.  As long as your program sticks to standard Fortran 95, both compilers should work.

---

