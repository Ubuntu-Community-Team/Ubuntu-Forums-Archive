---
title: "Using glib-2.0"
date: 2007-09-06
forum: Programming Talk
---

### Post by docmur on 2007-09-06
Hello all

I'm writting a program for my College 2nd year programming class and I can't seem to use 

#include<glib.h>

glib.h just tells me it can't find it so I searched for glib.h  and did

#include</usr/include/glib-2.0/glib.h>

Now it finds glib.h but I get 

/usr/include/glib-2.0/glib.h:30:26: error: glib/galloca.h: No such file or directory
/usr/include/glib-2.0/glib.h:31:25: error: glib/garray.h: No such file or directory
/usr/include/glib-2.0/glib.h:32:30: error: glib/gasyncqueue.h: No such file or directory
/usr/include/glib-2.0/glib.h:33:26: error: glib/gatomic.h: No such file or directory
/usr/include/glib-2.0/glib.h:34:29: error: glib/gbacktrace.h: No such file or directory
/usr/include/glib-2.0/glib.h:35:26: error: glib/gbase64.h: No such file or directory
/usr/include/glib-2.0/glib.h:36:32: error: glib/gbookmarkfile.h: No such file or directory
/usr/include/glib-2.0/glib.h:37:25: error: glib/gcache.h: No such file or directory
/usr/include/glib-2.0/glib.h:38:30: error: glib/gcompletion.h: No such file or directory
/usr/include/glib-2.0/glib.h:39:27: error: glib/gconvert.h: No such file or directory
/usr/include/glib-2.0/glib.h:40:27: error: glib/gdataset.h: No such file or directory
/usr/include/glib-2.0/glib.h:41:24: error: glib/gdate.h: No such file or directory
/usr/include/glib-2.0/glib.h:42:23: error: glib/gdir.h: No such file or directory
/usr/include/glib-2.0/glib.h:43:25: error: glib/gerror.h: No such file or directory
/usr/include/glib-2.0/glib.h:44:29: error: glib/gfileutils.h: No such file or directory
/usr/include/glib-2.0/glib.h:45:24: error: glib/ghash.h: No such file or directory
/usr/include/glib-2.0/glib.h:46:24: error: glib/ghook.h: No such file or directory
/usr/include/glib-2.0/glib.h:47:29: error: glib/giochannel.h: No such file or directory
/usr/include/glib-2.0/glib.h:48:27: error: glib/gkeyfile.h: No such file or directory
/usr/include/glib-2.0/glib.h:49:24: error: glib/glist.h: No such file or directory
/usr/include/glib-2.0/glib.h:50:26: error: glib/gmacros.h: No such file or directory
/usr/include/glib-2.0/glib.h:51:24: error: glib/gmain.h: No such file or directory
/usr/include/glib-2.0/glib.h:52:30: error: glib/gmappedfile.h: No such file or directory
/usr/include/glib-2.0/glib.h:53:26: error: glib/gmarkup.h: No such file or directory
/usr/include/glib-2.0/glib.h:54:23: error: glib/gmem.h: No such file or directory
/usr/include/glib-2.0/glib.h:55:28: error: glib/gmessages.h: No such file or directory
/usr/include/glib-2.0/glib.h:56:24: error: glib/gnode.h: No such file or directory
/usr/include/glib-2.0/glib.h:57:26: error: glib/goption.h: No such file or directory
/usr/include/glib-2.0/glib.h:58:27: error: glib/gpattern.h: No such file or directory
/usr/include/glib-2.0/glib.h:59:26: error: glib/gprimes.h: No such file or directory
/usr/include/glib-2.0/glib.h:60:25: error: glib/gqsort.h: No such file or directory
/usr/include/glib-2.0/glib.h:61:25: error: glib/gquark.h: No such file or directory
/usr/include/glib-2.0/glib.h:62:25: error: glib/gqueue.h: No such file or directory
/usr/include/glib-2.0/glib.h:63:24: error: glib/grand.h: No such file or directory
/usr/include/glib-2.0/glib.h:64:23: error: glib/grel.h: No such file or directory
/usr/include/glib-2.0/glib.h:65:25: error: glib/gregex.h: No such file or directory
/usr/include/glib-2.0/glib.h:66:27: error: glib/gscanner.h: No such file or directory
/usr/include/glib-2.0/glib.h:67:28: error: glib/gsequence.h: No such file or directory
/usr/include/glib-2.0/glib.h:68:25: error: glib/gshell.h: No such file or directory
/usr/include/glib-2.0/glib.h:69:25: error: glib/gslist.h: No such file or directory
/usr/include/glib-2.0/glib.h:70:25: error: glib/gspawn.h: No such file or directory
/usr/include/glib-2.0/glib.h:71:28: error: glib/gstrfuncs.h: No such file or directory
/usr/include/glib-2.0/glib.h:72:26: error: glib/gstring.h: No such file or directory
/usr/include/glib-2.0/glib.h:73:26: error: glib/gthread.h: No such file or directory
/usr/include/glib-2.0/glib.h:74:30: error: glib/gthreadpool.h: No such file or directory
/usr/include/glib-2.0/glib.h:75:25: error: glib/gtimer.h: No such file or directory
/usr/include/glib-2.0/glib.h:76:24: error: glib/gtree.h: No such file or directory
/usr/include/glib-2.0/glib.h:77:25: error: glib/gtypes.h: No such file or directory
/usr/include/glib-2.0/glib.h:78:27: error: glib/gunicode.h: No such file or directory
/usr/include/glib-2.0/glib.h:79:25: error: glib/gutils.h: No such file or directory


What I'm I doing wrong,,  Here is my gcc statment 

gcc `pkg-config --libs glib` helloworld.c  -o helloworld

Yes this is a simple hello world program

Thanks

Docmur

---

### Post by Compyx on 2007-09-06
Try doing a
```

sudo apt-get install libglib2.0-dev

```

That should pull in the necessary headers.

---

### Post by geraldm on 2007-09-06
if using the library, include the library's headers
you could change back to "#include <glib.h>"

Try
gcc -I/usr/include/glib-2.0 `pkg-config --libs glib` helloworld.c -o helloworld
/code

You may also need to add  "-I/usr/include "

Gerald

---

### Post by fct on 2007-09-06
> **docmur said:**
> 
What I'm I doing wrong,,  Here is my gcc statment 

gcc `pkg-config --libs glib` helloworld.c  -o helloworld

Hmmm...

```
$ pkg-config --list-all |grep glib
glib-2.0                    GLib - C Utility Library
```

So use:

```
gcc `pkg-config --libs **glib-2.0**` helloworld.c  -o helloworld
```

instead.

---

### Post by docmur on 2007-09-06
Okay I tried all of that, I had libglib2.0-dev installed being I knew I need ed to compile against it.   When I ran pkg-config | grep glib it shows glib-2.0 is installed so thats cool.  

I switched back to glib.h in the include statement and tried to use -l/usr/include/glib-2.0   But that just tells me glib.h doesn't exist which is weird.  

 gcc -l/usr/include/glib-2.0 `pkg-config --libs glib` helloworld.c -o helloworld
sh: glib-config: not found
sh: glib-config: not found
sh: glib-config: not found

Which is the output.  SO I'm not sure if thats a good sign but the output when I put in glib-2.0 in place of glibs

 gcc -l/usr/include/glib-2.0/`pkg-config --libs glib-2.0` helloworld.c -o helloworld
helloworld.c:1:18: error: glib.h: No such file or directory

So thats as far as I've gotten

Thanks for everyones help

DOCMUR

---

### Post by Awalton on 2007-09-06
Try this:

gcc `pkg-config --libs --cflags glib-2.0` helloworld.c -o helloworld

All `pkg-config --libs --cflags glib-2.0` is there for is to save you time as a programmer from having to do -llibrary-one -llibrary-2 etc. The `` means "run this".
 
Basically, this:
gcc `pkg-config --libs --cflags glib-2.0` helloworld.c -o helloworld

Runs:
pkg-config --libs --cflags glib-2.0
which outputs
-I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include  -lglib-2.0  (on my system)
which is then inserted into the gcc line
gcc -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include  -lglib-2.0  helloworld.c -o helloworld
which is then run as you would expect.

---

### Post by geraldm on 2007-09-06
as I wrote, using upper case i, sounds like "eye":
gcc -I/usr/include/glib-2.0 `pkg-config --libs glib` helloworld.c -o helloworld

as you wrote, using lower case L:
gcc -l/usr/include/glib-2.0 `pkg-config --libs glib` helloworld.c -o helloworld

big difference.

Gerald

---

### Post by Compyx on 2007-09-06
Post your code, so we won't be guessing about what could be wrong.

---

### Post by fct on 2007-09-07
> **docmur said:**
>  gcc -l/usr/include/glib-2.0/`pkg-config --libs glib-2.0` helloworld.c -o helloworld
helloworld.c:1:18: error: glib.h: No such file or directory

If the library is supposed to compile with pkg-config then you should make sure you're using it right before trying any other way. Examining the ouput of "pkg-config --libs --cflags package-name" is the first thing you should do to locate the errors.

So don't use -l/usr/include/glib-2.0 . pkg-config takes care of that, so don't mix the two methods for the same library.

Plus you didn't leave an space between the -l parameter and the ` , so gcc is probably receiving garbled input.

Apart from that, as Compyx said, it'd be helpful if you posted at least the #includes in your source. It wouldn't be the first time that someone types

```
#include < glib.h> // The space before glib.h is an error.
```

---

### Post by charlie cat on 2010-03-28
Sorry if this post is a little late for you, docmur, this is more for people looking through the threads like I was.

I got this simple program, glibtest.c, to compile:
```

#include "glib.h"
#include <stdio.h>

int main( void )
{
printf( "glib test\n" );
return 0;
}

```By typing:
```

gcc -o glibtest -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include glibtest.c

```at the terminal.  I'm not sure exactly why but it works for me.

---

