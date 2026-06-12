---
title: "HowTo: Install iRiverter on Breezy"
date: 2006-03-02
forum: Outdated Tutorials &amp; Tips
---

### Post by bikeboy on 2006-03-02
Ok everyone this is my first howto so go easy on me.

I've written it because iRiverter, a great GUI for making iRiver compatible videos using mencoder, is not in the Ubuntu respos and I wouldn't expect it to be anytime soon. The videos it creates can be used on iRiver H3xx, PMP, U10 and iAudio X5.

**Note: some packages may be dependencies that I already had, so if you run into issues it may be that you're missing something that I didn't realise. I also have a feeling that there are several alternative packages that can be used, particularly in fulfilling java dependencies. I will help find what's missing if you have trouble using my method.**

I did most of this from the terminal, except for finding out which versions of some things I needed, eg. mencoder, in which case I checked Synaptic.

Firstly, you will need the iRiverter Linux tarball from "http://iriverter.sourceforge.net". Currently it's version 0.15 that I'm using. Unzip that into your home directory somewhere:

```

tar xvjf iriverter-0.15.tar.bz2

```

Another obvious requirement is Mplayer of some variety, along with mencoder. I use Totem most of the time so have opted for a non-gui version of Mplayer to keep it smaller.

They're in the Multiverse repository so you will need that enabled, see here:
[https://wiki.ubuntu.com/AddingRepositoriesHowto](https://wiki.ubuntu.com/AddingRepositoriesHowto)

```

sudo apt-get install mplayer-nogui

```

Mencoder also has several versions, I have a PIII so I chose mencoder-586. Check out Synaptic for the different versions.

```

sudo apt-get install mencoder-586

```

I already had the Sun J2RE installed, it may or may not be needed. I am going to assume you have a java runtime environment installed (free or Sun) but if not see:
[https://wiki.ubuntu.com/RestrictedFormats](https://wiki.ubuntu.com/RestrictedFormats)

You will also need something call the Standard Widget Toolkit (SWT). There's a version in the repos so do this, with Universe enabled:

```

sudo apt-get install libswt-gtk-3.1-java

```

I needed some Python components as well, both from Universe:

```

sudo apt-get install pythonwx-gtk-2.6 pythonwx-version

```

Ok, I think that's the dependencies fulfilled, if not I will update based on your feedback.

Change to the directory where you unzipped iRiverter.

eg.
```

cd ~/downloads/iriverter-0.15/

```

Then do:

```

./configure --with-swt=/usr/share/java/swt-gtk-3.1.jar

```

At this point, if you get any errors, please let me know. I did too and that's usually a case of something you need installed. I lost track of what I tried installing so there may be an oversight in the Howto.

If there are no errors, proceed with:

```

make
sudo make install
```

At this point iRiverter appeared in my Gnome applications menu under Sound and Video. Try it out, iRiver H3xx models use xvid but I think this is covered by Mplayer's own codecs so you may not need to install that separately.

Enjoy

---

### Post by elfortunawe on 2006-04-28
I thought I'd done everything right, but after "sudo make install" Iriverter didn't show up in the menu.  I typed "Iriverter" into the terminal and got this:

[CENTER]Exception in thread "main" java.lang.UnsatisfiedLinkError: no swt-pi-gtk-3138 in java.library.path
        at java.lang.ClassLoader.loadLibrary(ClassLoader.java:1517)
        at java.lang.Runtime.loadLibrary0(Runtime.java:788)
        at java.lang.System.loadLibrary(System.java:834)
        at org.eclipse.swt.internal.Library.loadLibrary(Library.java:123)
        at org.eclipse.swt.internal.gtk.OS.<clinit>(OS.java:19)
        at org.eclipse.swt.internal.Converter.wcsToMbcs(Converter.java:63)
        at org.eclipse.swt.internal.Converter.wcsToMbcs(Converter.java:54)
        at org.eclipse.swt.widgets.Display.<clinit>(Display.java:122)
        at org.thestaticvoid.iriverter.ConverterUI.<init>(ConverterUI.java:31)
        at org.thestaticvoid.iriverter.ConverterUI.main(ConverterUI.java:629)
elfortunawe@gateway-71-109-189-239:~$
[/CENTER]

??????????

I got an IAudioX5 a while ago, and everything else about it is awesome.  Not being able to play videos isn't that big of a deal, but it bugs me that this one little thing just refuses to work.

Please, for the love of all that's good and holy, someone help me.

---

### Post by bionnaki on 2006-04-28
you rule.
I love my h340 :mrgreen:

---

### Post by bikeboy on 2006-04-28
[QUOTE=elfortunawe]

[CENTER]Exception in thread "main" java.lang.UnsatisfiedLinkError: no swt-pi-gtk-3138 in java.library.path
        at java.lang.ClassLoader.loadLibrary(ClassLoader.java:1517)
        at java.lang.Runtime.loadLibrary0(Runtime.java:788)
        at java.lang.System.loadLibrary(System.java:834)
        at org.eclipse.swt.internal.Library.loadLibrary(Library.java:123)
        at org.eclipse.swt.internal.gtk.OS.<clinit>(OS.java:19)
        at org.eclipse.swt.internal.Converter.wcsToMbcs(Converter.java:63)
        at org.eclipse.swt.internal.Converter.wcsToMbcs(Converter.java:54)
        at org.eclipse.swt.widgets.Display.<clinit>(Display.java:122)
        at org.thestaticvoid.iriverter.ConverterUI.<init>(ConverterUI.java:31)
        at org.thestaticvoid.iriverter.ConverterUI.main(ConverterUI.java:629)
elfortunawe@gateway-71-109-189-239:~$
[/CENTER]

[/QUOTE]

Looks like it's related to the swt thing, I'll have a look to try and see how to resolve that. I think I had the same problem for a while.

---

### Post by bikeboy on 2006-04-28
elfortunawe, do you have libswt-gtk-3.1-java installed?

To find out, one quick way is to type this into a terminal:

```

sudo find /usr/share/java -name swt-gtk-3.1.jar

```

---

### Post by elfortunawe on 2006-04-29
Yes, I checked Synaptic too and it's definitely there.

---

### Post by bikeboy on 2006-04-29
The iriverter website lists the GNU Java Compiler as an alternative to swt, perhaphs you could try installing that from Synaptic and doing ```
./configure --with-gcj=/path/to/gcj.jar
```
Where the path to gcj will probably be :
/usr/share/java/libgcj-4.0.jar

Follwing that do the make and sudo make install again too.

---

### Post by elfortunawe on 2006-05-01
I tried it with java again, and now I've got an icon in my menu, but when I clicked on it nothing happened.  I went to the terminal and got this again:

[CENTER]Exception in thread "main" java.lang.UnsatisfiedLinkError: no swt-pi-gtk-3138 in java.library.path
        at java.lang.ClassLoader.loadLibrary(ClassLoader.java:1517)
        at java.lang.Runtime.loadLibrary0(Runtime.java:788)
        at java.lang.System.loadLibrary(System.java:834)
        at org.eclipse.swt.internal.Library.loadLibrary(Library.java:123)
        at org.eclipse.swt.internal.gtk.OS.<clinit>(OS.java:19)
        at org.eclipse.swt.internal.Converter.wcsToMbcs(Converter.java:63)
        at org.eclipse.swt.internal.Converter.wcsToMbcs(Converter.java:54)
        at org.eclipse.swt.widgets.Display.<clinit>(Display.java:122)
        at org.thestaticvoid.iriverter.ConverterUI.<init>(ConverterUI.java:31)
        at org.thestaticvoid.iriverter.ConverterUI.main(ConverterUI.java:629)
elfortunawe@gateway-71-109-189-239:~$
[/CENTER]

Then I tried it with the GCJ thing, and it gave me this:

[CENTER]~/Desktop/iriverter-0.15$ ./configure --with-gcj=/usr/share/java//usr/share/java/libgcj-4.0.2.jar
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking for style of include used by make... GNU
checking for gcj... gcj
checking dependency style of gcj... none
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables...
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ANSI C... none needed
checking dependency style of gcc... gcc3
checking for a sed that does not truncate output... /bin/sed
checking for egrep... grep -E
checking for ld used by gcc... /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... yes
checking for /usr/bin/ld option to reload object files... -r
checking for BSD-compatible nm... /usr/bin/nm -B
checking whether ln -s works... yes
checking how to recognise dependent libraries... pass_all
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
checking dlfcn.h usability... yes
checking dlfcn.h presence... yes
checking for dlfcn.h... yes
checking for g++... g++
checking whether we are using the GNU C++ compiler... yes
checking whether g++ accepts -g... yes
checking dependency style of g++... gcc3
checking how to run the C++ preprocessor... g++ -E
checking for g77... no
checking for f77... no
checking for xlf... no
checking for frt... no
checking for pgf77... no
checking for fort77... no
checking for fl32... no
checking for af77... no
checking for f90... no
checking for xlf90... no
checking for pgf90... no
checking for epcf90... no
checking for f95... no
checking for fort... no
checking for xlf95... no
checking for ifc... no
checking for efc... no
checking for pgf95... no
checking for lf95... no
checking for gfortran... no
checking whether we are using the GNU Fortran 77 compiler... no
checking whether  accepts -g... no
checking the maximum length of command line arguments... 32768
checking command to parse /usr/bin/nm -B output from gcc object... ok
checking for objdir... .libs
checking for ar... ar
checking for ranlib... ranlib
checking for strip... strip
checking for correct ltmain.sh version... yes
checking if gcc supports -fno-rtti -fno-exceptions... no
checking for gcc option to produce PIC... -fPIC
checking if gcc PIC flag -fPIC works... yes
checking if gcc static flag -static works... yes
checking if gcc supports -c -o file.o... yes
checking whether the gcc linker (/usr/bin/ld) supports shared libraries... yes
checking dynamic linker characteristics... GNU/Linux ld.so
checking how to hardcode library paths into programs... immediate
checking whether stripping libraries is possible... yes
checking if libtool supports shared libraries... yes
checking whether to build shared libraries... no
checking whether to build static libraries... yes
configure: creating libtool
appending configuration tag "CXX" to libtool
checking for ld used by g++... /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... yes
checking whether the g++ linker (/usr/bin/ld) supports shared libraries... yes
checking for g++ option to produce PIC... -fPIC
checking if g++ PIC flag -fPIC works... yes
checking if g++ static flag -static works... yes
checking if g++ supports -c -o file.o... yes
checking whether the g++ linker (/usr/bin/ld) supports shared libraries... yes
checking dynamic linker characteristics... GNU/Linux ld.so
checking how to hardcode library paths into programs... immediate
appending configuration tag "F77" to libtool
appending configuration tag "GCJ" to libtool
checking if gcj supports -fno-rtti -fno-exceptions... (cached) no
checking for gcj option to produce PIC... -fPIC
checking if gcj PIC flag -fPIC works... no
checking if gcj static flag -static works... no
checking if gcj supports -c -o file.o... no
checking whether the gcj linker (/usr/bin/ld) supports shared libraries... yes
checking dynamic linker characteristics... gcj: libgcj.spec: No such file or directory
GNU/Linux ld.so
checking how to hardcode library paths into programs... immediate
checking for a BSD-compatible install... /usr/bin/install -c
checking for javac... /usr/bin/javac
checking for fastjar... /usr/bin/fastjar
checking for gcj-jar... no
checking for jar... /usr/bin/jar
configure: error: Can't find "swt.jar"
[/CENTER]

"Can't find swt.jar"?  I installed swt.

---

### Post by bikeboy on 2006-05-04
Sorry I haven't been able to work it out so far elfortunawe. I'll keep looking though.

---

### Post by dimatrod on 2006-05-11
I tried this since I've been meaning to get something to convert vids to my iAudio (and also for iPod, but current iriverter doesn't work) for linux, and finding that the program I used to use in XP actually had a Linux port, I gave this a try.  However, while ./configure'ing, it tells me ```
configure: error: Can't find "javac" in your PATH
``` while I already have Java installed correctly.  What is this javac?

---

### Post by bikeboy on 2006-05-11
[QUOTE=dimatrod]I tried this since I've been meaning to get something to convert vids to my iAudio (and also for iPod, but current iriverter doesn't work) for linux, and finding that the program I used to use in XP actually had a Linux port, I gave this a try.  However, while ./configure'ing, it tells me ```
configure: error: Can't find "javac" in your PATH
``` while I already have Java installed correctly.  What is this javac?[/QUOTE]

javac is the java compiler. I think the way I got around that was to install the GNU Java Compiler because there was no compiler with the Sun j2re.

"sudo apt-get install gcj-4.0"

After that check /etc/alternatives. There should be a symbolic link called javac.
If there is, do the ./configure again but with "--with-gcj" appended to the end.

It took me quite a bit of experimenting to get iriverter installed and I can't remember what worked and what didn't so there are some holes in my howto. I think I'll chuck in a livecd and try it from scratch to work out the steps better.

---

### Post by MrStaticVoid on 2006-05-16
[QUOTE=elfortunawe]I tried it with java again, and now I've got an icon in my menu, but when I clicked on it nothing happened.  I went to the terminal and got this again:

[CENTER]Exception in thread "main" java.lang.UnsatisfiedLinkError: no swt-pi-gtk-3138 in java.library.path
        at java.lang.ClassLoader.loadLibrary(ClassLoader.java:1517)
        at java.lang.Runtime.loadLibrary0(Runtime.java:788)
        at java.lang.System.loadLibrary(System.java:834)
        at org.eclipse.swt.internal.Library.loadLibrary(Library.java:123)
        at org.eclipse.swt.internal.gtk.OS.<clinit>(OS.java:19)
        at org.eclipse.swt.internal.Converter.wcsToMbcs(Converter.java:63)
        at org.eclipse.swt.internal.Converter.wcsToMbcs(Converter.java:54)
        at org.eclipse.swt.widgets.Display.<clinit>(Display.java:122)
        at org.thestaticvoid.iriverter.ConverterUI.<init>(ConverterUI.java:31)
        at org.thestaticvoid.iriverter.ConverterUI.main(ConverterUI.java:629)
elfortunawe@gateway-71-109-189-239:~$
[/CENTER]
[/QUOTE]

You are getting this error because SWT is looking for libswt-pi-gtk-3138.so, but it cannot find it.  I don't know where it is installed on Ubuntu, but wherever you find it you have two options:

Link it to /usr/local/lib (or /usr/lib):
$ sudo ln -s /path/to/libswt-pi-gtk-3138.so /usr/local/lib

or tell iriverter where to find it with:
$ LD_LIBRARY_PATH="/some/path" iriverter
where libswt-pi-gtk-3138.so is installed in "/some/path"

> 
Then I tried it with the GCJ thing, and it gave me this:

[CENTER]~/Desktop/iriverter-0.15$ ./configure --with-gcj=/usr/share/java//usr/share/java/libgcj-4.0.2.jar
<snip>
configure: error: Can't find "swt.jar"
[/CENTER]

"Can't find swt.jar"?  I installed swt.

You still have to specify the location of the swt.jar, like:

$ ./configure --with-swt=/usr/share/java/swt-gtk-3.1 --with-gcj

even with GCJ you still have to have libswt-pi-gtk-3138.so some where in the LD_LIBRARY_PATH.

If you have any other questions about iriverter please ask.  And be sure to try out 0.16.  I just released it yesterday.

---

### Post by zootm on 2006-05-29
[QUOTE=MrStaticVoid]You are getting this error because SWT is looking for libswt-pi-gtk-3138.so, but it cannot find it.  I don't know where it is installed on Ubuntu, but wherever you find it you have two options:

Link it to /usr/local/lib (or /usr/lib):
$ sudo ln -s /path/to/libswt-pi-gtk-3138.so /usr/local/lib

or tell iriverter where to find it with:
$ LD_LIBRARY_PATH="/some/path" iriverter
where libswt-pi-gtk-3138.so is installed in "/some/path"[/QUOTE]
It's actually all of the SWT JNI components that it complains about (the "pi" one is just the first it misses - if you use the first method it just complains about another).

The components are in:

/usr/lib/jni

So:

$ LD_LIBRARY_PATH="/usr/lib/jni" iriverter

Works great. Cheers for the help :)

I'm using Dapper, rather than Breezy, for what it's worth.

---

### Post by philipgm on 2006-05-29
Hi Zootm,

I'm using Dapper too but my JNI seem to be in /usr/lib, and now it works so thanks for the clues guys.

Phil

---

### Post by zootm on 2006-05-29
That's very strange that it'd be different, but I'm glad you got it sorted!

---

### Post by MetalMusicAddict on 2006-05-29
Kick a$$. Now if I could find a good app to build my database file for my H340. Soon to be a H360. (HD upgrade)

---

### Post by bikeboy on 2006-05-29
Awesome, glad people are getting past the probems I couldn't help with. I'll try to add this stuff to the OP when I get a chance, but right now exams and assignments are taking priority :(

---

### Post by pek on 2006-06-09
```
java.io.IOException: java.io.IOException: No such file or directory
   at java.lang.ConcreteProcess.<init>(libgcj.so.7)
   at java.lang.Runtime.execInternal(libgcj.so.7)
   at java.lang.Runtime.exec(libgcj.so.7)
   at java.lang.Runtime.exec(libgcj.so.7)
   at org.thestaticvoid.iriverter.Converter.runConversionCommand(Converter.java:409)
   at org.thestaticvoid.iriverter.Converter.convertSingleVideo(Converter.java:278)
   at org.thestaticvoid.iriverter.Converter.run(Converter.java:155)
Caused by: java.io.IOException: No such file or directory
   at java.lang.ConcreteProcess.nativeSpawn(libgcj.so.7)
   at java.lang.ConcreteProcess.spawn(libgcj.so.7)
   at java.lang.ConcreteProcess$ProcessManager.run(libgcj.so.7)
Exception in thread "Thread-1" java.lang.NullPointerException
   at org.thestaticvoid.iriverter.Converter.runConversionCommand(Converter.java:425)
   at org.thestaticvoid.iriverter.Converter.convertSingleVideo(Converter.java:278)
   at org.thestaticvoid.iriverter.Converter.run(Converter.java:155)

```

this is what i get :( when i try to convert something :(

---

### Post by seditiousmonkey on 2006-06-10
hey guys

also having trouble installing.  

when i initially configured with i configured with bikeboys script i got:

```
configure: error: Can't find "swt.jar"
```  
 
so tried adding  "--gcj" and got what i think is better results.

but make and sudo make install returned many errors and launching iriverter gives me

```
Exception in thread "main" java.lang.NoClassDefFoundError: org.thestaticvoid.iriverter.ConverterUI
   at gnu.java.lang.MainThread.run(libgcj.so.7)
Caused by: java.lang.ClassNotFoundException: org.thestaticvoid.iriverter.ConverterUI not found in gnu.gcj.runtime.SystemClassLoader{urls=[file:./], parent=gnu.gcj.runtime.ExtensionClassLoader{urls=[], parent=null}}
   at java.net.URLClassLoader.findClass(libgcj.so.7)
   at java.lang.ClassLoader.loadClass(libgcj.so.7)
   at java.lang.ClassLoader.loadClass(libgcj.so.7)
   at java.lang.Class.forName(libgcj.so.7)
   at gnu.java.lang.MainThread.run(libgcj.so.7)
joe@Joe-Downstairs:~/Desktop/iriverter-0.16$
```

so tried the linking SWT thing (dont know if thats what was wrong)  but it returns the same error.  i tried looking for libswt-pi-gtk-3138.so manually and found libswt-pi-gtk-3139.so   could the newer versian (i asume thats what it is) be causing my problems... or am i completly off track.

also went looking in synaptic for libswt-gtk-3.1-java but could only find libswt3.1-gtk.java which i hope is the same thing and is installed.

hope somone can help me and that i havent overwhelmed you all with details

---

### Post by bikeboy on 2006-06-10
[QUOTE=seditiousmonkey]

```
configure: error: Can't find "swt.jar"
```  
also went looking in synaptic for libswt-gtk-3.1-java but could only find libswt3.1-gtk.java which i hope is the same thing and is installed.

hope somone can help me and that i havent overwhelmed you all with details[/QUOTE]

Have you tried my original ./configure since you installed that libswt? I just checked the location of my swt-gtk-3.1.jar and it's definitely in /usr/share/java, it was installed from synaptic with "libswt-gtk-3.1-java", it's in the universe repo.

Try this in a term ```
 locate swt | grep .jar
``` to check that you have the thing that the configure script is looking for. If it shows this: "/usr/share/java/swt-gtk-3.1.jar", the configure should work with the following path.

./configure --with-swt=/usr/share/java/swt-gtk-3.1.jar

Very soon I will have to do the whole thing from scratch on a fresh install/livecd and document it so that I know if I've missed anything.

Edit: Don't have Dapper yet so I'll also test to see if anything needs to be done differently for that as well. Just over a week 'till holidays, so after that...

---

### Post by seditiousmonkey on 2006-06-12
thanks for your help bikeboy. still no luck with the SWT dependancy.  ill keep fiddling around till i figure it out.  it obviously can be done.

---

### Post by survient on 2006-12-30
lovely thing you've done here. I've done a lot of fiddling, and narrowed it down, but, still having issues getting it to run. I get a 
!!! no swt-pi-gtk-3235 in java.library.path
!!! 
!!! java.lang.ClassLoader.loadLibrary(ClassLoader.java:1682)
!!! java.lang.Runtime.loadLibrary0(Runtime.java:822)
!!! java.lang.System.loadLibrary(System.java:993)
!!! org.eclipse.swt.internal.Library.loadLibrary(Library.java:123)
!!! org.eclipse.swt.internal.gtk.OS.<clinit>(OS.java:22)
error primary when I just run "iriverter", and when I run LD_LIBRARY_PATH="/usr/lib" iriverter she gives me
 class java.lang.UnsatisfiedLinkError
--- iriverter 0.16
--- 
--- Settings:
--- 
--- 
!!! /usr/lib/libswt-pi-gtk-3235.so: /usr/lib/libswt-pi-gtk-3235.so: wrong ELF class: ELFCLASS32
and when it cries wrong elfclass, I know it's a 64 bit edgy issue. Anybody know where to get a x64_86 architecture version of libswt-pi-gtk-3235.so, or how to get it to run the 32 bit?

---

### Post by gardara on 2007-02-03
Has anyone managed to get iriverter working on edgy? I have been trying some tricks from this thread but I get stuck at [I]configure: error: Can't find "swt.jar"
[/I]

Any help would be appreciated.

---

### Post by ftmichael on 2007-03-05
I'm using Edgy and attempting to install iRiverter.

I followed the directions at [https://help.ubuntu.com/community/AudioPlayeriRiverH340](https://help.ubuntu.com/community/AudioPlayeriRiverH340) , which worked fine until I had to execute:

> ./configure --with-swt=/usr/lib/jvm/java-1.5.0-sun-1.5.0.08/jre/lib/ext/swt.jar

It says I should be in the iRiverter directory, which I assume is ~/swt .  I get this:

> michael@jeezychreezy:~/swt$ ./configure --with-swt=/usr/lib/jvm/java-1.5.0-sun-1.5.0.08/jre/lib/ext/swt.jar
bash: ./configure: No such file or directory
michael@jeezychreezy:~/swt$ 

Where the hell is the configure file?  Am I the only one with this issue?  What's up?

The contents of ~/swt:

> michael@jeezychreezy:~/swt$ ls
**about_files**
about.html
libcairo.so.1
libswt-atk-gtk-3138.so
libswt-awt-gtk-3138.so    
libswt-cairo-gtk-3138.so  
libswt-gnome-gtk-3138.so  
libswt-gtk-3138.so        
libswt-mozilla-gtk-3138.so
libswt-pi-gtk-3138.so
src.zip
swt.jar
michael@jeezychreezy:~/swt$ 

Neither src.zip nor swt.jar appears to contain any file called configure.

Michael

---

### Post by tehwa on 2007-03-06
> **ftmichael said:**
> I'm using Edgy and attempting to install iRiverter.

I followed the directions at [https://help.ubuntu.com/community/AudioPlayeriRiverH340](https://help.ubuntu.com/community/AudioPlayeriRiverH340) , which worked fine until I had to execute:



It says I should be in the iRiverter directory, which I assume is ~/swt .  I get this:



Where the hell is the configure file?  Am I the only one with this issue?  What's up?

The contents of ~/swt:



Neither src.zip nor swt.jar appears to contain any file called configure.

Michael
The "Iriverter directory" should be the directory that you extracted the iriverter-[version].tar.bz archive to, such as '/home/tehwa/src/iriverter-0.16'. You will find a configure file in here.

The wiki page has been clarified.

---

### Post by ftmichael on 2007-03-06
Got it; thanks!

Now that it's installed and running, can I delete the **~/src** and **~/swt** directories and all their contents?  They only hold stuff for iRiverter.

Michael

---

### Post by tetralis on 2007-07-29
OK my system is not Breezy however, I am using  Ubuntu 7.04, Feisty Fawn and the very same problem is present there.

I had to change the iriverter script so it look like:
#!/bin/sh
prefix=/usr
exec_prefix=${prefix}
java -Djava.library.path=$LD_LIBRARY_PATH:${exec_prefix}/lib:/usr/lib/jni -classpath $CLASSPATH:${prefix}/share/java/iriverter.jar:/usr/lib/java/swt.jar org.thestaticvoid.iriverter.ConverterUI $*

The only thing I added is :/usr/lib/jni to the end of the java.library.path define.

My setup is: 
 dpkg -l iriverter java-gcj-compat libswt3.2-gtk-java
==============-==============-============================================
ii  iriverter      0.16-0ubuntu2  converts video for use on various multimedia
ii  java-gcj-compa 1.0.65-8ubuntu Java runtime environment using GIJ
ii  libswt3.2-gtk- 3.2.2-0ubuntu3 Fast and rich GUI toolkit for Java, gtk2 ve

---

