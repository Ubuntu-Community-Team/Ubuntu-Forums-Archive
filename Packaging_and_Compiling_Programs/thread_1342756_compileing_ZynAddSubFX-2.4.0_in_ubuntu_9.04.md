---
title: "compileing ZynAddSubFX-2.4.0 in ubuntu 9.04"
date: 2009-12-01
forum: Packaging and Compiling Programs
---

### Post by seadao on 2009-12-01
i want to compile zynaddsubfx-2.4.0 in ubuntu 9.04 64 bit, i need the dssi functionality and jack support. i made the changes in the Makefile.inc:

CXX=g++

#You can set the on what OS is compiling (Linux/Windows)
OS_PORT=LINUX
#OS_PORT=WINDOWS

#The version of the FFTW which is used (2 or 3)
FFTW_VERSION=2
#FFTW_VERSION=3

#Assembler FLOAT to INT conversions
ASM_F2I=YES
#ASM_F2I=NO

#Graphic user interface disable option (ZynAddSubFX will run only in text-mode)
#DISABLE_GUI=YES
DISABLE_GUI=NO

# L I N U X   C O N F I G U R A T I O N
#Next line sets the midi input. It can be "ALSA", "OSS" or "NONE".
LINUX_MIDIIN=ALSA
#LINUX_MIDIIN=OSS
#LINUX_MIDIIN=NONE

#Next lines sets the audio output (OSS/JACK/PA)
#You may use only one at the time
#If you use "OSS_AND_JACK",,at runtime, zynaddsubfx will run by the default with jack support and 
#it will try OSS if JACK fails. At runtime you can set the OSS by default by command-line
#parameters (run 'zynaddsubfx --help' for help) 

#LINUX_AUDIOOUT=OSS_AND_JACK
#LINUX_AUDIOOUT=OSS
#LINUX_AUDIOOUT=NONE
LINUX_AUDIOOUT=JACK
#LINUX_AUDIOOUT=JACK_RT     JACK_RT support is broken
#for PortAudio (PA)
#LINUX_AUDIOOUT=PA


#Next line sets if the synth is compiled for DSSI plugin (as .so file)
#If this setting is "YES", MIDI in and AUDIOOUT are set automatically to DSSI
#LINUX_DSSI=NO
LINUX_DSSI=YES

#Next line sets if the LASH session handler will be used
#LINUX_USE_LASH=YES
LINUX_USE_LASH=NO

the compilation fails (i tried both fftw 2 and 3) this is the error:

```
rm -f zynaddsubfx zynaddsubfx.exe
rm -f Make.deps 
g++ -shared  -o zynaddsubfx.so */*.o *.o -lm  -lmxml -lz `fltk-config --ldflags`  -lrfftw -lfftw -lpthread 
/usr/bin/ld: Controls/Control.o: relocation R_X86_64_32S against `vtable for Control' can not be used when making a shared object; recompile with -fPIC
Controls/Control.o: could not read symbols: Bad value
collect2: ld returned 1 exit status
make: *** [all] Error 1

```

is this a gcc bug?? or 64bit issue?? please help

---

### Post by SevenMachines on 2009-12-01
do you have a link to the source you are using? and maybe more information about the steps you took to compile it if there were indeed more.

have you tried adding -fPIC to the gcc options?

---

### Post by seadao on 2009-12-01
the source is from sourceforge page:
[http://sourceforge.net/projects/zynaddsubfx](http://sourceforge.net/projects/zynaddsubfx)
i added -fPIC to Makefile in the /src and the first build finished(i think) i got the zynaddsubfx.so the second stage in /Spliter also build with no problems with a working spliter binery

but the last stage in controller fails with:
```
ZynAddSubFX-2.4.0/ExternalPrograms/Controller$ make
gcc `fltk-config --cflags` -c main.C -o main.o
In file included from main.C:2:
ControllerUI.h:6:23: error: FL/Fl_Box.h: No such file or directory
In file included from main.C:2:
ControllerUI.h:10: error: expected class-name before '{' token
make: *** [main.o] Error 1

```

i'm not really sure if the first stage is ok or not cuz i don't seen anything runable in the /src folder. i also have no clue how to package this since i don't see an install script or anything like that...

---

### Post by SevenMachines on 2009-12-01
looks like your missing the fltk headers, should be something like libfltk1.1-dev
this has the headers Fl_Box

$ dpkg -L libfltk1.1-dev|grep Box
/usr/include/FL/Fl_Box.H

---

### Post by SevenMachines on 2009-12-01
you'll need to change

#include <FL/Fl_Box.h>
to
#include <FL/Fl_Box.H>
in
ExternalPrograms/Controller/ControllerUI.h

---

### Post by seadao on 2009-12-01
i had them installed, libfltk1.1-dev version 1.1.9-6

```
cash@cash-laptop:~$ dpkg -L libfltk1.1-dev|grep Box
/usr/include/FL/Fl_Box.H
cash@cash-laptop:~$ cd '/home/cash/Desktop/ZynAddSubFX-2.4.0/ExternalPrograms/Controller' 
cash@cash-laptop:~/Desktop/ZynAddSubFX-2.4.0/ExternalPrograms/Controller$ make
gcc `fltk-config --cflags` -c main.C -o main.o
In file included from main.C:2:
ControllerUI.h:6:23: error: FL/Fl_Box.h: No such file or directory
In file included from main.C:2:
ControllerUI.h:10: error: expected class-name before '{' token
make: *** [main.o] Error 1
cash@cash-laptop:~/Desktop/ZynAddSubFX-2.4.0/ExternalPrograms/Controller$ 

```

---

### Post by SevenMachines on 2009-12-01
yep, see my last post, the .h in the header needs to be .H, capital, i dont know why fltk does this but it does :)

---

### Post by seadao on 2009-12-01
thank you that did it, controller runs, but what now?? where is the main program, like in the ubuntu repo?? i don't get it

maybe the first stage failed??

i make clean and make again in the /src

make[2]: Leaving directory `/home/cash/Desktop/ZynAddSubFX-2.4.0/src/Seq'
make[1]: Leaving directory `/home/cash/Desktop/ZynAddSubFX-2.4.0/src'
make objs
make[1]: Entering directory `/home/cash/Desktop/ZynAddSubFX-2.4.0/src'
g++ -O6 -Wall -g  -DOS_LINUX -DDSSIMIDIIN -DFFTW_VERSION_2 -DASM_F2I_YES -ggdb -fPIC -DFLTK_GUI `fltk-config --cflags`  -DDSSIAUDIOOUT    -c -o main.o main.cpp
make[1]: Leaving directory `/home/cash/Desktop/ZynAddSubFX-2.4.0/src'
rm -f zynaddsubfx zynaddsubfx.exe
rm -f Make.deps 
g++ -shared  -o zynaddsubfx.so */*.o *.o -lm  -lmxml -lz `fltk-config --ldflags`  -lrfftw -lfftw -lpthread 
cash@cash-laptop:~/Desktop/ZynAddSubFX-2.4.0/src$ ./zynaddsubfx.so  Segmentation fault
cash@cash-laptop:~/Desktop/ZynAddSubFX-2.4.0/src$

---

### Post by SevenMachines on 2009-12-01
without dssi support you get a working standalone executable binary called zynaddsubfx.
with dssi support enabled the output binary is a plugin, zynaddsubfx.so.

you'll need some dssi compatible software to load it into, there will be some in the repositories no doubt

---

### Post by seadao on 2009-12-01
ok thanks, i want to use it with qtractor, now how can i package this without an install script, i guess i can copy it into the system area but synaptic will probably not like that

whats my best option to get this to work as a qtractor dssi instrument?

---

### Post by SevenMachines on 2009-12-01
sorry, i know nothing about dssi, you might want to try the [multimedia production forum]("http://ubuntuforums.org/forumdisplay.php?f=335") for how to actually use dssi plugins with linux. i think thats probably the place where they're most likely to know how to set everything up

---

### Post by seadao on 2009-12-02
[http://fr2.rpmfind.net/linux/RPM/opensuse/11.2/x86_64/ZynAddSubFX-2.4.0-2.3.x86_64.html](http://fr2.rpmfind.net/linux/RPM/opensuse/11.2/x86_64/ZynAddSubFX-2.4.0-2.3.x86_64.html)

i found a suse 11.2 rpm with zynaddsubfx, it looks like the dssi functionality is implemented in it

/usr/lib64/dssi
/usr/lib64/dssi/zynaddsubfx.so

i tryed copying the so file i built to the same location, but jack-dssi-host faild to load it, same for qtractor. I also tryed to convert this package with alien, but that didn't work for me for some reason.

can anyone help me convert this suse rpm into a deb?? is that even possible??


EDIT: i guess dssi support is broken in the code?
[http://www.kvraudio.com/forum/viewtopic.php?t=263289](http://www.kvraudio.com/forum/viewtopic.php?t=263289)

---

### Post by SevenMachines on 2009-12-02
theres a couple of lines to change in src/Ouput/DSSIaudiooutput.cpp
that fixes loading the dssi plugin, if it doesnt work after that its zynaddsubfx that needs work upstream 
i've attached the diff and the new working DSSIaudiooutput.cpp
all i know is it loads... :)
$ jack-dssi-host -v ~/.dssi/zynaddsubfx.so 
jack-dssi-host: instance  0 on channel  0, plugin  0 is "/home/seven/.dssi/zynaddsubfx/ZASF/chan00"

---

### Post by seadao on 2009-12-02
WOW!! it loads with this patch!! it loads in jack-dssi-host and is selectable in qtractor on a midi track. however the ui does not showup and no sound is produced then connected to a virtual keyboard.

is there a way to load a patch from the bank of sounds without a ui?
it shows a:
```
cash@cash-laptop:~$ jack-dssi-host '/home/cash/Desktop/zyndssi64bit2.4.0/zynaddsubfx.so'
SSE2 detected

jack-dssi-host: OSC URL is:
osc.udp://cash-laptop:18195/dssi//home/cash/Desktop/zyndssi64bit2.4.0/zynaddsubfx/ZASF/chan00

host: Ready


```

so is it looking in /zynaddsubfx/ZASF/chan00 for a bank??

---

