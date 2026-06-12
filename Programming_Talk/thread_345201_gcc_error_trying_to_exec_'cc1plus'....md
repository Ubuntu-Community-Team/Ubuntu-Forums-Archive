---
title: "gcc: error trying to exec 'cc1plus'..."
date: 2007-01-24
forum: Programming Talk
---

### Post by fiveryanfrenzy on 2007-01-24
How do I compile C++ files?

I made one (.cpp) and put it in my home folder and then...

> rcalderoni@gabriel:~$ gcc
gcc: no input files
rcalderoni@gabriel:~$ gcc test.cpp
gcc: error trying to exec 'cc1plus': execvp: No such file or directory
rcalderoni@gabriel:~$ 

how do i get this to work?

---

### Post by runningwithscissors on 2007-01-24
gcc is the C compiler.
g++ is the C++ compiler.

To compile C++ programs:
```
$ g++ <c++ source file>
```

---

### Post by Silentvoice on 2007-01-24
and also you'll probably want to use the -o argument..

g++ test.cpp -o test.o

this makes it so you don't get a.out on every single compilation (because gcc doesn't care if a.out already exists, it will replace it every time)

---

### Post by TheXMan on 2007-02-08
I m facing the same problem with GCC & G++.

[B]gcc: error trying to exec 'cc1plus': execvp: No such file or directory
g++: error trying to exec 'cc1plus': execvp: No such file or directory[/B]

I tried to install Visual C#.net, but doesn't work. It gives 

[B]Runtime Error!
R6034
[/B]

I tried to install other windows application, it works fine.
This problem occurs only when installing application requires Ms .Net framework.

Please suggest me, how to install MS .NET on UBUNTU Linux.

---

### Post by ssc on 2007-03-01
Hi,

type the following : 

sudo apt-get install g++

This will help you a lot !

Saludos

---

### Post by hod139 on 2007-03-01
> **ssc said:**
> Hi,

type the following : 

sudo apt-get install g++

This will help you a lot !

Saludos
No it won't!!!  The package to install is build-essential, which is a meta package with dependencies on all the packages needed to build.  For example, installing g++ alone will not install the C++ standard library, which will only lead to confusion and problems.

---

### Post by danielmoita on 2007-03-20
Had the same problem and:
     sudo apt-get install g++ 
worked fine for me.

---

### Post by piccilli on 2007-10-03
gcc and g++ needs to be the same version.

take a look with "gcc --version" and "g++ --version"

---

### Post by chaumurky on 2007-10-11
I'm surprised it's not included in build-essential - I find myself needing it quite often.

---

### Post by Brazman on 2008-06-03
Thank you.  That did solve my problem.  My fault was similiar to the one above with output error:
gcc: error trying to exec 'cc1plus': execvp: No such file or directory
did sudo apt-get install g++ and my problem was corrected.  To compile the file I did:
 g++ -o hello.o hello.cpp
Maybe this will be of help.
thanks again.

---

### Post by Jens_Li on 2008-06-05
Isnt gcc supposed to invoke the right compiler for you if you pass it a .cpp, from the file sufix?

---

### Post by kefei_chen on 2009-03-26
hey, i think u cann reload the spm and then try to install gcc and g++
cheers

kefei

---

### Post by tyfius on 2009-03-26
> **Jens_Li said:**
> Isnt gcc supposed to invoke the right compiler for you if you pass it a .cpp, from the file sufix?Yes and no. I noticed that it does attempt to compile C++ applications but by default it doesn't link certain libraries. For example, when using math functions you need to specify -lm yourself.

---

### Post by jespdj on 2009-03-26
People please note that this is a very old thread!

---

### Post by jrama123 on 2009-03-26
> **piccilli said:**
> gcc and g++ needs to be the same version.

take a look with "gcc --version" and "g++ --version"

hi after I run the below command i get the error..how do i use c++ compiler in ubuntu please...

sudo apt-get install g++
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package g

cheers

---

### Post by dwhitney67 on 2009-03-26
> **jrama123 said:**
> hi after I run the below command i get the error..how do i use c++ compiler in ubuntu please...

sudo apt-get install g++
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package g

cheers

sudo apt-get install build-essential

---

### Post by jrama123 on 2009-03-30
> **dwhitney67 said:**
> sudo apt-get install build-essential

Many Thanks Whitney. Its working perfect now...

~r

---

### Post by bhaverkamp on 2010-02-19
Yup, that worked for me too. I had forgotten about that, used to be part of my basic install ritual.

---

### Post by hotthoughtguy on 2010-02-19
home@ubuntu:~/Desktop$ sudo apt-get install g++
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  g++: Depends: g++-4.0 (>= 4.0.3) but it is not going to be installed
E: Broken packages
home@ubuntu:~/Desktop$ 



any solution?

---

### Post by mrt_doulaty on 2010-06-13
> **TheXMan said:**
> I m facing the same problem with GCC & G++.

[B]gcc: error trying to exec 'cc1plus': execvp: No such file or directory
g++: error trying to exec 'cc1plus': execvp: No such file or directory[/B]

I tried to install Visual C#.net, but doesn't work. It gives 

[B]Runtime Error!
R6034
[/B]

I tried to install other windows application, it works fine.
This problem occurs only when installing application requires Ms .Net framework.

Please suggest me, how to install MS .NET on UBUNTU Linux.


What do you really want to do?

Are you trying to execute a Windows program on Linux? If yes, then try Wine [http://www.winehq.org/](http://www.winehq.org/)

If you want to develop .NET applications on Linux, then try Mono [http://www.mono-project.com]("http://www.mono-project.com/")

---

### Post by mrt_doulaty on 2010-06-13
> **hotthoughtguy said:**
> home@ubuntu:~/Desktop$ sudo apt-get install g++
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  g++: Depends: g++-4.0 (>= 4.0.3) but it is not going to be installed
E: Broken packages
home@ubuntu:~/Desktop$ 



any solution?

Try 'Synaptic Package Manager'
System -> Administration -> Synaptic Package Manager

---

### Post by donbis88 on 2010-10-05
Hi! 
I try to compile:
[B][COLOR=black]
g++ test.cpp -o test.o[/COLOR][/B]

but my on terminal appears:

**g++: error trying to exec 'cc1plus': execvp: No such file or directory**
I had just installed* build-essential* and *g++*and g++ and gcc is the same version....
What can I do?

best regards 
Simone

---

### Post by Zugzwang on 2010-10-06
> **donbis88 said:**
> 
What can I do?


As a start, please copy&paste the (complete) result of running "gcc -v" here, so we can have a look.

---

### Post by donbis88 on 2010-10-06
Using built-in specs.
Target: x86_64-linux-gnu
Configured with: ../src/configure -v --with-pkgversion='Ubuntu 4.4.3-4ubuntu5' --with-bugurl=file:///usr/share/doc/gcc-4.4/README.Bugs --enable-languages=c,c++,fortran,objc,obj-c++ --prefix=/usr --enable-shared --enable-multiarch --enable-linker-build-id --with-system-zlib --libexecdir=/usr/lib --without-included-gettext --enable-threads=posix --with-gxx-include-dir=/usr/include/c++/4.4 --program-suffix=-4.4 --enable-nls --enable-clocale=gnu --enable-libstdcxx-debug --enable-plugin --enable-objc-gc --disable-werror --with-arch-32=i486 --with-tune=generic --enable-checking=release --build=x86_64-linux-gnu --host=x86_64-linux-gnu --target=x86_64-linux-gnu
Thread model: posix
gcc version 4.4.3 (Ubuntu 4.4.3-4ubuntu5) 

thanks for your help!

---

### Post by Zugzwang on 2010-10-06
Ok, so check that the file "/usr/lib/gcc/x86_64-linux-gnu/4.4/cc1plus" exists and is executable.

---

### Post by donbis88 on 2010-10-06
I haven't this directory:
/usr/lib/gcc/x86_64-linux-gnu/4.4

---

### Post by Zugzwang on 2010-10-06
> **donbis88 said:**
> I haven't this directory:
/usr/lib/gcc/x86_64-linux-gnu/4.4

Use synaptic and check which g++ package is installed. Also double-check that "build-essential" is really installed - installation might have failed in the first place and you didn't notice the error message.

---

### Post by donbis88 on 2010-10-06
Also in synaptic, g++ and "build-essential" are installed.

---

### Post by Zugzwang on 2010-10-07
> **donbis88 said:**
> Also in synaptic, g++ and "build-essential" are installed.

There are multiple packages whose name start with "g++" Check that "g++-4.4" is installed an try reinstalling it. Watch out for error messages.

---

### Post by cem_sanal on 2011-05-14
I tried all above(reinstalling g++ and gcc, sudo apt-get build essential) and g++ and gcc are exactly the same version but, it says:
''g++: error trying to exec 'cc1plus': execvp: No such file or directory'' (I'm using Qdevelop) so, I can't build the project. Could you help?

---

### Post by TrophyNinjaShrub on 2013-04-17
I *think* you want to add a -c option (just compile, don't link), so: g++ -c hello.cpp -o hello.o. If what you want is a complete executable, ready-to-run, then .o is a very non-standard extension (it's usually used to name object files, which can then be linked together into an executable). In the latter case,
g++ hello.cpp -o hello
or if you like to keep binaries in a directory clearly indicating that (like I do)
mkdir ~/bin
g++ hello.cpp -o ~/bin/hello

> **Brazman said:**
> Thank you.  That did solve my problem.  My fault was similiar to the one above with output error:
gcc: error trying to exec 'cc1plus': execvp: No such file or directory
did sudo apt-get install g++ and my problem was corrected.  To compile the file I did:
 g++ -o hello.o hello.cpp
Maybe this will be of help.
thanks again.

---

