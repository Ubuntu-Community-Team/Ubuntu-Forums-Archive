---
title: "How to compile a program without a makefile?"
date: 2008-12-14
forum: Packaging and Compiling Programs
---

### Post by NorQue on 2008-12-14
Hello,

I have the following problem:

I want to compile _[simplefrontend](http://twolame.svn.sourceforge.net/viewvc/twolame/trunk/simplefrontend/)_, an example from twolame that should show how to use the twolame API.

It comes with a Makefile.am, but following several tutorials I couldn't get Automake 1.8 to make *anything*. I even followed this strange advice:> Still can't figure out what to run and in which order? Try running automake, aclocal, autoconf and autoheader in random combinations, and you'll usually end up with something useful after a couple of iterations. When you get a feeling of what is needed, write it down into autogen.sh, so you'll remember it next time.
but... it didn't get me anywhere. Nothing useful, at least.

Usually I don't use external libraries, so I can compile my (very) simple command line applications with "*gcc -Wall -g infile.c -o outfile*". When I do this with a stripped down version of simplefrontend that doesn't require anything from audio_wave.c/.h anymore I get these messages:```
user@comp:~/prog$ gcc -Wall -g mp2test.c -o mp2test
/tmp/ccQHA7Y5.o: In function `main':
/home/user/prog/mp2test.c:44: undefined reference to `twolame_init'
/home/user/prog/mp2test.c:45: undefined reference to `get_twolame_version'
/home/user/prog/mp2test.c:56: undefined reference to `twolame_set_mode'
/home/user/prog/mp2test.c:61: undefined reference to `twolame_set_in_samplerate'
/home/user/prog/mp2test.c:62: undefined reference to `twolame_set_out_samplerate'
/home/user/prog/mp2test.c:65: undefined reference to `twolame_set_bitrate'
/home/user/prog/mp2test.c:69: undefined reference to `twolame_init_params'
/home/user/prog/mp2test.c:85: undefined reference to `twolame_encode_buffer_interleaved'
/home/user/prog/mp2test.c:100: undefined reference to `twolame_encode_flush'
/home/user/prog/mp2test.c:104: undefined reference to `twolame_close'
collect2: ld returned 1 exit status
```These 'undefined references' are all functions that are defined in twolame.h. I have libtwolame-dev, libtwolame0 and twolame installed from the Ubuntu repositories.

What can I do to get this compiled? Is there any tutorial I should read? I hope I'm not wasting your time with asking an obvious question, but I'm really lost at the moment, *any* help is appreciated.

**EDIT:**
After fiddling around a bit more it turns out that the solution to this problem was simply to add "-l twolame" to the gcc commandline. Now it compiles and everything works like it should. D'oh. :)

Solved. :D

---

### Post by lensman3 on 2008-12-19
You need to add a -I to the gcc line.

Like:

gcc -Wall -g -I<Path-To-lamm> mp2test.c -o mp2test

The -I adds an include directory to the search path.  If there is no -I, then gcc "looks" in "/usr/include". You will have to look at the form of the twolame.h include.  Is it like:

#include <lame/twolame.h>

or

#include <twolame.h>

Your -I will have to have the form so that when gcc get to the include it expands to "/usr/include/lame/twolame.h" or "/usr/include/twolame.h"

If the include file lives in "/usr/include", the file will have <> (angle brackets) around the name.  If the file is local to the compile directory, then the file has "twolame.h" (double quotes) around the name.

---

