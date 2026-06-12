---
title: "Compiling against shared libraries"
date: 2010-12-04
forum: Packaging and Compiling Programs
---

### Post by Dangerouge on 2010-12-04
Hi everyone, I'm new to programming with C (and derivants), but I'm working on some projects that really require me to do programming with them, but I have run into certain problems...

When I'm using shared libraries (in my case libasound and libv8), I can't get the code to compile, and instead get errors trying to call the stuff that clearly is in the libraries:

```
$ g++ test.cpp 
/tmp/ccEAy2HG.o: In function `open_client()':
test.cpp:(.text+0x25): undefined reference to `snd_seq_open'
test.cpp:(.text+0x48): undefined reference to `snd_seq_set_client_name'
collect2: ld returned 1 exit status
```

where the code for test.cpp would just be ```
#include <alsa/asoundlib.h>
#include <stdio.h>

snd_seq_t *open_client()
{
	snd_seq_t *handle;
	int err;
	err = snd_seq_open(&handle, "default", SND_SEQ_OPEN_INPUT, 0);
	if (err < 0)
		return NULL;
	snd_seq_set_client_name(handle, "My Client");
	return handle;
}

int main()
{
	printf("yay");
	return 0;
}
```

I'm getting really frustrated with this, as the documentation for stuff hardly ever includes any "from the beginning to the end" kind of guides, which I would need since I'm such a beginner.

And I know, "get yourself the education", but c'mon, let's have some peer sharing the C-community is missing, yes?

---

### Post by SevenMachines on 2010-12-04
there are 4 good options to remember when starting out with gcc/g++

# Give my output file a name!
-o test

# Add the directory /some/dir to the search path for header .h files, my 'includes'
-I/some/dir 

(note, its a capital i )

# Add the directory /some/dir to the search path for libraries for the linking stage
-L/some/dir

# Link this library, needed for the libraries my program uses
-lsomelibrary

In your case this would end up as
>  $ g++ -o test test.cpp -lasoundTo simplify this, most packages use something called pkg-config which automatically generates these lines. In your case...

# Whats the name of the pkg-config file?
> $ dpkg -L libasound2-dev |grep pkgconfig
/usr/lib/pkgconfig
/usr/lib/pkgconfig/alsa.pc
# so pkg-config will generate, --libs to link to and --cflags with header files and such

> $ pkg-config --cflags --libs alsa
-I/usr/include/alsa  -lasound
So, using pkg-config, your command line now looks like
> 
$ g++ -o test test.cpp `pkg-config --cflags --libs alsa`

(note, those are back-quotes in the command above)
>  $ ./test 
yay

---

### Post by SevenMachines on 2010-12-04
Just a note, obviously for simple libraries pkg-config isnt essential but its very useful when you have a complicated library with lots of dependencies, for example consider...
> $ pkg-config --cflags --libs gtk+-2.0
-pthread -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/gdk-pixbuf-2.0 -I/usr/include/pango-1.0 -I/usr/include/gio-unix-2.0/ -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/pixman-1 -I/usr/include/freetype2 -I/usr/include/libpng12  -pthread -lgtk-x11-2.0 -lgdk-x11-2.0 -latk-1.0 -lgio-2.0 -lpangoft2-1.0 -lpangocairo-1.0 -lgdk_pixbuf-2.0 -lm -lcairo -lpng12 -lpango-1.0 -lfreetype -lfontconfig -lgobject-2.0 -lgmodule-2.0 -lgthread-2.0 -lrt -lglib-2.0

Eeek! But thanks to pkg-config we dont need to enter all that by hand!

---

### Post by Dangerouge on 2010-12-05
Thank you SO MUCH, this is exactly the guide that everyone should be starting their tutorials with, instead of the ancient hello world. Really, thank you, I've been looking for this everywhere. :)

---

### Post by SevenMachines on 2010-12-05
Glad it was useful. gnu tools are exceptionally good but can appear a little daunting when you first start using them, theres a lot of useful options for finer control, but the ones mentioned above are the 'crucial' ones to know, at least to me! perhaps the ubuntu wiki could be improved with a 'walkthrough' of the kind of issues you've come up against with a basic example program, anyone can add to it :*)

---

