---
title: "Installing Marathon..."
date: 2012-03-17
forum: New to Ubuntu
---

### Post by linux.convert on 2012-03-17
I should know the answer to this, but my knowledge on this is limited...

I have downloaded Marathon game files and the Aleph One source code, which is in tar.bz2, I have extracted and configured it, but when I got to the "make" stage, I hit a wall...

---------------------------------------------------
ldc@********:~/Downloads$ **cd AlephOne-20120128**/
ldc@********:~/Downloads/AlephOne-20120128$ **ls**
aclocal.m4                 config.sub    examples         Makefile.in
Aleph One Classic SDL.mcp  configure     Expat            missing
AlephOne.spec              configure.ac  INSTALL.BeOS     PBProjects
AlephOne.spec.in           COPYING       install-sh       README
AUTHORS                    COPYING.SDL   INSTALL.Unix     Resources
ChangeLog                  data          INSTALL.Windows  Source_Files
config.guess               depcomp       Makefile.am      THANKS
config.h.in                docs          Makefile.BeOS    tools
ldc@ldc-AOD257:~/Downloads/AlephOne-20120128$ **./configure**
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking target system type... i686-pc-linux-gnu
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for a thread-safe mkdir -p... /bin/mkdir -p
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking for gcc... gcc
checking whether the C compiler works... yes
checking for C compiler default output file name... a.out
checking for suffix of executables... 
checking whether we are cross compiling... no
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ISO C89... none needed
checking for style of include used by make... GNU
checking dependency style of gcc... gcc3
checking how to run the C preprocessor... gcc -E
checking for g++... no
checking for c++... no
checking for gpp... no
checking for aCC... no
checking for CC... no
checking for cxx... no
checking for cc++... no
checking for cl.exe... no
checking for FCC... no
checking for KCC... no
checking for RCC... no
checking for xlC_r... no
checking for xlC... no
checking whether we are using the GNU C++ compiler... no
checking whether g++ accepts -g... no
checking dependency style of g++... none
checking how to run the C++ preprocessor... /lib/cpp
configure: error: in `/home/ldc/Downloads/AlephOne-20120128':
configure: error: C++ preprocessor "/lib/cpp" fails sanity check
See `config.log' for more details
ldc@********:~/Downloads/AlephOne-20120128$ **make**
make: *** No targets specified and no makefile found.  Stop.
ldc@********:~/Downloads/AlephOne-20120128$ **sudo make**
[sudo] password for ldc: 
make: *** No targets specified and no makefile found.  Stop.
ldc@********:~/Downloads/AlephOne-20120128$ 
--------------------------------------------------------------

---

### Post by Perfect Storm on 2012-03-17
Did you install build-essential meta-package?

```
sudo apt-get install build-essential
```

---

### Post by linux.convert on 2012-03-17
I just got thru running the sudo apt-get, but it still gives me the same "error".

make: *** No targets specified and no makefile found.  Stop.

---

### Post by Toz on 2012-03-17
You should always review the error messages you get with each ./configure to see what packages are missing (or post back the results of your attempts). For example:
```
checking sndfile.h usability... no
checking sndfile.h presence... no
checking for sndfile.h... no
checking for VORBISFILE... no
configure: error: Package requirements (vorbisfile) were not met:

No package 'vorbisfile' found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables VORBISFILE_CFLAGS
and VORBISFILE_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.

```
...vorbisfile (libvorbis-dev) is missing. A complete error-free ./configure run would look like this:
```
$ ./configure
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking target system type... i686-pc-linux-gnu
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for a thread-safe mkdir -p... /bin/mkdir -p
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking for gcc... gcc
checking whether the C compiler works... yes
checking for C compiler default output file name... a.out
checking for suffix of executables... 
checking whether we are cross compiling... no
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ISO C89... none needed
checking for style of include used by make... GNU
checking dependency style of gcc... gcc3
checking how to run the C preprocessor... gcc -E
checking for g++... g++
checking whether we are using the GNU C++ compiler... yes
checking whether g++ accepts -g... yes
checking dependency style of g++... gcc3
checking how to run the C++ preprocessor... g++ -E
checking for ranlib... ranlib
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
checking for unistd.h... (cached) yes
checking pwd.h usability... yes
checking pwd.h presence... yes
checking for pwd.h... yes
checking for snprintf... yes
checking for vsnprintf... yes
checking for mkstemp... yes
checking for sdl-config... /usr/bin/sdl-config
checking for SDL - version >= 1.2.0... yes
checking SDL_image.h usability... no
checking SDL_image.h presence... no
checking for SDL_image.h... no
checking SDL_ttf.h usability... no
checking SDL_ttf.h presence... no
checking for SDL_ttf.h... no
checking SDL_net.h usability... yes
checking SDL_net.h presence... yes
checking for SDL_net.h... yes
checking for SDLNet_Init in -lSDL_net... yes
checking for library containing gethostbyname... none required
checking for library containing socket... none required
checking zlib.h usability... yes
checking zlib.h presence... yes
checking for zlib.h... yes
checking for zlibVersion in -lz... yes
checking for pkg-config... /usr/bin/pkg-config
checking pkg-config is at least version 0.9.0... yes
checking for ZZIP... yes
checking for PNG... yes
checking boost/bind.hpp usability... yes
checking boost/bind.hpp presence... yes
checking for boost/bind.hpp... yes
checking boost/function.hpp usability... yes
checking boost/function.hpp presence... yes
checking for boost/function.hpp... yes
checking smpeg/smpeg.h usability... no
checking smpeg/smpeg.h presence... no
checking for smpeg/smpeg.h... no
checking mad.h usability... no
checking mad.h presence... no
checking for mad.h... no
checking sndfile.h usability... no
checking sndfile.h presence... no
checking for sndfile.h... no
checking for VORBISFILE... yes
checking speex/speex.h usability... no
checking speex/speex.h presence... no
checking for speex/speex.h... no
checking alsa/asoundlib.h usability... yes
checking alsa/asoundlib.h presence... yes
checking for alsa/asoundlib.h... yes
checking for snd_pcm_open in -lasound... yes
checking for OpenGL support... yes
checking for gluScaleImage in -lGLU... yes
checking for GL/glext.h... yes
configure: creating ./config.status
config.status: creating Makefile
config.status: creating AlephOne.spec
config.status: creating Source_Files/Makefile
config.status: creating Source_Files/CSeries/Makefile
config.status: creating Source_Files/Expat/Makefile
config.status: creating Source_Files/Files/Makefile
config.status: creating Source_Files/GameWorld/Makefile
config.status: creating Source_Files/Input/Makefile
config.status: creating Source_Files/LibNAT/Makefile
config.status: creating Source_Files/Lua/Makefile
config.status: creating Source_Files/Misc/Makefile
config.status: creating Source_Files/ModelView/Makefile
config.status: creating Source_Files/Network/Makefile
config.status: creating Source_Files/Network/Metaserver/Makefile
config.status: creating Source_Files/RenderMain/Makefile
config.status: creating Source_Files/RenderOther/Makefile
config.status: creating Source_Files/Sound/Makefile
config.status: creating Source_Files/TCPMess/Makefile
config.status: creating Source_Files/XML/Makefile
config.status: creating tools/Makefile
config.status: creating data/Makefile
config.status: creating data/default_theme/Makefile
config.status: creating config.h
config.status: executing depfiles commands
Configuration done. Now type "make".

```

With respect to this package, there are additional required dependencies that you may be missing:
```
sudo apt-get install libsdl1.2-dev libsdl-net1.2* libzzip-dev libboost-all-dev libvorbis-dev
```

---

### Post by linux.convert on 2012-03-19
Thanks to the suggestions, I got past the make install stage, but it wouldn't run after typing "alephone" in the terminal. So I looked thru the Install.Unix file made sure all libraries were installed, then went thru the ./configure, make, sudo make install, and then this again....

----------------------------------------------------------------
ldc@********:~/Games/AlephOne-20120128$ alephone
Aleph One Linux 2012-01-28 1.0.1
[http://marathon.sourceforge.net/](http://marathon.sourceforge.net/)

Original code by Bungie Software <http://www.bungie.com/>
Additional work by Loren Petrich, Chris Pruett, Rhys Hill et al.
TCP/IP networking by Woody Zenfell
Expat XML library by James Clark
SDL port by Christian Bauer <Christian.Bauer@uni-mainz.de>

This is free software with ABSOLUTELY NO WARRANTY.
You are welcome to redistribute it under certain conditions.
For details, see the file COPYING.

Built with network play enabled.

Built with Lua scripting enabled.
FATAL: Please be sure the files 'Map', 'Shapes', 'Images' and 'Sounds' are correctly installed and try again. (error -1)
ldc@********:~/Games/AlephOne-20120128$ 
----------------------------------------------------------------

---

### Post by Perfect Storm on 2012-03-19
You need to install the game files as well.

---

### Post by linux.convert on 2012-03-19
The M1A1 folder as well as the Shapes, Images, Sounds and whatnot are all in the Aleph One folder.

--------------------------------------------
ldc@********:/usr/local/share/AlephOne/Marathon (A1)$ ls
Fonts.fntA        M1A1 Map.sceA     M1A1 Shapes.shpA  Plugins            Scripts
M1A1 Images.imgA  M1A1 Preferences  M1A1 Sounds.sndA  Read Me M1A1.html  Tracks
ldc@********:/usr/local/share/AlephOne/Marathon (A1)$ 
--------------------------------------------

---

### Post by Toz on 2012-03-19
The contents of the Marathon (A1) folder should be in /usr/local/share/AlephOne:
```
$ ls -l /usr/local/share/AlephOne/
total 29252
-rw-r--r-- 1 root root    22419 2012-03-19 14:11 Fonts
-rw-r--r-- 1 root root    22419 2012-03-19 14:16 Fonts.fntA
-rw-r--r-- 1 root root  1540224 2012-03-19 14:16 M1A1 Images.imgA
-rw-r--r-- 1 root root 11722270 2012-03-19 14:16 M1A1 Map.sceA
-rw-r--r-- 1 root root     1521 2012-03-19 14:16 M1A1 Preferences
-rwxr-xr-x 1 root root 13164680 2012-03-19 14:16 M1A1 Shapes.shpA
-rwxr-xr-x 1 root root  3431372 2012-03-19 14:16 M1A1 Sounds.sndA
drwxr-xr-x 2 root root     4096 2012-03-19 14:11 MML
drwxr-xr-x 5 root root     4096 2012-03-19 14:16 Plugins
-rwxr-xr-x 1 root root    12273 2012-03-19 14:16 Read Me M1A1.html
drwxr-xr-x 2 root root     4096 2012-03-19 14:16 Scripts
drwxr-xr-x 3 root root     4096 2012-03-19 14:11 Themes
drwxr-xr-x 2 root root     4096 2012-03-19 14:16 Tracks

```

---

### Post by linux.convert on 2012-03-19
As far as I an tell, all the files are there. 


-----------------------------------------------------------------
ldc@********:/usr/local/share/AlephOne/Marathon (A1)$ ls -l
total 29224
-rw-r--r-- 1 root root    22419 2012-01-28 20:13 Fonts.fntA
-rw-r--r-- 1 root root  1540224 2011-11-27 00:57 M1A1 Images.imgA
-rw-r--r-- 1 root root 11722270 2011-11-27 00:57 M1A1 Map.sceA
-rw-r--r-- 1 root root     1521 2011-11-27 00:57 M1A1 Preferences
-rwxr-xr-x 1 root root 13164680 2011-11-27 00:57 M1A1 Shapes.shpA
-rwxr-xr-x 1 root root  3431372 2011-11-27 00:57 M1A1 Sounds.sndA
drwxr-xr-x 5 root root     4096 2012-01-28 20:12 Plugins
-rwxr-xr-x 1 root root    12273 2011-11-27 00:57 Read Me M1A1.html
drwxr-xr-x 2 root root     4096 2012-01-28 20:12 Scripts
drwxr-xr-x 2 root root     4096 2012-01-28 20:12 Tracks
ldc@********:/usr/local/share/AlephOne/Marathon (A1)$ 
-----------------------------------------------------------------

Here's what I have in the Aleph One folder in usr/local/share

-----------------------------------------------------------------
ldc@********:/usr/local/share/AlephOne$ ls -l
total 36
-rw-r--r-- 1 root root 22419 2012-03-19 10:10 Fonts
drwxr-xr-x 5 root root  4096 2012-01-28 20:13 Marathon (A1)
drwxr-xr-x 2 root root  4096 2012-03-19 10:10 MML
drwxr-xr-x 3 root root  4096 2012-03-17 12:57 Themes
ldc@********:/usr/local/share/AlephOne$ 
-----------------------------------------------------------------

This folder is different from the /home/ldc/Games/AlephOne-20120128 folder

---------------------------------------------------------
ldc@********:/$ cd home/ldc/Games
ldc@********:~/Games$ ls
AlephOne-20120128  AlephOne-20120128.tar.bz2  Marathon-20120128-Data.zip
ldc@********:~/Games$ cd AlephOne-20120128/
ldc@********:~/Games/AlephOne-20120128$ ls -l
total 1460
-rw-r--r--  1 ldc ldc  47180 2011-11-30 19:18 aclocal.m4
-rwxr-xr-x  1 ldc ldc 702098 2012-02-07 20:36 Aleph One Classic SDL.mcp
-rw-rw-r--  1 ldc ldc   2416 2012-03-19 10:08 AlephOne.spec
-rw-rw-r--  1 ldc ldc   2418 2011-08-11 20:34 AlephOne.spec.in
-rw-rw-r--  1 ldc ldc    968 2011-08-11 20:34 AUTHORS
-rw-r--r--  1 ldc ldc      0 2011-11-30 19:06 ChangeLog
-rwxr-xr-x  1 ldc ldc  44643 2011-11-14 19:32 config.guess
-rw-rw-r--  1 ldc ldc   3575 2012-03-17 12:33 config.h
-rw-r--r--  1 ldc ldc   3207 2011-11-30 19:18 config.h.in
-rw-rw-r--  1 ldc ldc  46409 2012-03-19 10:08 config.log
-rwxrwxr-x  1 ldc ldc  37623 2012-03-19 10:08 config.status
-rwxr-xr-x  1 ldc ldc  35165 2011-11-14 19:32 config.sub
-rwxr-xr-x  1 ldc ldc 246140 2012-01-28 19:46 configure
-rw-rw-r--  1 ldc ldc   8672 2011-08-11 20:34 configure.ac
-rw-rw-r--  1 ldc ldc  35146 2011-08-11 20:34 COPYING
-rw-rw-r--  1 ldc ldc  23244 2011-08-11 20:34 COPYING.SDL
drwxr-xr-x  3 ldc ldc   4096 2012-03-19 10:08 data
-rwxr-xr-x  1 ldc ldc  18615 2011-11-14 19:32 depcomp
drwxr-xr-x  2 ldc ldc   4096 2012-02-07 20:35 docs
drwxr-xr-x  3 ldc ldc   4096 2012-02-07 20:35 examples
drwxr-xr-x  3 ldc ldc   4096 2012-02-07 20:35 Expat
-rw-rw-r--  1 ldc ldc   2689 2011-08-11 20:34 INSTALL.BeOS
-rwxr-xr-x  1 ldc ldc  13663 2011-11-14 19:32 install-sh
-rw-rw-r--  1 ldc ldc   4357 2011-08-11 20:34 INSTALL.Unix
-rw-rw-r--  1 ldc ldc   6042 2011-08-11 20:34 INSTALL.Windows
-rw-rw-r--  1 ldc ldc  33976 2012-03-19 10:08 Makefile
-rw-r--r--  1 ldc ldc   7370 2011-11-26 21:30 Makefile.am
-rw-rw-r--  1 ldc ldc   9104 2011-08-11 20:34 Makefile.BeOS
-rw-r--r--  1 ldc ldc  33416 2012-01-28 19:46 Makefile.in
-rwxr-xr-x  1 ldc ldc  11419 2011-11-14 19:32 missing
drwxr-xr-x  6 ldc ldc   4096 2012-02-07 20:35 PBProjects
-rw-rw-r--  1 ldc ldc  16603 2011-08-11 20:34 README
drwxr-xr-x  3 ldc ldc   4096 2012-02-07 20:36 Resources
drwxr-xr-x 18 ldc ldc   4096 2012-03-19 10:09 Source_Files
-rw-rw-r--  1 ldc ldc     23 2012-03-19 10:08 stamp-h1
-rw-r--r--  1 ldc ldc    659 2011-10-25 13:15 THANKS
drwxr-xr-x  2 ldc ldc   4096 2012-03-19 10:08 tools
ldc@********:~/Games/AlephOne-20120128$
------------------------------------------------------------

---

### Post by Toz on 2012-03-19
All of the files in the **Marathon (A1)** folder should be in the **/usr/local/share/AlephOne** folder (one level up). Try this:
```

cd /usr/local/share/AlephOne
sudo mv Marathon\ \(A1\)/* .

```

---

### Post by linux.convert on 2012-03-20
After making double-extra-triple sure that the files are in the right folder and all that jazz I get this again...

----------------------------------------------------------------------------
ldc@******:~$ alephone
Aleph One Linux 2012-01-28 1.0.1
[http://marathon.sourceforge.net/](http://marathon.sourceforge.net/)

Original code by Bungie Software <http://www.bungie.com/>
Additional work by Loren Petrich, Chris Pruett, Rhys Hill et al.
TCP/IP networking by Woody Zenfell
Expat XML library by James Clark
SDL port by Christian Bauer <Christian.Bauer@uni-mainz.de>

This is free software with ABSOLUTELY NO WARRANTY.
You are welcome to redistribute it under certain conditions.
For details, see the file COPYING.

Built with network play enabled.

Built with Lua scripting enabled.
FATAL: Please be sure the files 'Map', 'Shapes', 'Images' and 'Sounds' are correctly installed and try again. (error -1)
ldc@******:~$
----------------------------------------------------------------------------

Is it possible that the files in /usr/local/share/AlephOne are like blocked or something because you have to have root access? Because all the necessary files are in there: I complied, ran make and make install as root, and installed all libraries.

----------------------------------------------------------------------------
ldc@ldc-AOD257:/usr/local/share/AlephOne/Marathon (A1)$ ls
Fonts.fntA        M1A1 Preferences  Plugins            Tracks
M1A1 Images.imgA  M1A1 Shapes.shpA  Read Me M1A1.html
M1A1 Map.sceA     M1A1 Sounds.sndA  Scripts
ldc@ldc-AOD257:/usr/local/share/AlephOne/Marathon (A1)$ 
----------------------------------------------------------------------------

---

### Post by linux.convert on 2012-03-20
I found something on another forum that talks about the exact same thing I'm having trouble with but I otherwise have no idea what they are talking about...

[http://www.pfhorums.com/lofiversion/index.php/t6476.html](http://www.pfhorums.com/lofiversion/index.php/t6476.html)

---

### Post by Toz on 2012-03-20
> **linux.convert said:**
> 
ldc@ldc-AOD257:/usr/local/share/AlephOne/Marathon (A1)$ ls
Fonts.fntA        M1A1 Preferences  Plugins            Tracks
M1A1 Images.imgA  M1A1 Shapes.shpA  Read Me M1A1.html
M1A1 Map.sceA     M1A1 Sounds.sndA  Scripts
ldc@ldc-AOD257:/usr/local/share/AlephOne/Marathon (A1)$ 
These files are in the _wrong_ folder. They need to be in the **/usr/local/share/AlephOne** folder (_not_ /usr/local/share/AlephOne/Marathon (A1)).

---

### Post by linux.convert on 2012-03-20
Ok this is really dumb, I am trying to move all the files *inside* Marathon (A1) into AlephOne. The problem I'm having is that the files have spaces in them, and it prevents the syntax from being happy...


_________________________________________________________________
ldc@*****:~/Games/Marathon (A1)$ sudo cp **M1A1_Images.imgA** /usr/local/share/AlephOne
cp: cannot stat `**M1A1_Images.imgA**': No such file or directory

ldc@*****:~/Games/Marathon (A1)$ sudo cp **M1A1Images.imgA** /usr/local/share/AlephOne
cp: cannot stat `**M1A1Images.imgA**': No such file or directory

ldc@*****7:~/Games/Marathon (A1)$ ls

Fonts.fntA        M1A1 Map.sceA     M1A1 Shapes.shpA  Plugins            Scripts
**M1A1 Images.imgA**  M1A1 Preferences  M1A1 Sounds.sndA  Read Me M1A1.html  Tracks

ldc@*****:~/Games/Marathon (A1)$ sudo cp **M1A1 Images.imgA** /usr/local/share/AlephOne
cp: cannot stat `**M1A1**': No such file or directory
cp: cannot stat `**Images.imgA**': No such file or directory
_________________________________________________________________

---

### Post by Toz on 2012-03-20
Put the filenames in quotes:
```
sudo cp "M1A1 Images.imgA" /usr/local/share/AlephOne
```
...or escape the spaces:
```
sudo cp M1A1\ Images.imgA /usr/local/share/AlephOne
```
...or use the mv command to move them all at once - (from post #10):
```

cd /usr/local/share/AlephOne
sudo mv Marathon\ \(A1\)/* .
```

---

### Post by linux.convert on 2012-03-21
Ok, i got all the folders and files inside the Marathon folder in the AlephOne folder, and the game runs pretty good, with only 2 problems. All the menus show black inside the windows, like the preferences window, and the hud doesn't show, health ammo that sort of thing, and its got this error message up at the top repeating several times about "a nil value".

---

### Post by Toz on 2012-03-21
Glad to hear you got it working. As for the 2 problems, they sound like video card issues. What video card do you have:
```
lspci -vnn | grep -A10 VGA
```

and what is the exact wording of the error message that you are getting?

---

### Post by linux.convert on 2012-03-21
My graphics card is integrated, Intel Atom N570 Processor.

The error is:

[string "hud_script"]:272: attempt to index global 'pos' (a nil value)

-----------------------------------------------------------------
ldc@*******:~$ lspci -vnn | grep -A10 VGA
00:02.0 VGA compatible controller [0300]: Intel Corporation N10 Family Integrated Graphics Controller [8086:a011] (rev 02) (prog-if 00 [VGA controller])
	Subsystem: Acer Incorporated [ALI] Device [1025:0590]
	Flags: bus master, fast devsel, latency 0, IRQ 45
	Memory at 56180000 (32-bit, non-prefetchable) [size=512K]
	I/O ports at 40a0 [size=8]
	Memory at 40000000 (32-bit, prefetchable) [size=256M]
	Memory at 56000000 (32-bit, non-prefetchable) [size=1M]
	Expansion ROM at <unassigned> [disabled]
	Capabilities: <access denied>
	Kernel driver in use: i915
	Kernel modules: i915
-----------------------------------------------------------------

---

### Post by Toz on 2012-03-21
According to the release notes ([http://source.bungie.org/release-notes/20111201.html]("http://source.bungie.org/release-notes/20111201.html")), and ati or nvidia card is recommended. It might be that your integrated intel card isn't supported fully.

---

### Post by linux.convert on 2012-03-21
Well I guess that's that then, thanks for the help guys.

---

