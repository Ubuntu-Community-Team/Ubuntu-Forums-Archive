---
title: "building zsnes from source for hardy 64-bit"
date: 2008-09-12
forum: New to Ubuntu
---

### Post by Zieg30CT on 2008-09-12
I am attempting to build zsnes for linux from source as I had just successfully built kiba dock from source just a little while ago (first time building something from source). I took care of most of the dependencies zsnes needed and proceeded to build it however I am getting an error:
adrian1@Dracula:~$ cd zsnes
adrian1@Dracula:~/zsnes$ cd zsnes_1_51
adrian1@Dracula:~/zsnes/zsnes_1_51$ cd src
adrian1@Dracula:~/zsnes/zsnes_1_51/src$ ./configure --enable-release
checking build system type... x86_64-unknown-linux-gnu
checking host system type... x86_64-unknown-linux-gnu
checking target system type... x86_64-unknown-linux-gnu
checking for a BSD-compatible install... /usr/bin/install -c
checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables... 
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ISO C89... none needed
checking for g++... g++
checking whether we are using the GNU C++ compiler... yes
checking whether g++ accepts -g... yes
checking for nasm... nasm
checking for sdl-config... /usr/bin/sdl-config
checking for SDL - version >= 1.2.0... yes
checking for zlib - version >= 1.2.3... yes
checking for libpng - version >= 1.2.0... yes
checking if you want the zsnes debugger... yes
checking for initscr in -lcurses... yes
checking for initscr in -lncurses... yes
checking for initscr in -lpdcurses... no
checking if you want libao support... no
checking how to run the C preprocessor... gcc -E
checking for X... libraries , headers 
checking for glGetError in -lGL... yes
checking for OpenGL... yes
checking for JMA support... yes
checking for cpu info... found
checking if you want gdb friendly executable... no
checking which cpu architecture to optimize for... native
checking if you want crazy optimizations... yes
configure: WARNING: If you intend to distribute this binary, make sure you use force_arch and set to i586 (or whichever CPU Arch you intend for)
checking for grep that handles long lines and -e... /bin/grep
checking for egrep... /bin/grep -E
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
checking whether sys/types.h defines makedev... yes
configure: creating ./config.status
config.status: creating Makefile
config.status: creating config.h
config.status: config.h is unchanged


ZSNES v1.51

SDL support                   Version 1.2.12
NASM support                  NASM version 0.99.06-20071101 compiled on Nov 15 2007
zlib support                  Version 1.2.3.3
PNG support                   Yes, version 1.2.15beta5
OpenGL support                Yes
JMA support                   Yes
ZSNES debugger                Enabled

The binary will be installed in /usr/local/bin

Configure complete, now type 'make' and pray.

adrian1@Dracula:~/zsnes/zsnes_1_51/src$ sudo make install
tools/depbuild gcc " -pipe -I. -I/usr/local/include -I/usr/include -D__UNIXSDL__  -I/usr/include/SDL -D_GNU_SOURCE=1 -D_REENTRANT  -D__OPENGL__ -march=native -O3 -fomit-frame-pointer -fprefetch-loop-arrays -fforce-addr -s -D__RELEASE__" nasm " -w-orphan-labels -D__UNIXSDL__ -f elf -DELF -D__OPENGL__ -O99999999 -D__RELEASE__" cfg.o endmem.o init.o initc.o input.o md.o patch.o ui.o vcache.o version.o zloader.o zmovie.o zpath.o zstate.o ztime.o ztimec.o chips/c4emu.o chips/c4proc.o chips/dsp1emu.o chips/dsp1proc.o chips/dsp2proc.o chips/dsp3emu.o chips/dsp3proc.o chips/dsp4emu.o chips/dsp4proc.o chips/fxemu2.o chips/fxemu2b.o chips/fxemu2c.o chips/fxtable.o chips/obc1emu.o chips/obc1proc.o chips/sa1proc.o chips/sa1regs.o chips/sdd1emu.o chips/seta10.o chips/sfxproc.o chips/st10proc.o chips/7110proc.o chips/seta11.o chips/st11proc.o cpu/dma.o cpu/dsp.o cpu/dspproc.o cpu/execute.o cpu/executec.o cpu/irq.o cpu/memory.o cpu/memtable.o cpu/spc700.o cpu/stable.o cpu/table.o cpu/tablec.o debugasm.o debugger.o gui/gui.o gui/guifuncs.o gui/menu.o effects/burn.o effects/smoke.o effects/water.o jma/7zlzma.o jma/crc32.o jma/iiostrm.o	jma/inbyte.o jma/jma.o jma/lzma.o	jma/lzmadec.o jma/winout.o jma/zsnesjma.o mmlib/mm.o mmlib/linux.o  video/makev16b.o video/makev16t.o video/makevid.o video/mode716.o video/mode716b.o video/mode716d.o video/mode716e.o video/mode716t.o video/mode7.o video/mode7ext.o video/mv16tms.o video/m716text.o video/newg162.o video/newgfx.o video/newgfx16.o video/newgfx2.o video/procvid.o video/procvidc.o video/sw_draw.o video/2xsaiw.o video/hq2x16.o video/hq2x32.o video/hq3x16.o video/hq3x32.o video/hq4x16.o video/hq4x32.o video/ntsc.o video/copyvwin.o linux/audio.o linux/battery.o linux/sdlintrf.o linux/sdllink.o linux/gl_draw.o linux/sw_draw.o linux/safelib.o zip/unzip.o zip/zpng.o > makefile.dep
/usr/bin/install -c -d -m 0755 //usr/local/bin
/usr/bin/install -c -m 0755 zsnes //usr/local/bin
/usr/bin/install: cannot stat `zsnes': No such file or directory
make: *** [install] Error 1

I attempted to manually create the directory but no luck. I'm pretty sure that if I can get this folder made that zsnes will be set and ready for use once compiled.

If anyone can help me fix this error I'll be grateful. If you can't I guess I have no choice but to run zsnes in wine.

(Also. I wasn't sure whether I should post this here or in the x86-64 bit forum. If this thread isn't in the right place can someone move it to the correct one? Thanks)

---

### Post by Mister.Vash on 2008-09-13
split the steps apart

./configure --enable-release
make

just to see if you are getting an actual error during the make
if it makes without any issues, search the under the current folder for the zsnes file

If it's not there, then maybe it didn't get built.  If it is, try the

sudo make install  

./configure        - sets the build options
make               - compiles the program
sudo make install  - will compile the program if not already done and then install it for you

---

### Post by Zieg30CT on 2008-09-13
I'm running make now and so far there are no errors.:popcorn: If I still see a problem once it is done compiling I'll post it here.

---

### Post by Zieg30CT on 2008-09-13
Opps! spoke to soon I see. Now it is complaining about i386 architecture input files being incompatible with i386 x86-64 output.
(I'd post all the errors here but the forum is complaining about [img] tags and <img> tags that don't exist when I submit the post)
 

any ideas on how to make it compatible?

---

### Post by Zieg30CT on 2008-09-13
anybody know how?

---

