---
title: "gtkmm3.0 &amp;&amp; libgtkmm3.0-dev can't compile"
date: 2011-05-12
forum: Programming Talk
---

### Post by johnny3k on 2011-05-12
I need gtkmm 3.0 for tutorial 
[http://developer.gnome.org/gtkmm-tutorial/stable/sec-install-unix-and-linux.html.en](http://developer.gnome.org/gtkmm-tutorial/stable/sec-install-unix-and-linux.html.en)

unfortunately i can't compile it.
> 
ubuntu@ubuntu-machine:~/projects/gtkmm-3.0.1$ ./configure
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for a thread-safe mkdir -p... /bin/mkdir -p
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking how to create a pax tar archive... gnutar
checking whether to enable maintainer-specific portions of Makefiles... no
checking whether make supports GNU make features... yes
checking for g++... g++
checking whether the C++ compiler works... yes
checking for C++ compiler default output file name... a.out
checking for suffix of executables... 
checking whether we are cross compiling... no
checking for suffix of object files... o
checking whether we are using the GNU C++ compiler... yes
checking whether g++ accepts -g... yes
checking for style of include used by make... GNU
checking dependency style of g++... gcc3
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking for gcc... gcc
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ISO C89... none needed
checking dependency style of gcc... gcc3
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
checking whether we are using the GNU C++ compiler... (cached) yes
checking whether g++ accepts -g... (cached) yes
checking dependency style of g++... (cached) gcc3
checking how to run the C++ preprocessor... g++ -E
checking for objdir... .libs
checking if gcc supports -fno-rtti -fno-exceptions... no
checking for gcc option to produce PIC... -fPIC -DPIC
checking if gcc PIC flag -fPIC -DPIC works... yes
checking if gcc static flag -static works... yes
checking if gcc supports -c -o file.o... yes
checking if gcc supports -c -o file.o... (cached) yes
checking whether the gcc linker (/usr/bin/ld) supports shared libraries... yes
checking whether -lc should be explicitly linked in... no
checking dynamic linker characteristics... GNU/Linux ld.so
checking how to hardcode library paths into programs... immediate
checking whether stripping libraries is possible... yes
checking if libtool supports shared libraries... yes
checking whether to build shared libraries... yes
checking whether to build static libraries... no
checking for ld used by g++... /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... yes
checking whether the g++ linker (/usr/bin/ld) supports shared libraries... yes
checking for g++ option to produce PIC... -fPIC -DPIC
checking if g++ PIC flag -fPIC -DPIC works... yes
checking if g++ static flag -static works... yes
checking if g++ supports -c -o file.o... yes
checking if g++ supports -c -o file.o... (cached) yes
checking whether the g++ linker (/usr/bin/ld) supports shared libraries... yes
checking dynamic linker characteristics... GNU/Linux ld.so
checking how to hardcode library paths into programs... immediate
checking for native Windows host... no
checking for pkg-config... /usr/bin/pkg-config
checking pkg-config is at least version 0.9.0... yes
checking for GDKMM... no
configure: error: Package requirements (giomm-2.4 >= 2.27.93 pangomm-1.4 >= 2.27.1 gtk+-3.0 >= 3.0.0 cairomm-1.0 >= 1.9.2 gdk-pixbuf-2.0 >= 2.22.1) were not met:

No package 'giomm-2.4' found
No package 'pangomm-1.4' found
No package 'gtk+-3.0' found
No package 'cairomm-1.0' found
No package 'gdk-pixbuf-2.0' found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables GDKMM_CFLAGS
and GDKMM_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details


i can't find package giomm

---

### Post by johnny3k on 2011-05-12
update 
configure: error: Package requirements (giomm-2.4 >= 2.27.93 pangomm-1.4 >= 2.27.1 gtk+-3.0 >= 3.0.0 cairomm-1.0 >= 1.9.2 gdk-pixbuf-2.0 >= 2.22.1) were not met:

No package 'gtk+-3.0' found   i try install libgtk package..

---

### Post by johnny3k on 2011-05-12
finally i compile 'gtkmm-3.0.1' and try compile sample program
> 
#include <gtkmm.h>
int main(int argc, char *argv[])
{
  Gtk::Main kit(argc, argv);
  Gtk::Window window;
  Gtk::Main::run(window);
  return EXIT_SUCCESS;
}ubuntu@ubuntu-machine:~/projects$ g++ gtk_sample.cpp -o gtk_sample `pkg-config gtkmm-3.0 --cflags --libs`
ubuntu@ubuntu-machine:~/projects$ ./gtk_sample 
./gtk_sample: error while loading shared libraries: libgtkmm-3.0.so.1: cannot open shared object file: No such file or directory
ubuntu@ubuntu-machine:~/projects$ 

any idea to make it working?

ps.  thanks all i solve my problem

---

### Post by Robots on 2011-05-19
[SIZE=2]**Hello Johnny3k,**[/SIZE]

I am in the exact same situation! I upgraded from gtkmm2.4 where this example worked 

```
                              
#include <gtkmm.h>
int main(int argc, char *argv[])
{
  Gtk::Main kit(argc, argv);
  Gtk::Window window;
  Gtk::Main::run(window);
  return EXIT_SUCCESS;
}                      
```
to gtkmm3.0 where above code gives me the same error as you are getting. 
(This error)
```
./gtk_sample: error while loading shared libraries: libgtkmm-3.0.so.1: cannot open shared object file: No such file or directory
ubuntu@ubuntu-machine:~/projects$
```

Did you find a solution to this? Does anyone know how to solve this? I am very new to this, excuse my noviceness.

Robots

---

### Post by Earsplit on 2011-06-24
Same problem... any ideas?

---

### Post by Earsplit on 2011-06-24
Nevermind... sorry for resurrecting this...

If anyone comes across this thread as a search, I fixed this problem by running

```
$  sudo ldconfig
```

---

