---
title: "[SOLVED] Forgetting how to navigate to files within terminal"
date: 2008-05-21
forum: New to Ubuntu
---

### Post by ImThatNerd on 2008-05-21
Well this is the only thing that I seem to not be able to grasp on Ubuntu, and that is navigating and doing commands in terminal. 

I have the folder in home and it is called 'lmms-0.3.2'

And I am suppose to do:

```
   Go to the directory containing the package's source code and type:

     autoreconf -is
     ./configure
     make install
     lmms
```

The code above I will be able to do fine, it is just I am unsure how to really get to that folder. I can get into home, but not sure after that since  when I do 'cd /home/lmms-0.3.2' it says no file or directory. Any help would be great.

---

### Post by sdennie on 2008-05-21
I think you are looking for ~/lmms-0.3.2.  Also, remember that bash has completion rules that can help you.  Type "cd " and then hit tab and it should show you the directories you can cd into.

---

### Post by Monicker on 2008-05-21
Are you sure its directly under /home, or did you download and extract it to your desktop?  Use the ls command to list the directory contents.

```
ls /home/username
ls /home/username/Desktop
```

---

### Post by iaculallad on 2008-05-21
Try:

cd /home/your_user_name/lmms-0.3.2

on the terminal

Or list (and paste it here) the content of your Desktop and /home/your_user_name

ls ~/Desktop
ls /home/your_user_name

---

### Post by ImThatNerd on 2008-05-21
> **iaculallad said:**
> Try:

cd /home/your_user_name/lmms-0.3.2

on the terminal

Or list (and paste it here) the content of your Desktop and /home/your_user_name

ls ~/Desktop
ls /home/your_user_name

Alright great that first one worked, can't believe I forgot my name part. 

But I tried installing my program and it didn't work:

```
ryan@ryan-desktop:~$ /home/ryan/lmms-0.3.2
bash: /home/ryan/lmms-0.3.2: is a directory
ryan@ryan-desktop:~$ cd
cd          cdparanoia  cdrdao      cdrecord    
ryan@ryan-desktop:~$ cd /home/ryan/lmms-0.3.2
ryan@ryan-desktop:~/lmms-0.3.2$ autoreconf -is
aclocal: couldn't open directory `m4': No such file or directory
autoreconf: aclocal failed with exit status: 1
ryan@ryan-desktop:~/lmms-0.3.2$ ./configure
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking for g++... g++
checking for C++ compiler default output file name... a.out
checking whether the C++ compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables... 
checking for suffix of object files... o
checking whether we are using the GNU C++ compiler... yes
checking whether g++ accepts -g... yes
checking for style of include used by make... GNU
checking dependency style of g++... gcc3
checking for gcc... gcc
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ISO C89... none needed
checking dependency style of gcc... gcc3
checking whether ln -s works... yes
checking how to run the C preprocessor... gcc -E
checking for grep that handles long lines and -e... /bin/grep
checking for egrep... /bin/grep -E
checking whether gcc needs -traditional... no
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking for a sed that does not truncate output... /bin/sed
checking for ld used by gcc... /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... yes
checking for /usr/bin/ld option to reload object files... -r
checking for BSD-compatible nm... /usr/bin/nm -B
checking how to recognize dependent libraries... pass_all
checking for ANSI C header files... yes
checking for sys/types.h... yes
checking for sys/stat.h... yes
checking for stdlib.h... yes
checking for string.h... yes
checking for memory.h... yes
checking for strings.h... yes
checking for inttypes.h... yes
checking for stdint.h... yes
checking for unistd.h... yes
checking dlfcn.h usability... yes
checking dlfcn.h presence... yes
checking for dlfcn.h... yes
checking how to run the C++ preprocessor... g++ -E
checking for g77... no
checking for xlf... no
checking for f77... no
checking for frt... no
checking for pgf77... no
checking for cf77... no
checking for fort77... no
checking for fl32... no
checking for af77... no
checking for xlf90... no
checking for f90... no
checking for pgf90... no
checking for pghpf... no
checking for epcf90... no
checking for gfortran... no
checking for g95... no
checking for xlf95... no
checking for f95... no
checking for fort... no
checking for ifort... no
checking for ifc... no
checking for efc... no
checking for pgf95... no
checking for lf95... no
checking for ftn... no
checking whether we are using the GNU Fortran 77 compiler... no
checking whether  accepts -g... no
checking the maximum length of command line arguments... 98304
checking command to parse /usr/bin/nm -B output from gcc object... ok
checking for objdir... .libs
checking for ar... ar
checking for ranlib... ranlib
checking for strip... strip
checking if gcc supports -fno-rtti -fno-exceptions... no
checking for gcc option to produce PIC... -fPIC
checking if gcc PIC flag -fPIC works... yes
checking if gcc static flag -static works... yes
checking if gcc supports -c -o file.o... yes
checking whether the gcc linker (/usr/bin/ld) supports shared libraries... yes
checking whether -lc should be explicitly linked in... no
checking dynamic linker characteristics... GNU/Linux ld.so
checking how to hardcode library paths into programs... immediate
checking whether stripping libraries is possible... yes
checking if libtool supports shared libraries... yes
checking whether to build shared libraries... yes
checking whether to build static libraries... yes
configure: creating libtool
appending configuration tag "CXX" to libtool
checking for ld used by g++... /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... yes
checking whether the g++ linker (/usr/bin/ld) supports shared libraries... yes
checking for g++ option to produce PIC... -fPIC
checking if g++ PIC flag -fPIC works... yes
checking if g++ static flag -static works... yes
checking if g++ supports -c -o file.o... yes
checking whether the g++ linker (/usr/bin/ld) supports shared libraries... yes
checking dynamic linker characteristics... GNU/Linux ld.so
(cached) (cached) checking how to hardcode library paths into programs... immediate
appending configuration tag "F77" to libtool
checking platform to build for... Linux, will enable support for it
checking for X... libraries , headers 
checking for gethostbyname... yes
checking for connect... yes
checking for remove... yes
checking for shmat... yes
checking for IceConnectionNumber in -lICE... yes
checking QTDIR... configure: error: *** QTDIR must be defined, or --with-qtdir option given
ryan@ryan-desktop:~/lmms-0.3.2$ make install
make: *** No rule to make target `install'.  Stop.
ryan@ryan-desktop:~/lmms-0.3.2$ lmms
The program 'lmms' is currently not installed.  You can install it by typing:
sudo apt-get install lmms
bash: lmms: command not found
ryan@ryan-desktop:~/lmms-0.3.2$ make install lmms
make: *** No rule to make target `install'.  Stop.
ryan@ryan-desktop:~/lmms-0.3.2$ 

```

Also

```
ryan@ryan-desktop:~/lmms-0.3.2$ make
make: *** No targets specified and no makefile found.  Stop.
ryan@ryan-desktop:~/lmms-0.3.2$ make check
make: *** No rule to make target `check'.  Stop.
ryan@ryan-desktop:~/lmms-0.3.2$ make install
make: *** No rule to make target `install'.  Stop.

```

So I installed the same applicated from the package manager but it never created an icon or link in the Applications menu for me to launch it.

---

### Post by iaculallad on 2008-05-21
Post the result of ls when entered on the terminal:

ryan@ryan-desktop:~/lmms-0.3.2$ls

---

### Post by ImThatNerd on 2008-05-21
> **iaculallad said:**
> Post the result of ls when entered on the terminal:

ryan@ryan-desktop:~/lmms-0.3.2$ls

Well I had it in the home folder, so I moved it to the desktop and put 

~/lmms-0.3.2$ls

and got

ryan@ryan-desktop:~$ ~/lmms-0.3.2$ls
bash: /home/ryan/lmms-0.3.2: is a directory

---

### Post by ad_267 on 2008-05-21
> So I installed the same applicated from the package manager but it never created an icon or link in the Applications menu for me to launch it.

Try typing lmms into a terminal to see if it installed properly. If it has then you can create a new launcher in the menu by going to System - Preferences - Main Menu.

---

### Post by ImThatNerd on 2008-05-21
> **ad_267 said:**
> Try typing lmms into a terminal to see if it installed properly. If it has then you can create a new launcher in the menu by going to System - Preferences - Main Menu.

Alright I installed through the package manager and just typed that in and it launched fine. Going to add a launcher in the morning.

Thanks everyone for the help, especially iaculallad.

---

### Post by Xiong Chiamiov on 2008-05-21
I believe all that iaculallad is trying to do is to get you to post what's in the directory.  You can do that by cd-ing to it, then entering the ls command.

That said, since you've gotten it installed through the repos (always a better choice), you should be able to run it by pressing alt+f2 and entering the command lmms.  If that works, you can [create a menu entry for it]("http://www.ubuntugeek.com/howto-add-entries-in-gnome-menu.html").

---

### Post by iaculallad on 2008-05-21
You're very much welcome ImThatNerd. Go Ubuntu

---

