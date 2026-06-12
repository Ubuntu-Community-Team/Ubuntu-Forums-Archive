---
title: "[SOLVED] compiling basic pidgin plugin, C header files not found."
date: 2008-03-26
forum: Programming Talk
---

### Post by Glich on 2008-03-26
EDIT: I changed helloworld.c's location to be with "notify.h" (cant believe I missed that) but now, when I run the compile command there are so many errors the command line does not show the top one! I'm gona try to figure out how to dump them to text file.

EDIT: grrrrrr I dont know how to dump the errors to file to have a look at the first error! 
gcc -c helloworld.c -o helloworld.o >> errors.txt
does not work! please help!


I'm trying to compile the hello world example taken from:
[http://developer.pidgin.im/wiki/CHowTo/BasicPluginHowto](http://developer.pidgin.im/wiki/CHowTo/BasicPluginHowto)

The file that I've saved as helloworld.c starts like this:

```
#define PURPLE_PLUGINS

#include <glib.h>

#include "notify.h"
#include "plugin.h"
#include "version.h"
```

I use the command line to brows to the directory which contains helloworld.c.

I put the command line into root using 'su' command.

I execute 'gcc -c helloworld.c -o helloworld.o'.

The output is:

```
helloworld.c:3:18: error: glib.h: No such file or directory
helloworld.c:5:20: error: notify.h: No such file or directory
helloworld.c:6:20: error: plugin.h: No such file or directory
helloworld.c:7:21: error: version.h: No such file or directory
helloworld.c:12: error: expected &#8216;=&#8217;, &#8216;,&#8217;, &#8216;;&#8217;, &#8216;asm&#8217; or &#8216;__attribute__&#8217; before &#8216;plugin_load&#8217;
helloworld.c:19: error: expected &#8216;=&#8217;, &#8216;,&#8217;, &#8216;;&#8217;, &#8216;asm&#8217; or &#8216;__attribute__&#8217; before &#8216;info&#8217;
helloworld.c:53: error: expected &#8216;)&#8217; before &#8216;*&#8217; token
helloworld.c: In function &#8216;PURPLE_INIT_PLUGIN&#8217;:
helloworld.c:57: error: expected &#8216;{&#8217; at end of input
```

So I find glib.h, which is at location /usr/include/glib-2.0, and specify in the source of helloworld.c where it is, like so:

```
#define PURPLE_PLUGINS

#include <glib-2.0/glib.h>

#include "notify.h"
#include "plugin.h"
#include "version.h"
```

Then, I try compiling again using the same command: 'gcc -c helloworld.c -o helloworld.o'.

This time I get these errors:


```
In file included from helloworld.c:3:
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
helloworld.c:5:20: error: notify.h: No such file or directory
helloworld.c:6:20: error: plugin.h: No such file or directory
helloworld.c:7:21: error: version.h: No such file or directory
helloworld.c:12: error: expected &#8216;=&#8217;, &#8216;,&#8217;, &#8216;;&#8217;, &#8216;asm&#8217; or &#8216;__attribute__&#8217; before &#8216;plugin_load&#8217;
helloworld.c:19: error: expected &#8216;=&#8217;, &#8216;,&#8217;, &#8216;;&#8217;, &#8216;asm&#8217; or &#8216;__attribute__&#8217; before &#8216;info&#8217;
helloworld.c:53: error: expected &#8216;)&#8217; before &#8216;*&#8217; token
helloworld.c: In function &#8216;PURPLE_INIT_PLUGIN&#8217;:
helloworld.c:57: error: expected &#8216;{&#8217; at end of input

```

How can I show the compiler where these files are without editing glib.h?

Thanks.

---

### Post by WW on 2008-03-26
> **Glich said:**
> 
I put the command line into root using 'su' command.

Why?  This is usually a bad idea.

> **Glich said:**
> 
So I find glib.h, which is at location /usr/include/glib-2.0, and specify in the source of helloworld.c where it is, like so:

```
#define PURPLE_PLUGINS

#include <glib-2.0/glib.h>

```

Don't do that.  Leave the include statement like you originally had it, and use **pkg-config** to tell gcc where to find the headers.  See the [Glib reference manual](http://library.gnome.org/devel/glib/2.16/glib-compiling.html) for details.

---

### Post by WW on 2008-03-26
> **Glich said:**
> EDIT: I changed helloworld.c's location to be with "notify.h" (cant believe I missed that) ...

What do you mean when you say 'to be with "notify.h"'?  If you are using libnotify, you should also use pkg-config to tell gcc where its header files are.  Your code is best kept in your home directory.

---

### Post by Glich on 2008-03-27
ah! thanks! you've given me some nice leads to go after.

---

### Post by Glich on 2008-04-05
this is how I ended up comiling it. first I moved the source helloworld.c to /usr/include/libpurple

then I ran these commands:

cd /usr/include/libpurple
sudo gcc -o helloworld.so -shared -fPIC helloworld.c `pkg-config pidgin glib --cflags --libs` -g -Wall -Werror
sudo cp helloworld.so /usr/lib/purple-2/helloworld.so

---

### Post by SadaraX on 2008-08-14
I am aware this is an old, and the issue has been solved thread, but I wanted to share with you some useful information.

Glitch, first thank you. Though your methods did not exactly work for me, I learned something from them that helped me get things working for myself.

A word of warning to you Glich: it is generally a poor idea to ever to do work within the system directories. Good user practice is to only do work under /home and /media or possible /tmp. The system directories should be handled mostly by the system. ;)

So, basically I do not do work in /usr/include/libpurple. After reading through the official pidgin plugin tutorials online, I picked up a few pointers

Here is my solution:

1) Download a copy of the latest stable pidgin source code
2) Extract the source .tar.gz file to a directory. 
3) Do your coding development within there. I worked in .../pidgin-source/libpurple/

For compiling a basic skeleton of a pidgin plugin, I found this worked best:

```
gcc plugin_name.c -o plugin_name.so -shared `pkg-config pidgin --cflags --libs glib-2.0`
```

The other GCC options you had are not necessary, though they may be useful.

The important difference I want to draw your attention to is the pkg-config section. I put 'glib-2.0' after the --libs section. I did this after reading the official Gnome Documentation on Glib reference.

I hope this helps. I know your other work helped me.

---

