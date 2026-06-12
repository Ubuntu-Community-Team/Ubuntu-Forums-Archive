---
title: "AMD CodeAnalyst from source: How?"
date: 2006-09-20
forum: Packaging and Compiling Programs
---

### Post by kflorek on 2006-09-20
CodeAnalyst is a very cool program. (I know from the Windows XP version.) The most interesting part is that it shows you where the jams and wasted cycles are at the CPU level, by a graphical display of exactly what is happening in the CPUs pipeline. It could be very useful to others beside me to get it to run on Ubuntu AMD64. And I could make progress getting free of Windows. It's not that I dislike Windows especially; it's just that I don't like being chained to anything if I don't have to be.

I've been trying to puzzle through this one for a few days. I can't get past the ./configure errors.

 I'm not much of a programmer. Just an amateur who can do enough C++ and x86 assembly language for his own use, mostly in mathematics.


I got past ./configure not finding g++ by creating symbolic links. I got past it not finding qt by adding the switch --with-qt=/usr/share/qt3. Then nothing I have guessed gets past:

checking for QT runtime library... configure: error: no

 That's where the output ends. There are no errors output before this.

 The configure script is over 400K, so following the whole thing is impossible, and I'm very vague on the scripting language anyway. Fortunately a search through configure narrow to a single spot where "runtime" occurs (on 2 adjacent lines). Unfortunately the chain by which the variables get their values at this point is beyond me to follow.

 Within the configure script there are quite a lot   of possible switches listed. One of them is --with-qt-libraries, which would seem to be logical, but setting it equal to every lib directory I could find did not produce any different error. The error seems to be at the exact same spot judging by the config.log file, regardless of what I set the switch to.

 The last numbered lines in the config.log are

configure:5610: g++ -o conftest -g -02 -I /usr/share/qt3/include -L$/usr/lib64 conftest.cc -L/usr/lib64 -L/usr/share/qt3/ -lqt -lpopt >&5

/usr/bin/ld cannot find -lqt
collect2: ld returned 1 exit status
configure:5616: $? = 1
configure: failed program was:
| /* confdefs.h */
 the rest of the program

configure:5636: error: no

Maybe someone familiar with g++, configure scripts, or CodeAnalyst has some clues. I guess that -lqt (and -lpopt ?) are supposed to be set to some library directory in order for the g++ command line to make sense, is that right? My extrasensory perception fails me as to what to set to what. :-({|= 




--------------- chapter 2

I see there are fewer than 6 people, other than myself, that even had an interest sufficient to take a look, so this is going nowhere.

 I figured out the configure script enough to tell that it was looking for a library named qt. A lead in this forum in the thread about qt got me to where I realized that Ubuntu does not have a library containing qt (which is what -lqt refers to), but only the multi-threaded qt, named qt-mt, the library they say that is practically the only one still used; and so this area of the script will always fail. However, the script will instead look for the library "qt-mt" when there exists a subdirectory named lib64 in the "qt" directory (/usr/share/qt3, that is). Instead of lib64, Ubuntu has the subdirectory lib.(For AMD64, directories named lib seem to default to 64 bits, and symbolic links named lib64 point to the plain lib.) So I made a symlink called lib64 that linked to qt "lib." That got me past a few thousand more lines in the configure script, (about half way through.:cool: ) But the error there looks like a real stopper.

checking for x86-64 architecture... yes
checking for arch/kernel version combination...ok
checking for preempt patch ... yes
configure: error: unsupported kernel configuration CONFIG_PREEMPT

 I can can only guess what CONFIG_PREEMPT might be. It might just be to head off (PREEMPT?) a potential insecurity (a crash) if the program were to be used with something that was unknown to the programmer who wrote this, in which case I might disable this part of the script (if I knew how.) OTOH PREEMPT might refer to a kernel type for which no code was written. Or maybe an "include" file for PREEMPT, whatever it is, is not where the configure script can figure out.

---

### Post by thejam on 2007-03-14
I vaguely recall that  the CONFIG_PREEMPT kernel option is used to improve/reduce latency in the kernel to user interrupts like mouse movements and other interactions to make the machine feel more responsive.  I don't think it's a security risk.  You'll have to recompile the kernel after reconfiguring with "make menuconfig" in the appropriate "/usr/src/linux" dir, in order  to get rid of CONFIG_PREEMPT.

---

### Post by zeusfaber on 2007-05-11
I'm not sure if this will help but here's what I did to install this on feisty (32bit).

install libqt3-mt-dev, libqt3-mt, binutils-dev, libpopt-dev, automake, oprofile, libtool

symlink /usr/share/automake-1.10/  to /usr/share/automake-1.9/

./autogen.sh

./configure (with whatever you need)

make

make install

once complete things seem to run properly although i have not throughly tested.


thanks.
-joe

---

### Post by kflorek on 2007-05-12
zeusfaber,
 Thanks for the updated info about Feisty and CodeAnalyst.

 (Yes I'm doing this for AMD64. I'm a creepy wierdo that is interested in  64 bit assembly language programming.)

 I did considerably more futile work on this since September, until I was totally sick, and unwilling to think about it any more. I've somewhat recuperated by now. I did my upgrade to FF a few days ago, so it was worth another effort. I got the newer CA source from AMD, and reinstalled all the requirements as mentioned, just to be sure, although with linux varients who knows?

 "./configure" went error free all the way through (without me having to create any links or anything) but "make" gets errors. Unfortunately I am completely clueless about what to do in response.Here's where it starts to look wrong:


make[5]: Entering directory `/media/kf/files/AMD/CodeAnalyst_Linux-2.6.16/src/ca/libs/libca'
/bin/bash ../../../../libtool --tag=CXX --mode=link g++  -g -O2   -o libCA.la -rpath /usr/local/lib -no-undefined elfreader.lo symbolengine.lo symbolengine.moc.lo catranslate.lo xpwin.lo eventsfile.lo catranslate_gui.lo catranslate_gui_display.lo catranslate_console.lo catranslate_console_display.lo proctree.lo  -liberty -lpopt 
g++ -shared -nostdlib /usr/lib/gcc/x86_64-linux-gnu/4.1.2/../../../../lib64/crti.o /usr/lib/gcc/x86_64-linux-gnu/4.1.2/crtbeginS.o  .libs/elfreader.o .libs/symbolengine.o .libs/symbolengine.moc.o .libs/catranslate.o .libs/xpwin.o .libs/eventsfile.o .libs/catranslate_gui.o .libs/catranslate_gui_display.o .libs/catranslate_console.o .libs/catranslate_console_display.o .libs/proctree.o  -liberty /usr/lib/libpopt.so -L/usr/lib/gcc/x86_64-linux-gnu/4.1.2 -L/usr/lib/gcc/x86_64-linux-gnu/4.1.2/../../../../lib64 -L/lib/../lib64 -L/usr/lib/../lib64 -lstdc++ -lm -lc -lgcc_s /usr/lib/gcc/x86_64-linux-gnu/4.1.2/crtendS.o /usr/lib/gcc/x86_64-linux-gnu/4.1.2/../../../../lib64/crtn.o  -Wl,-soname -Wl,libCA.so.0 -o .libs/libCA.so.0.0.0
/usr/bin/ld: /usr/lib/gcc/x86_64-linux-gnu/4.1.2/../../../../lib64/libiberty.a(cplus-dem.o): relocation R_X86_64_32S against `_sch_istable' can not be used when making a shared object; recompile with -fPIC
/usr/lib/gcc/x86_64-linux-gnu/4.1.2/../../../../lib64/libiberty.a: could not read symbols: Bad value
collect2: ld returned 1 exit status
make[5]: *** [libCA.la] Error 1
make[5]: Leaving directory `/media/kf/files/AMD/CodeAnalyst_Linux-2.6.16/src/ca/libs/libca'
make[4]: *** [all-recursive] Error 1
make[4]: Leaving directory `/media/kf/files/AMD/CodeAnalyst_Linux-2.6.16/src/ca/libs/libca'
make[3]: *** [all-recursive] Error 1
make[3]: Leaving directory `/media/kf/files/AMD/CodeAnalyst_Linux-2.6.16/src/ca/libs'
make[2]: *** [all-recursive] Error 1
make[2]: Leaving directory `/media/kf/files/AMD/CodeAnalyst_Linux-2.6.16/src/ca'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/media/kf/files/AMD/CodeAnalyst_Linux-2.6.16/src'
make: *** [all-recursive] Error 1

The informative part seems to be:

/usr/bin/ld: /usr/lib/gcc/x86_64-linux-gnu/4.1.2/../../../../lib64/libiberty.a(cplus-dem.o): relocation R_X86_64_32S against `_sch_istable' can not be used when making a shared object; recompile with -fPIC
/usr/lib/gcc/x86_64-linux-gnu/4.1.2/../../../../lib64/libiberty.a: could not read symbols: Bad value
collect2: ld returned 1 exit status
make[5]: *** [libCA.la] Error 1

...all pertaining to libiberty.a, I guess, which is in directory /usr/lib/gcc/x86_64-linux-gnu/4.1.2/../../../../lib64/, which is actually /usr/lib64/. libiberity.a is in fact there. It is an archive and it does contain cplus-dem.o. I'm supposed to recompile it with the switch -fPIC and replace it in the archive? You have to be kidding! Even if I figure it out, isn't that bound to screw up the versioning for the package managers and whatever libiberty is used for?

 I'm sick again.:lolflag: 

 For some reason libiberty is not mentioned as present in any package when searching in Synaptic. Huh?

---

### Post by WW on 2007-05-12
> **kflorek said:**
> 
For some reason libiberty is not mentioned as present in any package when searching in Synaptic. Huh?
The library libiberty is provided by **binutils-dev**.

---

### Post by kflorek on 2007-05-24
Thanks WW. So I downloaded the sources for binutils.

 Since the way you are supposed to do this (and have it work!) is to run "./configure" in the base directory and then  "make," my task was to figure out how to do this and "recompile with -fPIC."  Putting -fPIC or --fPIC after ./configure didn't do a thing I could discern. The --help didn't list any plausible options. Well ... let's skip all the things that didn't work. There were a lot.

 Here's what did work:
With the freshly unpacked files in some convenient directory, do the ./configure" and  "make" in the that directory. Until you do that, the "make" files you need in the next step do not yet exist.

 Change to the libiberty sub-directory. Do "./configure --enable-shared." The --enable-shared turns out to be the thing that gets the "fPIC" thing going. Then do "make." There will be a file called "libiberty.a" which you might jump to the conclusion (like I did repeatedly) would be the one that has been compiled with -fPIC. No, you get exactly the same error with that one. A subdirectory of libiberty called "pic" has been created. "libiberty.a" from there is the one. Replace libiberty.a in the /usr/lib/ directory with this one. Probably rename the old one to something else first, so you can put it back in case something else gets screwed up with the new version (which seem likely, if anything else uses it at all.)

 I don't think you want to do a "make install" and possibly install a lot of things.

 If the owner and group are not "root" for the new file, it seems like good practice to change it to root. Mine had me as the owner. Although I tried to do the whole shebang as a user, not root, as we're often told is best, at some later steps some things "could not be created" until I repeated the commands with "sudo," so there is a mixture. OTOH, I hate to screw up working things really badly (which I have done) while doing something as "root."

 After that, the steps as mentioned by zeusfaber go to conclusion without error. Although I said I didn't have to create any links, I forgot that I _upgraded_ to Feisty, and I think the links I created before still are there.

 CodeAnalyst started up and seemed visually functional. I did not get to trying it on some code at that session. Just getting this far after so long at 3 AM had me doing somersaults. I was not expecting it.

  I thought I ought to check after writing this, and all I got was this:

X Error: BadDevice, invalid or uninitialized input device 167
  Major opcode:  146
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 167
  Major opcode:  146
  Minor opcode:  3
  Resource id:  0x0
Failed to open device

 And in a dialog box; "Failed to load Oprofile Driver". Then back to the command line without CodeAnalyst. Too bad. Looks as if trying a different video card temporarily (because of something unrelated) has somehow screwed up something for CodeAnalyst or X.

---

### Post by ILoveBobbyMarley on 2008-06-28
Hello I had the exact same problem but the solution didn't work for me. 

I was baffled.

Then I remembered that I had installed (probably badly) gcc-4.2 earlier today  from sources so I could run the ACML numerical libraries with all the parallel process blah blah blah 

anyway I typed

./configure CXX=g++-4.1

make, sudo make install and it works okay.

Hope this helps,

tom

---

### Post by Dori02 on 2008-10-17
If someone from ubuntu managers/ AMD developers see this, it could be great if AMD's CodeAnalyst could find its way to Debian packages.](*,)

It is a pity to have to use XP in order to use the Codeanalyst. :(

If anyone else wants this too, please let your voice be heard on this post

---

