---
title: "Trying to build &quot;the machine emulator&quot; - Linker problem"
date: 2011-02-02
forum: Programming Talk
---

### Post by ansar68pk on 2011-02-02
I need to emulate a Sparc2 workstation on my Maverick box. I tried qemu but although x86 emulation works well, the sparc emulation with openboot prom is beset with problems.

Then I decided to experiment with "The Machine Emulator" by Matt Fredette. This, although in its early stages, still holds more promise than qemu as it can emulate Sparc2. Qemu can only do Sparc5 and above (correct me if i am wrong here).

I did a './configure' and 'make'. I encountered one problem during 'make' with -Werror (treat warnings as errors) as gcc did it's compile thing. I did a quick and dirty fix by editing the configure.sh file and removed -Werror from CFLAGS. 

Right now I am stuck with the 'make install' and the problem follows: 
.
.
.
test -z "/usr/local/lib/tme" || /bin/mkdir -p "/usr/local/lib/tme"
 /bin/bash ../../libtool --mode=install /usr/bin/install -c  'tme_ic_m68k.la' '/usr/local/lib/tme/tme_ic_m68k.la'
libtool: install: warning: relinking `tme_ic_m68k.la'
(cd /home/ansar/temp/tme-0.8/ic/m68k; /bin/bash ../../libtool  --tag=CC --mode=relink gcc -g -O2 -Wundef -Wall -module -version-info 0:0:0 -o tme_ic_m68k.la -rpath /usr/local/lib/tme m68k-opmap.lo m68k-insns.lo m68k-misc.lo m68010.lo m68020.lo m6888x.lo ../../libtme/libtme.la ../../generic/libtme-generic.la ../ieee754/libtme-ieee754.la )  

[COLOR=Red]*** Warning: Linking the shared library tme_ic_m68k.la against the loadable module
*** libtme-ieee754.so is not portable![/COLOR]
gcc -shared  .libs/m68k-opmap.o .libs/m68k-insns.o .libs/m68k-misc.o .libs/m68010.o .libs/m68020.o .libs/m6888x.o  -L/usr/local/lib -ltme -L/home/ansar/temp/tme-0.8/libltdl/.libs -ltme-generic -ltme-ieee754  -Wl,-soname -Wl,tme_ic_m68k.so.0 -o .libs/tme_ic_m68k.so.0.0.0
/usr/bin/ld:[COLOR=Orange] cannot find -ltme-ieee754[/COLOR]
collect2: ld returned 1 exit status
libtool: install: error: [COLOR=Orange]relink `tme_ic_m68k.la' with the above command before installing it[/COLOR]
make[4]: *** [install-pkglibLTLIBRARIES] Error 1
make[4]: Leaving directory `/home/ansar/temp/tme-0.8/ic/m68k'
make[3]: *** [install-am] Error 2
make[3]: Leaving directory `/home/ansar/temp/tme-0.8/ic/m68k'
make[2]: *** [install] Error 2
make[2]: Leaving directory `/home/ansar/temp/tme-0.8/ic/m68k'
make[1]: *** [install-recursive] Error 1
make[1]: Leaving directory `/home/ansar/temp/tme-0.8/ic'
make: *** [install-recursive] Error 1
#

Here is some info about my box.

# uname -r
2.6.35-25-generic

# gcc -v
Using built-in specs.
Target: i686-linux-gnu
Configured with: ../src/configure -v --with-pkgversion='Ubuntu/Linaro 4.4.4-14ubuntu5' --with-bugurl=file:///usr/share/doc/gcc-4.4/README.Bugs --enable-languages=c,c++,fortran,objc,obj-c++ --prefix=/usr --program-suffix=-4.4 --enable-shared --enable-multiarch --enable-linker-build-id --with-system-zlib --libexecdir=/usr/lib --without-included-gettext --enable-threads=posix --with-gxx-include-dir=/usr/include/c++/4.4 --libdir=/usr/lib --enable-nls --with-sysroot=/ --enable-clocale=gnu --enable-libstdcxx-debug --enable-objc-gc --enable-targets=all --disable-werror --with-arch-32=i686 --with-tune=generic --enable-checking=release --build=i686-linux-gnu --host=i686-linux-gnu --target=i686-linux-gnu
Thread model: posix
gcc version 4.4.5 (Ubuntu/Linaro 4.4.4-14ubuntu5) 
#

I want to know whether anyone has had a similar experience with this software or whether someone more familiar with linkers and libraries than me can help?

Thanks.

---

### Post by ansar68pk on 2011-02-02
I am sorry but I think I have posted this in the wrong forum! Admin is requested to move it to the building and compiling forum please!

---

### Post by SevenMachines on 2011-02-02
You'd need to look into the order things are being done in the Makefile to sort it out properly, maybe adding library paths or re-arranging the order of installation but a quick fix is just...
```
$ sudo cp ./ic/ieee754/.libs/libtme-ieee754.so* /usr/local/lib
$ sudo make install
```assuming you've installed to the default /usr/local/ anyway.  make uninstall will remove all these files.
As i say, not a fix but a hack :)

---

### Post by ansar68pk on 2011-02-02
Worked like a charm. The 'sudo make install' finished without any further warnings or errors.

However when the 'tmesh' (short for tme shell?) program was run, it complained about a missing libtmesh.so.0 shared library.

#tmesh
tmesh: error while loading shared libraries: libtmesh.so.0: cannot open shared object file: No such file or directory
#

In the same spirit I tried to copy this file from ./tmesh/.libs to /usr/local/lib as well as /usr/local/lib/tme ..... to no avail.

Had to do a 'export LD_LIBRARY_PATH=/usr/local/lib/tme' in the end as recommended by the author. In fact, I had done this export prior to the 'make install' as well but got the problem reported above and which was solved by copying the offending ieee754 lib(s) to /usr/local/lib.

The program works now or at least doesn't complain about mysteriously missing libraries any more.

#tmesh
usage: tmesh [OPTIONS] INITIAL-CONFIG
where OPTIONS are:
  --log LOGFILE          log to LOGFILE
  -c, --noninteractive   read no commands from standard input
#

I still don't know why Make couldn't find the libs in the first place and why I had to do the export LD_LIBRARY_PATH? Shouldn't these things already be in place? Or is there something different in the way gcc and ld handle things in ubuntu?

But the program works.... I am going to put it through it's paces now.

Thanks a lot for the help!

---

### Post by SevenMachines on 2011-02-02
The /usr/lib/local directory isn't on the system path by default so you need to either

* Add it at the command line, as you have done
```
$ LD_LIBRARY_PATH=/usr/local/lib runme
```
Note, this would probably have worked in the make install stage instead of the copying

* Add it to the system libs by creating a file

/etc/ld.so.conf.d/local.conf:
```
/usr/local/lib
```

Then update ld list
```
$ sudo ldconfig -v
```

---

### Post by ansar68pk on 2011-02-02
there was no local.conf in my /etc/ld.so.conf.d so i made one and added the line:

```
/usr/local/lib
```

followed by:

```
ldconfig -v
```

and I now also know how to use the CODE tag in my posts!

One keeps learning :p

---

### Post by SevenMachines on 2011-02-02
:) i'm always learning something new but forgetting something else! by the way, the local.conf name was only an example, it could have been called anything.

---

### Post by ansar68pk on 2011-02-02
Here is one last thing: 

I earlier mentioned that I had removed -Werror from CFLAGS to compile successfully. Being curious, I reinserted the -Werror flag in configure.sh and here is what we get with 'make':

```
 gcc -DHAVE_CONFIG_H -I. -I.. -I.. -I. -I. -pthread -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/gdk-pixbuf-2.0 -I/usr/include/pango-1.0 -I/usr/include/gio-unix-2.0/ -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/pixman-1 -I/usr/include/freetype2 -I/usr/include/libpng12 -D_TME_IMPL -DTME_NO_LOG -DTME_NO_DEBUG_LOCKS -DTME_NO_AUDIT_ATOMICS -DNDEBUG -g -O2 -Wundef -Wall [COLOR=DarkOrange]-Werror[/COLOR] -MT module.lo -MD -MP -MF .deps/module.Tpo -c module.c  -fPIC -DPIC -o .libs/module.o
[COLOR=DarkOrange]cc1: warnings being treated as errors[/COLOR]
module.c: In function 'tme_module_open':
[COLOR=DarkOrange]module.c:251: error: format not a string literal and no format arguments
module.c:261: error: format not a string literal and no format arguments
module.c:303: error: format not a string literal and no format arguments
module.c:328: error: format not a string literal and no format arguments[/COLOR]
make[4]: *** [module.lo] Error 1
make[4]: Leaving directory `/home/ansar/temp/tme-0.8/libtme'
make[3]: *** [all-recursive] Error 1
make[3]: Leaving directory `/home/ansar/temp/tme-0.8/libtme'
make[2]: *** [all] Error 2
make[2]: Leaving directory `/home/ansar/temp/tme-0.8/libtme'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/ansar/temp/tme-0.8'
make: *** [all] Error 2
```

Here is the function which offends gcc in module.c:
Note, that this code is not mine. (google 'the machine emulator'). However, I would definitely like to modify it to please gcc with -Werror flag thrown in.

```
/* this opens a module: */
int
tme_module_open(const char *module_fake_pathname, void **_module, [COLOR=DarkOrange]char **_output[/COLOR])
{
  char *module_raw_name;
  char *p1, c, *first_slash;
  FILE *modules_index;
  char *modules_dir;
  char line_buffer[1024];
  char **tokens;
  int tokens_count;
  char *module_basename;
  char *module_pathname;
  lt_dlhandle handle;
  struct tme_module *module;
  
  /* strip leading slashes from the fake module pathname: */
  for (; *module_fake_pathname == '/'; module_fake_pathname++);

  /* turn all of the non-alphanumerics in the fake module pathname
     into underscores, and remember where the first slash was: */
  module_raw_name = tme_strdup(module_fake_pathname);
  first_slash = NULL;
  for (p1 = module_raw_name;
       (c = *p1) != '\0';
       p1++) {
    if (!isalnum((unsigned char) c)) {
      *p1 = '_';
      if (c == '/'
      && first_slash == NULL) {
    first_slash = p1;
      }
    }
  }

  /* if there were no slashes in the fake module pathname, there is no
     top name, which is incorrect: */
  if (first_slash == NULL) {
[COLOR=Red]    tme_output_append_error(_output, module_fake_pathname);
[/COLOR]    tme_free(module_raw_name);
    return (EINVAL);
  }
```

later on:

 ```
 if (modules_index == NULL) {
   [COLOR=Red] tme_output_append_error(_output, module_fake_pathname);[/COLOR]

```

there are two more instances of 'tme_output_append_error()' function in module.c. I think that gcc doesn't like the way the '_output' argument is being passed (earlier declared as a char**).

My C knowledge has rusted and fallen to pieces by now. The last time I coded something in C was in 1995!

What would be the correct format for the '_output' argument in the call to tme_output_append_error function to stop gcc moaning about it?

---

### Post by gmargo on 2011-02-02
I wasted too much time today playing with this :(

All of those warnings/errors will go away by changing all 14 instances of
```
[COLOR=Black] tme_output_append[_error](_output, something);[/COLOR]
```[COLOR=Black] to 
[/COLOR]```
[COLOR=Black] tme_output_append[_error](_output, "%s", something);[/COLOR]
```There are also other problems with the makefiles.  Not all generated objects are removed on "make distclean".  And some generated objects are shipped in the distribution.

I had to execute the following shell script after a "make distclean" (or before first compile) to clean out the auto-generated objects:
```

#!/bin/sh
set -x

# tme's "make distclean" does not clean up enough stuff.
# Plus some stuff is shipped in the tar that should not be there.

# Leftovers
rm -f libtme/recode-host.c
rm -f libtme/shlibvar.h
rm -f machine/sun/tme-sun-eeprom
rm -f machine/sun/tme-sun-idprom
rm -f tme/recode-host.h
rm -f tme/tme-plugins.txt
rm -f tme-preopen.txt
rm -f tmeconfig.h
rm -f tmesh/tmesh-input.loT

# Built libraries are not removed
find . -type f -name '*.la' -exec rm {} \;

# Force parser rebuild - build with Berkeley yacc (byacc), not bison
rm -f tmesh/tmesh-input.c

# Auto-generated stuff shipped in tar file
rm -f generic/fb-xlat-auto.c
rm -f ./libtme/memory-auto.h
rm -f ./libtme/memory-auto.c
rm -f ./ic/ieee754/ieee754-ops-auto.c
rm -f ./ic/ieee754/ieee754-misc-auto.c
rm -f ./ic/ieee754/ieee754-auto.h
rm -f ./ic/ieee754/ieee754-ops-auto.h
rm -f ./ic/sparc/sparc-bus-auto.c
rm -f ./ic/sparc/sparc-vis-auto.c
rm -f ./ic/sparc/sparc-fpu-auto.c
rm -f ./ic/sparc/sparc-auto.h
rm -f ./ic/sparc/sparc-insns-auto.c
rm -f ./ic/m68k/m68k-auto.h
rm -f ./ic/m68k/m6888x-auto.c
rm -f ./ic/m68k/m68k-insns-auto.c
rm -f ./ic/m68k/m68k-bus-auto.c
rm -f ./ic/m68k/m68k-opmap.c

```

---

### Post by SevenMachines on 2011-02-02
[COLOR=Black]gcc issues warnings about these now as they're a security risk due to 
[http://en.wikipedia.org/wiki/Format_string_vulnerabilities](http://en.wikipedia.org/wiki/Format_string_vulnerabilities)[/COLOR] [COLOR=Black]

typically there used to be a lot of lines like
[/COLOR]```
[COLOR=Black]printf(something);[/COLOR]
```[COLOR=Black]
that needed to be changed to include a format string too...
[/COLOR]```
[COLOR=Black]printf("%s", something);[/COLOR]
```[COLOR=Black]
or similar

In this case, as a guess, I  imagine changing[/COLOR]  [COLOR=Black]
[/COLOR]```
[COLOR=Black]tme_output_append_error(_output, module_fake_pathname);[/COLOR]
```[COLOR=Black]
[/COLOR] [FONT=monospace][COLOR=Black]to
[/COLOR][/FONT]```
tme_output_append_error(_output, "%s", module_fake_pathname);
```[COLOR=Black]or something like that would work but you'd need to look through the code more carefully to be sure

[EDIT] In other words i agree with gmargo!
[/COLOR]

---

### Post by ansar68pk on 2011-02-03
So it was the const char* which was the culprit.

I ran gmargo's shell script before compiling and edited all offending instances of code with "%s". 

Compiles and installs beautifully but the software is buggy. A GTK window comes up and tmesh sits at its prompt, waiting for commands..... and then as soon as I type a command, it freezes. Much ado about nothing!

Looks like I have to catch up with things. A lot has changed over the years.

You guys have been a great help. I have been a regular guest visitor since Dapper. I went on to Intrepid and then Maverick. In my opinion, Ubuntu forums are a million times better than Microsoft support. You guys rock! :p

):P

---

### Post by ansar68pk on 2011-02-03
Ok, tmesh gives a beautiful sparc2 workstation screen output. It works like a real one. I am going to install SunOS4.1.4 for sparc on it.

Earlier I installed 'byacc' added two more lines to gmargo's clean script and edited the force parser rebuild line from tmesh-input.c to tmesh-input.y

```
#!/bin/sh
set -x

# tme's "make distclean" does not clean up enough stuff.
# Plus some stuff is shipped in the tar that should not be there.

# Leftovers
rm -f libtme/recode-host.c
rm -f libtme/shlibvar.h
rm -f machine/sun/tme-sun-eeprom
rm -f machine/sun/tme-sun-idprom
rm -f tme/recode-host.h
rm -f tme/tme-plugins.txt
rm -f tme-preopen.txt
rm -f tmeconfig.h
rm -f tmesh/tmesh-input.loT

# Built libraries are not removed
find . -type f -name '*.la' -exec rm {} \;

# Force parser rebuild - build with Berkeley yacc (byacc), not bison
rm -f tmesh/tmesh-input.y

# Auto-generated stuff shipped in tar file
rm -f generic/fb-xlat-auto.c
rm -f ./libtme/memory-auto.h
rm -f ./libtme/memory-auto.c
rm -f ./ic/ieee754/ieee754-ops-auto.c
rm -f ./ic/ieee754/ieee754-misc-auto.c
rm -f ./ic/ieee754/ieee754-auto.h
rm -f ./ic/ieee754/ieee754-ops-auto.h
rm -f ./ic/sparc/sparc-bus-auto.c
rm -f ./ic/sparc/sparc-vis-auto.c
rm -f ./ic/sparc/sparc-fpu-auto.c
rm -f ./ic/sparc/sparc-auto.h
rm -f ./ic/sparc/sparc-insns-auto.c
rm -f ./ic/m68k/m68k-auto.h
rm -f ./ic/m68k/m6888x-auto.c
rm -f ./ic/m68k/m68k-insns-auto.c
rm -f ./ic/m68k/m68k-bus-auto.c
rm -f ./ic/m68k/m68k-opmap.c
rm -f ./generic/bus-device-auto.c
rm -f ./generic/float-auto.c
```

I had also edited module.c, tmesh-input.c, sun2-mainbus.c,  sun3-mainbus.c and sun4-mainbus.c to include "%s" in offending function  calls.

I also created a file named 'local.conf' in /etc/ld.so.conf.d. This file has the line /usr/local/lib. I followed this by doing 'sudo ldconfig'

Why tmesh was freezing remains unknown but when issued an 'ls' command after invocation it seemed to do nothing.

After some thought, I commented out the command
```

command board0 power up
```
from the SUN4C sparc2 template file and that is what got it working.
I guess that a computer needs a "power-up" to actually do some work! :lolflag:
After the sparc2 screen comes up, the 'ls' command and all other commands in tmesh shell started working too.

See the attached screen shot.

I guess that wraps it all up! I hope this information will be of some help to someone.

Thanks guys.

---

### Post by gmargo on 2011-02-03
> **ansar68pk said:**
> ```

rm -f tmesh/tmesh-input.y
```
I'm not surprised that I missed a couple of auto-generated files (well, I'm a little surprised.)  But it is not proper to remove the tmesh-input.y file.  Yacc processes that file to generate tmesh-input.c.

---

### Post by ansar68pk on 2011-02-03
I wrongly thought that it was the other way round.

I am not familiar with the 'yacc' parser and things were a bit mixed up back there so may be I made a mistake. I am making again and .y is still not in the tmesh folder.
.
.
.
It built ok but you are correct. The way it happened for me was that 'make' kept hitting an error due to the format string problem and mentioned the yerror() function call. I found that in tmesh-input.c and happily edited it with "%s" and then I deleted the .y file from the tmesh folder.

Oddly that seems to make gcc happy or more likely I didn't pay attention to any warning(s) as the screen scrolled too fast. 

So the correct code really is like the one you posted previously:
```
rm -f tmesh/tmesh-input.c
```
and the problem is that it keeps generating the tmesh-input.c file with the offending code bringing gcc to a screeching halt every time. I wonder how you did it.

It is time for me to do a 'yacc for dummies' course!

Thanks for pointing it out and teaching me something again :p

---

### Post by gmargo on 2011-02-04
> **ansar68pk said:**
> and the problem is that it keeps generating the tmesh-input.c file with the offending code bringing gcc to a screeching halt every time. I wonder how you did it.

Edit the yacc file.  There's C code in there.  It's the same edit you made everywhere else. (line 304)

I had install Berkeley yacc (the **byacc** package) and run configure with a "YACC=byacc" environment variable to prevent it from using **bison(1)**, which for some reason generated code that would not compile.

---

### Post by ansar68pk on 2011-02-04
from tmesh-input.y
```
.
.
.
/* this is called by the parser when it encounters an error: */
static void
yyerror(char *msg)
{
  tme_output_append(_tmesh_output, "%s", msg);
  _tmesh_input->tmesh_scanner.tmesh_scanner_in_args = FALSE;
}
.
.
```

Done proper now.

---

