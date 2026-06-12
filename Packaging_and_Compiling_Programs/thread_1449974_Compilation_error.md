---
title: "Compilation error"
date: 2010-04-08
forum: Packaging and Compiling Programs
---

### Post by newport_j on 2010-04-08
I tried to compile a program and received the following error:



/usr/bin/ld: cannot find -lstdc++
collect2: ld returned 1 exit status

A Googling of the this error states that one should:

Install libstdc++5 package. I did, but I still got the error.

I also changed the PATH to be able to find :

/usr/lib

where this file package should reside. 

Please tell what is wrong. I did what was stated to solve this problem and I still get the error.

Please note : I have posted this message before, but it never got on the Forum BB.

I just want the program to compile.


Newport_j

---

### Post by newport_j on 2010-04-08
errol@fermi:/usr/lib$ ls libstdc*
libstdc++.so libstdc++.so.5 libstdc++.so.5.0.7 libstdc++.so.6 libstdc++.so.6.0.10
errol@fermi:/usr/lib$ ls -al libstdc*
lrwxrwxrwx 1 root root 25 2010-04-08 15:35 libstdc++.so -> /usr/lib64/libstdc++.so.6
lrwxrwxrwx 1 root root 18 2010-04-08 13:39 libstdc++.so.5 -> libstdc++.so.5.0.7
-rw-r--r-- 1 root root 829424 2008-05-07 01:12 libstdc++.so.5.0.7
lrwxrwxrwx 1 root root 19 2009-10-06 14:28 libstdc++.so.6 -> libstdc++.so.6.0.10
-rw-r--r-- 1 root root 1023448 2009-03-16 21:03 libstdc++.so.6.0.10


errol@fermi:/usr/lib$ sudo ln -s /usr/lib/libstdc++.so.5.0.7 /usr/lib/libstdc++.so
ln: creating symbolic link `/usr/lib/libstdc++.so': File exists


In trying to create symbolic link with the last command I got a /usr/lib/libstdc++.so file exists error. It does, but only on by a link to libstdc++so.6. How do I get rid of this error? The whole thing was initiated when I go the error on compliation thta

"cannot find -lstdc++" 


I am trying to put the library that has the file (-lstdc++) in the correct directory.

What is the correct library and what directory does it go into to correct this error?

Newport_j

---

### Post by gmargo on 2010-04-08
That type of error usually indicates that you need to install a -dev package.

You seem to be using 9.04 Jaunty, so install the **libstdc++6-4.3-dev** package.

---

### Post by newport_j on 2010-04-09
I am using 8.04. But I will try to install the package anyway and see what happens. Thanks
 
Newport_j

---

### Post by newport_j on 2010-04-09
I installed libstdc++6.4.3-dev package. I was able to compile in 64 bit mode. When I tried to complie in 32 bit mode I got the following message:

/usr/bin/ld: skipping incompatible /usr/lib/gcc/x86_64-linux-gnu/4.3.3/libstdc++.so when searching for -lstdc++
/usr/bin/ld: skipping incompatible /usr/lib/gcc/x86_64-linux-gnu/4.3.3/libstdc++.a when searching for -lstdc++
/usr/bin/ld: skipping incompatible /usr/lib/gcc/x86_64-linux-gnu/4.3.3/libstdc++.so when searching for -lstdc++
/usr/bin/ld: skipping incompatible /usr/lib/gcc/x86_64-linux-gnu/4.3.3/libstdc++.a when searching for -lstdc++
/usr/bin/ld: skipping incompatible /usr/lib/gcc/x86_64-linux-gnu/4.3.3/../../../libstdc++.so when searching for -lstdc++
/usr/bin/ld: skipping incompatible /usr/lib/libstdc++.so when searching for -lstdc++
/usr/bin/ld: cannot find -lstdc++
collect2: ld returned 1 exit status


My first question a few days ago was since I was in 32 bit mode compile why did it even look in the 64 bit libraries. I think that has been answered.

I want to compile in 32 bit mode. I want to use that mode. 

i am not sure if the install you said to do had any effect. I have not run any 64 bit compiles in months. It did compile after that install in 64 bit mode.

I just need to know what file must be installed to get a 32 bit compile. I need that library name. 

I am guessing that and libstdc++6.4.3-dev package is for 64 bit use.

It seems that their must be a similar one for 32 bit.

I am using 8.04 Ubuntu and I have both 32 and 64 bit compile capability. I just change the designation -m32 or -m64 when I want to compile for 32 or 64 bits, respectively.


Newport_j

---

### Post by gmargo on 2010-04-09
For 8.04 Hardy, the default development package is **libstdc++6-4.2-dev**.  But the listing you gave indicates a later version.

Anyway, you've got to match the version of the compiler you are using with the libstdc++ version.  For 8.04 Hardy, the default compiler is gcc 4.2.3, so you need "4.2" development libraries (shared library 6.0.9).  For 8.10 Intrepid, the default compiler is gcc 4.3.1, so you need "4.3" libraries (shared library 6.0.10).  For 9.04 Jaunty, gcc 4.3.3, "4.3" libraries (shared library 6.0.10).  For 9.10 Karmic, gcc 4.4.1, "4.4" libraries (shared library 6.0.13).

Since your listing shows shared library 6.0.10, I assumed you were using Jaunty (or Intrepid).  If you are using Hardy, then I don't know how you managed to install the "4.3" library since it's not in the Hardy repository.

---

### Post by newport_j on 2010-04-09
I am using someone else's computer remotely that is how you saw the output that made you think it was 9.04 Jaunty. It was 9.04 jaunty! The 9.04 jaunty installation is for 64 bits, but I have been able to compile applications for 32 bits several times.  

The c programming that I am doing is being done on that computer, remotely.

I installed libstdc++6.4.3-dev with the apt-get install command. It was no problem. 

As I said the system supports both 32-bit and 64-bit for compilation. I just use -m32 when I want a 32 bit compile and -m64 when I want a 64bit compile.

Newport_j

---

### Post by newport_j on 2010-04-09
As you can see when I compile I get this error again. Cannot find a file.

errol@fermi:~/Desktop/desktop_cleanup/WEGtest$ ./compile5.sh
/usr/bin/ld: skipping incompatible /usr/lib/gcc/x86_64-linux-gnu/4.3.3/libstdc++.so when searching for -lstdc++
/usr/bin/ld: skipping incompatible /usr/lib/gcc/x86_64-linux-gnu/4.3.3/libstdc++.a when searching for -lstdc++
/usr/bin/ld: skipping incompatible /usr/lib/gcc/x86_64-linux-gnu/4.3.3/libstdc++.so when searching for -lstdc++
/usr/bin/ld: skipping incompatible /usr/lib/gcc/x86_64-linux-gnu/4.3.3/libstdc++.a when searching for -lstdc++
/usr/bin/ld: skipping incompatible /usr/lib/gcc/x86_64-linux-gnu/4.3.3/../../../libstdc++.so when searching for -lstdc++
/usr/bin/ld: skipping incompatible /usr/lib/libstdc++.so when searching for -lstdc++
/usr/bin/ld: cannot find -lstdc++
collect2: ld returned 1 exit status


errol@fermi:~/Desktop/desktop_cleanup/WEGtest$ echo $LD_LIBRARY_PATH
/usr/local/cuda/lib::/usr/lib/

errol@fermi:~/Desktop/desktop_cleanup/WEGtest$ cd /usr/lib/
errol@fermi:/usr/lib$ ls libstdc*
libstdc++.so  libstdc++.so.5  libstdc++.so.5.0.7  libstdc++.so.6  libstdc++.so.6.0.10

errol@fermi:/usr/lib$ ls -al libstdc*
lrwxrwxrwx 1 root root      25 2010-04-08 15:35 libstdc++.so -> /usr/lib64/libstdc++.so.6
lrwxrwxrwx 1 root root      18 2010-04-08 13:39 libstdc++.so.5 -> libstdc++.so.5.0.7
-rw-r--r-- 1 root root  829424 2008-05-07 01:12 libstdc++.so.5.0.7
lrwxrwxrwx 1 root root      19 2009-10-06 14:28 libstdc++.so.6 -> libstdc++.so.6.0.10
-rw-r--r-- 1 root root 1023448 2009-03-16 21:03 libstdc++.so.6.0.10

What is the library that has the 32 bit version of -lstdc++, and what directory is it in? 


As I said before this complies with no trouble in 64 bit mode. It gives the above error in 32 bit compile mode.

I am using Ubuntu 9.04.


Newport_j

---

### Post by gmargo on 2010-04-09
Perhaps the **lib32stdc++6** package.

[http://packages.ubuntu.com/jaunty/lib32stdc++6](http://packages.ubuntu.com/jaunty/lib32stdc++6)

---

### Post by newport_j on 2010-04-12
Thank you very much for your help. I will give it a try. 
 
Newport_j

---

### Post by newport_j on 2010-04-12
Perhaps the lib32stdc++6 package.

[http://packages.ubuntu.com/jaunty/lib32stdc++6](http://packages.ubuntu.com/jaunty/lib32stdc++6)

What package is that a part of? lib32stdc++6.dev?

Newport_j

---

### Post by gmargo on 2010-04-12
_**lib32stdc++6**_ is the name of the package.  You will only see it available on the 64-bit system.

---

