---
title: "Howto compile bleeding edge FlightGear"
date: 2006-08-31
forum: Outdated Tutorials &amp; Tips
---

### Post by fubadubrub on 2006-08-31
Howto compile bleeding edge FlightGear.




Dependencies.

1. Install these.  **freeglut3, freeglut3-dev, libglut3, libglut3-dev, zlib1g, zlib1g-dev, plib1.8.4c2, plib1.8.4-dev, libmetakit2.4.9.3c2, libmetakit2.4.9.3-dev**.




First the software OpenAL.

1. Open a terminal and type: **svn checkout http://www.openal.org/repos/openal/trunk openal**


2. Type: **cd /home/username/openal/OpenAL-Sample**


3. Type: **./autogen.sh**


4. Type: **./configure**


5. Type: **make**


6. Type: **sudo make install**


7. Type: **cd /home/username/openal/alut**


8. Type: **./autogen.sh**


9. Type: **./configure**


10. Type: **make**


11. Type: **sudo make install**


12. Type: **cd**




Now SimGear.

1. Type: **cvs -d :pserver:cvsguest@cvs.simgear.org:/var/cvs/SimGear-0.3 login**


2. Type: **guest**


3. Type: **cvs -d :pserver:cvsguest@cvs.simgear.org:/var/cvs/SimGear-0.3 co source**


4. Type: **cd /home/username/source**


5. Type: **./autogen.sh**


6. Type: **./configure**


7. Type: **make**


8. Type: **sudo make install**


9.  Type: **cd**




Now FlightGear.

1. Type: **mkdir FlightGear-0.9**


2. Type: **cd /home/username/Flight-Gear-0.9**


3. Type: **cvs -d :pserver:cvsguest@cvs.flightgear.org:/var/cvs/FlightGear-0.9 login**


4. Type: **guest**


5. Type: **cvs -d :pserver:cvsguest@cvs.flightgear.org:/var/cvs/FlightGear-0.9 co source**




Now check out a copy of the base data.

6. Type: **cvs -d :pserver:cvsguest@cvs.flightgear.org:/var/cvs/FlightGear-0.9 login**


7. Type: **guest**


8. Type: **cvs -d :pserver:cvsguest@cvs.flightgear.org:/var/cvs/FlightGear-0.9 co data**


9. Type: **cd /home/username/Flight-Gear-0.9/source**


10. Type: **./autogen.sh**


11. Type: **./configure**


12. Type: **make**


13. Type: **sudo make install**


14. Type: **cd**




Now we test FlightGear.

1. Type: **cd /home/username/FlightGear-0.9/source/src/Main**


2. Type: **./fgfs --fg-root=/home/username/FlightGear-0.9**

> If you get any error like this: **./fgfs: error while loading shared libraries: libalut.so.0: cannot open shared object file: No such file or directory**
Then you need to do this: **sudo your-favorite-text-editor-here /etc/ld.so.conf**

Now add this line to file on it's own line: **/usr/local/lib** save file and close your-favorite-text-editor-here.

Now type: **ldconfig**




Keeping your bleeding edge versions up to date.

1. For OpenAL simply type in your terminal: **svn checkout http://www.openal.org/repos/openal/trunk openal**


2. For SimGear simply type: **cd /home/username/source**  Then type: **cvs update -dP**


3. For FlightGear simply type: **cd /home/username/Flight-Gear-0.9/source**  Then type: **cvs update -d -P**


4. For FlightGear data simply type: **cd /home/username/Flight-Gear-0.9/data**  Then type: **cvs update -d -P**




If you pulled new source code files you must rebuild OpenAL, SimGear, FlightGear.  Simply repeat above compiling steps.




Optionally configuring your .bashrc.

1. You may want to add the lines as exactly as shown but simply replace username with your username to your .bashrc file.  Put them at the very end of the file:

> However if you added **/usr/local/lib** to **ld.so.conf** then simply remove the following lines completely: [B]LD_LIBRARY_PATH=/home/username/FlightGear-0.9/lib:$LD_LIBRARY_PATH
export LD_LIBRARY_PATH[/B] they will no longer be necessary.

[B]LD_LIBRARY_PATH=/home/username/FlightGear-0.9/lib:$LD_LIBRARY_PATH
export LD_LIBRARY_PATH
FG_HOME=/home/username/FlightGear-0.9
export FG_HOME
FG_ROOT=/home/username/FlightGear-0.9/data
export FG_ROOT
FG_SCENERY=$FG_ROOT/Scenery:$FG_ROOT/WorldScenery
export FG_SCENERY[/B]




Optionally you may want to also add a .fgfsrc file in **/home/username**

1. Here is my file to get you started, however please understand that you would need to modify the setting for **YOU**.  How do you know what to put in the .fgfsrc file, simple type: **cd /home/username/FlightGear-0.9/source/src/Main**  Then type: **./fgfs --help --verbose**

Sample .fgfsrc file:

[B]--disable-intro-music
--control=mouse
--units-feet
--enable-anti-alias-hud
--enable-random-objects
--enable-ai-models
--bpp=24
--geometry=800x600
--disable-auto-coordination
--timeofday=real
--time-match-real
--enable-real-weather-fetch[/B]




If you do the optional components then you will no longer need to cd to the FlightGear directory.  You will be able to simply type: **fgfs**.  Also I do not recomend full screen game mode as this is bleeding edge code and you will want easy access to terminal in order to terminate misbehavior




[http://www.flightgear.org](http://www.flightgear.org) FlightGear web site.
[http://www.simgear.org](http://www.simgear.org) SimGear web site.
[http://www.openal.org](http://www.openal.org) OpenAL web site.

---

### Post by Darganot on 2008-02-15
Hello, openal doesn't seem to want to compile.  I've followed the directions so far plus install the few other packages not listed (libtools, etc.)  I'm running a fresh install of Mint Daryna 4.0.

My errors while running make and install:

> daddy@Melvin-IV:~/openal/OpenAL-Sample$ make
make  all-recursive
make[1]: Entering directory `/home/daddy/openal/OpenAL-Sample'
Making all in admin
make[2]: Entering directory `/home/daddy/openal/OpenAL-Sample/admin'
Making all in pkgconfig
make[3]: Entering directory `/home/daddy/openal/OpenAL-Sample/admin/pkgconfig'
make[3]: Nothing to be done for `all'.
make[3]: Leaving directory `/home/daddy/openal/OpenAL-Sample/admin/pkgconfig'
make[3]: Entering directory `/home/daddy/openal/OpenAL-Sample/admin'
make[3]: Nothing to be done for `all-am'.
make[3]: Leaving directory `/home/daddy/openal/OpenAL-Sample/admin'
make[2]: Leaving directory `/home/daddy/openal/OpenAL-Sample/admin'
Making all in src
make[2]: Entering directory `/home/daddy/openal/OpenAL-Sample/src'
Making all in arch
make[3]: Entering directory `/home/daddy/openal/OpenAL-Sample/src/arch'
Making all in i386
make[4]: Entering directory `/home/daddy/openal/OpenAL-Sample/src/arch/i386'
test -d .libs || mkdir .libs
echo '# Generated by ltmain.sh - GNU libtool 1.5 (1.1220 2003/04/05 19:32:58)' >x86_cpu_caps_detect_prk.lo
echo "pic_object='.libs/x86_cpu_caps_detect_prk.o'" >>x86_cpu_caps_detect_prk.lo
echo "non_pic_object='x86_cpu_caps_detect_prk.o'" >>x86_cpu_caps_detect_prk.lo
/usr/bin/yasm -f elf x86_cpu_caps_detect_prk.nasm -o .libs/x86_cpu_caps_detect_prk.o -l x86_cpu_caps_detect_prk.lo.lst
x86_cpu_caps_detect_prk.nasm:77: invalid argument to [SECTION]
x86_cpu_caps_detect_prk.nasm:77: undefined symbol `.note.GNU' (first use)
x86_cpu_caps_detect_prk.nasm:77: undefined symbol `stack' (first use)
x86_cpu_caps_detect_prk.nasm:77:  (Each undefined symbol is reported only once.)
make[4]: *** [x86_cpu_caps_detect_prk.lo] Error 1
make[4]: Leaving directory `/home/daddy/openal/OpenAL-Sample/src/arch/i386'
make[3]: *** [all-recursive] Error 1
make[3]: Leaving directory `/home/daddy/openal/OpenAL-Sample/src/arch'
make[2]: *** [all-recursive] Error 1
make[2]: Leaving directory `/home/daddy/openal/OpenAL-Sample/src'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/daddy/openal/OpenAL-Sample'
make: *** [all] Error 2
daddy@Melvin-IV:~/openal/OpenAL-Sample$ sudo make install
[sudo] password for daddy:
Making install in admin
make[1]: Entering directory `/home/daddy/openal/OpenAL-Sample/admin'
Making install in pkgconfig
make[2]: Entering directory `/home/daddy/openal/OpenAL-Sample/admin/pkgconfig'
make[3]: Entering directory `/home/daddy/openal/OpenAL-Sample/admin/pkgconfig'
test -z "/usr/local/bin" || /bin/mkdir -p "/usr/local/bin"
 /usr/bin/install -c 'openal-config' '/usr/local/bin/openal-config'
test -z "/usr/local/lib/pkgconfig" || /bin/mkdir -p "/usr/local/lib/pkgconfig"
 /usr/bin/install -c -m 644 'openal.pc' '/usr/local/lib/pkgconfig/openal.pc'
make[3]: Leaving directory `/home/daddy/openal/OpenAL-Sample/admin/pkgconfig'
make[2]: Leaving directory `/home/daddy/openal/OpenAL-Sample/admin/pkgconfig'
make[2]: Entering directory `/home/daddy/openal/OpenAL-Sample/admin'
make[3]: Entering directory `/home/daddy/openal/OpenAL-Sample/admin'
make[3]: Nothing to be done for `install-exec-am'.
make[3]: Nothing to be done for `install-data-am'.
make[3]: Leaving directory `/home/daddy/openal/OpenAL-Sample/admin'
make[2]: Leaving directory `/home/daddy/openal/OpenAL-Sample/admin'
make[1]: Leaving directory `/home/daddy/openal/OpenAL-Sample/admin'
Making install in src
make[1]: Entering directory `/home/daddy/openal/OpenAL-Sample/src'
Making install in arch
make[2]: Entering directory `/home/daddy/openal/OpenAL-Sample/src/arch'
Making install in i386
make[3]: Entering directory `/home/daddy/openal/OpenAL-Sample/src/arch/i386'
test -d .libs || mkdir .libs
echo '# Generated by ltmain.sh - GNU libtool 1.5 (1.1220 2003/04/05 19:32:58)' >memcpy_mmx_prk.lo
echo "pic_object='.libs/memcpy_mmx_prk.o'" >>memcpy_mmx_prk.lo
echo "non_pic_object='memcpy_mmx_prk.o'" >>memcpy_mmx_prk.lo
/usr/bin/yasm -f elf memcpy_mmx_prk.nasm -o .libs/memcpy_mmx_prk.o -l memcpy_mmx_prk.lo.lst
memcpy_mmx_prk.nasm:103: invalid argument to [SECTION]
memcpy_mmx_prk.nasm:103: undefined symbol `.note.GNU' (first use)
memcpy_mmx_prk.nasm:103: undefined symbol `stack' (first use)
memcpy_mmx_prk.nasm:103:  (Each undefined symbol is reported only once.)
make[3]: *** [memcpy_mmx_prk.lo] Error 1
make[3]: Leaving directory `/home/daddy/openal/OpenAL-Sample/src/arch/i386'
make[2]: *** [install-recursive] Error 1
make[2]: Leaving directory `/home/daddy/openal/OpenAL-Sample/src/arch'
make[1]: *** [install-recursive] Error 1
make[1]: Leaving directory `/home/daddy/openal/OpenAL-Sample/src'
make: *** [install-recursive] Error 1

Thank you for this How-to if it winds up working, I love FG and would really like to get the FULL use out of it by having the CVS.  If this is an out of date guide, sorry, just point me to the correct place (it was the only one on here and newer than the instructions on the FG website).

---

### Post by promag on 2008-05-26
You should remove yasm:

sudo apt-get remove --purge yasm

and then instal nasm:

sudo apt-get install nasm

then rebuild

./autogen && ./configure && make && make install

---

### Post by RexdPont on 2009-01-08
I am trying to reinstall a modified version of FG 9.8 (all the mods in the FG) and I am having a problem that when I go to compile SimGear the configure script fails to include -lalut in the Makefiles.   So the complile fails when it hits an alut function.

I have edited all the Makefiles to fix the problem and it works, but there must be a better way.  How do you force the inclusion of a library?  It's not the loacation that is the problem, but the Makefile.

I am using kubuntu 8.04.  I have found references to the problem, but no solution.  

The Makefile in SimGear (3.8) shows "openal_LIBS = -lopenal -lm"  It should inclue -lalut.  

Do you know a way to force the correction into all the Makefiles?

Thanks,

Rex du Pont
[email]rhett333@verizon.net[/email]

---

