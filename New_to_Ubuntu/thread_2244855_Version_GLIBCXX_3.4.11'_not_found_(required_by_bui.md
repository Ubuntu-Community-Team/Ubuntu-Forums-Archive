---
title: "Version GLIBCXX_3.4.11' not found (required by buildW.mexglx)"
date: 2014-09-19
forum: New to Ubuntu
---

### Post by souraklis on 2014-09-19
I am trying to compile a c++ ubuntu project via matlab [here]("http://vision.is.tohoku.ac.jp/~kyamagu/research/clothing_parsing/"). When I am trying to use it after the compilation with make command, I am getting the following error:

```
Invalid MEX-file
'////fashionista_v0.2/lib/+bsr/buildW.mexglx':
 //local/MATLAB/R2011a/bin/glnx86/../../sys/os/glnx86/libstdc++.so.6: version
`GLIBCXX_3.4.11' not found (required by
 ////fashionista_v0.2/lib/+bsr/buildW.mexglx)
```


I am not familiar with those processes, so I couldnt understand the several proposed solutions like that([http://unix.stackexchange.com/questions/134266/how-to-specify-the-libstdc-so-6-to-use](http://unix.stackexchange.com/questions/134266/how-to-specify-the-libstdc-so-6-to-use)). What is exactly libstdc++ and GLIBCXX and how can I solve the problem?

I am trying to fix the problem using the proposed link [https://gcc.gnu.org/onlinedocs/libstdc++/faq.html#faq.how_to_set_paths:](https://gcc.gnu.org/onlinedocs/libstdc++/faq.html#faq.how_to_set_paths:)

```
export LD_LIBRARY_PATH=${prefix}/lib:$LD_LIBRARY_PATH
```

However, due to lack of unix shell knowledge I don't understand what to put in the command.

---

### Post by steeldriver on 2014-09-19
Do you actually have the older version of the libstdc++ library on your system? if so where/how did you get it?

I think the basic problem is that the version of Matlab that you are using only supports a specific version of the gcc compiler (gcc-4.3) when compiling mex files, whereas the default version of gcc on Ubuntu 12.04 is gcc-4.6 (and on 14.04 is gcc-4.8)

[http://www.mathworks.com/support/compilers/R2011a/glnxa64.html](http://www.mathworks.com/support/compilers/R2011a/glnxa64.html)

---

### Post by souraklis on 2014-09-19
I am having r2011a 32bit version of matlab, I am using Ubuntu 12.04 and i found in /usr/lib/gcc/i686-linux-gnu folder gcc 4.6 version. I ve installed libstdc++ via sudo apt-get install libstdc++6. So what should I change in my system?? The steps for me is just to install gcc 4.3? After that how can i set it as default compiler instead of the new version? Also what about libstdc++?

Thanks in advance.

---

### Post by souraklis on 2014-09-19
I ve tried to install gcc 4.3 using the following command ```
  sudo apt-get install gcc-4.3 
``` however I am received the following:

```
Building dependency tree       
Reading state information... Done
Package gcc-4.3 is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source

E: Package 'gcc-4.3' has no installation candidate

```

---

### Post by steeldriver on 2014-09-19
AFAIK the oldest version of gcc/g++ that is directly installable in 12.04 is 4.4

Do you have the possibility to upgrade your matlab?

---

### Post by souraklis on 2014-09-19
Yes which version should I install (caution I am running in 32bit machine)? Basically I am downloading [http://www.mathworks.com/support/compilers/R2012a/glnxa64.html](http://www.mathworks.com/support/compilers/R2012a/glnxa64.html) it seems that its ok with gcc 4.4.

EDIT: I ve installed gcc 4.4 but inside the folder I couldnt locate libstdc++ .a and .so file.

---

