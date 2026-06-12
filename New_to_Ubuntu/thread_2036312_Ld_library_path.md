---
title: "Ld_library_path"
date: 2012-08-01
forum: New to Ubuntu
---

### Post by newport_j on 2012-08-01
I installed Ubuntu 11.10 as a virtual machine on Centos. Ubuntu is the guest and Centos 6.3 is the host. 
 
I tried some basic compile commands and it kept giving me the error message:
 
undefined reference to 'log10'
 
undefined reference to 'sqrt'
 
It obviously was not linking to the math libary during compile and link the stage. However, I was using the -lm command correctly and I discovered the when I entered 
 
echo $LD_LIBRARY_PATH
 
gave me nothing, so I must reinitialize my LD_LIBRARY_PATH to avoid the errors shown above.
 
I am not sure what library holds log10 and sqrt math functions. I believe that they are in the same library, I am just not sure which one.
 
Also, since I compile for 32 and 64 bit applications, I am sure the 32 and 64 bit libaraies are not the same. So my LD_LIBARY_PATH must accomodate both. 
 
Exactly, what libararies are needed? Can I run some command line comand and just build the LD_LIBRARY_PATH?
 
Thanks in advance.
 
Newport_j

---

### Post by alexpage on 2012-09-11
Are you sure this wasn't the problem?: [http://stackoverflow.com/questions/7824439/c-math-linker-problems-on-ubuntu-11-10](http://stackoverflow.com/questions/7824439/c-math-linker-problems-on-ubuntu-11-10)

---

