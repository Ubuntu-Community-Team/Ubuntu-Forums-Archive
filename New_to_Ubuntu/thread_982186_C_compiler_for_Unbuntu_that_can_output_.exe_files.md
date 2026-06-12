---
title: "C compiler for Unbuntu that can output .exe files"
date: 2008-11-14
forum: New to Ubuntu
---

### Post by BadEyedia on 2008-11-14
Ok, I have a really strange question...Right now i am in a class that uses the C programing language. Basically we are sending in code and .exe files to be graded on. The submissions must include the executable file. At the moment this computer is functioning as a duel system boot. Just curious about how i could get a C compiler that will output into a .exe file for Ubuntu?

---

### Post by igknighted on 2008-11-14
> **BadEyedia said:**
> Ok, I have a really strange question...Right now i am in a class that uses the C programing language. Basically we are sending in code and .exe files to be graded on. The submissions must include the executable file. At the moment this computer is functioning as a duel system boot. Just curious about how i could get a C compiler that will output into a .exe file for Ubuntu?

I guess you might be able to install cygwin in wine to use GCC, but that just sounds weird...

---

### Post by snova on 2008-11-14
There is a cross compiler package for Ubuntu. Search for 'mingw' in the package manager, you may have some luck with it (I have not tried it).

Alternatively, since you have a dual-boot, download the "real" MinGW for Windows and compile from there, it's more likely to work.

Cygwin is another possibility (for Windows).

---

### Post by kellemes on 2008-11-14
[http://wiki.wxwidgets.org/Install_The_Mingw_Cross-Compiler]("http://wiki.wxwidgets.org/Install_The_Mingw_Cross-Compiler")

---

### Post by Carl Hamlin on 2008-11-14
> **BadEyedia said:**
> Ok, I have a really strange question...Right now i am in a class that uses the C programing language. Basically we are sending in code and .exe files to be graded on. The submissions must include the executable file. At the moment this computer is functioning as a duel system boot. Just curious about how i could get a C compiler that will output into a .exe file for Ubuntu?

The man file for gcc indicates that the -fvisibility-ms-compat option "attempts to use visibility settings to make GCC’s C++ linkage model compatible with that of Microsoft Visual Studio." I'd start there and see what I could get out of gcc.

---

### Post by Kain000 on 2008-11-14
I'm in EXACTLY the same situation at school, I'm taking c++ and on windows everyone uses DevC++ but doesnt work that well in linux, sooo


you just need the packages  called build essentials

search syntapic because i'm not sure of the spelling

but ```
sudo apt-get install build essentials
```\

and you can use any text editor....   ones that support the c language for highlighting reasons are prefered.   

I prefer Gedit because it's ubuntu's editor of choice .... and it's really powerful while being user friendly, and lightweight.     

If you choose gedit, you need to go to syntapic to download gedit plugins package.

In gedit under preferences you can all all the plugins you want, like bracket highlighting and such.    You can choose the highlight mode of the editor under view>highlight mode> source> c or c++ or any other for that matter.


(important****   you will need to save your text files as blahblahblah**_.c_**
so the compiler will use it correctly.*****)



The way you compile and run things is to pull up a terminal.....

cd (change directory ) to the folder that you have your text file saved into
for example:
```
cd /home/sean/C/
```

once in the right directory you may want to type ls to see how your files are spelled... (i know i do)

to excute the compile command type:
```
gcc filename.c -o filename
```

gcc is the compile program, the filename.c that you need to compile and -o tells it to OUTPUT the compiled excutable with the name filename   if you left the -o blah blah out, then it would make an excutable called a out by default.    you can always change that later but it keeps things in order.    


After you've worked out all the bugs and have compiled into an excutable.... rename the ectutiable to filename**_.exe_**

(.exe is a ms DOS filetype that your instructor's computer should be able to excute)

edit!!!  sorry i forgot to add to run your excuted file to check if your code runs like you planed you need to type in a terminal:

./filename

this will run your excutable file in the terminal.

if you need any help just ask!
-sean

---

### Post by snova on 2008-11-14
Please disregard the post above. Renaming a file is not sufficient.

Dev-Cpp may run under Wine, so I suggest you try that in addition.

The -fvisibility-ms-compat option is also useless, since the OP appears not to be attempting to link with MSVC libraries. At any rate, he couldn't without a cross-compiler.

---

### Post by Carl Hamlin on 2008-11-14
> **Kain000 said:**
> After you've worked out all the bugs and have compiled into an excutable.... rename the ectutiable to filename**_.exe_**

(.exe is a ms DOS filetype that your instructor's computer should be able to excute)

if you need any help just ask!
-sean

Sean:

If you're going through these steps in your class, then one of these things is true:

1. You've performed an additional step which is not mentioned here which is causing gcc to output PE formatted binary by default
2. Your instructor runs linux and recognizes an ELF formatted binary when he/she sees one.
3. You're new to the class and haven't turned anything in yet, and are about to receive an unfortunate shock.

Crossing my fingers for you and hoping it's not 3.

---

### Post by Simian Man on 2008-11-14
I find it really odd that your instructor is asking you to submit .exe files for grading.  Most just ask for code and compile it themselves.  If you wanted to be bad, that's a great opportunity :).

Anyway, since it's for a grade, I wouldn't muck around with cross-compiling; it is tricky to get working.  You could easily turn in a program that won't actually run on Windows, so you would really have to test it on a Windows machine first.  In which case you may as well just compile it on Windows...

It sucks to have a class be dependent on a certain platform...

---

### Post by Kain000 on 2008-11-14
> **Carl Hamlin said:**
> Sean:

If you're going through these steps in your class, then one of these things is true:

1. You've performed an additional step which is not mentioned here which is causing gcc to output PE formatted binary by default
2. Your instructor runs linux and recognizes an ELF formatted binary when he/she sees one.
3. You're new to the class and haven't turned anything in yet, and are about to receive an unfortunate shock.

Crossing my fingers for you and hoping it's not 3.


what do you mean?    

when i compile gcc spits out an  executable (application/x-executable) file type but if his instructor wants a .exe file he just needs to rename and it will be recongized as a MS DOS executable.


Our class is just printing out our code rather than uploading executables, but that would work just fine wouldnt it?

---

### Post by Kain000 on 2008-11-14
> Simian Man;6178722]I find it really odd that your instructor is asking you to submit .exe files for grading.  Most just ask for code and compile it themselves.  If you wanted to be bad, that's a great opportunity :). 
[/QUOTE]

hahaha
VERY GOOD POINT!!

---

### Post by Kain000 on 2008-11-14
> **snova said:**
> Please disregard the post above. Renaming a file is not sufficient.

Dev-Cpp may run under Wine, so I suggest you try that in addition.

The -fvisibility-ms-compat option is also useless, since the OP appears not to be attempting to link with MSVC libraries. At any rate, he couldn't without a cross-compiler.

dev c++ will run under wine untill you need to compile and it trys to open a command line terminal where there is none.

---

### Post by Carl Hamlin on 2008-11-14
> **Kain000 said:**
> when i compile gcc spits out an  executable (application/x-executable) file type but if his instructor wants a .exe file he just needs to rename and it will be recongized as a MS DOS executable.

Sorry, that's not correct. Windows executables are formatted according to the PE (Portable Executable) binary format. Most linux executables are formatted according to the ELF (Executable and Linking Format) binary format. (How's that for a little redundancy?)

The two formats are fundamentally different, and do not run natively across platforms. gcc is going to be producing ELF formatted binaries by default, and adding a .exe extension to the filename won't change the binary format.

> **Kain000 said:**
> Our class is just printing out our code rather than uploading executables, but that would work just fine wouldnt it?

Nope. Renaming the binary doesn't change it's format. It's a really good guess, but unfortunately incorrect.

---

### Post by Kain000 on 2008-11-14
> **Carl Hamlin said:**
> Sorry, that's not correct. Windows executables are formatted according to the PE (Portable Executable) binary format. Most linux executables are formatted according to the ELF (Executable and Linking Format) binary format. (How's that for a little redundancy?)

The two formats are fundamentally different, and do not run natively across platforms. gcc is going to be producing ELF formatted binaries by default, and adding a .exe extension to the filename won't change the binary format.



Nope. Renaming the binary doesn't change it's format. It's a really good guess, but unfortunately incorrect.

Thanks for the clarification then what would you use to convert that ELF file into the PE .exe for windows use?

---

### Post by Carl Hamlin on 2008-11-14
> **Kain000 said:**
> Thanks for the clarification then what would you use to convert that ELF file into the PE .exe for windows use?

I'm not currently aware of a conversion utility for ELF/PE, but it would be a fantastic addition to Ubuntu.

---

### Post by Kain000 on 2008-11-15
> **Carl Hamlin said:**
> I'm not currently aware of a conversion utility for ELF/PE, but it would be a fantastic addition to Ubuntu.

agreed, I guess for now I (and anyone else in this predicament)  will just need to flash drive/email ect. their text file and open in your windows compiler.

---

### Post by cwmoser on 2008-11-17
A C compiler that will output a .EXE file.

How about MonoDevelop?  It is a C# development environment that allows you to write command line utilities or GUI apps.  The output is a .exe file.

An example to illustrate is the following I wrote:

#!/bin/sh
# Start X10
# ----------
mono /home/carl/c#/c5/c5/bin/Release/c5.exe

MonoDevelop created the output file c5.exe for me.  This .exe file will not run directly under Ubuntu but will run with the runtime program mono.  I can take the .exe file to a Windows PC and run it directly.

MonoDevelop is available via Synaptic.

Carl

---

### Post by chips24 on 2008-11-17
if youre working with executables get wine, of make your devopment on windows...

---

### Post by directhex on 2008-11-17
> **cwmoser said:**
> A C compiler that will output a .EXE file.

How about MonoDevelop?  It is a C# development environment that allows you to write command line utilities or GUI apps.  The output is a .exe file.

An example to illustrate is the following I wrote:

#!/bin/sh
# Start X10
# ----------
mono /home/carl/c#/c5/c5/bin/Release/c5.exe

MonoDevelop created the output file c5.exe for me.  This .exe file will not run directly under Ubuntu but will run with the runtime program mono.  I can take the .exe file to a Windows PC and run it directly.

MonoDevelop is available via Synaptic.

Carl

C# is not C, and there's no guarantees that the instructor will have the .NET framework installed

---

### Post by cwmoser on 2008-11-18
> **directhex said:**
> C# is not C, and there's no guarantees that the instructor will have the .NET framework installed

Your instructor must like booting MSDOS 6.2 :-) Nah, he just wants to run you app to see if it works as required.

Sounds like you would be better off getting an old copy of MSC or Turbo C and install on Ubuntu using wine or Crossover.

Another alternative is to download VMWare and run a virtualized copy of Windows in an Ubuntu Window.  This is probably the better approach if your instructor is a stickler for details.

Carl

---

### Post by directhex on 2008-11-18
Or, as already covered in another thread: install the "mingw32" package, and use "i586-mingw32msvc-gcc" instead of "gcc"

Bam, you're making Windows .exe files instead of ELF binaries

---

### Post by scorp123 on 2008-11-18
> **Kain000 said:**
>  After you've worked out all the bugs and have compiled into an excutable.... rename the ectutiable to filename**_.exe_** 

(.exe is a ms DOS filetype that your instructor's computer should be able to excute) Nope, that's not going to work, LOL. :lolflag:

You can rename an ELF binary whatever you want ... it's still an ELF binary, specifically compiled to be run on Linux. No renaming of any sorts is going to change that :)

---

### Post by Nergar on 2008-12-04
> **directhex said:**
> Or, as already covered in another thread: install the "mingw32" package, and use "i586-mingw32msvc-gcc" instead of "gcc"

Bam, you're making Windows .exe files instead of ELF binaries

Is this working for anyone? aka bump.

---

