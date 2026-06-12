---
title: "C++ binary wont run on server if not compiled there"
date: 2010-08-15
forum: Programming Talk
---

### Post by Zilioum on 2010-08-15
Hi,

I'm currently writing a little program in c++, that should convert some stuff for me. The app should run on my server, but I'm currently writing it on my desktop pc with eclipse. On my pc, I can execute the binary that eclipse creates by typing ```
./Converter
```
If I copy the file to my server now and type the same thing I get:
```
-bash: ./Converter: cannot execute binary file

```
But if I copy the .cpp files to the server and compile them there, I can start the problem without trouble using ```
./Converter
```
Why's that and what do I have to do, so that the binary compiled on my pc works on my server?
(My server also runs on Ubuntu).

Cheers

---

### Post by MadCow108 on 2010-08-15
was the file compiled with platform specific flags? (e.g. -mtune -m32 -march -msse etc .)

do the cpu's work with the same number of bits?(32/64bit)

to fix either do a generic compile (-march=generic -m32) or compile with gcc -v on the server and compile with the same flags on your local pc
of course in the latter case it may not work on your local pc

---

### Post by Zilioum on 2010-08-15
Thank you for your quick answer!

> **MadCow108 said:**
> was the file compiled with platform specific flags? (e.g. -mtune -m32 -march -msse etc .)

I dont know about eclipse, I just used the "build" command. I have no idea if it does set some flags. On the server I used g++ and didnt set any flags.
> 
do the cpu's work with the same number of bits?(32/64bit)

No, my server is 32bit and my pc is 64bit

> to fix either do a generic compile (-march=generic -m32) 
How would I do that with eclipse?


Cheers

---

### Post by MadCow108 on 2010-08-15
> **Zilioum said:**
> 
No, my server is 32bit and my pc is 64bit

Here's the problem.
gcc by default compiles files for the wordwidth of the local machine.
So you compile 64 bit executables on your pc, which do not work on an 32 bit system.

You have to explicitly compile 32 bit executables with the -m32 flag (I do not know how to get eclipse to do thats)
you may also need to install 32 bit libraries on your 64 bit system:
sudo apt-get install ia32-libs gcc-multilib g++-multilib

---

### Post by Zilioum on 2010-08-15
Yeah, of course, that makes sense. Will try that out.
Thanks a lot for your help!

Cheers

---

