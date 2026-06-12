---
title: "How do I install MinGW-64bit?"
date: 2013-01-26
forum: New to Ubuntu
---

### Post by regency on 2013-01-26
How do I install MingGW-64 bit? What sudo commands must I issue?

I am new to Ubuntu and have 12.10, 64 bit, US English installed. I plan to compile code for 64-bit Microsoft Windows.

---

### Post by linuxsyst on 2013-01-26
Simply run ```
sudo apt-get install mingw-w64
```
Or
```
gcc-mingw-w64
```
I'm not sure

---

### Post by andrew.46 on 2013-01-27
An easy way to find available packages is:

```

andrew@corinth:~$ **[COLOR="Red"]apt-cache search mingw | grep 64[/COLOR]**
binutils-mingw-w64 - Cross-binutils for Win32 and Win64 using MinGW-w64
binutils-mingw-w64-i686 - Cross-binutils for Win32 (x86) using MinGW-w64
binutils-mingw-w64-x86-64 - Cross-binutils for Win64 (x64) using MinGW-w64
g++-mingw-w64 - GNU C++ compiler for MinGW-w64
g++-mingw-w64-i686 - GNU C++ compiler for MinGW-w64 targeting Win32
g++-mingw-w64-x86-64 - GNU C++ compiler for MinGW-w64 targeting Win64
gcc-mingw-w64 - GNU C compiler for MinGW-w64
gcc-mingw-w64-base - GNU Compiler Collection for MinGW-w64 (base package)
gcc-mingw-w64-i686 - GNU C compiler for MinGW-w64 targeting Win32
gcc-mingw-w64-x86-64 - GNU C compiler for MinGW-w64 targeting Win64
gdb-mingw-w64 - Cross-debugger for Win32 and Win64 using MinGW-w64
gdb-mingw-w64-target - Cross-debugger server for Win32 and Win64 using MinGW-w64
gfortran-mingw-w64 - GNU Fortran compiler for MinGW-w64
gfortran-mingw-w64-i686 - GNU Fortran compiler for MinGW-w64 targeting Win32
gfortran-mingw-w64-x86-64 - GNU Fortran compiler for MinGW-w64 targeting Win64
gnat-mingw-w64 - GNU Ada compiler for MinGW-w64
gnat-mingw-w64-i686 - GNU Ada compiler for MinGW-w64 targeting Win32
gnat-mingw-w64-x86-64 - GNU Ada compiler for MinGW-w64 targeting Win64
gobjc++-mingw-w64 - GNU Objective-C++ compiler for MinGW-w64
gobjc++-mingw-w64-i686 - GNU Objective-C++ compiler for MinGW-w64 targeting Win32
gobjc++-mingw-w64-x86-64 - GNU Objective-C++ compiler for MinGW-w64 targeting Win64
gobjc-mingw-w64 - GNU Objective-C compiler for MinGW-w64
gobjc-mingw-w64-i686 - GNU Objective-C compiler for MinGW-w64 targeting Win32
gobjc-mingw-w64-x86-64 - GNU Objective-C compiler for MinGW-w64 targeting Win64
**[COLOR="Red"]mingw-w64 - Development environment targetting 32- and 64-bit Windows[/COLOR]**
mingw-w64-dev - Development files for MinGW-w64 (transitional package)
mingw-w64-i686-dev - Development files for MinGW-w64 targeting Win32
mingw-w64-tools - Development tools for 32- and 64-bit Windows
mingw-w64-x86-64-dev - Development files for MinGW-w64 targeting Win64

```

I have not used this on Linux but I have used MinGW under Windows where it works nicely enough...

---

### Post by regency on 2013-01-30
@ andrew.46

Thanks for your reply.

I downloaded mingw-w64-bin_x86_64-linux_20121031.tar.bz2 from MinGW-w64's Sourceforge website. It is about 259MB in size.

Could you show me how to install it?

Or is there any difference in functionality if I install it using your "apt-cache search" method?

---

### Post by andrew.46 on 2013-01-31
Ooops looks like I have created some confusion :(. The *apt-cache search* syntax merely finds a package name. To install mingw-64 on Ubuntu you would be best to run:

```
sudo apt-get install mingw-w64 
```

rather than download the file from sourceforge. On Windows I use the automated mingw installer...

---

### Post by ikt on 2013-01-31
> **regency said:**
> Or is there any difference in functionality if I install it using your "apt-cache search" method?

First point to call when installing programs should always be through the software centre or apt-get or synaptic eg your local repositories. If it's not available then check for a ".deb" package and then lastly check for a .tar.gz

Compiling programs for me is very 2003, I just don't do it anymore.

---

### Post by linuxsyst on 2013-02-10
```
tar xvzf pkg.tar.gz
```** ( If File Is a GZ) **```
tar xvjf pkg.tar.bz2
```** ( If Files is a BZ)**
After this command a New Folder Would Be Created in the Same Location with the Package Name.

**2.N**ext Move Into The Newly Created Folder.
Use[COLOR=#000080]** *"ls"***[/COLOR] command to look for the folder Then Type ```
cd pkg(Enter)
```** ( Here pkg is the Name of the Newly Created Folder )**

**3. N**ext Go Into Super User Mode. Super User Mode in Linux is Like Having temparary Admin Priviledges just to install programs and perform other complex tasks.
Type ```
sudo -s (Enter)
```Then Type in Your ROOT password when prompted

**4. N**ow We’ll Install The App.
Type** ```
./configure (Enter)
```**
Type ```
make (Enter)
```Then ```
make install (Enter)
```
Then ```
make clean (Enter)
```
Then [COLOR=#000080]**"exit" (Enter)**[/COLOR]

---

