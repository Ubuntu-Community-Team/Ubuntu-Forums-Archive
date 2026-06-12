---
title: "[SOLVED] gcc on Xubuntu in fluxbox"
date: 2008-07-09
forum: New to Ubuntu
---

### Post by incen on 2008-07-09
I just installed Xubuntu on my old laptop. Since it only got 256-MB ram, I put fluxbox on it and right now am using Xubuntu with fluxbox.
I need gcc for compiling C code on this machine. However, I wrote a simple "Hello World" program but I got the error message while compiling:
```
test.c:1:19: error: stdio.h: No such file or directory
test.c: In function ‘main’:
test.c:4: warning: incompatible implicit declaration of built-in function ‘printf’
```

Why is stdio.h missing? And where should I get it?
Also, I did this to search for g++
```
sudo aptitude search g++
```
But then, plenty of unwanted packages show up. How should I correctly install g++ compiler?

Thanks in advance! :)

---

### Post by incen on 2008-07-09
Oh, I forgot to say...
And the problem is even weird that this is aptitude search,
```

p   colorgcc                                  - Colorizer for GCC warning/error messages            
iu  gcc                                       - The GNU C compiler                                  
p   gcc-3.3                                   - The GNU C compiler                                  
p   gcc-3.3-base                              - The GNU Compiler Collection (base package)          
p   gcc-3.3-doc                               - Documentation for the GNU compilers (gcc, gobjc, g++
p   gcc-3.4                                   - The GNU C compiler                                  
p   gcc-3.4-base                              - The GNU Compiler Collection (base package)          
p   gcc-3.4-doc                               - Documentation for the GNU compilers (gcc, gobjc, g++
p   gcc-4.1                                   - The GNU C compiler                                  
p   gcc-4.1-base                              - The GNU Compiler Collection (base package)          
p   gcc-4.1-doc                               - Documentation for the GNU compilers (gcc, gobjc, g++
p   gcc-4.1-locales                           - The GNU C compiler (native language support files)  
p   gcc-4.1-multilib                          - The GNU C compiler (multilib files)                 
p   gcc-4.1-source                            - Source of the GNU Compiler Collection               
i   gcc-4.2                                   - The GNU C compiler                                  
i   gcc-4.2-base                              - The GNU Compiler Collection (base package)          
p   gcc-4.2-doc                               - Documentation for the GNU compilers (gcc, gobjc, g++
p   gcc-4.2-locales                           - The GNU C compiler (native language support files)  
p   gcc-4.2-multilib                          - The GNU C compiler (multilib files)                 
p   gcc-4.2-source                            - Source of the GNU Compiler Collection               
p   gcc-avr                                   - The GNU C compiler (cross compiler for avr)         
p   gcc-doc                                   - Documentation for the GNU C compilers (gcc, gobjc, g
p   gcc-h8300-hms                             - The GNU C compiler (cross compiler for h8300-hitachi
p   gcc-m68hc1x                               - GNU C compiler for the Motorola 68HC11/12 processors
p   gcc-multilib                              - The GNU C compiler (multilib files)                 
p   gcc-snapshot                              - A SNAPSHOT of the GNU Compiler Collection           
p   gccxml                                    - XML output extension to GCC                         
p   lib64gcc1                                 - GCC support library (64bit)                         
p   lib64gcc1-dbg                             - GCC support library (debug symbols)                 
i   libgcc1                                   - GCC support library                                 
p   libgcc1-dbg                               - GCC support library (debug symbols)                 
p   pocketpc-gcc                              - The GNU C compiler for Pocket PC                    
p   ppu-gcc                                   - PPU C compiler                                      
p   spu-gcc                                   - SPU cross-compiler (preprocessor and C compiler) 

```

I think I already have gcc. Am I right? Do I need something else?
Last time when I installed Xubuntu, the gcc is all right. I don't know what the problem is now. :(

---

### Post by mali2297 on 2008-07-09
Have you installed [build-essential]("http://packages.ubuntu.com/hardy/build-essential")?
```

sudo apt-get install build-essential

```

(It will install libc6-dev which contains the missing header file.)

---

### Post by incen on 2008-07-09
Yes, thanks! Now I can use both gcc and g++! ^^

---

