---
title: "common music 3.9 not installing"
date: 2014-05-14
forum: Packaging and Compiling Programs
---

### Post by fr-andres on 2014-05-14
Hi everyone,

I'm trying to install Grace (common music 3.9) on my ubuntu 14.04
I have succesfully installed the release 3.8 from this webpage:
[http://sourceforge.net/projects/commonmusic/files/cm/3.8.0/Grace-3.8.0-ubuntu.zip/download](http://sourceforge.net/projects/commonmusic/files/cm/3.8.0/Grace-3.8.0-ubuntu.zip/download)
it works perfectly, but it just doesn't recognice my FOMUS libraries. I get this error when trying to export:

```
>>> Error: Fomus: can't find FOMUS library
>>> Error: don't know how to open "fomus.ly"
```

The compillation of FOMUS with g++ was also an issue, but I managed to install it and test it from the terminal; it works pefectly so that's not the problem.
Here the related post:
[http://ubuntuforums.org/showthread.php?t=2224136](http://ubuntuforums.org/showthread.php?t=2224136)
I have also my libfomus.so file in /usr/lib, so I fullfill every requisites formuled here:
[http://comments.gmane.org/gmane.lisp.ccrma.general/3587](http://comments.gmane.org/gmane.lisp.ccrma.general/3587)

In my situation I can only think in 2 solutions: one would be recompile grace 3.8, and tell it where to look. As far as I know that is not possible If I only got a stand-alone...

SO:
compiling Grace 3.9 from source might be the solution.

I downloaded the tarball from the official webpage:
[http://commonmusic.sourceforge.net/](http://commonmusic.sourceforge.net/)

and followed the respective instructions:
[http://commonmusic.sourceforge.net/cm/readme.text](http://commonmusic.sourceforge.net/cm/readme.text)

It didn't work: make returns this error:

```
juce/modules/juce_gui_basics/juce_gui_basics.cpp:127:35: fatal error: X11/Xcursor/Xcursor.h: No such file or directory
   #include <X11/Xcursor/Xcursor.h>
                                                    ^
```

I grepped for include, Xcursor, etc... and no answer. I don't know where to look to fix this issue, but, as suggested in this solved post
[http://ubuntuforums.org/showthread.php?t=1281658](http://ubuntuforums.org/showthread.php?t=1281658)
(and that's why I ask here) it might be a problem from "premake": User mjerting suggests:

"Use Premake 3.7, NOT Premake4."

BUT I have readen that the premake4 files aren't at all compatible with premake 3, and I couldn't trick the premake4.lua file to work with premake 3.7, so it might be true...
So my question to mjertin and to everybody:

-How can it be posible to make it work with premake3?
-Should I rather debug the premake4? Where could I find the bug? (i.e., some missing libraries¿?¿)
-Is there a possibility to install grace via SVN? I googled and found nothing, and I'm totally noob with it. Maybe older versions work better.
-Do I miss some other solution?

I really appreciate your help!
Thanks in advance and best regards
Andres

---

### Post by steeldriver on 2014-05-14
Hello and welcome to the forums

I have no experience with 'Grace' and have certainly never tried building it, but it sounds like the **libxcursor-dev** package is a prerequisite - have you installed it?

In fact, unless your system is very lacking in disk space, you may want to install the **xorg-dev** metapackage, which will pull in a number of common X development libraries that may be required.

---

### Post by oldos2er on 2014-05-14
Moved to Packaging & Compiling Programs.

---

### Post by fr-andres on 2014-05-14
Thank you very much for your fast response!

It helped me to get much further. I had still had failing libraries:
This error for sndlib:
```
/usr/bin/ld: cannot find -lsndlib
```

was solved following the steps here:
path/to/cm/sndlib/sndlib.html
namely:
```
mkdir /usr/local/lib/pkgconfig
cd /path/to/cm/sndlib
./configure
make
make install (as root)
```

The same for JUCE:
```
cd /path/to/cm/juce/extras/Introjucer/Builds/Linux
make
```

Then I edited premake4.lua to include fomus: in line 350 removed the string "include":
```
if not file_exists(fomus .. "/fomus.h") then
```
(EDITx2: this step is INDEED necessary, sorry for the confusion ;)

Now the call to premake4 works perfectly:
```
premake4 --with-fomus=/usr/local/fomus/src/lib/api
```

Then calling "make" gives yet 2 errors:
```
/usr/bin/ld: cannot find -lgsl
/usr/bin/ld: cannot find -lgslcblas
```

Solved by:
```
sudo apt-get install libgsl0-dev
```

And there is the binary, in /path/to/cm/bin/grace.
Grace 3.9 works now, and I don't get this error anymore when I try to export:
"Fomus: can't find FOMUS library"

I still get the second one, though, 
>>> Error: don't know how to open "xxxxx.ly"

Any suggestions?
Thank you anyway, I'll keep trying und will post in case I find the solution.

---

### Post by fr-andres on 2014-05-14
Here is some clue. 
[http://comments.gmane.org/gmane.lisp.ccrma.general/3682](http://comments.gmane.org/gmane.lisp.ccrma.general/3682)
Rick Taube (the programmer of Grace) writes:

"yes you didnt build the c sources with fomus option enabled, if you had you would see it listed in the herald"

a little gratuitous, but here is my herald: no FOMUS on it:

```
Grace - Graphical Realtime Algorithmic Composition Environment
(c) 2014 University of Illinois Board of Trustees.
JUCE v3.0.5 (c) 2014 Julian Storer
S7 Scheme 3.5 (17-Feb-14), Sndlib 23 (c) 2014 William Schottstaedt

 /\\\
---\\\---------
----\\\--------
----/\\\------- Common Music 3.9.0
---/--\\\------
--/----\\\-----
 /-------\\\/---

```
so back to premake!
I have posted a new thread called "FOMUS 0.1.18 installation" to refer exactly which kind of installation do I have, if anyone wants to follow/correct it.
For the moment I'm going to try to get it working as it is, the solution seems to be close.

Best regards
Andres

EDIT: this is how it should look like!
[http://linux-sound.org/images/blog/full-size/1-grace-console.png](http://linux-sound.org/images/blog/full-size/1-grace-console.png)

---

### Post by fr-andres on 2014-05-16
OK, the edition that I suggested to premake4.lua was false: fomus.h is indeed in /usr/include, So taking a brand new file another time, we make the following changes:
lines 343 and 345, change the path "/usr/local" for just "/usr".
Now, the call
```
premake4 --with-fomus
```
will just work fine.

And if we take a close look to the functions concerning FOMUS, we notice that there are 2 groups. One between lines 339 and 360:

```
if _OPTIONS["with-fomus"] then
   -- if no path given, default to standard directory for OS
   if (_OPTIONS["with-fomus"] == "") then
      if (WINDOWS) then
         _OPTIONS["with-fomus"] = "/usr"
      else
         _OPTIONS["with-fomus"] = "/usr"
   end
end

   fomus = insure_slash(_OPTIONS["with-fomus"])
   if not file_exists(fomus .. "include/fomus.h") then
      error("\nBuild option --with-fomus=" .. fomus ..
            " is incorrect: the file " .. fomus .. "include/fomus.h does not exist.")
   end
   includedirs({fomus .. "include"})
   files({"src/Fomus.cpp", "src/Fomus.h"})
   defines({"WITH_FOMUS"})
   defines({"FOMUSLIBPATH=\\\"" .. fomus .. "lib\\\""})
   libdirs({fomus .. "lib"})
   --linkoptions({"-v"})
end
```


and the other between 392 and 398

```
-- Linux
configuration({"linux"})
links({"dl", "pthread", "rt", "X11","GL","GLU","Xinerama",
       "asound","freetype", "Xext"})
if _OPTIONS["with-fomus"] then
   links({"gsl", "gslcblas", "m"}) 
end
```

Regarding the first one, the symbol "fomus" is evaluated as /usr/, and the two points ".." represent the "concatenate" function in lua. the function "insure_slash" just adds a slash at the end of a string, if not there. The files Fomus.cpp and .h are in /path/to/cm/src, so that is probably right there...
I guess that the point of all is to tell grace where to look for FOMUS, maybe in the lines of includedirs, files, libdirs... I don't know, and since the program compiles without error messages I feel a little lost... any ideas out there? I'll appreciate!

And I don't know what the second group is supposed to mean, i searched in the document for gsl and gslcblas but nothing appeared... I'll keep trying anyway, before trying the svn solution.
regards,
Andres

---

### Post by fr-andres on 2014-05-23
Solved!

Thanks to Rick Taube, who suggested:
```

premake4 cleanall
premake4 … --with-fomus="whatever"
make verbose=1
```

As debugging option. The problem was that the static library "libfomus.a" was not linking.
So, I must admit that I messed too much with the premake4.lua...

1. I took a fresh premake4.lua file, and removed the "/local/" string in lines 343 and 345. 
2. I have my libfomus.a file in both following adresses:
/usr/lib/libfomus.a
/usr/share/fomus/libfomus.a

I did the code of Mr. Taube and this time it worked perfectly.

```
Grace - Graphical Realtime Algorithmic Composition Environment
(c) 2014 University of Illinois Board of Trustees.
JUCE v3.0.5 (c) 2014 Julian Storer
S7 Scheme 3.5 (17-Feb-14), Sndlib 23 (c) 2014 William Schottstaedt
FOMUS 0.1.18-alpha (c) 2014 David Psenicka

 /\\\
---\\\---------
----\\\--------
----/\\\------- Common Music 3.9.0
---/--\\\------
--/----\\\-----
 /      \\\/

```

Now, this should create a wonderful score!
```

(define (cyc-pat n dur)
  (process repeat n
           with k-pat = (make-cycle '(60 64 67 64)) do
           (mp:midi :key (next k-pat) :dur dur)
           (wait dur)))
 
(sprout (cyc-pat 500 1/2) "/tmp/pat-exp-1.ly"))

```

And thanks very much to steeldrive for giving the solution to the thread.
Best regards
Andres

---

### Post by isabel3 on 2014-06-28
So after following all the steps mentioned on this thread, it has worked -mostly-. But there is still this error when invoking "make": 

```
==== Building juce (debug) ====
==== Building Grace (debug) ====
Creating bin
Running pre-build commands
res/bin/sndlib.sh
=== Configuring Sndlib ====
premake4 --with-g++
/home/isabel/cm/sndlib/premake4.lua:95: attempt to call field 'is64bit' (a nil value)
=== Making Sndlib ====
gcc  headers.o audio.o io.o sound.o xen.o vct.o clm.o sndlib2xen.o clm2xen.o s7.o -o libsndlib.so -shared  -lasound -lgsl -lgslcblas -lm     -lm -ldl
ar -rc libsndlib.a headers.o audio.o io.o sound.o xen.o vct.o clm.o sndlib2xen.o clm2xen.o s7.o
: libsndlib.a
SndLib.cpp
src/SndLib.cpp: In member function ‘int InstrumentTable::DemoDataSorter::compareElements(juce::XmlElement*, juce::XmlElement*) const’:
src/SndLib.cpp:454:9: error: ‘const class juce::String’ has no member named ‘compareLexicographically’
         compareLexicographically(second->getStringAttribute(attributeToSort));
         ^
src/SndLib.cpp:457:57: error: ‘const class juce::String’ has no member named ‘compareLexicographically’
         result = first->getStringAttribute(indexString).compareLexicographically(second->getStringAttribute(indexString));
                                                         ^
make[1]: *** [obj/Grace/Debug/SndLib.o] Error 1
make: *** [Grace] Error 2
```

What could be the cause and the possible solutions? 


Best regards, 


Isabel

---

### Post by jwmatthys on 2014-07-01
A recent change to JUCE has replaced compareLexicographically with compareNatural. Changing these two lines fixed it for me.

---

