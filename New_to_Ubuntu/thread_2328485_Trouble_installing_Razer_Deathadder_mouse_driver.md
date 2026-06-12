---
title: "Trouble installing Razer Deathadder mouse driver"
date: 2016-06-21
forum: New to Ubuntu
---

### Post by vpiercy on 2016-06-21
I downloaded the razercfg tarball from this site: [https://bues.ch/cms/hacking/razercfg.html#download](https://bues.ch/cms/hacking/razercfg.html#download). I searched the Ubuntu forums and this thread seemed closest to my concern:

[http://ubuntuforums.org/showthread.php?t=2278442&highlight=install+razercfg](http://ubuntuforums.org/showthread.php?t=2278442&highlight=install+razercfg)

That's why I'm posting in the New to Ubuntu section. I'm not all that new to Ubuntu, but getting this Razer Deathadder mouse to work is making me feel very noobish. 

I downloaded the file razerdfg-o.33.tar.bz2 and I extracted it so I have a folder named razerdfg-0.33 with other folders and files in it. 

The README lists dependencies. I added those. 

Then it asked for 

[HTML]$ cmake .
$ make[/HTML]

And I got: 

[HTML]v@Ubuntu-15:~$ cmake .
CMake Error: The source directory "/home/v" does not appear to contain CMakeLists.txt.
Specify --help for usage, or press the help button on the CMake GUI.[/HTML]

Okay. Do I go to the folder the extraction made of the tarball? razerdfg-0.33

Or do I have to go into the sub-folder that contains the CMakeLists.txt? 

Assuming I try the latter, I run [HTML]cmake .[/HTML] and [HTML]make[/HTML]  there, right? 

Do I just type them or is there a file I need to direct them to? 

So then I went to the razer subfolder and got the following after invoking [HTML]cmake .[/HTML]

[HTML] v@Ubuntu-15:~/razercfg-0.33/razerd$ cmake .
-- The C compiler identification is GNU 5.2.1
-- The CXX compiler identification is GNU 5.2.1
-- Check for working C compiler: /usr/bin/cc
-- Check for working C compiler: /usr/bin/cc -- broken
CMake Error at /usr/share/cmake-3.5/Modules/CMakeTestCCompiler.cmake:61 (message):
  The C compiler "/usr/bin/cc" is not able to compile a simple test program.

  It fails with the following output:

   ```
Change Dir: /home/v/razercfg-0.33/razerd/CMakeFiles/CMakeTmp

  

  Run Build Command:"/usr/bin/make" "cmTC_7ef23/fast"

  /usr/bin/make -f CMakeFiles/cmTC_7ef23.dir/build.make
  CMakeFiles/cmTC_7ef23.dir/build

  make[1]: Entering directory
  '/home/v/razercfg-0.33/razerd/CMakeFiles/CMakeTmp'

Building C object CMakeFiles/cmTC_7ef23.dir/testCCompiler.c.o

  /usr/bin/cc -o CMakeFiles/cmTC_7ef23.dir/testCCompiler.c.o -c
  /home/v/razercfg-0.33/razerd/CMakeFiles/CMakeTmp/testCCompiler.c

  Linking C executable cmTC_7ef23

  /usr/bin/cmake -E cmake_link_script CMakeFiles/cmTC_7ef23.dir/link.txt
  --verbose=1

  /usr/bin/cc CMakeFiles/cmTC_7ef23.dir/testCCompiler.c.o -o cmTC_7ef23
  -rdynamic

  /usr/bin/ld:
  /usr/lib/gcc/x86_64-linux-gnu/5/../../../x86_64-linux-gnu/crti.o:
  unrecognized relocation (0x2a) in section `.init'

  /usr/bin/ld: final link failed: Bad value

  collect2: error: ld returned 1 exit status

  CMakeFiles/cmTC_7ef23.dir/build.make:97: recipe for target 'cmTC_7ef23'
  failed

Building C object CMakeFiles/cmTC_7ef23.dir/testCCompiler.c.o

  /usr/bin/cc -o CMakeFiles/cmTC_7ef23.dir/testCCompiler.c.o -c
  /home/v/razercfg-0.33/razerd/CMakeFiles/CMakeTmp/testCCompiler.c

  Linking C executable cmTC_7ef23

  /usr/bin/cmake -E cmake_link_script CMakeFiles/cmTC_7ef23.dir/link.txt
  --verbose=1

  /usr/bin/cc CMakeFiles/cmTC_7ef23.dir/testCCompiler.c.o -o cmTC_7ef23
  -rdynamic

  /usr/bin/ld:
  /usr/lib/gcc/x86_64-linux-gnu/5/../../../x86_64-linux-gnu/crti.o:
  unrecognized relocation (0x2a) in section `.init'

  /usr/bin/ld: final link failed: Bad value

  collect2: error: ld returned 1 exit status

  CMakeFiles/cmTC_7ef23.dir/build.make:97: recipe for target 'cmTC_7ef23'
  failed


  make[1]: *** [cmTC_7ef23] Error 1

  make[1]: Leaving directory
  '/home/v/razercfg-0.33/razerd/CMakeFiles/CMakeTmp'

  Makefile:126: recipe for target 'cmTC_7ef23/fast' failed

  make: *** [cmTC_7ef23/fast] Error 2



CMake will not be able to correctly generate this project.
Call Stack (most recent call first):
  CMakeLists.txt


CMake Warning (dev) in CMakeLists.txt:
  No cmake_minimum_required command is present.  A line of code such as

    cmake_minimum_required(VERSION 3.5)

  should be added at the top of the file.  The version specified may be lower
  if you wish to support older CMake versions for this project.  For more
  information run "cmake --help-policy CMP0000".
This warning is for project developers.  Use -Wno-dev to suppress it.

-- Configuring incomplete, errors occurred!
See also "/home/v/razercfg-0.33/razerd/CMakeFiles/CMakeOutput.log".
See also "/home/v/razercfg-0.33/razerd/CMakeFiles/CMakeError.log".
```

I wish I could just find a .deb version of the file and have Ubuntu Store install it. I dowloaded a file titled "razertool-gtk_0.07-1_i386.deb" and "installed it," but nothing happened. 

Typing 

[HTML]$ sudo ldconfig [/HTML]

returns just a prompt.

---

### Post by X-RED_Tech on 2016-06-21
Yes, you need to run the commands in the extracted folder. Also pay attention to the dependencies mentioned in the README file and install them before compiling.

---

### Post by vpiercy on 2016-06-21
Thank you for the reply. I installed the dependencies, following the README, and figured out that I needed to run the commands in the extracted folder. I still got the error message (the last big set of code lines in my first message). Not sure what to do at this point.

---

### Post by wildmanne39 on 2016-06-22
Please use code tags - if you are using New Reply button - highlight text and use the # button in the text box header. 
 
If using Quick Reply then [noparse]```
[/noparse] at the beginning and [noparse]
```[/noparse] at the end.

---

### Post by X-RED_Tech on 2016-06-22
Delete the folder, extract again and start over. Otherwise you may have to use 'make clean' or something like that

---

