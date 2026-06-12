---
title: "How to wipe out (uninstall) package installed via cmake"
date: 2011-08-26
forum: Programming Talk
---

### Post by mvandemar on 2011-08-26
I am teaching myself game programming, and I wanted to try my hand at c++. I already installed build-essential and was able to play around and compile projects using gcc. I was trying to install allegro 5.0.4 via the downloaded source from here (the repositories only have liballegro4.2):

[http://alleg.sourceforge.net/download.html](http://alleg.sourceforge.net/download.html)

Just so you have all of the info, I unzipped it onto my desktop, and following the instructions in the readme I created a new directory named Build, cd'd into that directory, and ran the following commands:

```

$ cmake ~/Desktop/allegro-5.0.4/
$ make
$ make install

```

It failed the first time, so then I ran sudo make install instead and it seemed to work. I have attached a tarred up text file of all of the output from that.

However, when I tried compiling a sample program I get the following errors:

1) If I use: 

#include <allegro.h>

I get "ascreen.cpp:1:21: fatal error: allegro.h: No such file or directory". I tried adding /usr/local/include/allegro5 to my path, but that did not work either. However, if I use the full path in the include statement that error goes away:

#include </usr/local/include/allegro5/allegro.h>

2) At this point when I try and compile I am getting scope errors tho:

```

ascreen.cpp: In function ‘int main(int, char**)’:
ascreen.cpp:4:15: error: ‘allegro_init’ was not declared in this scope
ascreen.cpp:5:19: error: ‘install_keyboard’ was not declared in this scope
ascreen.cpp:6:15: error: ‘GFX_AUTODETECT’ was not declared in this scope
ascreen.cpp:6:42: error: ‘set_gfx_mode’ was not declared in this scope
ascreen.cpp:7:10: error: ‘readkey’ was not declared in this scope
ascreen.cpp: At global scope:
ascreen.cpp:10:13: error: expected constructor, destructor, or type conversion at end of input

```

From what I read that is solved by adding `allegro-config --libs` to the compile statement:

gcc ascreen.cpp `allegro-config --libs`

which produces this error (followed by the same scope errors):

```

The program 'allegro-config' is currently not installed.  You can install it by typing:
sudo apt-get install liballegro4.2-dev

```

Which is the version of allegro that is in the repositories, so obviously I did something wrong when I tried installing from source. I say all of that to ask this... while I was researching how to fix this, I came across a suggestion that many of the linking and path issues can be solved if you install via svn using these instructions:

[http://wiki.allegro.cc/index.php?title=Install_Allegro5_From_SVN/Linux/Debian](http://wiki.allegro.cc/index.php?title=Install_Allegro5_From_SVN/Linux/Debian)

and in those instructions the only thing I see differently is using ccmake instead of cmake, and the following parameter used when calling it:

```

ccmake -DCMAKE_INSTALL_PREFIX=/usr ..

```

So I would like to try and reinstall it starting with that command instead, and if that fails just installing 4.2 from the repositories. My problem is, how do I uninstall what I have already done? I would like to start with a clean slate, in order to avoid any conflicts, but I don't know how to to that. I do know that nothing is showing in synaptic as installed, and the following did not work:

```

$ whereis liballegro
liballegro: /usr/local/lib/liballegro.so
$ sudo apt-get remove liballegro
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package liballegro

```

Any help would be appreciated, thanks. :)

-Michael

---

### Post by gnometorule on 2011-08-26
Before you completely reinstall, have a look at this chapter...

[http://www.network-theory.co.uk/docs/gccintro/gccintro_21.html](http://www.network-theory.co.uk/docs/gccintro/gccintro_21.html)

and set the environmental variables that apply to you (C or C++) to values you can figure out typing

# whereis allegro

which should show you the location of your libraries and include files. I have allegro on my system from the repositories, and the includes and libs are installed in standard locations. Before you try anything else, make sure your code is properly linked.

---

### Post by mvandemar on 2011-08-26
> **gnometorule said:**
> Before you completely reinstall, have a look at this chapter...

[http://www.network-theory.co.uk/docs/gccintro/gccintro_21.html](http://www.network-theory.co.uk/docs/gccintro/gccintro_21.html)

and set the environmental variables that apply to you (C or C++) to values you can figure out typing

# whereis allegro

which should show you the location of your libraries and include files. I have allegro on my system from the repositories, and the includes and libs are installed in standard locations. Before you try anything else, make sure your code is properly linked.

See, that is part of the issue I was having:

```

$ whereis allegro
allegro:
$ whereis allegro5
allegro5:
$ sudo apt-get remove allegro
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package allegro

```

The chapter that you linked to states this:

> 
By default, gcc searches the following directories for header files:
```

/usr/local/include/
/usr/include/

```


And when I go through the output from the make install, it looks like that is exactly where it was installed:

```

Install the project...
-- Install configuration: "RelWithDebInfo"
-- Installing: /usr/local/lib/liballegro.so.5.0.4
-- Installing: /usr/local/lib/liballegro.so.5.0
-- Installing: /usr/local/lib/liballegro.so
-- Installing: /usr/local/include/allegro5/allegro5.h
-- Installing: /usr/local/include/allegro5/allegro.h
{etc}

```

But it is still not finding it.

-Michael

---

### Post by mvandemar on 2011-08-26
Ok, so while I would still ike to know at some point how to uninstall something installed via cmake, I actually got this somewhat working. The tutorial I was following was apparently outdated enough that almost none of it applies to allegro5. For instance, the following include does work:

```

#include <allegro5/allegro.h>

```

And alegro5 uses pkg-config instead of allegro-config, so the actual compile command is:

```

gcc -Wall ascreen5.cpp -o ascreen5 `pkg-config --libs allegro-5.0`

```

And it does in fact compile without errors. :) Only issue I am having now is I get this when trying to run it:

```

./ascreen5: error while loading shared libraries: liballegro.so.5.0: cannot open shared object file: No such file or directory

```

Off to do more research.

edit: which was fixed with "sudo ldconfig" :D Thanks!

-Michael

---

### Post by gnometorule on 2011-08-26
Good you got it running. However, I think you might still be a bit confused about how to use the paths. Here is what I believe happened:

You need to cd until you find the exact location of the header files and lib files you mean to include. If you did not adjust the environmental variable (for headers only, lib similarly) as follows:
CPLUS_INCLUDE_PATH=/usr/local/include/allegro5

[FONT=Verdana](I believe it is allegro 5 in your case, but only you know), then, as your actual header file 
is in a sub directory of the search directory, you are still stuck. Similarly for your l
ibraries. So always find the actual location of the header and lib file first (do not merely
rely on installation output as you might have), then adjust your path, and gcc should 
compile in the much easier form of

gcc -o (outputfilename) (inputfilename).cpp,

plus obviously any option that allegro tells you to use additionally. The Wall option, say,
is default enabled. From memory, allegro is a pain with gdb - google that first if you
debug with gdb. 

whereis sometimes fails. If that happens, you can give it another try as in

find / -name allegro.h

which should work. and you cannot apt-get remove anything you haven't installed using
apt-get in the first place. 

have fun. :)
[/FONT]

---

