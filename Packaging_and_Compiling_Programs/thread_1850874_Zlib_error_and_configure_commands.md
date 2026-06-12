---
title: "Zlib error and configure commands???"
date: 2011-09-26
forum: Packaging and Compiling Programs
---

### Post by PayPaul on 2011-09-26
I tried to find a fractal program called Quat in the repo but couldn't So I found a tar file and opened it up in archive manager. Now I've got files with no extensions and can't even use the apt-get install command to install quat. How do I find the correct directory path to put in terminal so I can install the program?

---

### Post by MG&amp;TL on 2011-09-26
There will be a README somewhere, hopefully. Don't hijack threads, go make your own.

Usually:

```
cd to folder containing a file called 'makefile'
./configure
make
sudo make install
```Note that these commands may take up a long time

---

### Post by PayPaul on 2011-09-26
I'm not hijacking this thread. I'm referencing what [seawolf167]("http://ubuntuforums.org/member.php?u=1042634") said about finding directories. This is the only thread I've found that relates to opening tar.gz files specifically. There is unfortunately no readme file and I can't seem to navigate to the directory in terminal using the commands that seawolf167 gave here.

this command didn't quite work for me even when I input what I believed to be the correct path to the file that I extracted. 

cd /location/of/filename.tar.gz



Should I move the extracted folder and its contents to a place more closer to the main directory that terminal opens up in? It's now in a sub folder of a sub folder in the home directory. I even did a *dir* command to see what directories were visible and that subdirectory appeared but I couldn't navigate to it using the *cd *command.. I even tried searching for a custom command to open it up with in the "open with" dialog box but that didn't work.

---

### Post by MG&amp;TL on 2011-09-26
You have to *extract* it first. A .tar.gz is similiar to a Windows .zip file.

Right-click on the file in your file browser, and click, "extract here". A directory should appear without the .tar.gz extension, although it might take a while. Then you should be able to browse and cd to it. You can remove the .tar.gz after extraction.

---

### Post by PayPaul on 2011-09-26
> **MG&TL said:**
> You have to *extract* it first. A .tar.gz is similiar to a Windows .zip file.

Right-click on the file in your file browser, and click, "extract here". A directory should appear without the .tar.gz extension, although it might take a while. Then you should be able to browse and cd to it. You can remove the .tar.gz after extraction.

Do I browse to it in the Open with Application dialog box where looking for a custom command?

---

### Post by MG&amp;TL on 2011-09-27
No. Not necessary. Just extract it, then look for instruction or a makefile.

---

### Post by PayPaul on 2011-09-27
> **MG&TL said:**
> No. Not necessary. Just extract it, then look for instruction or a makefile.

Now I have to look up what to do with a makefile. Can I just click on it. I have both the binaries and the source code. It's the source code that has two makefiles. One is makefile.am and the other is makefile.in.

I used the configure command (./configure) first and thought things were going smoothly until it ran into an error and aborted. It seems [COLOR=Red]zlib[/COLOR] is missing? Ok, another term I need to to look up. Sheesh!

---

### Post by PayPaul on 2011-09-27
i found a few threads relating to my problem but they were kind of old and seem related to older versions of Ubuntu so I hoped that posting a new thread on the same subject wouldn't be a problem

I'm going through the first steps of installing from a source file for Quat, a fractal editor, and used the configure command to start off. I got the error that I needed [COLOR=Red]zlib[/COLOR] and the command process aborted. I did a search for [COLOR=Red]zlib[/COLOR] in here and found a way of finding all the possible downloads for this type of file. Using that command line there was a good bunch of them. I'm not entirely sure which download to use the apt-get install command on. I also searched in the Software center and found a bunch of related compression programs. My impression from the information gathered so far is one often needs multiple packages installed successively in order to get the whole thing working. I wish I could have found a deb file or even the self installing program Quat in the software center but such was not the case. Can someone assist me in proceeding further. I feel I got this far, conquering the *cd* command, getting into that directory and starting the configure process. Now it's [COLOR=Red]zlib[/COLOR] that's the stumbling block. In case you don't look, I'm using Ubuntu 11.04.

---

### Post by nothingspecial on 2011-09-27
Is there a README file?

and if so, what does it say?

---

### Post by PayPaul on 2011-09-27
> **nothingspecial said:**
> Is there a README file?

and if so, what does it say?


There is but it's empty. No text or instructions at all. Yuck! Why would that be?

---

### Post by MG&amp;TL on 2011-09-27
Right:

Open synaptic package manager, search for zlib. Install it, then reboot if necessary.

Run ./configure again, see if it returns any errors.

When it returns no error, run:

```
make
make install
```

The makefile just tells the terminal what to do with 'make and make install'

---

### Post by PayPaul on 2011-09-27
> **MG&TL said:**
> Right:
Open synaptic package manager, search for zlib. Install it, then reboot if necessary.


OK. I found a number of zlib packages and I'm in the process of installing them. I hope it doesn't require a reboot....crossing fingers..

---

### Post by oldos2er on 2011-09-27
You only need to install the *-dev packages when compiling. Also you don't "run" a makefile directly, you run **make**

[http://www.sis.pitt.edu/~mbsclass/tutorial/advanced/makefile/whatis.htm](http://www.sis.pitt.edu/~mbsclass/tutorial/advanced/makefile/whatis.htm)

[https://help.ubuntu.com/community/CompilingEasyHowTo](https://help.ubuntu.com/community/CompilingEasyHowTo)

[https://wiki.ubuntu.com/CompilingSoftware](https://wiki.ubuntu.com/CompilingSoftware)

If you need more specific help, please post a link to where you downloaded quat from.

---

### Post by PayPaul on 2011-09-27
Ok. The zlib packages installed with synaptic thank you very much for that. No reboot required apparently. Please be patient with what follows. At least now I know how to put in the code into threads so it has a scroller. I went through all the subsequent commands required and there are no apparent glitches, yet I can't find the Quat program installed anywhere.

Here's what I proceeded to do after installing the zlib packages:

```
paulw@ubuntu:~$ cd quat-1.20
paulw@ubuntu:~/quat-1.20$ ./configure
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... no
checking for mawk... mawk
checking whether make sets ${MAKE}... yes
checking for gcc... gcc
checking for C compiler default output... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables... 
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for style of include used by make... GNU
checking dependency style of gcc... gcc3
checking for a BSD-compatible install... /usr/bin/install -c
checking for gawk... (cached) mawk
checking whether ln -s works... yes
checking for ranlib... ranlib
checking for gcc option to accept ANSI C... none needed
checking for an ANSI C-conforming const... yes
checking for inline... inline
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
checking for stdlib.h... (cached) yes
checking for working malloc... yes
checking for memmove... yes
checking for memset... yes
checking for strchr... yes
checking for strrchr... yes
checking for strstr... yes
checking for strtod... yes
checking for strtol... yes
checking build system type... x86_64-unknown-linux-gnu
checking host system type... x86_64-unknown-linux-gnu
checking whether the C compiler supports -Wall... yes
checking whether the C compiler supports -O3... yes
checking whether the C compiler supports -ffast-math... yes
checking for library containing pow... -lm
checking for floor... yes
checking for pow... yes
checking for sqrt... yes
checking zlib.h usability... yes
checking zlib.h presence... yes
checking for zlib.h... yes
checking for gzopen in -lz... yes
checking for fltk-config... no
configure: WARNING:
   'fltk-config' not found. Compiling console version.
   If FLTK 1.1.x is not installed, please install it first if you want to
   compile the GUI version (strongly recommended).
   If FLTK 1.1.x is installed, and 'fltk-config' is not in your path, use
   the variable 'FLTK' in the configure command. Example:
   ./configure FLTK=/usr/local/fltk-1.1.0/bin/fltk-config
checking for select... yes
checking whether time.h and sys/time.h may both be included... yes
checking termios.h usability... yes
checking termios.h presence... yes
checking for termios.h... yes
checking sys/time.h usability... yes
checking sys/time.h presence... yes
checking for sys/time.h... yes
checking for memory.h... (cached) yes
checking conio.h usability... no
checking conio.h presence... no
checking for conio.h... no
configure: creating ./config.status
config.status: creating Makefile
config.status: creating doc/Makefile
config.status: creating kernel/Makefile
config.status: creating gui/Makefile
config.status: creating config.h
config.status: executing default-1 commands
paulw@ubuntu:~/quat-1.20$ make
cd . \
      && CONFIG_FILES= CONFIG_HEADERS=config.h \
         /bin/bash ./config.status
config.status: creating config.h
config.status: config.h is unchanged
config.status: executing default-1 commands
make  all-recursive
make[1]: Entering directory `/home/paulw/quat-1.20'
Making all in kernel
make[2]: Entering directory `/home/paulw/quat-1.20/kernel'
source='calculat.c' object='calculat.o' libtool=no \
    depfile='.deps/calculat.Po' tmpdepfile='.deps/calculat.TPo' \
    depmode=gcc3 /bin/bash ../depcomp \
    gcc -DHAVE_CONFIG_H -I. -I. -I..     -Wall -O3 -ffast-math -c `test -f calculat.c || echo './'`calculat.c
calculat.c: In function ‘IsNumber’:
calculat.c:261:10: warning: ignoring return value of ‘strtod’, declared with attribute warn_unused_result
source='colors.c' object='colors.o' libtool=no \
    depfile='.deps/colors.Po' tmpdepfile='.deps/colors.TPo' \
    depmode=gcc3 /bin/bash ../depcomp \
    gcc -DHAVE_CONFIG_H -I. -I. -I..     -Wall -O3 -ffast-math -c `test -f colors.c || echo './'`colors.c
source='files.c' object='files.o' libtool=no \
    depfile='.deps/files.Po' tmpdepfile='.deps/files.TPo' \
    depmode=gcc3 /bin/bash ../depcomp \
    gcc -DHAVE_CONFIG_H -I. -I. -I..     -Wall -O3 -ffast-math -c `test -f files.c || echo './'`files.c
files.c: In function ‘ParseFile’:
files.c:151:25: warning: ignoring return value of ‘fgets’, declared with attribute warn_unused_result
source='iter.c' object='iter.o' libtool=no \
    depfile='.deps/iter.Po' tmpdepfile='.deps/iter.TPo' \
    depmode=gcc3 /bin/bash ../depcomp \
    gcc -DHAVE_CONFIG_H -I. -I. -I..     -Wall -O3 -ffast-math -c `test -f iter.c || echo './'`iter.c
iter.c: In function ‘cutnorm’:
iter.c:605:18: warning: ‘n2[0]’ may be used uninitialized in this function
iter.c:605:18: warning: ‘n2[1]’ may be used uninitialized in this function
iter.c:605:18: warning: ‘n2[2]’ may be used uninitialized in this function
source='png.c' object='png.o' libtool=no \
    depfile='.deps/png.Po' tmpdepfile='.deps/png.TPo' \
    depmode=gcc3 /bin/bash ../depcomp \
    gcc -DHAVE_CONFIG_H -I. -I. -I..     -Wall -O3 -ffast-math -c `test -f png.c || echo './'`png.c
png.c: In function ‘PosOverIHDR’:
png.c:574:9: warning: ignoring return value of ‘fread’, declared with attribute warn_unused_result
png.c:576:9: warning: ignoring return value of ‘fread’, declared with attribute warn_unused_result
png.c: In function ‘ReadPNGLine’:
png.c:273:18: warning: ignoring return value of ‘fread’, declared with attribute warn_unused_result
png.c:278:18: warning: ignoring return value of ‘fread’, declared with attribute warn_unused_result
png.c:280:18: warning: ignoring return value of ‘fread’, declared with attribute warn_unused_result
png.c: In function ‘ReadChunkData’:
png.c:174:9: warning: ignoring return value of ‘fread’, declared with attribute warn_unused_result
png.c:175:9: warning: ignoring return value of ‘fread’, declared with attribute warn_unused_result
png.c: In function ‘GetNextChunk’:
png.c:159:9: warning: ignoring return value of ‘fread’, declared with attribute warn_unused_result
png.c:161:9: warning: ignoring return value of ‘fread’, declared with attribute warn_unused_result
png.c: In function ‘InitPNG’:
png.c:113:9: warning: ignoring return value of ‘fread’, declared with attribute warn_unused_result
png.c:119:9: warning: ignoring return value of ‘fread’, declared with attribute warn_unused_result
png.c:121:9: warning: ignoring return value of ‘fread’, declared with attribute warn_unused_result
png.c:126:9: warning: ignoring return value of ‘fread’, declared with attribute warn_unused_result
png.c:137:9: warning: ignoring return value of ‘fread’, declared with attribute warn_unused_result
source='qmath.c' object='qmath.o' libtool=no \
    depfile='.deps/qmath.Po' tmpdepfile='.deps/qmath.TPo' \
    depmode=gcc3 /bin/bash ../depcomp \
    gcc -DHAVE_CONFIG_H -I. -I. -I..     -Wall -O3 -ffast-math -c `test -f qmath.c || echo './'`qmath.c
source='quat.c' object='quat.o' libtool=no \
    depfile='.deps/quat.Po' tmpdepfile='.deps/quat.TPo' \
    depmode=gcc3 /bin/bash ../depcomp \
    gcc -DHAVE_CONFIG_H -I. -I. -I..     -Wall -O3 -ffast-math -c `test -f quat.c || echo './'`quat.c
quat.c: In function ‘CalculateFractal’:
quat.c:797:4: warning: passing argument 1 of ‘time’ makes pointer from integer without a cast
/usr/include/time.h:186:15: note: expected ‘time_t *’ but argument is of type ‘long int’
quat.c:952:6: warning: passing argument 1 of ‘time’ makes pointer from integer without a cast
/usr/include/time.h:186:15: note: expected ‘time_t *’ but argument is of type ‘long int’
source='textver.c' object='textver.o' libtool=no \
    depfile='.deps/textver.Po' tmpdepfile='.deps/textver.TPo' \
    depmode=gcc3 /bin/bash ../depcomp \
    gcc -DHAVE_CONFIG_H -I. -I. -I..     -Wall -O3 -ffast-math -c `test -f textver.c || echo './'`textver.c
gcc  -Wall -O3 -ffast-math   -o quat-txt  calculat.o colors.o files.o iter.o png.o qmath.o quat.o textver.o  -lz -lm 
make[2]: Leaving directory `/home/paulw/quat-1.20/kernel'
Making all in gui
make[2]: Entering directory `/home/paulw/quat-1.20/gui'
make  all-am
make[3]: Entering directory `/home/paulw/quat-1.20/gui'
make[3]: Nothing to be done for `all-am'.
make[3]: Leaving directory `/home/paulw/quat-1.20/gui'
make[2]: Leaving directory `/home/paulw/quat-1.20/gui'
Making all in doc
make[2]: Entering directory `/home/paulw/quat-1.20/doc'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/paulw/quat-1.20/doc'
make[2]: Entering directory `/home/paulw/quat-1.20'
make[2]: Leaving directory `/home/paulw/quat-1.20'
make[1]: Leaving directory `/home/paulw/quat-1.20'

paulw@ubuntu:~/quat-1.20$ sudo make install
[sudo] password for paulw: 
Making install in kernel
make[1]: Entering directory `/home/paulw/quat-1.20/kernel'
make[2]: Entering directory `/home/paulw/quat-1.20/kernel'
/bin/bash ../mkinstalldirs /usr/local/bin
  /usr/bin/install -c quat-txt /usr/local/bin/quat-txt
make[2]: Nothing to be done for `install-data-am'.
make[2]: Leaving directory `/home/paulw/quat-1.20/kernel'
make[1]: Leaving directory `/home/paulw/quat-1.20/kernel'
Making install in gui
make[1]: Entering directory `/home/paulw/quat-1.20/gui'
make[2]: Entering directory `/home/paulw/quat-1.20/gui'
/bin/bash ../mkinstalldirs /usr/local/bin
make[2]: Nothing to be done for `install-data-am'.
make[2]: Leaving directory `/home/paulw/quat-1.20/gui'
make[1]: Leaving directory `/home/paulw/quat-1.20/gui'
Making install in doc
make[1]: Entering directory `/home/paulw/quat-1.20/doc'
make[2]: Entering directory `/home/paulw/quat-1.20/doc'
make[2]: Nothing to be done for `install-exec-am'.
/bin/bash ../mkinstalldirs /usr/local/share/quat
mkdir /usr/local/share/quat
 /usr/bin/install -c -m 644 quat-de.html /usr/local/share/quat/quat-de.html
 /usr/bin/install -c -m 644 quat-de-1.html /usr/local/share/quat/quat-de-1.html
 /usr/bin/install -c -m 644 quat-de-2.html /usr/local/share/quat/quat-de-2.html
 /usr/bin/install -c -m 644 quat-de-3.html /usr/local/share/quat/quat-de-3.html
 /usr/bin/install -c -m 644 quat-de-4.html /usr/local/share/quat/quat-de-4.html
 /usr/bin/install -c -m 644 quat-de-5.html /usr/local/share/quat/quat-de-5.html
 /usr/bin/install -c -m 644 quat-us.html /usr/local/share/quat/quat-us.html
 /usr/bin/install -c -m 644 quat-us-1.html /usr/local/share/quat/quat-us-1.html
 /usr/bin/install -c -m 644 quat-us-2.html /usr/local/share/quat/quat-us-2.html
 /usr/bin/install -c -m 644 quat-us-3.html /usr/local/share/quat/quat-us-3.html
 /usr/bin/install -c -m 644 quat-us-4.html /usr/local/share/quat/quat-us-4.html
 /usr/bin/install -c -m 644 quat-us-5.html /usr/local/share/quat/quat-us-5.html
 /usr/bin/install -c -m 644 gpl.html /usr/local/share/quat/gpl.html
 /usr/bin/install -c -m 644 quat.png /usr/local/share/quat/quat.png
 /usr/bin/install -c -m 644 chart_de.png /usr/local/share/quat/chart_de.png
 /usr/bin/install -c -m 644 chart_us.png /usr/local/share/quat/chart_us.png
 /usr/bin/install -c -m 644 oe.png /usr/local/share/quat/oe.png
 /usr/bin/install -c -m 644 ve.png /usr/local/share/quat/ve.png
 /usr/bin/install -c -m 644 ce.png /usr/local/share/quat/ce.png
 /usr/bin/install -c -m 644 ie.png /usr/local/share/quat/ie.png
 /usr/bin/install -c -m 644 ote.png /usr/local/share/quat/ote.png
 /usr/bin/install -c -m 644 ex_1.jpg /usr/local/share/quat/ex_1.jpg
 /usr/bin/install -c -m 644 ex_2.jpg /usr/local/share/quat/ex_2.jpg
 /usr/bin/install -c -m 644 ex_3.jpg /usr/local/share/quat/ex_3.jpg
 /usr/bin/install -c -m 644 Dendr_st.jpg /usr/local/share/quat/Dendr_st.jpg
make[2]: Leaving directory `/home/paulw/quat-1.20/doc'
make[1]: Leaving directory `/home/paulw/quat-1.20/doc'
make[1]: Entering directory `/home/paulw/quat-1.20'
make[2]: Entering directory `/home/paulw/quat-1.20'
make[2]: Nothing to be done for `install-exec-am'.
/bin/bash ./mkinstalldirs /usr/local/share
 /usr/bin/install -c -m 644 ././Makefiles /usr/local/share/Makefiles
/usr/bin/install: omitting directory `././Makefiles'
 /usr/bin/install -c -m 644 ././examples /usr/local/share/examples
/usr/bin/install: omitting directory `././examples'
 /usr/bin/install -c -m 644 ./quat.iss /usr/local/share/quat.iss
make[2]: Leaving directory `/home/paulw/quat-1.20'
make[1]: Leaving directory `/home/paulw/quat-1.20'

```There is only one or two entries that seem to indicate a possible problem. What does it mean when it says "Nothing to be done for `install-exec-am'? Could that be a problem? It doesn't have the word "error" in it. 

So where do I go from here? Is it actually installed and why can't I find Quat in installed programs? Do I have to reboot after all?  I've gotten this far and still feel like I've Mount Everest to climb.


... I think I see the error myself. 

[COLOR=Red]configure: WARNING:    'fltk-config' not found. Compiling console version.    If FLTK 1.1.x is not installed, please install it first if you want to    compile the GUI version (strongly recommended).    If FLTK 1.1.x is installed, and 'fltk-config' is not in your path, use    the variable 'FLTK' in the configure command. Example:    ./configure FLTK=/usr/local/fltk-1.1.0/bin/fltk-config[/COLOR]

Hmmm. One more thing to install. is Ubuntu like that character playing Jackie Chan's Uncle in the animated series? He always goes to Jackie and screams out: "one more thing!!". Can i find that package listed, install it and then re-run those commands again?

---

### Post by oldos2er on 2011-09-27
Thread moved to Packaging & Compiling Programs.

Also I've merged all the relevant posts here to help solve your problem.

---

### Post by oldos2er on 2011-09-27
It's installed the console version, so type **quat** into a terminal and see what happens.

**apt-cache search fltk** gives a lot of results. I would try installing libfltk1.3-dev, run **make clean** then retry **make**.

You do know there are several fractal generators in the repositories?

And again, a link to a website would be nice.

---

### Post by PayPaul on 2011-09-27
> **oldos2er said:**
> It's installed the console version, so type **quat** into a terminal and see what happens.

**apt-cache search fltk** gives a lot of results. I would try installing libfltk1.3-dev, run **make clean** then retry **make**.

Ahh. Run make clean in the directory where Quat is located? Not bad for  logical command structure. I do like how much of these commands and such  have a reasonable syntax. _[COLOR=SeaGreen]Clean[/COLOR]_ the make huh.. very good.. LOL!

I guess I can use synaptic to find that libfltk 1.3-dev package. That was handy when trying to get the zlib packages. I installed every one of those that had any connection with zlib or compression as such.

> You do know there are several fractal generators in the repositories?

I have some of them but I like what Quat does with 3d Fractal images.

> And again, a link to a website would be nice.

Hmmm. Here's the Quat website in case anyone is interested.

[http://www.physcip.uni-stuttgart.de/phy11733/quat_e.html](http://www.physcip.uni-stuttgart.de/phy11733/quat_e.html)

---

### Post by PayPaul on 2011-09-27
> **oldos2er said:**
> It's installed the console version, so type **quat** into a terminal and see what happens.

**apt-cache search fltk** gives a lot of results. I would try installing libfltk1.3-dev, run **make clean** then retry **make**.


OK. I did all that, installed libfltk1.3-dev from synaptic and then ran make clean. 
Here are the results from terminal:

```
paulw@ubuntu:~$ cd quat-1.20
paulw@ubuntu:~/quat-1.20$ make clean
Making clean in doc
make[1]: Entering directory `/home/paulw/quat-1.20/doc'
make[1]: Nothing to be done for `clean'.
make[1]: Leaving directory `/home/paulw/quat-1.20/doc'
Making clean in gui
make[1]: Entering directory `/home/paulw/quat-1.20/gui'
test -z "" || rm -f 
rm -f *.o core *.core
make[1]: Leaving directory `/home/paulw/quat-1.20/gui'
Making clean in kernel
make[1]: Entering directory `/home/paulw/quat-1.20/kernel'
test -z "quat-txt" || rm -f quat-txt
test -z "" || rm -f 
rm -f *.o core *.core
make[1]: Leaving directory `/home/paulw/quat-1.20/kernel'
Making clean in .
make[1]: Entering directory `/home/paulw/quat-1.20'
make[1]: Nothing to be done for `clean-am'.
make[1]: Leaving directory `/home/paulw/quat-1.20'
paulw@ubuntu:~/quat-1.20$ make
make  all-recursive
make[1]: Entering directory `/home/paulw/quat-1.20'
Making all in kernel
make[2]: Entering directory `/home/paulw/quat-1.20/kernel'
source='calculat.c' object='calculat.o' libtool=no \
    depfile='.deps/calculat.Po' tmpdepfile='.deps/calculat.TPo' \
    depmode=gcc3 /bin/bash ../depcomp \
    gcc -DHAVE_CONFIG_H -I. -I. -I..     -Wall -O3 -ffast-math -c `test -f calculat.c || echo './'`calculat.c
calculat.c: In function &#8216;IsNumber&#8217;:
calculat.c:261:10: warning: ignoring return value of &#8216;strtod&#8217;, declared with attribute warn_unused_result
source='colors.c' object='colors.o' libtool=no \
    depfile='.deps/colors.Po' tmpdepfile='.deps/colors.TPo' \
    depmode=gcc3 /bin/bash ../depcomp \
    gcc -DHAVE_CONFIG_H -I. -I. -I..     -Wall -O3 -ffast-math -c `test -f colors.c || echo './'`colors.c
source='files.c' object='files.o' libtool=no \
    depfile='.deps/files.Po' tmpdepfile='.deps/files.TPo' \
    depmode=gcc3 /bin/bash ../depcomp \
    gcc -DHAVE_CONFIG_H -I. -I. -I..     -Wall -O3 -ffast-math -c `test -f files.c || echo './'`files.c
files.c: In function &#8216;ParseFile&#8217;:
files.c:151:25: warning: ignoring return value of &#8216;fgets&#8217;, declared with attribute warn_unused_result
source='iter.c' object='iter.o' libtool=no \
    depfile='.deps/iter.Po' tmpdepfile='.deps/iter.TPo' \
    depmode=gcc3 /bin/bash ../depcomp \
    gcc -DHAVE_CONFIG_H -I. -I. -I..     -Wall -O3 -ffast-math -c `test -f iter.c || echo './'`iter.c
iter.c: In function &#8216;cutnorm&#8217;:
iter.c:605:18: [COLOR=Red]warning[/COLOR]: &#8216;n2[0]&#8217; may be used uninitialized in this function
iter.c:605:18: [COLOR=Red]warning[/COLOR]: &#8216;n2[1]&#8217; may be used uninitialized in this function
iter.c:605:18: [COLOR=Red]warning[/COLOR]: &#8216;n2[2]&#8217; may be used uninitialized in this function
source='png.c' object='png.o' libtool=no \
    depfile='.deps/png.Po' tmpdepfile='.deps/png.TPo' \
    depmode=gcc3 /bin/bash ../depcomp \
    gcc -DHAVE_CONFIG_H -I. -I. -I..     -Wall -O3 -ffast-math -c `test -f png.c || echo './'`png.c
png.c: In function &#8216;PosOverIHDR&#8217;:
png.c:574:9: [COLOR=Red]warning[/COLOR]: ignoring return value of &#8216;fread&#8217;, declared with attribute warn_unused_result
png.c:576:9: [COLOR=Red]warning[/COLOR]: ignoring return value of &#8216;fread&#8217;, declared with attribute warn_unused_result
png.c: In function &#8216;ReadPNGLine&#8217;:
png.c:273:18: warning: ignoring return value of &#8216;fread&#8217;, declared with attribute warn_unused_result
png.c:278:18: warning: ignoring return value of &#8216;fread&#8217;, declared with attribute warn_unused_result
png.c:280:18: warning: ignoring return value of &#8216;fread&#8217;, declared with attribute warn_unused_result
png.c: In function &#8216;ReadChunkData&#8217;:
png.c:174:9: warning: ignoring return value of &#8216;fread&#8217;, declared with attribute warn_unused_result
png.c:175:9: warning: ignoring return value of &#8216;fread&#8217;, declared with attribute warn_unused_result
png.c: In function &#8216;GetNextChunk&#8217;:
png.c:159:9: warning: ignoring return value of &#8216;fread&#8217;, declared with attribute warn_unused_result
png.c:161:9: warning: ignoring return value of &#8216;fread&#8217;, declared with attribute warn_unused_result
png.c: In function &#8216;InitPNG&#8217;:
png.c:113:9: warning: ignoring return value of &#8216;fread&#8217;, declared with attribute warn_unused_result
png.c:119:9: warning: ignoring return value of &#8216;fread&#8217;, declared with attribute warn_unused_result
png.c:121:9: warning: ignoring return value of &#8216;fread&#8217;, declared with attribute warn_unused_result
png.c:126:9: warning: ignoring return value of &#8216;fread&#8217;, declared with attribute warn_unused_result
png.c:137:9: warning: ignoring return value of &#8216;fread&#8217;, declared with attribute warn_unused_result
source='qmath.c' object='qmath.o' libtool=no \
    depfile='.deps/qmath.Po' tmpdepfile='.deps/qmath.TPo' \
    depmode=gcc3 /bin/bash ../depcomp \
    gcc -DHAVE_CONFIG_H -I. -I. -I..     -Wall -O3 -ffast-math -c `test -f qmath.c || echo './'`qmath.c
source='quat.c' object='quat.o' libtool=no \
    depfile='.deps/quat.Po' tmpdepfile='.deps/quat.TPo' \
    depmode=gcc3 /bin/bash ../depcomp \
    gcc -DHAVE_CONFIG_H -I. -I. -I..     -Wall -O3 -ffast-math -c `test -f quat.c || echo './'`quat.c
quat.c: In function &#8216;CalculateFractal&#8217;:
quat.c:797:4: warning: passing argument 1 of &#8216;time&#8217; makes pointer from integer without a cast
/usr/include/time.h:186:15: note: expected &#8216;time_t *&#8217; but argument is of type &#8216;long int&#8217;
quat.c:952:6: warning: passing argument 1 of &#8216;time&#8217; makes pointer from integer without a cast
/usr/include/time.h:186:15: note: expected &#8216;time_t *&#8217; but argument is of type &#8216;long int&#8217;
source='textver.c' object='textver.o' libtool=no \
    depfile='.deps/textver.Po' tmpdepfile='.deps/textver.TPo' \
    depmode=gcc3 /bin/bash ../depcomp \
    gcc -DHAVE_CONFIG_H -I. -I. -I..     -Wall -O3 -ffast-math -c `test -f textver.c || echo './'`textver.c
gcc  -Wall -O3 -ffast-math   -o quat-txt  calculat.o colors.o files.o iter.o png.o qmath.o quat.o textver.o  -lz -lm 
make[2]: Leaving directory `/home/paulw/quat-1.20/kernel'
Making all in gui
make[2]: Entering directory `/home/paulw/quat-1.20/gui'
make  all-am
make[3]: Entering directory `/home/paulw/quat-1.20/gui'
make[3]: Nothing to be done for `all-am'.
make[3]: Leaving directory `/home/paulw/quat-1.20/gui'
make[2]: Leaving directory `/home/paulw/quat-1.20/gui'
Making all in doc
make[2]: Entering directory `/home/paulw/quat-1.20/doc'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/paulw/quat-1.20/doc'
make[2]: Entering directory `/home/paulw/quat-1.20'
make[2]: Leaving directory `/home/paulw/quat-1.20'
make[1]: Leaving directory `/home/paulw/quat-1.20'
paulw@ubuntu:~/quat-1.20$ sudo make install
[sudo] password for paulw: 
Making install in kernel
make[1]: Entering directory `/home/paulw/quat-1.20/kernel'
make[2]: Entering directory `/home/paulw/quat-1.20/kernel'
/bin/bash ../mkinstalldirs /usr/local/bin
  /usr/bin/install -c quat-txt /usr/local/bin/quat-txt
make[2]: Nothing to be done for `install-data-am'.
make[2]: Leaving directory `/home/paulw/quat-1.20/kernel'
make[1]: Leaving directory `/home/paulw/quat-1.20/kernel'
Making install in gui
make[1]: Entering directory `/home/paulw/quat-1.20/gui'
make[2]: Entering directory `/home/paulw/quat-1.20/gui'
/bin/bash ../mkinstalldirs /usr/local/bin
make[2]: Nothing to be done for `install-data-am'.
make[2]: Leaving directory `/home/paulw/quat-1.20/gui'
make[1]: Leaving directory `/home/paulw/quat-1.20/gui'
Making install in doc
make[1]: Entering directory `/home/paulw/quat-1.20/doc'
make[2]: Entering directory `/home/paulw/quat-1.20/doc'
make[2]: Nothing to be done for `install-exec-am'.
/bin/bash ../mkinstalldirs /usr/local/share/quat
 /usr/bin/install -c -m 644 quat-de.html /usr/local/share/quat/quat-de.html
 /usr/bin/install -c -m 644 quat-de-1.html /usr/local/share/quat/quat-de-1.html
 /usr/bin/install -c -m 644 quat-de-2.html /usr/local/share/quat/quat-de-2.html
 /usr/bin/install -c -m 644 quat-de-3.html /usr/local/share/quat/quat-de-3.html
 /usr/bin/install -c -m 644 quat-de-4.html /usr/local/share/quat/quat-de-4.html
 /usr/bin/install -c -m 644 quat-de-5.html /usr/local/share/quat/quat-de-5.html
 /usr/bin/install -c -m 644 quat-us.html /usr/local/share/quat/quat-us.html
 /usr/bin/install -c -m 644 quat-us-1.html /usr/local/share/quat/quat-us-1.html
 /usr/bin/install -c -m 644 quat-us-2.html /usr/local/share/quat/quat-us-2.html
 /usr/bin/install -c -m 644 quat-us-3.html /usr/local/share/quat/quat-us-3.html
 /usr/bin/install -c -m 644 quat-us-4.html /usr/local/share/quat/quat-us-4.html
 /usr/bin/install -c -m 644 quat-us-5.html /usr/local/share/quat/quat-us-5.html
 /usr/bin/install -c -m 644 gpl.html /usr/local/share/quat/gpl.html
 /usr/bin/install -c -m 644 quat.png /usr/local/share/quat/quat.png
 /usr/bin/install -c -m 644 chart_de.png /usr/local/share/quat/chart_de.png
 /usr/bin/install -c -m 644 chart_us.png /usr/local/share/quat/chart_us.png
 /usr/bin/install -c -m 644 oe.png /usr/local/share/quat/oe.png
 /usr/bin/install -c -m 644 ve.png /usr/local/share/quat/ve.png
 /usr/bin/install -c -m 644 ce.png /usr/local/share/quat/ce.png
 /usr/bin/install -c -m 644 ie.png /usr/local/share/quat/ie.png
 /usr/bin/install -c -m 644 ote.png /usr/local/share/quat/ote.png
 /usr/bin/install -c -m 644 ex_1.jpg /usr/local/share/quat/ex_1.jpg
 /usr/bin/install -c -m 644 ex_2.jpg /usr/local/share/quat/ex_2.jpg
 /usr/bin/install -c -m 644 ex_3.jpg /usr/local/share/quat/ex_3.jpg
 /usr/bin/install -c -m 644 Dendr_st.jpg /usr/local/share/quat/Dendr_st.jpg
make[2]: Leaving directory `/home/paulw/quat-1.20/doc'
make[1]: Leaving directory `/home/paulw/quat-1.20/doc'
make[1]: Entering directory `/home/paulw/quat-1.20'
make[2]: Entering directory `/home/paulw/quat-1.20'
make[2]: Nothing to be done for `install-exec-am'.
/bin/bash ./mkinstalldirs /usr/local/share
 /usr/bin/install -c -m 644 ././Makefiles /usr/local/share/Makefiles
/usr/bin/install: omitting directory `././Makefiles'
 /usr/bin/install -c -m 644 ././examples /usr/local/share/examples
/usr/bin/install: omitting directory `././examples'
 /usr/bin/install -c -m 644 ./quat.iss /usr/local/share/quat.iss
make[2]: Leaving directory `/home/paulw/quat-1.20'
make[1]: Leaving directory `/home/paulw/quat-1.20'

```

I still don't see the program, Quat in installed programs in the Software Manager nor in Applications. Is there an additional step or steps to be taken? I notice quite a number of [COLOR=Red]warnings[/COLOR] and *ignore* lines in these results.

---

### Post by MG&amp;TL on 2011-09-27
What happens when you type:

```
quat
```

in a terminal?

---

### Post by oldos2er on 2011-09-27
> **PayPaul said:**
> 
I still don't see the program, Quat in installed programs in the Software Manager nor in Applications. Is there an additional step or steps to be taken? 

That's pretty old code, but it might work.

Type **quat** into a terminal. What happens? If by 'Software Manager' you mean Ubuntu Software Center, that's normal. Compiling and installing source code takes place outside of the APT system.

---

### Post by MG&amp;TL on 2011-09-27
Yeah, I was thinking about that; if compiled source code is outside the apt system, does that mean you have to manually purge the prog if you want to remove it? Unless they had a "make clean" rule, and you happened to keep the source around.

---

### Post by oldos2er on 2011-09-27
If you used 'sudo make install' to install the code, you can go back into the source folder and run 'sudo make uninstall.' You do need to keep the source folder around to do that though.

---

### Post by SevenMachines on 2011-09-27
checkinstall is a good method of allowing make installs to be managed by the package manager, it means you dont need to have the source code to do a make uninstall as well.

---

### Post by PayPaul on 2011-09-27
> **SevenMachines said:**
> checkinstall is a good method of allowing make installs to be managed by the package manager, it means you dont need to have the source code to do a make uninstall as well.

Would it be sufficient to type in "checkinstall" on the command line where the directory in this case would be quat-1.20?

I was able to make a deb package out of that source code by using sudo checkinstall. Yet when I attempt to then install it (the thing is now a deb file) from the software center I'm given the error message  

The Package Is Of Bad Quality

The installation of a package which violates the quality standards isn't allowed. This could cause serious problems on your computer. Please contact the person or organisation who provided this package file and include the details beneath.

Lintian check results for /home/paulw/quat-1.20/quat_1.20-1_amd64.deb:
E: quat: maintainer-name-missing root@ubuntu 
E: quat: maintainer-address-malformed root@ubuntu

I'm real upset that the programs contributor seems to have an invalid or unreachable email address that's posted on their website. 

What is a "malformed root"? I had only seen those kind of things at a farmers market a few years ago. They were enlarged sugar beets. LOL!

---

### Post by SevenMachines on 2011-09-27
```
$ sudo apt-get install checkinstall
$ sudo checkinstall
```
Then just keep pressing enter to use the defaults
Package should then be created and automatically installed

---

### Post by PayPaul on 2011-09-27
> **SevenMachines said:**
> ```
$ sudo apt-get install checkinstall
$ sudo checkinstall
```Then just keep pressing enter to use the defaults
Package should then be created and automatically installed

What happened was that I used sudo checkinstall in the directory of the source code. when the package was created I was informed where it was placed. I then clicked on it and chose software center to install it. It's a deb file. Then I was given the error or warning message I posted above.

Should I try it again using the apt-get install checkinstall command first?

Here's what I got when I entered the first command:

paulw@ubuntu:~/quat-1.20$ sudo apt-get install checkinstall
[sudo] password for paulw: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
checkinstall is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 25 not upgraded.

The second command I already performed and this is what I got:

 Done. The new package has been installed and saved to

 /home/paulw/quat-1.20/quat_1.20-1_amd64.deb

 You can remove it from your system anytime using: 

      dpkg -r quat

So where's the program? I don't see Quat on my list of applications.

---

### Post by SevenMachines on 2011-09-27
If you build an application from source and use make install, this wont mean that it shows up in application menus or in the package manager. By using checkinstall you allow the package manager to look after installation and uninstallation, it still doesnt have anything to do with that package showing up in menus. To see what files you've installed you can, since you've used checkinstall, do,
```
 $ dpkg -L quat
```which will list the files you've installed
You should see files in something like /usr/local/bin, try running
```
 $ quat
```or 
```
 $ quat-text
```(is it?)
from the command line and see if it works

Finally I would say, this program is 6 years old, thats a lifetime in linux terms, maybe you should search for fractal programs in synaptic or the software-centre. These are much more likely to work, will be easily installable from the software centre, and will most likely show up in menus

---

### Post by SevenMachines on 2011-09-27
Oh yes, and software centre will warn about checkinstall packages, its meant to protect you from installing poor or dangerous packages you might have downloaded. It's not something you should use to install self-made checkinstall packages, use 
```
 $ sudo dpkg -i quat
```
to install
```
 $ sudo dpkg -r quat 
```
to uninstall, 
or use synaptic

---

### Post by PayPaul on 2011-09-27
> **SevenMachines said:**
> If you build an application from source and use make install, this wont mean that it shows up in application menus or in the package manager. By using checkinstall you allow the package manager to look after installation and uninstallation, it still doesnt have anything to do with that package showing up in menus. To see what files you've installed you can, since you've used checkinstall, do,
```
 $ dpkg -L quat
```which will list the files you've installed
You should see files in something like /usr/local/bin, try running
```
 $ quat
```or 
```
 $ quat-text
```(is it?)
from the command line and see if it works

Finally I would say, this program is 6 years old, thats a lifetime in linux terms, maybe you should search for fractal programs in synaptic or the software-centre. These are much more likely to work, will be easily installable from the software centre, and will most likely show up in menus

I understand that last part but this is the only program I know of that makes 3d fractals of the kind. The fractal apps in the repository are just too limited in their scope.

Here's what I got when I used those commands. Something about a reinstall. 

```
paulw@ubuntu:~$ dpkg -l quat
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name           Version        Description
+++-==============-==============-============================================
ii  quat           1.20-1         Quat 120 EOF
paulw@ubuntu:~$ quat
No command 'quat' found, did you mean:
 Command 'quot' from package 'quota' (main)
quat: command not found
paulw@ubuntu:~$ quat-text
quat-text: command not found
paulw@ubuntu:~$ 


```

---

### Post by SevenMachines on 2011-09-27
```
$ dpkg -L quat
```
Note, capital L!
You may need to use the full path, should be listed by the above command, something like
```
 $ /usr/local/bin/quat
```

---

### Post by PayPaul on 2011-09-27
> **SevenMachines said:**
> ```
$ dpkg -L quat
```Note, capital L!
You may need to use the full path, should be listed by the above command, something like
```
 $ /usr/local/bin/quat
```

You're very helpful and yet this doesn't make sense to me....yet..

This is what I got when I amended that command to use the "L" in caps. At least I got something. Now what I can do with it is another matter. 

```
paulw@ubuntu:~/quat-1.20$ dpkg -L quat
/.
/usr
/usr/share
/usr/share/doc
/usr/share/doc/quat
/usr/share/doc/quat/AUTHORS
/usr/share/doc/quat/NEWS
/usr/share/doc/quat/doc
/usr/share/doc/quat/doc/ex_3.jpg
/usr/share/doc/quat/doc/quat-us-5.html
/usr/share/doc/quat/doc/quat-us-4.html
/usr/share/doc/quat/doc/quat-de-3.html
/usr/share/doc/quat/doc/quat-us.html
/usr/share/doc/quat/doc/quat-us-3.html
/usr/share/doc/quat/doc/ex_2.jpg
/usr/share/doc/quat/doc/chart_us.png
/usr/share/doc/quat/doc/ex_1.jpg
/usr/share/doc/quat/doc/Dendr_st.jpg
/usr/share/doc/quat/doc/chart_de.png
/usr/share/doc/quat/doc/ie.png
/usr/share/doc/quat/doc/quat-de-4.html
/usr/share/doc/quat/doc/quat-de-1.html
/usr/share/doc/quat/doc/oe.png
/usr/share/doc/quat/doc/ote.png
/usr/share/doc/quat/doc/Makefile.am
/usr/share/doc/quat/doc/quat-de-5.html
/usr/share/doc/quat/doc/gpl.html
/usr/share/doc/quat/doc/ce.png
/usr/share/doc/quat/doc/quat-de-2.html
/usr/share/doc/quat/doc/quat-us-1.html
/usr/share/doc/quat/doc/quat-de.html
/usr/share/doc/quat/doc/Makefile
/usr/share/doc/quat/doc/quat.png
/usr/share/doc/quat/doc/Makefile.in
/usr/share/doc/quat/doc/ve.png
/usr/share/doc/quat/doc/quat-us-2.html
/usr/share/doc/quat/COPYING
/usr/share/doc/quat/INSTALL
/usr/share/doc/quat/README
/usr/share/doc/quat/ChangeLog
/usr/local
/usr/local/share
/usr/local/share/quat.iss
/usr/local/share/quat
/usr/local/share/quat/ex_3.jpg
/usr/local/share/quat/quat-us-5.html
/usr/local/share/quat/quat-us-4.html
/usr/local/share/quat/quat-de-3.html
/usr/local/share/quat/quat-us.html
/usr/local/share/quat/quat-us-3.html
/usr/local/share/quat/ex_2.jpg
/usr/local/share/quat/chart_us.png
/usr/local/share/quat/ex_1.jpg
/usr/local/share/quat/Dendr_st.jpg
/usr/local/share/quat/chart_de.png
/usr/local/share/quat/ie.png
/usr/local/share/quat/quat-de-4.html
/usr/local/share/quat/quat-de-1.html
/usr/local/share/quat/oe.png
/usr/local/share/quat/ote.png
/usr/local/share/quat/quat-de-5.html
/usr/local/share/quat/gpl.html
/usr/local/share/quat/ce.png
/usr/local/share/quat/quat-de-2.html
/usr/local/share/quat/quat-us-1.html
/usr/local/share/quat/quat-de.html
/usr/local/share/quat/quat.png
/usr/local/share/quat/ve.png
/usr/local/share/quat/quat-us-2.html
/usr/local/bin
/usr/local/bin/quat-txt
paulw@ubuntu:~/quat-1.20$ 

```

It seems like a list of all the files that are in the directory containing the source files for this program. Hmmm.. ?

---

### Post by SevenMachines on 2011-09-27
No, that looks fine. quat-text is the text version, doesnt look like the gui version has been built and installed though
Running
```
 $ /usr/local/bin/quat-txt
```
should work though

---

### Post by PayPaul on 2011-09-27
> **SevenMachines said:**
> No, that looks fine. quat-text is the text version, doesnt look like the gui version has been built and installed though
Running
```
 $ /usr/local/bin/quat-txt
```should work though


Hmmm. This is what I get when I run that code in terminal 

paulw@ubuntu:~/quat-1.20$ /usr/local/bin/quat-txt
Didn't understand the given parameters. For help use -h
paulw@ubuntu:~/quat-1.20$ quat-txt
Didn't understand the given parameters. For help use -h
paulw@ubuntu:~/quat-1.20$ 

thank you for your patience with a noob. I tried a similar program called Fract-o-rama from source and that experience wasn't much better. It came as a deb file but there was an error regarding python and dependency, whatever that means.

---

### Post by SevenMachines on 2011-09-28
The gui for quat *does* build on natty, but it takes an amount of hacking. The best thing to do would be to either ask around and see if...

* any of the main repository fractal programs you might of missed will do what you want
* Or if theres a 3rd part repository that provides something you could use
* Or theres a more up-to-date fractal program that will build without substantial hacking

---

### Post by MG&amp;TL on 2011-09-28
```
/usr/local/bin/quat-txt -h
```

Should tell you how to do it.

---

