---
title: "Undefined reference to all JACK functions"
date: 2011-01-25
forum: Packaging and Compiling Programs
---

### Post by ssj71 on 2011-01-25
I'm trying to make a C++ JACK application in Netbeans that reads from the trackpad and outputs a MIDI control.

However ANY call to a function from jack/jack.h the linker (?) returns an error, "undefined reference to `jack_get_version_string'" or whatever function.

Why? Is the libjack-jackd2-dev package just missing a library file or something? Trying an example program from the JACK source code doesn't compile either.
I'm using JACK2 for several programs and am reluctant to move to JACK1 and install libjack-dev etc. because it also removes ardour and other things I use.

Any help is welcome. Thanks,

---

### Post by SevenMachines on 2011-01-26
Include weakjack.h *before* jack.h, ie
> #include <jack/weakjack.h>
#include <jack/jack.h>Seems to be and api change thing, don't know anything about jack to know why though

/usr/include/jack/jack.h:
 > /*************************************************************
     * NOTE: JACK_WEAK_EXPORT ***MUST*** be used on every function
     * added to the JACK API after the 0.116.2 release.
     * 
     * Functions that predate this release are marked with 
     * JACK_WEAK_OPTIONAL_EXPORT which can be defined at compile
     * time in a variety of ways. The default definition is empty,
     * so that these symbols get normal linkage. If you wish to
     * use all JACK symbols with weak linkage, include 
     * <jack/weakjack.h> before jack.h.
     *************************************************************/

[EDIT] I imagine theres a better way to use this but it'll take a qualified jack-ician to know how exactly to adapt to the change best

---

### Post by SevenMachines on 2011-01-26
Ignore the above, having all symbols as weak isnt the right way on second thoughts. weak linking not really something i know much about :)

---

### Post by SevenMachines on 2011-01-26
Sometimes i wonder what the world is coming to, i really do :) Maybe your problem looks a little like this....

test.c:
> #include <stdio.h>
#include <jack/jack.h>

int main(int args, char * argv[]){
    const char * outstr = jack_get_version_string();
    printf("%s\n", outstr);
    return 0;
}
But, when i try to compile theres an undefined reference.
> $ gcc -ljack -o test test.c 
/tmp/cc9o9EDt.o: In function `main':
test.c:(.text+0xa): undefined reference to `jack_get_version_string'
collect2: ld returned 1 exit statusbut wait! with the linker flags after the source files....
> $ gcc -o test test.c -ljack
niall@cryodynamic:~/Desktop$ ./test 
1.9.7
Why it works with the linker flags after the source files and not before i've no idea, if a compiling guru has the answer i'm curious :)

---

### Post by MadCow108 on 2011-01-26
is jack only available as static library?
for these the order of arguments on the command line is important

the compiler needs to know all symbols it needs before linking with the library which provides them or if B depends on A, B must be before A on the command line.

you can work around this with -Wl,--start-group ... -Wl,--end-group
this will "permutate" all arguments in the group until all references are resolved, but its is a bit slower.

---

### Post by SevenMachines on 2011-01-26
It's not static i think, i thought the ordering might be due to the use of weak linking, but i really know nothing about that.

---

### Post by ssj71 on 2011-01-26
Thanks, I got around that using the linker flag, but now all my references to various X functions from Xinput.h say undefined reference. Is there another flag I need? How do I know what flags to use?

Thanks again,

---

### Post by SevenMachines on 2011-01-27
If you use a library you'll need to link to it obviously, a quick way to look for an unknown set of flags might be

* Search for installed packages that provide a file
```
$ dpkg -S XInput.h
libxi-dev: /usr/include/X11/extensions/XInput.h
```* Look for pkg-config setup
```
$ dpkg -L libxi-dev |grep pkgconfig
/usr/lib/pkgconfig
/usr/lib/pkgconfig/xi.pc
```* Add pkg-config to compile line, file is xi.pc so add xi
```
 `pkg-config --cflags --libs xi`
```* Or, if no pkg-config data then find lib and use it
```
$ dpkg -L libxi-dev |grep lib/
/usr/lib/libXi.a
/usr/lib/pkgconfig
/usr/lib/pkgconfig/xi.pc
/usr/lib/libXi.so
```Library /usr/lib/libXi.so so add -lXi to compile line

---

