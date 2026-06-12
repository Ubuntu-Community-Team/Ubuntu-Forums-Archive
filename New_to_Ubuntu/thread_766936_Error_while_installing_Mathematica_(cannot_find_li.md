---
title: "Error while installing Mathematica (cannot find libstdc++.so.5)"
date: 2008-04-25
forum: New to Ubuntu
---

### Post by yangli on 2008-04-25
Got Hardy and installed it. I got a problem when trying to install Mathematica 6.0. The installation didn't finish, and the error message says "[FONT="Fixedsys"]/usr/local/Wolfram/Mathematica/6.0/SystemFiles/Kernel/Binaries/Linux/MathKernel: error while loading shared libraries: libstdc++.so.5: cannot open shared object file: No such file or directory[/FONT]"

What should I do now? How to install that libstdc++.so.5 file? Thanks a lot.

---

### Post by RealPSL on 2008-04-28
```
sudo apt-get install libstdc++5
``` will install the missing library in questions libstdc++.so.5.

---

### Post by oferfrid on 2008-11-07
worked for me thanks

---

### Post by minollo on 2009-01-10
> **RealPSL said:**
> ```
sudo apt-get install libstdc++5
``` will install the missing library in questions libstdc++.so.5.

It worked also for me! Thanks-you RealPSL!

---

### Post by Le Chat on 2009-12-08
Ok, I'm using the latest release of Kubuntu, 9.10, newbee in Linux.
I have met the same problem as topicstarter while installing Mathematica 6.0

After the recommended input solution I found the next code:

```
sudo apt-get install libstdc++5
[sudo] password for master
Reading package lists... Done
Building dependency tree
Reading state information... Done
Package libstdc++5 is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or is only available from another source
E: Package libstdc++5 has no installation candidate
```

I saw in my package installer manager that libstdc++6 - 4.4.1-4Ubuntu8 (The GNU Standard C++ Library v3) is already installed. So where is a problem?

Any help will be greatly appreciated. Thanks in advance.

---

### Post by asahin on 2009-12-08
> **Le Chat said:**
> Ok, I'm using the latest release of Kubuntu, 9.10, newbee in Linux.
I have met the same problem as topicstarter while installing Mathematica 6.0

After the recommended input solution I found the next code:

```
sudo apt-get install libstdc++5
[sudo] password for master
Reading package lists... Done
Building dependency tree
Reading state information... Done
Package libstdc++5 is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or is only available from another source
E: Package libstdc++5 has no installation candidate
```I saw in my package installer manager that libstdc++6 - 4.4.1-4Ubuntu8 (The GNU Standard C++ Library v3) is already installed. So where is a problem?

Any help will be greatly appreciated. Thanks in advance.
I think, replacing libstdc++.so.5 with libstdc++.so.6 in Mathematica 6.0 will work.
```

sed -i 's/libstdc++.so.5/libstdc++.so.6/g' [your_file]

```
after that line you can re-run Mathematica 6.0

---

### Post by Le Chat on 2009-12-08
Excuse me, but which file must be behind[your_file]?

I tried to patch my installation .sh file by this procedure, but the installation after it also was unsuccessful, there is still the same error about libstdc++.so.5 in error log.

---

### Post by asahin on 2009-12-08
> **Le Chat said:**
> Excuse me, but which file must be behind[your_file]?

I tried to patch my installation .sh file by this procedure, but the installation after it also was unsuccessful, there is still the same error about libstdc++.so.5 in error log.

If you get that error:
> "/usr/local/Wolfram/Mathematica/6.0/SystemFiles/Kernel/Binaries/Linux/MathKernel: error while loading shared libraries: libstdc++.so.5: cannot open shared object file: No such file or directory"
 and you have libstdc++.so.6 instead of libstdc++.so.5, you should use:

```
sed -i 's/libstdc++.so.5/libstdc++.so.6/g' /usr/local/Wolfram/Mathematica/6.0/SystemFiles/Kernel/Binaries/Linux/MathKernel
```
after the process is completed you can retry to install Mathematica again

---

### Post by Le Chat on 2009-12-08
It is not a solution: reinstallation to the same directory will erase all the files contained there. The problem is still leaving, I tried.

If I could run Mathematica after patching the kernel.., but i don't know how. There is no any link in program menu, probably because the installation doesn't reach the end, and command "mathematica" in console doesn't give anything.

Why the installation of this product is so complicated? Why developers simply do not make standard .rpm or .deb package?

---

### Post by Le Chat on 2009-12-19
I've already solved this problem: there is no libstdc++.so.5 in repositories of Ubuntu 9.10, so I had to download and install it manually. To download go [here]("http://packages.debian.org/lenny/i386/libstdc++5/download").
After the installation all was correct!
Great thanx to all of you!

---

### Post by newport_j on 2010-04-08
errol@fermi:/usr/lib$ ls libstdc*
libstdc++.so  libstdc++.so.5  libstdc++.so.5.0.7  libstdc++.so.6  libstdc++.so.6.0.10
errol@fermi:/usr/lib$ ls -al libstdc*
lrwxrwxrwx 1 root root      25 2010-04-08 15:35 libstdc++.so -> /usr/lib64/libstdc++.so.6
lrwxrwxrwx 1 root root      18 2010-04-08 13:39 libstdc++.so.5 -> libstdc++.so.5.0.7
-rw-r--r-- 1 root root  829424 2008-05-07 01:12 libstdc++.so.5.0.7
lrwxrwxrwx 1 root root      19 2009-10-06 14:28 libstdc++.so.6 -> libstdc++.so.6.0.10
-rw-r--r-- 1 root root 1023448 2009-03-16 21:03 libstdc++.so.6.0.10


errol@fermi:/usr/lib$ sudo ln -s /usr/lib/libstdc++.so.5.0.7 /usr/lib/libstdc++.so
ln: creating symbolic link `/usr/lib/libstdc++.so': File exists


In trying to create symbolic link with the last command I got a /usr/lib/libstdc++.so file exists error. It does, but only on by a link to libstdc++so.6. How do I get rid of this error? The whole thing was initiated when I go the error on compliation thta

"cannot find -lstdc++" 

 
I am trying to put the library that has the file (-lstdc++) in the correct directory.

What is the correct library and what directory does it go into to correct this error?

Newport_j

---

