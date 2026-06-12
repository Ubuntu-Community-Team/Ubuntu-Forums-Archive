---
title: "Shared libraries and external Kernel Modules"
date: 2009-10-23
forum: Packaging and Compiling Programs
---

### Post by vanhorng on 2009-10-23
All -
 
I have a program that i would like to make into an external kernel module, however, it uses about 4 or 5 shared libraries that I also wrote.   Normally, to run the program I have my LD_LIBRARY_PATH set accordingly in my .bashrc and just launch the main application.   
 
My question is if i make the main application into an external kernel module and then run insmod... what is the best way to still have access to the shared libraries?  Should i just copy them to /usr/lib?  Or, is there some way to include them in the kernel module?   
 
I am somewhat new to this making of kernel modules.    Any suggestions would be appreciated.  
 
Regards,
Gerry

---

