---
title: "Intel Fortran ifort installation problem"
date: 2011-12-05
forum: New to Ubuntu
---

### Post by iprasad on 2011-12-05
Hi,

I just downloaded and installed the Intel Compiler. I tried to run a program using the ifort compiler, but I got this message:

"Can't exec "ifort": No such file or directory at"

I think part of the problem lies in defining a path so programs can easily find the compiler, therefore, I used this after the installation: 

 gedit ~ /. bashrc
# compiler source / opt/intel/Compiler/bin/ifortvars.sh PATH = $ PATH: / opt/intel/Compiler/bin / export PATH # intel debugger fortran source / opt/intel/Compiler/bin/ia32/idbvars.sh PATH = $ PATH: / opt/intel/Compiler/bin/ia32 / export PATH
I am a beginner with Linux. So I tried to run my program and got the error stated above. Am I doing anything wrong, any help will be much appreciated. 

Thank you

---

### Post by tjoff on 2011-12-08
It it several years since I last installed ifort on ubuntu, so I do not remember all details. I do not know if it is the formatting of your post or if the following is really in your .bashrc file:

```
# compiler source / opt/intel/Compiler/bin/ifortvars.sh PATH = $ PATH: / opt/intel/Compiler/bin / export PATH # intel debugger fortran source / opt/intel/Compiler/bin/ia32/idbvars.sh PATH = $ 
PATH: / opt/intel/Compiler/bin/ia32 / export PATH
```

There are several issues here with comments, linebreaks and whitespaces. Try to cleaning it up by putting the following in your .bashrc instead:
```

source /opt/intel/Compiler/bin/ifortvars.sh 
PATH = $PATH:/opt/intel/Compiler/bin 
export PATH 
source /opt/intel/Compiler/bin/ia32/idbvars.sh 
PATH = $PATH:/opt/intel/Compiler/bin/ia32
export PATH
```

Actually i think you should be fine with just
```

source /opt/intel/Compiler/bin/ifortvars.sh 
source /opt/intel/Compiler/bin/ia32/idbvars.sh 

```
since i think that the scripts set the PATH for you, but try it out.

---

### Post by kourlandreas on 2011-12-08
hello all!i have succesfully installed intel fortran composer xe 2011 in my Ubuntu 10.04 but when i try to compile a program i have all i get is:
/opt/intel/composer_xe_2011_sp1.7.256/compiler/lib/ia32/for_main.o: In function `main':
/export/users/nbtester/x86linux_nightly/branch-12_1/20111012_000000/libdev/frtl/src/libfor/for_main.c:(.text+0x50): undefined reference to `MAIN__
apparently i am missing ipp,arbb and tbb libraries.any ideas how to fix this???thanks in advance

---

### Post by tjoff on 2011-12-09
Hi and welcome to ubuntuforums kourlandreas

It is better if you start a separate thread for your question. 
In this way your post becomes more visible, and it is possible for others to find your post by searching thread titles. It is also more considerate not to divert attention from the original posters question.

---

