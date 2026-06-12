---
title: "Possible to change properties of .so"
date: 2012-09-07
forum: Programming Talk
---

### Post by IAMTubby on 2012-09-07
Hey,

1)I have a shared library file called libcunit.so.1.0.1 which is in intel PC format as you can see below. This is part of the CUnit testing framework.
 
But I want to run on a build it and generate executables for a PowerPC architecture.

```

$ file libcunit.so.1.0.1
libcunit.so.1.0.1: ELF 32-bit LSB shared object, Intel 80386, version 1 (SYSV), not stripped

``` 

I believe(I'm just assuming) that changing this file to PowerPC format will compile my application successfully.
Is there a way to convert this from IntelPC to PowerPC form ?


2)I have one more question .
I am not able to perform any shell command(I tried cd, ls , clear) into the directory containing the libraries of the original PowerPC code.
```

$ ls
ls: error while loading shared libraries: libc.so.6: ELF file data encoding not little-endian

```

Why does it show an error ? I am not compiling , building etc. I am just trying to do an ls on one directory in my system ? 

Thanks.

---

### Post by Bachstelze on 2012-09-07
1) No.
2) Have you modified some environment variables such as LD_LIBRARY_PATH or LD_PRELOAD?

---

### Post by IAMTubby on 2012-09-07
> **Bachstelze said:**
> 1) No.

Okay, Sir, can you advise me on how I go about solving 1?
When I open the Makefile, I can see some lines like
```

export CROSS_LIB =$(ROOT_DIR)/ppc_4xx/lib
export CROSS_INCLUDE =$(ROOT_DIR)/ppc_4xx/usr/include
export CROSS_COMPILE = ppc_4xx-
# this is needed to keep the kernel happy
export CROSS_CMP     = ppc_4xx-

export CC = $(CCACHE_BIN)$(CROSS_BIN)/$(CROSS_COMPILE)gcc

```
I thought these ppc lines should take care of the cross compiling issues. But no!. It gives me errors like
```

find: error while loading shared libraries: libc.so.6: ELF file data encoding not little-endian

```

> 
2) Have you modified some environment variables such as LD_LIBRARY_PATH or LD_PRELOAD?

No I haven't.
[code]
echo $LD_LIBRARY_PATH gives /home/aftab_hassan/local/lib:
echo $LD_PRELOAD :  I guess it's not set. Gives a blank line as o/p.

---

### Post by IAMTubby on 2012-09-07
Just wanted to add that the above lines are not from Makefile, but from a file called mak.inc

Thanks.

---

### Post by Bachstelze on 2012-09-07
What exactly are you trying to do?

---

### Post by IAMTubby on 2012-09-07
Okay.
There is an existing application targeted at the PowerPC environment.

I have to write a CUnit test to test some of those C files.

So, I compiled my application with CUnit code, after adding all the required CUnit libraries etc. But when I added -L/Path_to_CUnit - lcunit (some library required by CUnit framework) to the existing makefile, it gives the error
```

find: error while loading shared libraries: libc.so.6: ELF file data encoding not little-endian

```

because the .so's in the Cunit/lib folder are obviously Intel-PC based.

So basically I have to find a way to allow the CUnit libraries compatible with the PowerPC environment.

Does that convey ?

---

### Post by ofnuts on 2012-09-07
You need a PowerPC  version of the compiled libs, or their source to recompile them for the PowerPC. PowerPC vs. x86 isn't only a matter of big-endian vs. little-endian, they use completely different machine code instructions.

---

### Post by Bachstelze on 2012-09-07
You need to either find a compiled PPC verison of the library, or get the source and compile one yourself. Do you have a PPC machine in the first place?

---

### Post by IAMTubby on 2012-09-07
> **ofnuts said:**
> You need a PowerPC  version of the compiled libs
Okay , what then is the function of the these lines mentioned below ? All it does is, to compile C code for the PowerPC environment ? Ideally, shouldn't the ppc_4xx-gcc take care of converting the libs from Intel-PC to PowerPC-architecture ?
```

export CROSS_LIB =$(ROOT_DIR)/ppc_4xx/lib
export CROSS_INCLUDE =$(ROOT_DIR)/ppc_4xx/usr/include
export CROSS_COMPILE = ppc_4xx-
# this is needed to keep the kernel happy
export CROSS_CMP     = ppc_4xx-

export CC = $(CCACHE_BIN)$(CROSS_BIN)/$(CROSS_COMPILE)gcc

```

> 
or their source to recompile them for the PowerPC. 

I have this source tarball. CUnit-2.1-2-src.tar.bz2
It has the subdirectories doc, include, lib, and share on extracting. Will I be able to do something with that ?


> **Bachstelze said:**
> You need to either find a compiled PPC verison of the library 
Finding one might be difficult. I'm not able to find one on the internet.

> 
or get the source and compile one yourself.

As I said, I have the source tarball. Doesn't that contain the source also ? or only libraries ? Sorry Sir, I'm unaware.

> 
Do you have a PPC machine in the first place?
Yes

---

### Post by Bachstelze on 2012-09-07
If you have a PPC machine, then you do not need to worry about cross-compilation. Just extract the source and compile it normally, it will compile a PPC version.

---

### Post by IAMTubby on 2012-09-07
My PPC machine is not capable of compiling , it can only run a few CLI commands.

So you were asking me to get the CUnit code, so that I can run it on the PPC machine, and generate the .so files myself ?

---

### Post by Bachstelze on 2012-09-07
Then...

> **IAMTubby said:**
> 
Finding one might be difficult. I'm not able to find one on the internet.


[Here](http://packages.debian.org/squeeze/powerpc/libcunit1/download), download the package in any Debian-based system, extract it with [font=monospace]dpkg -x[/font] and you will get the library file.

---

### Post by dwhitney67 on 2012-09-07
> **IAMTubby said:**
> My PPC machine is not capable of compiling , it can only run a few CLI commands.

So you were asking me to get the CUnit code, so that I can run it on the PPC machine, and generate the .so files myself ?

Therefore you need to either a) download a pre-compiled library slated for the PPC, or b) get the source code to compile it yourself for the PPC.

The purpose of the cross-compiler, if it is built correctly, is so that you can generate executables and/or libraries on a foreign host (eg. Intel-based) that are slated for the target host (eg. PPC-based).

Question... who built your cross-compiler?  Does that person or organization offer support?


P.S.  Verify that you do NOT have a dot-character in your PATH setting; for example:
```

$ echo $PATH
.:/some/path

```

If you do, remove it, for this could be causing you to reference the incorrect 'ls' command (or other command) when you are in the PPC area of your host machine.

---

### Post by IAMTubby on 2012-09-07
Bachstelze, dwhitney.
Thank you so much! (Not yet done, still in the process. But I think I'm beginning to understand better now)
Bachstelze, thank you so much for the links. I'll try and get back in a few minutes.

Can I rephrase the dwhitney's last reply based on Bachstelze's last reply.
> 
Therefore you need to either a) download a pre-compiled library slated for the PPC, or b) get the source code to compile it yourself for the PPC.

That means, either 
a)Use the CUnit debian packages for powerpc that Bachstelze has sent links of.
b)Do the following steps on the power pc itself
> **dwhitney67 said:**
> Step 1:  Download CUnit package from Source Forge.

Step 2:  Find where you saved the package on your system, and uncompress it:
```

tar xjf CUnit-2.1-2-src.tar.bz2

```

Step 3: Go into the CUnit-2.1.2 directory.
```

cd CUnit-2.1.2

```

Step 4: Run the following sequence of commands:
```

mkdir -p $HOME/local
./configure --prefix=$HOME/local
make clean
make
make install

```

Step 5:  Goto the directory $HOME/local.  Verify that you have the following sub-directories: doc, include, lib, and share.  Each of these should have the products you seek.

Step 6.  To build an application using CUnit, something like this is used:
```

gcc -Wall -I$HOME/local/include MyProg.c -L$HOME/local/lib -lcunit -o myprog

```

Note:  In your source code, include CUnit header files such as:
```

#include <CUnit/CUnit.h>
...

```

Please advise.

---

### Post by Bachstelze on 2012-09-07
You said earlier that you are unable to compile on your PPC...

---

### Post by IAMTubby on 2012-09-07
Yes Bachstelze, 
I cannot compile on my powerPC, but was just confirming if I have understood the concept from the replies.

---

### Post by dwhitney67 on 2012-09-07
> **IAMTubby said:**
> 
Please advise.

Step 4 needs to be refined.  You need to tell 'configure' which compiler to use; by default it will use your host system's native compiler.  Instead you want it to use your cross-compiler.

---

### Post by IAMTubby on 2012-09-07
Okay, so will that look something like
```

./configure --host=x86-linux --target=powerpc-linux CROSS_COMPILE=ppc_4xx --prefix=$HOME/local

```

---

### Post by dwhitney67 on 2012-09-07
> **IAMTubby said:**
> Okay, so will that look something like...
Yes.  Now, the $10K question... does that statement work?  Will configure know where to find that compiler (to test its capabilities) with you merely indicating this "CROSS_COMPILE=ppc_4xx"?

Surely configure will need to know the path where the compiler is located.

---

### Post by IAMTubby on 2012-09-07
Sorry for the long gap. Was trying out something.

I thought I have 2 solutions, but now neither seems to work.

Solution1:
I tried doing this in the /local/lib created by CUnit. I was having a problem with my libcunit.so.1.0.1 file for Cunit under /local/lib being an Intel-PC file, and after doing this compilation, it gave me a file of type PowerPC or cisco. 
```

./configure --host=x86-linux --target=powerpc-linux  CROSS_COMPILE=/opt/toolchain/usr/bin/ppc_4xx- CC=/opt/toolchain/usr/bin/ppc_4xx-gcc

```

This is the output of ```
file libcunit.so.1.0.1
```
```

libcunit.so.1.0.1: ELF 32-bit MSB shared object, PowerPC or cisco 4500, version 1 (SYSV), not stripped

```

I was happy, but when I tried compiling the entire application, it again gives me an error saying
```

find: error while loading shared libraries: libc.so.6: ELF file data encoding not little-endian
make[1]: *** [clean] Error 127
make[1]: Leaving directory `/home/projects/rootsrc'
make: *** [clean] Error 2

```

So it doesn't work.

Solution2 :
I tried downloading the file Bachstelze provided link to.
But my system is Redhat based and so dpkg doesn't work.

What's the reason for Solution1 failing ?

Thanks.

---

### Post by dwhitney67 on 2012-09-07
> **IAMTubby said:**
> 
I was happy, but when I tried compiling the entire application, it again gives me an error saying
```

find: error while loading shared libraries: libc.so.6: ELF file data encoding not little-endian
make[1]: *** [clean] Error 127
make[1]: Leaving directory `/home/projects/rootsrc'
make: *** [clean] Error 2

```

So it doesn't work.

What were you compiling?  Were you using the appropriate compiler?

---

### Post by IAMTubby on 2012-09-07
I was compiling an existing application that runs on the PowerPC architecture.

I was using a makefile which includes the required compiler.

What could be the reason in general ?
Have I not installed something ?
Are some of my libraries still Intel-PC architecture ?
Am I not using the correct gcc ?

---

### Post by dwhitney67 on 2012-09-07
> **IAMTubby said:**
> I was compiling an existing application that runs on the PowerPC architecture.

I was using a makefile which includes the required compiler.

What could be the reason in general ?
Have I not installed something ?
Are some of my libraries still Intel-PC architecture ?
Am I not using the correct gcc ?

Show me the Makefile.  Better yet, show me the output that the Makefile produces; not just the errors, but all of it.

---

### Post by dwhitney67 on 2012-09-07
Another thought... try running through these simple steps...

1.  Create this file (call it cunit.c):
```

#include <Cunit/Basic.h>

int main()
{
    if (CUE_SUCCESS != CU_initialize_registry())
        return CU_get_error();

    return 0;
} 

```

2.  Compile/Link it as such:
```

/opt/toolchain/usr/bin/ppc_4xx-gcc -I$HOME/local/include cunit.c -L/$HOME/local/lib -lcunit

```

P.S.  Don't bother trying to run the resulting a.out (if any).

---

### Post by IAMTubby on 2012-09-07
dwhitney, I am sorry I don't find an attach option to attach the Makefile.
The Makefile is around 900 lines long and there are multiple Makefiles.

I think I'll just go ahead with the step you mentioned in the last post.

---

### Post by IAMTubby on 2012-09-07
Okay, can we make 1 more attempt.

Can this be a clue : 
The makefile log says
```

Removing libraries from /home/projects/lib.
find: error while loading shared libraries: libc.so.6: ELF file data encoding not little-endian
make[1]: *** [clean] Error 127

```

Now even if I go to /home/projects/lib and do a shell command, say ls, it still gives the same error.
Does this mean that the error was never in my code, but in the system(can't find another word) ?

> **dwhitney67 said:**
> P.S. Verify that you do NOT have a dot-character in your PATH setting
No, I don't have a dot character in my PATH setting.
This is the output of echo $PATH
```
/usr/kerberos/bin:/usr/local/bin:/bin:/usr/bin:/home/bin
```

Thanks.

---

### Post by dwhitney67 on 2012-09-07
Maybe the Makefile itself is adjusting PATH to reference the cross-compiler stuff, and then attempting to use the system's native 'find' executable in /usr/bin.

I've worked with cross-compilers only a couple of times, with the most recent experience being a breeze.  Of course, the cross-compiler was a COTS product.

Here's a snip of code that was included in the Makefile I developed:
```

ifeq ($(PPC), 1)
# power-pc
ARCH = ppc
PROC = 83xx
CXX  = $(ARCH)_$(PROC)-g++
AR   = $(ARCH)_$(PROC)-ar
else
ifeq ($(P3), 1)
# pentium-3
ARCH = x86
PROC = pentium3
else
# pentium-4
ARCH = x86
PROC = pentium4
endif
CXX  = $(PROC)-g++
AR   = $(PROC)-ar
endif

TARGET          := /opt/montavista/cge/devkit/$(ARCH)/$(PROC)
PATH            := $(TARGET)/bin:$(PATH)
LD_LIBRARY_PATH := $(TARGET)/usr/lib/
...

```
The main point of the code above was to deduce the ARCH and PROC that would be used to compile the code.  The project supported 3 types of CPUs:  PPC, P4, and P-III.  If not obvious, it was a C++ project, not C.

How was your attempt at the simple code I provided earlier?

It is hard to give you exact answer to the problem(s) you are experiencing since I am unable to duplicate the anomalies you are seeing.  But somehow I think you are "crossing" your environments up... native vs. PPC.

---

### Post by spjackson on 2012-09-07
> **IAMTubby said:**
> Okay, can we make 1 more attempt.

Can this be a clue : 
The makefile log says
```

Removing libraries from /home/projects/lib.
find: error while loading shared libraries: libc.so.6: ELF file data encoding not little-endian
make[1]: *** [clean] Error 127

```

Now even if I go to /home/projects/lib and do a shell command, say ls, it still gives the same error.
Does this mean that the error was never in my code, but in the system(can't find another word) ?


No, I don't have a dot character in my PATH setting.
This is the output of echo $PATH
```
/usr/kerberos/bin:/usr/local/bin:/bin:/usr/bin:/home/bin
```

If you are getting the same error from ls, then it isn't the Makefile that's screwing up your make but your environment. Of course the Makefile could also be breaking it, but that would not affect you when you type ls.

Your environment is causing shared libraries in general and libc.so.6 in particular to be sought in the wrong place. I don't know where you have your PPC libc installed on your build system, but wherever it is, you shouldn't be looking there when running programs - only your PPC linker should be looking there.

What can cause shared libraries to be sought in the wrong place? Not PATH but LD_LIBRARY_PATH. Why would the symptoms change when you change directory? Only if you have . or some other relative path in LD_LIBRARY_PATH.

If it isn't LD_LIBRARY_PATH, then it would have to be something more system-wide ("man ld.so" for details), but then everything would be broken all the time.

---

### Post by IAMTubby on 2012-09-13
> **spjackson said:**
> If you are getting the same error from ls, then it isn't the Makefile that's screwing up your make but your environment.Not PATH but LD_LIBRARY_PATH.
Spot on Sir. The error was in the LD_LIBRARY_PATH. I had set the LD_LIBRARY_PATH as follows when I was writing CUnit applications for the native compiler and forgot about it.
I had edited my ~/.bashrc file as follows
```

# .bashrc

# Source global definitions
if [ -f /etc/bashrc ]; then
        . /etc/bashrc
fi

# User specific aliases and functions
export LD_LIBRARY_PATH=~/local/lib:${LD_LIBRARY_PATH}

``` 

_Scenario_
There are many export LD_LIBRARY_PATH instances in other Makefiles within the application.(Huge application).

_Problem_:
When I make that change to ~/.bashrc, I think the other LD_LIBRARY_PATH gets overwritten and it shows a make error in the beginning of the compilation itself. 
If I comment out that line from the ~/.bashrc, build happens till the CUnit file. And the good news is :) ,it detects the new .o file I have added in the Makefile and tries to compile it. But it flags of a make error saying that it couldn't get the libraries.

_Make output now_ :
I think(hopefully) my compiling is now working, my run is not.
```

warning: libcunit.so.1, needed by /home/projects/trunk/src/ open/lib/libfile.so, not found (try using -rpath or -rpath-link)
/home/projects/trunk/src/open/lib/libfile.so: undefined reference to `CU_basic_run_tests'
/home/projects/trunk/src/open/lib/libfile.so: undefined reference to `CU_add_test'
/home/projects/trunk/src/open/lib/libfile.so: undefined reference to `CU_cleanup_registry'
/home/projects/trunk/src/open/lib/libfile.so: undefined reference to `CU_assertImplementation'
/home/projects/trunk/src/open/lib/libfile.so: undefined reference to `CU_add_suite'
/home/projects/trunk/src/open/lib/libfile.so: undefined reference to `CU_get_error'
/home/projects/trunk/src/open/lib/libfile.so: undefined reference to `CU_initialize_registry'
/home/projects/trunk/src/open/lib/libfile.so: undefined reference to `CU_basic_set_mode'
collect2: ld returned 1 exit status
make[1]: *** [file] Error 1
make[1]: Leaving directory `/home/projects/trunk/src/ip/map/build/file/app/linux'
make: *** [build] Error 2

```

_Possible reason_ :
I'm guessing it's because as dwhitney said, this is how you run a CUnit application.
> **dwhitney67 said:**
> To run your application.  Try something like:
```

LD_LIBRARY_PATH=$HOME/local/lib ./Basic_Simple

```


_What I now need_ : 
Please give the 2 solutions to run my CUnit file called CUnitFile.o with this LD_LIBRARY_PATH addition. Two ways I could think of was:
1)Add it to the Makefile in a syntax such that.
if(building CUnitFile.o)
{
 LD_LIBRARY_PATH=$HOME/local/lib ./CUnitFile 
}

2)Add export LD_LIBRARY_PATH=$HOME/local/lib to the ~/.bashrc in a way that we are **appending** to the other LD_LIBRARY_PATH's mentioned in the other makefiles, not overwriting as before.
Please note : I cannot hardcode all the paths to LD_LIBRARY_PATH in ~/.bashrc because the paths come from multiple Makefiles.
So,I cannot do something like
```

export LD_LIBRARY_PATH="/list/of/library/paths:/another/path"

```
Thanks a lot.

---

### Post by IAMTubby on 2012-09-13
Just realized that dwhitney's syntax on altering the LD_LIBRARY_PATH, actually does appending and not overwriting.
```

export LD_LIBRARY_PATH=${LD_LIBRARY_PATH}:$HOME/local/lib

``` 

But this is what I get when and try and compile the application with the above code inside my ~/.bashrc
```

find: error while loading shared libraries: libc.so.6: ELF file data encoding not                                                                                        little-endian
make[1]: *** [clean] Error 127
make[1]: Leaving directory `/home/projects/trunk/src/ope                                                                                     n/rootsrc'
make: *** [clean] Error 2

```


And this build fails within a minute, whereas without that change in ~/.bashrc, it runs for around 40 minutes, with the make errors mentioned in the previous post.

What could be the reason ?

This makes me feel, it would be better to mention the LD_LIBRARY_PATH for CUnitFile.o in the makefile itself.
That way atleast it's sure to compile **atleast** until this stage. 

Please advise.
Thanks.

---

### Post by dwhitney67 on 2012-09-13
> **IAMTubby said:**
> 
Please advise.
Thanks.

You should avoid tinkering with your working environment (ie. .bashrc).  If you require a particular setting for LD_LIBRARY_PATH, then set it within your Makefile.

You indicated that you have lots of Makefiles, and that you do not have the desire to edit every one of them.  You may have to; but before that, try something like this when invoking 'make':
```

LD_LIBRARY_PATH=$HOME/local/lib make

```
Remember... restore your LD_LIBRARY_PATH (or remove if not needed) within .bashrc.

Btw, when working on large projects, it is quite common to create one ore more files that contain either common definitions or make-rules; these files are then included within Makefile so that they can "inherit" common settings.  Should one of these settings need to be modified, only one file needs to be edited.  I would suggest that you pursue this set up; it will undoubtedly save you time/grief in the future.

---

### Post by IAMTubby on 2012-09-13
> **dwhitney67 said:**
> 
```

LD_LIBRARY_PATH=$HOME/local/lib make

```

Will this append to the LD_LIBRARY_PATH's already derived as the makefile is running. Or will this be the equivalent of saying that LD_LIBRARY_PATH is only $HOME/local/lib ?

---

### Post by dwhitney67 on 2012-09-13
> **IAMTubby said:**
> Will this append to the LD_LIBRARY_PATH's already derived as the makefile is running. Or will this be the equivalent of saying that LD_LIBRARY_PATH is only $HOME/local/lib ?

It will override it.  If you have more to add to the path, then add it.

The thing I was attempting to convey is that you can set variables on the command line when executing an application; whether this be 'make', 'a.out', or some other application, the same principle applies.

BTW... this is important... LD_LIBRARY_PATH is NOT used by the source code/object files when compiling or linking an application.  It is only referenced when running an application.  Perhaps I should have indicated this earlier.

When cross-compiling (I assume you are still attempting this), you need to ensure that you cross-compiler was built successfully; it should NOT reference any of the files on that are native to you system.  To verify, run the cross compiler using this option:  --print-search-dirs.  For example, for the native gcc:
```

gcc --print-search-dirs

```
I forgot what your cross-compiler is called, but merely substitute it for the above 'gcc'.

Again, it should be added that LD_LIBRARY_PATH can be used when invoking your compiler; for example:
```

LD_LIBRARY_PATH=blah gcc ...

```

---

### Post by IAMTubby on 2012-09-13
> **dwhitney67 said:**
> LD_LIBRARY_PATH is NOT used when compiling or linking an application.  It is only referenced when running an application.  Perhaps I should have indicated this earlier.
Thanks for that dwhitney. But I don't want it to override ?

Can you tell me how to add 
```
export LD_LIBRARY_PATH=$HOME/local/lib
``` in the makefile such that it applies only to a file called CUnitFile.o ?

That's how you run a CUnit file right ?
> **dwhitney67 said:**
> Sorry about that; I forgot to offer the instructions to run your application.  Try something like:
```

LD_LIBRARY_PATH=$HOME/local/lib ./Basic_Simple

```


---

### Post by IAMTubby on 2012-09-13
All I want to do is,
"Let everything else compile as it is mentioned in the makefile cuz it's working well. Just want to change the CUnit file called CUnitFile.o to run as follows".
```

LD_LIBRARY_PATH=$HOME/local/lib ./Basic_Simple

```

Did I convey ?

---

### Post by dwhitney67 on 2012-09-13
> **IAMTubby said:**
> Thanks for that dwhitney. But I don't want it to override ?

Can you tell me how to add 
```
export LD_LIBRARY_PATH=$HOME/local/lib
``` in the makefile such that it applies only to a file called CUnitFile.o ?

That's how you run a CUnit file right ?

One thing you should attempt to do is spend a few minutes creating a small project (perhaps only one file is needed).  Try building this in a temporary directory so that you can separate your "fears" of working with a large project.

As for LD_LIBRARY_PATH, it applies to all commands that you are used to build the project; not just to one file, unless you create a special make-rule for that file.

For instance, my personal working environment does not have LD_LIBRARY_PATH set.  However, if I want to use a cross-compiler, I need to set LD_LIBRARY_PATH to reference the appropriate path where dependent libraries reside.  From within the Makefile, I have a statement like this:
```

export LD_LIBRARY_PATH = $(TARGET)/usr/lib

```
TARGET corresponds to a directory containing library files that are associated with my target architecture (eg. PPC); this directory lived in the bowels of the MontaVista cross-compiler.  Surely you have something similar.  If not, then you have an incomplete cross-compiler.

Anyhow, back to the small project... create this now!  I asked you to do this before, but I guess you did not see the value in it.  Also create a Makefile that can be used to build this project.  Test it out... see if a) it builds, and b) it runs on your target environment.  Take the lessons learned and apply it to the bigger project.

---

### Post by IAMTubby on 2012-09-13
dwhitney, please give me a few minutes. I'll do and get back to you.

---

