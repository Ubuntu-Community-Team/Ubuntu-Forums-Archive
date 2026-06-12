---
title: "Need help with Conky"
date: 2012-07-13
forum: New to Ubuntu
---

### Post by Mkellers on 2012-07-13
Hi :)

I'm pretty new to Ubuntu- and Linux in general for that matter- so don't berate me if the solution here is seemingly obvious :-P

So I downloaded Conky from this website : [http://conky.sourceforge.net/](http://conky.sourceforge.net/)

I extracted the folder from the Terminal, then proceeded to configure the source files. Here's what came up:    	 	 	 	 	 	    checking for a BSD-compatible install... /usr/bin/install -c 
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
 checking how to print strings... printf 
 checking for ld used by gcc... /usr/bin/ld 
 checking if the linker (/usr/bin/ld) is GNU ld... yes 
 checking for BSD- or MS-compatible name lister (nm)... /usr/bin/nm -B 
 checking the name lister (/usr/bin/nm -B) interface... BSD nm 
 checking whether ln -s works... yes 
 checking the maximum length of command line arguments... 1572864 
 checking whether the shell understands some XSI constructs... yes 
 checking whether the shell understands "+="... yes 
 checking how to convert x86_64-unknown-linux-gnu file names to x86_64-unknown-linux-gnu format... func_convert_file_noop 
 checking how to convert x86_64-unknown-linux-gnu file names to toolchain format... func_convert_file_noop 
 checking for /usr/bin/ld option to reload object files... -r 
 checking for objdump... objdump 
 checking how to recognize dependent libraries... pass_all 
 checking for dlltool... no 
 checking how to associate runtime and link libraries... printf %s\n 
 checking for ar... ar 
 checking for archiver @FILE support... @ 
 checking for strip... strip 
 checking for ranlib... ranlib 
 checking command to parse /usr/bin/nm -B output from gcc object... ok 
 checking for sysroot... no 
 checking for mt... mt 
 checking if mt is a manifest tool... no 
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
 checking ncurses.h usability... no 
 checking ncurses.h presence... no 
 checking for ncurses.h... no 
 configure: error: required header(s) not found


To be honest I'm not exactly sure what to do here :/ Hence the coming on the forum lol. Is the config error because of something wrong with the release itself or do I have to go and do something??


I would be SO grateful if someone could help me with this! xD

---

### Post by TheAlliedFleet on 2012-07-13
Conky should be in the Software centre, just search for it and download and the software centre should do the rest. Just in case you don't know you launch Conky from the Terminal :)

---

### Post by sandyd on 2012-07-13
Go to unity dash -> type in "terminal", select terminal
type in
```

sudo apt-get install conky

```

---

### Post by Kopkins on 2012-07-13
Do:
```
sudo apt-get install conky
```
as the previous poster said. 

If you have a conky config file you want to use, run this from terminal:
```
conky -c /path/to/conky/config
```

Or you can move the file to the default conky config location. 
```
mv /path/to/conky/config /home/your-username/.conkyrc
```
then,
```
conky
```

Best of luck with conky, it's a very useful program.
Kopkins

---

### Post by Shadius on 2012-07-13
The folks over [here]("http://ubuntuforums.org/showthread.php?t=281865&page=2017") can probably better assist you. They deal with all things Conky! Very good thread to subscribe to.

The method that was suggested to me is the following:
```
sudo add-apt-repository ppa:vincent-c/conky
sudo apt-get update
```

This method adds the PPA. I noticed that Ubuntu Software Center still has the previous version of 1.8.1 instead of the newer version that the conky site itself has. I was told that adding the PPA was the best method.

---

### Post by Cheesemill on 2012-07-13
> **Mkellers said:**
> So I downloaded Conky from this website : [http://conky.sourceforge.net/](http://conky.sourceforge.net/)

Your problem is that you downloaded software from a website, there is no need to do this when you are using Ubuntu. Instead all software should be installed from the Software Center or by using the apt-get command in a terminal:
```
sudo apt-get install conky
```
For more information:
[http://psychocats.net/ubuntu/installingsoftware](http://psychocats.net/ubuntu/installingsoftware)

---

### Post by Mkellers on 2012-07-14
Thanks guys! xD

---

