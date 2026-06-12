---
title: "Code works on 32 bit, crashes on 64 -- glibc related."
date: 2010-08-14
forum: Programming Talk
---

### Post by formaldehyde_spoon on 2010-08-14
I'm using a library for grammatical evolution called libGE for a project at uni.
 I've compiled the library and run one of it's example programs on my 32 bit netbook just fine, but the same program crashes every time I try to run it on my 64 bit desktop.

  At random places during processing it will crash with a message similar to (but never exactly the same as) one of the following three examples :

  *** glibc detected *** ./GEGCC: munmap_chunk(): invalid pointer: 0x00000000013444c0 ***

  *** glibc detected *** ./GEGCC: free(): invalid size: 0x0000000001d864c0 ***

  *** glibc detected *** ./GEGCC: corrupted double-linked list: 0x0000000001487800 ***

  The addresses and function names/reasons are always different.  

I've also had just a plain old seg fault, without any other info (but only once, it's usually as above).  

It does helpfully give a memory dump and stack trace, but as the error is always different, and the code is fine on a 32 bit machine I haven't looked at them much.  

I found I had the 32 bit gnu c library installed, so replaced it with the 64 bit version, but that made no difference.  
I tried compiling and running with ''linux32 -B -3 '' as a prefix to the compiler and the program itself, but that didn't help either (no apparent change).  

Why this is happening, and what I can do about it? 
To be honest, I don't understand what is going on at all....

---

### Post by Bachstelze on 2010-08-14
The code is probably doing some stupid things. Where can we get it?

---

### Post by MadCow108 on 2010-08-14
run the program in valgrind to get better information.
it is corrupting the memory at some point and later crashes due to that.

valgrind should be able to give you exact error locations

---

### Post by formaldehyde_spoon on 2010-08-15
Thanks for the replies guys. 

The libGE code is here: [http://amnesia.csisdmz.ul.ie/GE/GrEvo/libGE-0.27.4.tar.gz](http://amnesia.csisdmz.ul.ie/GE/GrEvo/libGE-0.27.4.tar.gz) 
$ ./configure
$ make
$ make install
 
The example program also needs galib to be installed: [http://lancet.mit.edu/ga/dist/galib247.tgz](http://lancet.mit.edu/ga/dist/galib247.tgz)
 $ make
$ make test
$ make install

 then in libGE-0.27.4/EXAMPLES/SantaFeAntTrail/GE_MITGALIB
$ make GEGCC
$ ./GEGCC

 So the problem is not related to glibc then?  
Is there a way to force the compiling and running of GEGCC to be done in 32 bit only (like I tried to do with linux32)?

---

### Post by MadCow108 on 2010-08-15
> **formaldehyde_spoon said:**
> 
 So the problem is not related to glibc then? 

yes
these errors come from user code in 99.9999999999999% of cases.
they appear to come from glib because your program corrupts memory which glib uses internally

> 
Is there a way to force the compiling and running of GEGCC to be done in 32 bit only (like I tried to do with linux32)?

add the flag -m32

./configure CFLAGS='-m32' CXXFLAGS='-m32'
it can also be done in the make step

but you need 32 bit libraries to link with: 
sudo apt-get install ia32-libs gcc-multilib g++-multilib

---

### Post by formaldehyde_spoon on 2010-08-15
> **MadCow108 said:**
>  
add the flag -m32

./configure CFLAGS='-m32' CXXFLAGS='-m32'
it can also be done in the make step

but you need 32 bit libraries to link with: 
sudo apt-get install ia32-libs gcc-multilib g++-multilib

 Thanks MadCow, got it! 
Installed those packages, recompiled libge and galib with -m32, inserted -m32 into one of the source files that had a ''system(gcc ....)'' call, recompiled the example program with -m32, and it worked.

Cheers :D

---

