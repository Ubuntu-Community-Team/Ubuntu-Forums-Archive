---
title: "Can't get adobe flash plugin working for mozilla"
date: 2011-09-21
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by bikewrecker on 2011-09-21
Hey guys, Ubuntu noob here. I'm having trouble installing the adobe flash 11 plugin for my firefox. 

When I go to youtube and try to watch a video it says i need upgrade my adobe flash player to watch the video, so i click on the 'update your adobe flash player' link and it takes me a few more pages to get to download the linux 64bit adobe flash plugin file. 

After it's downloaded I have no idea what to do. It give me a tarball with the folder usr and libflashplayer.so in it. I read a post that said to extract it to the "~/.mozilla/plugin" folder which doesn't appear to exist...so I'm assuming that there is some command in the terminal that will extract the files to this invisible location, but I don't know what it is or if that's even the right thing to do. It's frustrating how installing ANYTHING in ubuntu turns out to be a 7 hour project...

Has anyone else had this problem?  It's probably a really easy fix I just have no idea what I'm doing in this OS. 

Thanks for your help!

---

### Post by flipper T on 2011-09-21
install & run the "flash aid" add on in firefox

this should solve most problems

should take about 1 minute

:)

---

### Post by garvinrick4 on 2011-09-21
>  with the folder usr and[COLOR=Red] libflashplayer.so[/COLOR]
It go's in /usr/lib/mozilla/plugins (in Ubuntu)
You are better off just going to tools to addons to flash aid in search.
Install flash aid.
in upper right corner of firefox page there will be a red circle with and f in it.
click on that choose one of the three ways to run the script. Will do it all
for you, you just do what it tells you.

---

### Post by Quackers on 2011-09-21
+1 for flash aid :-)

---

### Post by bikewrecker on 2011-09-21
Yea ok the flash aid worked. thanks guys so much for the replies!

Why wouldn't mozilla just come with that? It seems like it's an absolute necessity...

---

### Post by Quackers on 2011-09-21
Didn't forum member Lovinglinux write that, or at least have a hand in its writing?

---

### Post by flipper T on 2011-09-21
> **bikewrecker said:**
> 

Why wouldn't mozilla just come with that? It seems like it's an absolute necessity...

the use of flash, being non-open source, is rather looked down upon by certain members of this community.

---

### Post by garvinrick4 on 2011-09-21
> Didn't forum member Lovinglinux write that, or at least have a hand in its writing? As far as I know lovinglinux wrote the script and set it up as an addon and
improves it everytime I turn around. All these users that flash aid assists in their flash
woes should say a big thank you to lovinglinux. We are just the messengers of his work.
It is okay with me, their are some users that make you want to strive to be better.

---

### Post by seeker5528 on 2011-09-22
> **bikewrecker said:**
> After it's downloaded I have no idea what to do. It give me a tarball with the folder usr and libflashplayer.so in it. I read a post that said to extract it to the "~/.mozilla/plugin" folder which doesn't appear to exist...so I'm assuming that there is some command in the terminal that will extract the files to this invisible location

Personally I prefer doing something like....

```
cd ~/.mozilla
mkdir plugins
cd plugins
tar xvzf ~/Downloads/Flash/flashplayer11_rc1_install_lin_64_090611.tar.gz
```

Alternatively, assuming you are using Nautilus, you could click 'View --> show hidden files', then use Nautilus to extract the files, copy the extrated file and directory, create the plugins directory, then paste.

Should work similarly with other file managers, but the option to view hidden files may be in a different place.

To me sticking unmanaged files in a managed location (like flashaid does when it downloads flash from adobe) is a bad habit to get into.

Later, Seeker

---

### Post by ratcheer on 2011-09-22
I have had no problem whatsoever with simply copying the .so file to the mozilla plugins directory.

Tim

---

### Post by tekstr1der on 2011-09-22
> **seeker5528 said:**
> Personally I prefer doing something like....

```
cd ~/.mozilla
mkdir plugins
cd plugins
tar xvzf ~/Downloads/Flash/flashplayer11_rc1_install_lin_64_090611.tar.gz
```

Alternatively, assuming you are using Nautilus, you could click 'View --> show hidden files', then use Nautilus to extract the files, copy the extrated file and directory, create the plugins directory, then paste.

Should work similarly with other file managers, but the option to view hidden files may be in a different place.

To me sticking unmanaged files in a managed location (like flashaid does when it downloads flash from adobe) is a bad habit to get into.

Later, Seeker


Ditto!

If you have a multi-user machine, and need flash player installed for all users, then you'd put libflashplayer.so in /usr/lib/mozilla/plugins rather than your ~/

---

### Post by bikewrecker on 2011-09-22
> **seeker5528 said:**
> Personally I prefer doing something like....

```
cd ~/.mozilla
mkdir plugins
cd plugins
tar xvzf ~/Downloads/Flash/flashplayer11_rc1_install_lin_64_090611.tar.gz
```Alternatively, assuming you are using Nautilus, you could click 'View --> show hidden files', then use Nautilus to extract the files, copy the extrated file and directory, create the plugins directory, then paste.

Should work similarly with other file managers, but the option to view hidden files may be in a different place.

To me sticking unmanaged files in a managed location (like flashaid does when it downloads flash from adobe) is a bad habit to get into.

Later, Seeker
Ok, that's awesome! But where do you learn how to do all this stuff? I would love to use the terminal more to do all my stuff, but I simply don't know enough yet. 

so what you're doing is you're going to the hidden mozilla folder, making a plugins file then extracting the downloaded tarball into your new plugins folder right? I guess I just never know where to extract downloaded tarballs to in order to get them running. 

thanks again for the replies guys! I really appreciate it!

---

### Post by garvinrick4 on 2011-09-22
> I guess I just never know where to extract downloaded tarballs to in order to get them running. This is a bit of Linux 101.  It seems daunting but there are INSTALL and READ me files to help.
Hope this helps just a bit. Seeker5528 has a great skill set if you can get him to give some 101 since
he is in this thread. Have a nice day and enjoy your Ubuntu. (Stick with it and read, read and read.)
Nice little pdf book in my signature.

```
# 1: Uncompress tarball

To uncompress them, execute the following command(s) depending on the extension:
$ tar zxf file.tar.gz
$ tar zxf file.tgz
$ tar jxf file.tar.bz2
$ tar jxf file.tbz2

Now change directory
$ ls
$ cd path-to-software/

# 2: Build and install software

Generally you need to type 3 commands as follows for building and compiling software:
# ./configure
# make
# make install

Where,

   [COLOR=Red] ./configure[/COLOR] will configure the software to ensure your system has the 
    necessary functionality and libraries to successfully compile the package
  [COLOR=Red]  make[/COLOR] will compile all the source files into executable binaries.
    Finally, [COLOR=Red]make install [/COLOR]will install the binaries and any supporting
    files into the appropriate locations.

# 3: Read INSTALL / README  comes with these files to help with 
       installation and build instructions.


```

---

### Post by bikewrecker on 2011-09-22
> **garvinrick4 said:**
> This is a bit of Linux 101.  It seems daunting but there are INSTALL and READ me files to help.
Hope this helps just a bit. Seeker5528 has a great skill set if you can get him to give some 101 since
he is in this thread. Have a nice day and enjoy your Ubuntu. (Stick with it and read, read and read.)
Nice little pdf book in my signature.

```
# 1: Uncompress tarball

To uncompress them, execute the following command(s) depending on the extension:
$ tar zxf file.tar.gz
$ tar zxf file.tgz
$ tar jxf file.tar.bz2
$ tar jxf file.tbz2

Now change directory
$ ls
$ cd path-to-software/

# 2: Build and install software

Generally you need to type 3 commands as follows for building and compiling software:
# ./configure
# make
# make install

Where,

   [COLOR=Red] ./configure[/COLOR] will configure the software to ensure your system has the 
    necessary functionality and libraries to successfully compile the package
  [COLOR=Red]  make[/COLOR] will compile all the source files into executable binaries.
    Finally, [COLOR=Red]make install [/COLOR]will install the binaries and any supporting
    files into the appropriate locations.

# 3: Read INSTALL / README  comes with these files to help with 
       installation and build instructions.


```

Oh wow, that's going to help so much! Thank you! I'm saving this to a .txt on my computer till I have it down.  Thanks again!

---

### Post by bikewrecker on 2011-09-22
Ok I'm trying to get conky installed on my computer so heres what i did 
```

daniel@daniel-EP45-UD3L:/etc/conky$ sudo tar zxf ~/Downloads/conky-1.8.1.tar.gz
daniel@daniel-EP45-UD3L:/etc/conky$ ls
conky-1.8.1  conky.conf  conky_no_x11.conf
daniel@daniel-EP45-UD3L:/etc/conky$ ./configure
bash: ./configure: No such file or directory
daniel@daniel-EP45-UD3L:/etc/conky$ sudo ./configure
sudo: ./configure: command not found
daniel@daniel-EP45-UD3L:/etc/conky$ cd conky-1.8.1
daniel@daniel-EP45-UD3L:/etc/conky/conky-1.8.1$ ls
aclocal.m4  config.guess  configure.ac.in  extras      m4           README
AUTHORS     config.rpath  COPYING          INSTALL     Makefile.am  src
autogen.sh  config.sub    data             install-sh  Makefile.in  text2c.sh
ChangeLog   configure     depcomp          ltmain.sh   missing      TODO
compile     configure.ac  doc              lua         NEWS
daniel@daniel-EP45-UD3L:/etc/conky/conky-1.8.1$ ./configure
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for a thread-safe mkdir -p... /bin/mkdir -p
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking for gcc... gcc
checking whether the C compiler works... yes
checking for C compiler default output file name... a.out
checking for suffix of executables... 
checking whether we are cross compiling... no
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ISO C89... none needed
checking for style of include used by make... GNU
checking dependency style of gcc... gcc3
checking build system type... x86_64-unknown-linux-gnu
checking host system type... x86_64-unknown-linux-gnu
checking for a sed that does not truncate output... /bin/sed
checking for grep that handles long lines and -e... /bin/grep
checking for egrep... /bin/grep -E
checking for fgrep... /bin/grep -F
checking for ld used by gcc... /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... yes
checking for BSD- or MS-compatible name lister (nm)... /usr/bin/nm -B
checking the name lister (/usr/bin/nm -B) interface... BSD nm
checking whether ln -s works... yes
checking the maximum length of command line arguments... 1572864
checking whether the shell understands some XSI constructs... yes
checking whether the shell understands "+="... yes
checking for /usr/bin/ld option to reload object files... -r
checking for objdump... objdump
checking how to recognize dependent libraries... pass_all
checking for ar... ar
checking for strip... strip
checking for ranlib... ranlib
checking command to parse /usr/bin/nm -B output from gcc object... ok
checking how to run the C preprocessor... gcc -E
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
checking for dlfcn.h... yes
checking for objdir... .libs
checking if gcc supports -fno-rtti -fno-exceptions... no
checking for gcc option to produce PIC... -fPIC -DPIC
checking if gcc PIC flag -fPIC -DPIC works... yes
checking if gcc static flag -static works... yes
checking if gcc supports -c -o file.o... yes
checking if gcc supports -c -o file.o... (cached) yes
checking whether the gcc linker (/usr/bin/ld -m elf_x86_64) supports shared libraries... yes
checking whether -lc should be explicitly linked in... no
checking dynamic linker characteristics... GNU/Linux ld.so
checking how to hardcode library paths into programs... immediate
checking whether stripping libraries is possible... yes
checking if libtool supports shared libraries... yes
checking whether to build shared libraries... yes
checking whether to build static libraries... yes
checking whether gcc and cc understand -c and -o together... yes
checking for pkg-config... yes
checking for pkg-config... /usr/bin/pkg-config
checking pkg-config is at least version 0.19... yes
checking for fopencookie... yes
checking for funopen... no
checking for X11... yes
checking for LUA... no
checking for LUA51... no
checking for LUA51... configure: error: Package requirements (lua5.1 >= 5.1) were not met:

No package 'lua5.1' found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables LUA51_CFLAGS
and LUA51_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.

daniel@daniel-EP45-UD3L:/etc/conky/conky-1.8.1$ make
make: *** No targets specified and no makefile found.  Stop.
daniel@daniel-EP45-UD3L:/etc/conky/conky-1.8.1$ make install
make: *** No rule to make target `install'.  Stop.

```
Do you happen to know what I did wrong?

---

### Post by flipper T on 2011-09-22
this is an enormous conky thread on the main "general help" board. that would be the place to start

---

### Post by ronacc on 2011-09-22
> **bikewrecker said:**
> Ok I'm trying to get conky installed on my computer so heres what i did 
```

daniel@daniel-EP45-UD3L:/etc/conky$ sudo tar zxf ~/Downloads/conky-1.8.1.tar.gz
daniel@daniel-EP45-UD3L:/etc/conky$ ls
conky-1.8.1  conky.conf  conky_no_x11.conf
daniel@daniel-EP45-UD3L:/etc/conky$ ./configure
bash: ./configure: No such file or directory
daniel@daniel-EP45-UD3L:/etc/conky$ sudo ./configure
sudo: ./configure: command not found
daniel@daniel-EP45-UD3L:/etc/conky$ cd conky-1.8.1
daniel@daniel-EP45-UD3L:/etc/conky/conky-1.8.1$ ls
aclocal.m4  config.guess  configure.ac.in  extras      m4           README
AUTHORS     config.rpath  COPYING          INSTALL     Makefile.am  src
autogen.sh  config.sub    data             install-sh  Makefile.in  text2c.sh
ChangeLog   configure     depcomp          ltmain.sh   missing      TODO
compile     configure.ac  doc              lua         NEWS
daniel@daniel-EP45-UD3L:/etc/conky/conky-1.8.1$ ./configure
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for a thread-safe mkdir -p... /bin/mkdir -p
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking for gcc... gcc
checking whether the C compiler works... yes
checking for C compiler default output file name... a.out
checking for suffix of executables... 
checking whether we are cross compiling... no
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ISO C89... none needed
checking for style of include used by make... GNU
checking dependency style of gcc... gcc3
checking build system type... x86_64-unknown-linux-gnu
checking host system type... x86_64-unknown-linux-gnu
checking for a sed that does not truncate output... /bin/sed
checking for grep that handles long lines and -e... /bin/grep
checking for egrep... /bin/grep -E
checking for fgrep... /bin/grep -F
checking for ld used by gcc... /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... yes
checking for BSD- or MS-compatible name lister (nm)... /usr/bin/nm -B
checking the name lister (/usr/bin/nm -B) interface... BSD nm
checking whether ln -s works... yes
checking the maximum length of command line arguments... 1572864
checking whether the shell understands some XSI constructs... yes
checking whether the shell understands "+="... yes
checking for /usr/bin/ld option to reload object files... -r
checking for objdump... objdump
checking how to recognize dependent libraries... pass_all
checking for ar... ar
checking for strip... strip
checking for ranlib... ranlib
checking command to parse /usr/bin/nm -B output from gcc object... ok
checking how to run the C preprocessor... gcc -E
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
checking for dlfcn.h... yes
checking for objdir... .libs
checking if gcc supports -fno-rtti -fno-exceptions... no
checking for gcc option to produce PIC... -fPIC -DPIC
checking if gcc PIC flag -fPIC -DPIC works... yes
checking if gcc static flag -static works... yes
checking if gcc supports -c -o file.o... yes
checking if gcc supports -c -o file.o... (cached) yes
checking whether the gcc linker (/usr/bin/ld -m elf_x86_64) supports shared libraries... yes
checking whether -lc should be explicitly linked in... no
checking dynamic linker characteristics... GNU/Linux ld.so
checking how to hardcode library paths into programs... immediate
checking whether stripping libraries is possible... yes
checking if libtool supports shared libraries... yes
checking whether to build shared libraries... yes
checking whether to build static libraries... yes
checking whether gcc and cc understand -c and -o together... yes
checking for pkg-config... yes
checking for pkg-config... /usr/bin/pkg-config
checking pkg-config is at least version 0.19... yes
checking for fopencookie... yes
checking for funopen... no
checking for X11... yes
checking for LUA... no
checking for LUA51... no
checking for LUA51... configure: error: Package requirements (lua5.1 >= 5.1) were not met:

No package 'lua5.1' found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables LUA51_CFLAGS
and LUA51_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.

daniel@daniel-EP45-UD3L:/etc/conky/conky-1.8.1$ make
make: *** No targets specified and no makefile found.  Stop.
daniel@daniel-EP45-UD3L:/etc/conky/conky-1.8.1$ make install
make: *** No rule to make target `install'.  Stop.

```
Do you happen to know what I did wrong?

often when compiling from source  you will find that some files are needed to compile them , the configure file will tell you which ones , when it stops ( like now ) because it can't find a file , open synaptic and search for that file and install it ,then rerun the configure.script ,
often running apt-get build-dep <name of source> in the directory will pull in what you need .

---

### Post by bikewrecker on 2011-09-22
> **ronacc said:**
> often when compiling from source  you will find that some files are needed to compile them , the configure file will tell you which ones , when it stops ( like now ) because it can't find a file , open synaptic and search for that file and install it ,then rerun the configure.script ,
often running apt-get build-dep <name of source> in the directory will pull in what you need .
Ok so i went into synaptic pm and downloaded lua5.1 but it still didnt work

I noticed that if I type 'conky' in the terminal it makes a conky monitor but I can't do anything with it. none of the options in the man file seem to work. Think I should just email the conky site about my problem?

---

### Post by cariboo on 2011-09-22
This is the thread to check to solve all your conky problems:

[http://ubuntuforums.org/showthread.php?t=281865](http://ubuntuforums.org/showthread.php?t=281865)

---

### Post by rbrick49 on 2011-09-22
did you login as root on the terminal

---

### Post by seeker5528 on 2011-09-22
> **bikewrecker said:**
> Ok, that's awesome! But where do you learn how to do all this stuff?

Many moonlit nights of banging your head on the..... uhm.... I mean reading man pages, googling, etc..:p 

Here's a starting point...

[http://www.trainsignal.com/blog/linux-command-line-101](http://www.trainsignal.com/blog/linux-command-line-101)

Man pages are not really designed to be tutorials, but sometimes they are the only documentation you get, if you are at the command line reading some documentation in '/usr/share/doc/somepackage' and some of the documentation is compressed you can use zcat or zless to view it without having to docompress it first, then use cat or less, there is also zgrep and zdiff for their relative capabilities.

Looks like yelp (gnome help) decided to be much less helpful than it used to be, khelpcenter still lets you browse man and info pages.

Later, Seeker

---

