---
title: "How to install gimp-2.8.0-RC1.tar.bz2 ubuntu 10.04 or higher?"
date: 2012-04-04
forum: Packaging and Compiling Programs
---

### Post by davidvandoren on 2012-04-04
I have tried all day long to install Gimp 2.8 from source using this  gimp-2.8.0-RC1.tar.bz2 file.
Luckily I did this in a virtual pc and not on my host system, because that system is completely toast now. 
There were so many dependencies to solve that at the end I marked something like ATK for removal which almost completely erased everything. 

Has anyone come across a step by step guide on How to install that source file yet? If so, please share.

Thanks!

---

### Post by oldos2er on 2012-04-04
Moved to Packaging and Compiling Programs.

---

### Post by 23dornot23d on 2012-04-04
I thought I would have a go ....

Got it from here - [http://www.gimpusers.com/downloads/58-gimp-2-8-0-rc1-source-code](http://www.gimpusers.com/downloads/58-gimp-2-8-0-rc1-source-code)

There is a INSTALL

Document in the release ..... although I too followed it and get stuck at GLIB

this is a 12.04 Kubuntu install and why it thinks there are 2 versions of GLIB 
I do not know ..... ( [COLOR=Red]**but I do know both are greater than what is needed**[/COLOR] )

Yet it does not let me continue .....

Not a lot of help I know - but I would like to point this out to the devs as to me
this should not happen and it also should allow me to carry on using the latest
version ....... BABL went in fine pkg-config went in fine .... Initltool went in fine

> 
root@keith-Aspire-7730ZG:/# find / -name glib-2.0
/usr/include/glib-2.0
/usr/local/include/glib-2.0
/usr/local/lib/i386-linux-gnu/glib-2.0
/usr/local/share/glib-2.0
/usr/lib/i386-linux-gnu/glib-2.0
/usr/share/glib-2.0
Then we stopped ..... is there an easy way to point this to the correct one
I have come across this before and not known how to resolve the double
version issue .....

> 
checking for fsync... yes
checking for BABL... yes
checking for pkg-config... (cached) /usr/bin/pkg-config
checking pkg-config is at least version 0.16... yes
[COLOR=Blue]**checking for GLIB - version >= 2.28.0... **[/COLOR]
*** 'pkg-config --modversion [COLOR=Blue]**glib-2.0' returned 2.31.17, but GLIB (2.32.0)**[/COLOR]
*** was found! If pkg-config was correct, then it is best
*** to remove the old version of GLib. You may also be able to fix the error
*** by modifying your LD_LIBRARY_PATH enviroment variable, or by editing
*** /etc/ld.so.conf. Make sure you have run ldconfig if that is
*** required on your system.
*** If pkg-config was wrong, set the environment variable PKG_CONFIG_PATH
*** to point to the correct configuration files
no
configure: error: 
[COLOR=Red]***** GLIB 2.28.0 or better is required**[/COLOR]. The latest version of
*** GLIB is always available from [ftp://ftp.gtk.org/](ftp://ftp.gtk.org/).
keith@keith-Aspire-7730ZG:~/Downloads/gegl$ echo LD_LIBRARY_PATH
LD_LIBRARY_PATH
keith@keith-Aspire-7730ZG:~/Downloads/gegl$ echo $LD_LIBRARY_PATH

keith@keith-Aspire-7730ZG:~/Downloads/gegl$ 

[COLOR=Red][B]

The install document has these requirements in it  PLUS - MUCH MORE INFORMATION TOO

PLEASE READ IT AS IT COULD BREAK THINGS IF YOU INSTALL IT AND IT GOES WRONG

WHEN INSTALLING FROM SOURCE FILES THERE IS NO EASY RETURN JOURNEY[/B][/COLOR]

> 
  1. You need to have installed a recent version of pkg-config available
     from [http://www.freedesktop.org/software/pkgconfig/](http://www.freedesktop.org/software/pkgconfig/). done ///

  2. You need intltool (at least 0.40.1, but preferably a newer version).
     Intltool can be downloaded from
     [http://ftp.gnome.org/pub/gnome/sources/intltool/](http://ftp.gnome.org/pub/gnome/sources/intltool/). done ///

  3. You need to have GEGL version 0.2.0 or newer and babl version
     0.1.10 or newer. You can get them from [http://gegl.org/](http://gegl.org/) or clone
     them from the GNOME git repository:

       git://git.gnome.org/babl
       git://git.gnome.org/gegl

  4. You need to have installed GTK+ version 2.24.10 or newer.
     GIMP also need a recent versions of GLib (>= 2.30.2), GDK-Pixbuf
     (>= 2.24.1), and Pango (>= 1.29.4). Sources for these can be grabbed
     from [ftp://ftp.gtk.org/](ftp://ftp.gtk.org/).

  5. We use cairo >= 1.10.2, which is hosted at
     [http://www.cairographics.org/](http://www.cairographics.org/).

  6. We require PangoCairo, a Pango backend using Cairo. Make sure you
     have Cairo, FreeType2 and fontconfig installed before you compile
     Pango. GIMP depends on freetype2 being newer than version 2.1.7
     and fontconfig 2.2.0 or newer. Older versions are known to have
     bugs that seriously affect the stability of GIMP.

  7. We use dbus-glib if available. Grab it from
     [http://dbus.freedesktop.org/releases/dbus-glib/](http://dbus.freedesktop.org/releases/dbus-glib/)

  8. Access of remote files is implemented in the URI plug-in. There
     are several possible implementations for this. The implementation
     used is determined when you configure GIMP. By default the
     GIO/GVfs backend is used. If you don't have GVfs support on your
     target platform, you should pass the '--without-gvfs' option to
     configure. The configure script will then try to detect another
     method for accessing remote files.

  9. You may want to install other third party libraries or programs
     that are needed for some of the available plug-ins. We recommend
     to check that the following libraries are installed: lcms,
     libpng, libjpeg, libpoppler, libtiff, webkit, libmng, librsvg,
     libwmf, libz, libbzip2, libgs (Ghostscript), libaa and libjasper.

 10. The Python extension requires Python development headers to be
     present. You will also need PyGTK and the respective development
     headers.

 11. Configure GIMP by running the `configure' script. You may want
     to pass some options to it, see below.

 12. Build GIMP by running `make'. The use of GNU make is recommended.
     If you need to tweak the build to make it work with other flavours
     of make, we'd appreciate if you'd send us a patch with the changes.

 13. Install GIMP by running `make install'. In order to avoid clashes
     with other versions of GIMP, we install a binary called gimp-2.8.
     By default there's also a link created so that you can type 'gimp'
     to start gimp-2.8.

Please make sure you don't have any old GTK+-2.x, jpeg, etc. libraries
lying around on your system, otherwise configure may fail to find the
new ones.



---

### Post by mc4man on 2012-04-05
Only have 12.04 so only in regards to that. (only earlier ubuntu release you'd need to get a higher libglib I believe

Pretty easy, 12.04 provides all that's needed except gegl & babl versions required.
(acquiring build-deps here - [http://ubuntuforums.org/showpost.php?p=11821399&postcount=21](http://ubuntuforums.org/showpost.php?p=11821399&postcount=21)
So you'd build both of those then gimp-2.8 (or wait for a ppa to do

Here's a page that lays out the basic's to build to /opt, I did a varition of that type of build, did use /opt
(have a local build of 2.7.5 in /usr/local, so /opt worked best, plus didn't want the new gegl & babl to interfere

[http://www.gimpusers.com/tutorials/compiling-gimp-for-ubuntu](http://www.gimpusers.com/tutorials/compiling-gimp-for-ubuntu)

Here's the full listing of commands I used, start to finish in the same terminal (you must use the same terminal or if not then rerun the export commands before resuming

**Do note** - 
gegl will build with avformat support if the headers are installed. I had a local static build of a recent git FFmpeg. It built off of that without incident but there was a runtime issue
So I temp removed my local FFmpeg package & used the 12.04 libavcodec-dev, libavformat-dev

Also - 
I used checkinstall to install all, mainly because I dump my 12.04 installs weekly & I can, with care, re-use the .debs.
Also the gimp source compiled is large, almost 1/2 GB, so I can remove after moving the .deb out, or keep & clean
 Will post the commands I used, there is some leeway there, I didn't use --defaults so commands are longer, wanted it to stop at the package config screen to review

( if using checkinstall & want to have the repo or 2.7.X installed then make sure the package name is not gimp, I used gimp2

You should review the results of the ./autogen.sh & or ./configure to make sure all that's wanted to be enabled is before running a make.

The are various ways to run & add the .desktop, ect. The binary is gimp-2.8

One could also look for snapshots of gegl & babl instead of a git clone - fine today, you never know down the road.., if so a ./configure ... usually will suffice instead of a ./autogen.sh ...

If desired you can build in /tmp like in link
```

mkdir gimp_build && cd gimp_build

export PATH=/opt/gimp-2.8/bin:$PATH
export PKG_CONFIG_PATH=/opt/gimp-2.8/lib/pkgconfig
export LD_LIBRARY_PATH=/opt/gimp-2.8/lib

git clone git://git.gnome.org/babl
cd babl
./autogen.sh --prefix=/opt/gimp-2.8
make


sudo make install

or

sudo checkinstall --pkgname=babl --pkgversion=0.1.10 --backup=no --deldoc=yes \
--fstrans=no --backup=no --deldoc=yes --deldesc=yes --delspec=yes --default
cd ..
git clone git://git.gnome.org/gegl
cd gegl
./autogen.sh --prefix=/opt/gimp-2.8

# if dep packages are added after the above use this till correct
./configure  --prefix=/opt/gimp-2.8  
make


sudo make install

or 

sudo checkinstall --pkgname=gegl --pkgversion=0.2 --backup=no --deldoc=yes \
--fstrans=no --backup=no --deldoc=yes --deldesc=yes --delspec=yes --default

cd ..
cd gimp-2.8.0  # I unpacked the gimp-2.8 tar into the gimp_build
./configure --prefix=/opt/gimp-2.8
make


sudo make install 

or

sudo checkinstall --backup=no --deldoc=yes --fstrans=no --backup=no --deldoc=yes \
--deldesc=yes --delspec=yes --pkgname=gimp2 --pkgversion=2.8.0-rc1 \
--provides gimp-2.8.0 --default
```



For a .desktop I used ~/... like 
```
gedit ~/.local/share/applications/gimp2.desktop
```
```

[Desktop Entry]
Version=1.0
Type=Application
Name=Gimp 2.8
Comment=Create images and edit photographs
Exec=/opt/gimp-2.8/bin/gimp-2.8 %U
TryExec=/opt/gimp-2.8/bin/gimp-2.8
Icon=gimp
Terminal=false
Categories=Graphics;2DGraphics;RasterGraphics;GTK;
X-GNOME-Bugzilla-Bugzilla=GNOME
X-GNOME-Bugzilla-Product=GIMP
X-GNOME-Bugzilla-Component=General
X-GNOME-Bugzilla-Version=2.8.0-RC1
X-GNOME-Bugzilla-OtherBinaries=gimp-2.8
MimeType=application/postscript;application/pdf;image/bmp;image/g3fax;image/gif;image/x-fits;image/pcx;image/x-portable-anymap;image/x-portable-bitmap;image/x-portable-graymap;image/x-portable-pixmap;image/x-psd;image/x-sgi;image/x-tga;image/x-xbitmap;image/x-xwindowdump;image/x-xcf;image/x-compressed-xcf;image/x-gimp-gbr;image/x-gimp-pat;image/x-gimp-gih;image/tiff;image/jpeg;image/x-psp;image/png;image/x-icon;image/x-xpixmap;image/svg+xml;application/pdf;image/x-wmf;image/jp2;image/jpeg2000;image/jpx;image/x-xcursor;
```

Note - if gimp-2.6 or 2.7 isn't installed normally then full path the Icon= line, EX.
Icon=/opt/gimp-2.8/share/icons/hicolor/48x48/apps/gimp.png

---

### Post by LinkofHyrule89 on 2012-04-05
I've tried for hours to compile this on my newly installed Ubuntu 12.04 with no luck can you just upload the .deb for Ubuntu x64?

---

### Post by davidvandoren on 2012-04-05
Here I get stuck and don't know how to go on.
With installing gimp 2.8 of course. ):P
cd ..
git clone git://git.gnome.org/gegl
cd gegl
./autogen.sh --prefix=/opt/gimp-2.8

# if dep packages are added after the above use this till correct
./configure  --prefix=/opt/gimp-2.8  

```
checking for vapigen... no
*** Check for vapigen failed.
checking for fsync... yes
checking for BABL... yes
checking for pkg-config... (cached) /usr/bin/pkg-config
checking pkg-config is at least version 0.16... yes
checking for GLIB - version >= 2.28.0... yes (version 2.32.0)
checking for DEP... yes
checking for bind_textdomain_codeset... yes
./configure: line 17639: syntax error near unexpected token `0.40.1'
./configure: line 17639: `IT_PROG_INTLTOOL(0.40.1)'

```

---

### Post by davidvandoren on 2012-04-05
thanks to everyone I got it up and running.

some things I remember so far.

as a starter 

```
sudo apt-get install build-essential checkinstall
```then 
```
sudo apt-get install cvs subversion git-core mercurial 
``````
 cd /tmp
```then 
```
mkdir gimp_build && cd gimp_build
```execute each line
```
export PATH=/opt/gimp-2.8/bin:$PATH
export PKG_CONFIG_PATH=/opt/gimp-2.8/lib/pkgconfig
export LD_LIBRARY_PATH=/opt/gimp-2.8/lib 
``````
git clone git://git.gnome.org/babl
cd babl
./autogen.sh --prefix=/opt/gimp-2.8
make
sudo make install 
``````
sudo apt-get install libtool
```Till here then it was a lot of fixing dependencies and sorry I really forgot how it went on.

---

### Post by 23dornot23d on 2012-04-05
Good one .... type history in the terminal

it will show all the commands you used ...... 

But that is good - gives me confidence - am doing a safe-upgrade then going to try it
again .... mine is still failing ..... new error now .....

> 
checking for perl... /usr/bin/perl
checking for pkg-config... /usr/bin/pkg-config
checking pkg-config is at least version 0.9.0... yes
checking for gobject-introspection... no (disabled, use --enable-introspection to enable)
checking for vapigen... no
*** Check for vapigen failed.
checking for fsync... yes
checking for BABL... yes
./configure: line 17133: syntax error near unexpected token `$GLIB_REQUIRED_VERSION,'
./configure: line 17133: `AM_PATH_GLIB_2_0($GLIB_REQUIRED_VERSION, :,'
keith@keith-K53SV:~/tmp/gimp/gimp-2.8.0-RC1/gegl$ 



---

### Post by davidvandoren on 2012-04-05
I did the history command but it will confuse you even more.

Just read after each attempt the error messages in the last 7 lines and try to find the packages that are missing. 

I rmember I had to install one through the software center and the installed synaptic to speed things up a little bit.  

You'll need python dev. Some Tiff dev etc.
Just show us how far you get and the last terminal outputs maybe I can trace it back then.

---

### Post by 23dornot23d on 2012-04-05
I get this ......

> 
checking for vapigen... no
*** Check for vapigen failed.
what is vapigen ..... and where is it installed ......

[https://www.google.com/search?client=ubuntu&channel=fs&q=vapigen&ie=utf-8&oe=utf-8](https://www.google.com/search?client=ubuntu&channel=fs&q=vapigen&ie=utf-8&oe=utf-8)

Ok installed vala

now ...

> 
checking whether we can compile SSE code... yes
checking for perl5... no
checking for perl... /usr/bin/perl
checking for pkg-config... /usr/bin/pkg-config
checking pkg-config is at least version 0.9.0... yes
checking for gobject-introspection... no (disabled, use --enable-introspection to enable)
checking for vapigen... /usr/bin/vapigen
checking for fsync... yes
checking for BABL... yes
./configure: line 17133: syntax error near unexpected token `$GLIB_REQUIRED_VERSION,'
./configure: line 17133: `AM_PATH_GLIB_2_0($GLIB_REQUIRED_VERSION, :,'
keith@keith-K53SV:~/tmp/gimp/gimp-2.8.0-RC1/gegl$ 



a little further

> 
checking for pkg-config... (cached) /usr/bin/pkg-config
checking pkg-config is at least version 0.16... yes
checking for GLIB - version >= 2.28.0... yes (version 2.32.0)
checking for DEP... yes
checking for bind_textdomain_codeset... yes
./configure: line 17639: syntax error near unexpected token `0.40.1'
./configure: line 17639: `IT_PROG_INTLTOOL(0.40.1)'
keith@keith-K53SV:~/tmp/gimp/gimp-2.8.0-RC1/gegl$ 



---

### Post by davidvandoren on 2012-04-05
> **23dornot23d said:**
> Good one .... type history in the terminal

it will show all the commands you used ...... 

But that is good - gives me confidence - am doing a safe-upgrade then going to try it
again .... mine is still failing ..... new error now .....

Install synaptic from the software center.
Close your software center and open synaptic go to  settings and repository and 
check everything then Other software and check everything 
close this tab and refresh your software list.

[B]I installed valac-0.16  via synaptic

[/B]While you are at it**, **I removed intltool-debian and reinstalled intltool 0.50.2-2

---

### Post by davidvandoren on 2012-04-05
```
./configure: line 17133: syntax error near unexpected token `$GLIB_REQUIRED_VERSION,'
./configure: line 17133: `AM_PATH_GLIB_2_0($GLIB_REQUIRED_VERSION, :,'
keith@keith-K53SV:~/tmp/gimp/gimp-2.8.0-RC1/gegl$ 
```

After this error I think I did this

```
apt-cache search openexr &#8658; libopenexr-dev
```
```
apt-cache search rsvg &#8658; librsvg2-dev
```
```
sudo apt-get install libjpeg62-dev libopenexr-dev librsvg2-dev
```

---

### Post by davidvandoren on 2012-04-05
also open synaptic 

and install autoconf 2.68-1ubuntu2

You'll need python2.7-dev also and python-dev 2.7.2-9 is installede on my system as well

Sorry I only remember bits and pieces


Then install with synaptic also 

libtiff-tools 3.9.5-2ubuntu1
libtiff4
libtiffxx0c2
libtiff4-dev

---

### Post by 23dornot23d on 2012-04-05
Ok cheers ..... the initltool thing got me by the problem 

```

keith@keith-K53SV:~/tmp/gimp/gimp-2.8.0-RC1/gegl$ ./autogen.sh
autoreconf: Entering directory `.'
autoreconf: configure.ac: not using Gettext
autoreconf: running: aclocal --force -I m4 ${ACLOCAL_FLAGS}
autoreconf: configure.ac: tracing
autoreconf: running: libtoolize --install --copy --force
libtoolize: putting macros in AC_CONFIG_MACRO_DIR, `m4'.
libtoolize: copying file `m4/libtool.m4'
libtoolize: copying file `m4/ltoptions.m4'
libtoolize: copying file `m4/ltsugar.m4'
libtoolize: copying file `m4/ltversion.m4'
libtoolize: copying file `m4/lt~obsolete.m4'
autoreconf: running: /usr/bin/autoconf --force
autoreconf: running: /usr/bin/autoheader --force
autoreconf: running: automake --add-missing --copy --force-missing
autoreconf: Leaving directory `.'
checking whether make supports nested variables... yes
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for a thread-safe mkdir -p... /bin/mkdir -p
checking for gawk... gawk
checking whether make sets $(MAKE)... yes
checking whether to enable maintainer-specific portions of Makefiles... yes
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
checking for g++... g++
checking whether we are using the GNU C++ compiler... yes
checking whether g++ accepts -g... yes
checking dependency style of g++... gcc3
checking whether make sets $(MAKE)... (cached) yes
checking for special C compiler options needed for large files... no
checking for _FILE_OFFSET_BITS value needed for large files... 64
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking how to print strings... printf
checking for a sed that does not truncate output... /bin/sed
checking for grep that handles long lines and -e... /bin/grep
checking for egrep... /bin/grep -E
checking for fgrep... /bin/grep -F
checking for ld used by gcc... /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... yes
checking for BSD- or MS-compatible name lister (nm)... /usr/bin/nm -B
checking the name lister (/usr/bin/nm -B) interface... BSD nm
checking whether ln -s works... yes
checking the maximum length of command line arguments... 1572864
checking whether the shell understands some XSI constructs... yes
checking whether the shell understands "+="... yes
checking how to convert i686-pc-linux-gnu file names to i686-pc-linux-gnu format... func_convert_file_noop
checking how to convert i686-pc-linux-gnu file names to toolchain format... func_convert_file_noop
checking for /usr/bin/ld option to reload object files... -r
checking for objdump... objdump
checking how to recognize dependent libraries... pass_all
checking for dlltool... no
checking how to associate runtime and link libraries... printf %s\n
checking for ar... ar
checking for archiver @FILE support... @
checking for strip... strip
checking for ranlib... ranlib
checking command to parse /usr/bin/nm -B output from gcc object... ok
checking for sysroot... no
checking for mt... mt
checking if mt is a manifest tool... no
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
checking for dlfcn.h... yes
checking for objdir... .libs
checking if gcc supports -fno-rtti -fno-exceptions... no
checking for gcc option to produce PIC... -fPIC -DPIC
checking if gcc PIC flag -fPIC -DPIC works... yes
checking if gcc static flag -static works... yes
checking if gcc supports -c -o file.o... yes
checking if gcc supports -c -o file.o... (cached) yes
checking whether the gcc linker (/usr/bin/ld) supports shared libraries... yes
checking whether -lc should be explicitly linked in... no
checking dynamic linker characteristics... GNU/Linux ld.so
checking how to hardcode library paths into programs... immediate
checking for shl_load... no
checking for shl_load in -ldld... no
checking for dlopen... no
checking for dlopen in -ldl... yes
checking whether a program can dlopen itself... yes
checking whether a statically linked program can dlopen itself... no
checking whether stripping libraries is possible... yes
checking if libtool supports shared libraries... yes
checking whether to build shared libraries... yes
checking whether to build static libraries... no
checking how to run the C++ preprocessor... g++ -E
checking for ld used by g++... /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... yes
checking whether the g++ linker (/usr/bin/ld) supports shared libraries... yes
checking for g++ option to produce PIC... -fPIC -DPIC
checking if g++ PIC flag -fPIC -DPIC works... yes
checking if g++ static flag -static works... yes
checking if g++ supports -c -o file.o... yes
checking if g++ supports -c -o file.o... (cached) yes
checking whether the g++ linker (/usr/bin/ld) supports shared libraries... yes
checking dynamic linker characteristics... (cached) GNU/Linux ld.so
checking how to hardcode library paths into programs... immediate
checking for GNUC variadic macros... yes
checking for ISO C99 variadic macros in C... yes
checking for ISO C99 variadic macros in C++... yes
checking whether to turn on debugging... no
checking whether to turn on profiling... no
checking for C/C++ restrict keyword... __restrict
checking for aclocal flags... 
checking for target architecture... i686-pc-linux-gnu
checking for dynamic library filename suffix... .so
checking for some Darwin platform... no
checking for some Win32 platform... no
checking for native Win32... no
checking to see if compiler understands -mmmx... yes
checking whether we can compile MMX code... yes
checking to see if compiler understands -msse... yes
checking to see if compiler understands -ftree-vectorize... yes
checking to see if compiler understands -ffast-math... yes
checking whether we can compile SSE code... yes
checking for perl5... no
checking for perl... /usr/bin/perl
checking for pkg-config... /usr/bin/pkg-config
checking pkg-config is at least version 0.9.0... yes
checking for gobject-introspection... no (disabled, use --enable-introspection to enable)
checking for vapigen... /usr/bin/vapigen
checking for fsync... yes
checking for BABL... yes
checking for pkg-config... (cached) /usr/bin/pkg-config
checking pkg-config is at least version 0.16... yes
checking for GLIB - version >= 2.28.0... yes (version 2.32.0)
checking for DEP... yes
checking for bind_textdomain_codeset... yes
checking whether NLS is requested... yes
checking for intltool >= 0.40.1... 0.50.2 found
checking for intltool-update... /usr/bin/intltool-update
checking for intltool-merge... /usr/bin/intltool-merge
checking for intltool-extract... /usr/bin/intltool-extract
checking for xgettext... /usr/bin/xgettext
checking for msgmerge... /usr/bin/msgmerge
checking for msgfmt... /usr/bin/msgfmt
checking for gmsgfmt... /usr/bin/msgfmt
checking for perl... /usr/bin/perl
checking for perl >= 5.8.1... 5.14.2
checking for XML::Parser... ok
checking locale.h usability... yes
checking locale.h presence... yes
checking for locale.h... yes
checking for LC_MESSAGES... yes
checking libintl.h usability... yes
checking libintl.h presence... yes
checking for libintl.h... yes
checking for ngettext in libc... yes
checking for dgettext in libc... yes
checking for bind_textdomain_codeset... (cached) yes
checking for msgfmt... (cached) /usr/bin/msgfmt
checking for dcgettext... yes
checking if msgfmt accepts -c... yes
checking for gmsgfmt... (cached) /usr/bin/msgfmt
checking for xgettext... (cached) /usr/bin/xgettext
checking if GLib is version 2.21.0 or newer... yes
checking for gtkdoc-check... no
checking for gtkdoc-rebase... no
checking for gtkdoc-mkpdf... no
checking whether to build gtk-doc documentation... no
checking for perl5... /usr/bin/perl
checking for ruby... no
configure: WARNING:
*** Could not find Ruby interpreter. The HTML API reference
will not be updated.

checking for enscript... no
checking for asciidoc... no
*** Check for asciidoc failed.
checking for dot... no
*** Check for dot command failed.
checking for a Python interpreter with version >= 2.5.0... python
checking for python... /usr/bin/python
checking for python version... 2.7
checking for python platform... linux2
checking for python script directory... ${prefix}/lib/python2.7/dist-packages
checking for python extension module directory... ${exec_prefix}/lib/python2.7/dist-packages
checking for CAIRO... yes
checking for PANGO... yes
checking for PANGOCAIRO... yes
checking for GDK_PIXBUF... yes
checking for LENSFUN... no
checking for jpeg_destroy_decompress in -ljpeg... yes
checking for jpeglib.h... yes
checking for jpeg_save_markers in -ljpeg... yes
checking for PNG... yes
checking for RSVG... yes
checking for OPENEXR... yes
checking for sdl-config... no
*** Check for SDL library failed.
checking for OPENRAW... no
checking for JASPER... no
checking for jas_stream_freopen in -ljasper... no
checking for dot... no
*** Check for dot command from graphviz failed.
checking for LUA... no
checking for LUA... no
checking for AVFORMAT... no
checking linux/videodev.h usability... no
checking linux/videodev.h presence... no
checking for linux/videodev.h... no
checking for run_spiro in -lspiro... no
checking for EXIV2... no
checking for umfpack_dl_solve in -lumfpack... no
checking execinfo.h usability... yes
checking execinfo.h presence... yes
checking for execinfo.h... yes
checking for w3m... no
checking for rint... no
checking for rint in -lm... yes
checking to see if compiler understands -Wall... yes
checking to see if compiler understands -Wdeclaration-after-statement... yes
checking to see if compiler understands -Wmissing-prototypes... yes
checking to see if compiler understands -Wmissing-declarations... yes
checking to see if compiler understands -Winit-self... yes
checking to see if compiler understands -Wpointer-arith... yes
checking to see if compiler understands -Wold-style-definition... yes
configure: creating ./config.status
config.status: creating Makefile
config.status: creating bin/Makefile
config.status: creating gegl/Makefile
config.status: creating gegl/gegl-version.h
config.status: creating gegl/buffer/Makefile
config.status: creating gegl/graph/Makefile
config.status: creating gegl/module/Makefile
config.status: creating gegl/operation/Makefile
config.status: creating gegl/process/Makefile
config.status: creating gegl/property-types/Makefile
config.status: creating gegl/opencl/Makefile
config.status: creating libs/Makefile
config.status: creating libs/rgbe/Makefile
config.status: creating operations/Makefile
config.status: creating operations/core/Makefile
config.status: creating operations/common/Makefile
config.status: creating operations/common/perlin/Makefile
config.status: creating operations/external/Makefile
config.status: creating operations/generated/Makefile
config.status: creating operations/transform/Makefile
config.status: creating operations/workshop/Makefile
config.status: creating operations/workshop/external/Makefile
config.status: creating operations/workshop/generated/Makefile
config.status: creating tools/Makefile
config.status: creating docs/Makefile
config.status: creating docs/index-static.txt
config.status: creating docs/gallery/Makefile
config.status: creating docs/gallery/data/Makefile
config.status: creating examples/Makefile
config.status: creating examples/data/Makefile
config.status: creating tests/Makefile
config.status: creating tests/buffer/Makefile
config.status: creating tests/buffer/reference/Makefile
config.status: creating tests/buffer/tests/Makefile
config.status: creating tests/compositions/Makefile
config.status: creating tests/compositions/data/Makefile
config.status: creating tests/python/Makefile
config.status: creating tests/simple/Makefile
config.status: creating tests/xml/Makefile
config.status: creating tests/xml/data/Makefile
config.status: creating po/Makefile.in
config.status: creating gegl-uninstalled.pc
config.status: creating gegl-0.2.pc
config.status: creating config.h
config.status: config.h is unchanged
config.status: executing depfiles commands
config.status: executing libtool commands
config.status: executing default-1 commands
config.status: executing po/stamp-it commands

Building GEGL with prefix=/usr/local

Optional features:
  GEGL docs:       yes
  Build workshop:  no
  Build website:   no  (asciidoc not found)
  SIMD:            sse:yes mmx:yes
  Vala support:    yes

Optional dependencies:
  asciidoc:        no  (asciidoc not found)
  enscript:        no  (enscript not found)
  Ruby:            no
  Lua:             no  (usable lua not found)
  Cairo:           yes
  Pango:           yes
  pangocairo:      yes
  GDKPixbuf:       yes
  JPEG:            yes
  PNG:             yes
  OpenEXR:         yes
  rsvg:            yes
  SDL:             no  (SDL library not found)
  openraw:         no  (openraw library not found)
  Jasper:          no  (jasper library not found)
  graphviz:        no  (graphviz not found)
  avformat:        no  (libavformat not found)
  V4L:             no
  spiro:           no  (usable SPIRO library not found)
  EXIV:            no  (exiv2 library not found)
  umfpack:         no  (usable umfpack library not found)

keith@keith-K53SV:~/tmp/gimp/gimp-2.8.0-RC1/gegl$ 


```gegl is installed now ...... will follow the rest of the install and your commands above
see if I can get it going now

Thanks ..... ;)

> 
checking cairo-pdf.h usability... yes
checking cairo-pdf.h presence... yes
checking for cairo-pdf.h... yes
checking cairo-ps.h usability... yes
checking cairo-ps.h presence... yes
checking for cairo-ps.h... yes
checking cairo-svg.h usability... yes
checking cairo-svg.h presence... yes
checking for cairo-svg.h... yes
checking for pkg-config... (cached) /usr/bin/pkg-config
checking pkg-config is at least version 0.16... yes
./configure: line 24134: syntax error near unexpected token `0.10.1'
./configure: line 24134: `GOBJECT_INTROSPECTION_CHECK(0.10.1)'
keith@keith-K53SV:~/tmp/gtk+-3.4.0$



---

### Post by davidvandoren on 2012-04-05
in synaptic 
python  2.7.2-9
python-gobject-dev 3.2.0-1
python-gi-dev 3.2.0-1
python-gobject-2-dev 2.28.6.10



That's what I got in synaptic and I installed it via synaptic

---

### Post by 23dornot23d on 2012-04-05
Cheers all of those are installed ..... but fails for me at

> 
checking for GLIB... yes
checking for GOBJECT... yes
checking for GMODULE... yes
checking for GIO... yes
checking for GIO_UNIX... yes
checking for CAIRO... yes
checking for CAIRO_GOBJECT... yes
checking for SCANNER... yes
checking for FFI... yes
checking size of char... 1
checking size of short... 2
checking size of int... 4
checking size of long... 4
checking for GIREPO... yes
./configure: line 13682: syntax error near unexpected token `1.15,--flavour'
./configure: line 13682: `GTK_DOC_CHECK(1.15,--flavour no-tmpl)'
root@keith-K53SV:/home/keith/tmp/gobject-introspection# 



Tried the gobject-introspection from synaptic and that made no difference so am
trying to compile it .... 

But it stops here now .........

---

### Post by LinkofHyrule89 on 2012-04-05
So no one can't just post the compiled installer?

---

### Post by davidvandoren on 2012-04-05
> **LinkofHyrule89 said:**
> So no one can't just post the compiled installer?

If you tell me how to generate one deb package I would do that.

---

### Post by Notsonoble on 2012-04-05
I can't seem to get gegl to build correctly
```
(lt-gegl:22295): GEGL-gegl-node.c-WARNING **: Failed to set operation type gegl:png-load, using a passthrough op instead

(lt-gegl:22295): GEGL-gegl-c.c-WARNING **: gegl_node:GeglChantnop_c has no property named: 'path'
/bin/bash: line 1: 22295 Segmentation fault      (core dumped) GEGL_DEBUG_TIME=yes GEGL_SWAP=RAM GEGL_PATH=../../operations ../../bin/gegl OpenRaster-00.xml -o `echo OpenRaster-00.png | sed s?./??` > `echo OpenRaster-00.png | sed s?./?? | sed -e s/png/txt/`
make[4]: *** [OpenRaster-00.png] Error 139
./OpenRaster-01.xml

(lt-gegl:22324): GEGL-gegl-node.c-WARNING **: Failed to set operation type gegl:text, using a passthrough op instead

(lt-gegl:22324): GEGL-gegl-extension-handler.c-WARNING **: No loader for extension ".png", falling back to "gegl:magick-load"

(lt-gegl:22324): GEGL-gegl-node.c-WARNING **: Failed to set operation type gegl:png-load, using a passthrough op instead

(lt-gegl:22324): GEGL-gegl-c.c-WARNING **: gegl_node:GeglChantnop_c has no property named: 'path'
/bin/bash: line 1: 22324 Segmentation fault      (core dumped) GEGL_DEBUG_TIME=yes GEGL_SWAP=RAM GEGL_PATH=../../operations ../../bin/gegl OpenRaster-01.xml -o `echo OpenRaster-01.png | sed s?./??` > `echo OpenRaster-01.png | sed s?./?? | sed -e s/png/txt/`
make[4]: *** [OpenRaster-01.png] Error 139
./OpenRaster-04.xml

(lt-gegl:22353): GEGL-gegl-node.c-WARNING **: Failed to set operation type gegl:text, using a passthrough op instead

(lt-gegl:22353): GEGL-gegl-extension-handler.c-WARNING **: No loader for extension ".jpg", falling back to "gegl:magick-load"

(lt-gegl:22353): GEGL-gegl-node.c-WARNING **: Failed to set operation type gegl:png-load, using a passthrough op instead

(lt-gegl:22353): GEGL-gegl-c.c-WARNING **: gegl_node:GeglChantnop_c has no property named: 'path'
/bin/bash: line 1: 22353 Segmentation fault      (core dumped) GEGL_DEBUG_TIME=yes GEGL_SWAP=RAM GEGL_PATH=../../operations ../../bin/gegl OpenRaster-04.xml -o `echo OpenRaster-04.png | sed s?./??` > `echo OpenRaster-04.png | sed s?./?? | sed -e s/png/txt/`
make[4]: *** [OpenRaster-04.png] Error 139
make[3]: *** [images.stamp] Error 2
make[3]: Leaving directory `/home/nohays/gimp_build/gegl/docs/gallery'
make[2]: *** [install-recursive] Error 1
make[2]: Leaving directory `/home/nohays/gimp_build/gegl/docs/gallery'
make[1]: *** [install-recursive] Error 1
make[1]: Leaving directory `/home/nohays/gimp_build/gegl/docs'
make: *** [install-recursive] Error 1
```

---

### Post by 23dornot23d on 2012-04-05
Used Mc4mans instructions on a KahelOS ( Arch ) build and it completed as a success

[http://ubuntuforums.org/showpost.php?p=11818686&postcount=4](http://ubuntuforums.org/showpost.php?p=11818686&postcount=4)

Sure it will work on Ubuntu too .... 

[IMG]http://img854.imageshack.us/img854/6405/snapshot34r.jpg[/IMG]

[[COLOR=Red]**VIDEO**[/COLOR]]("http://www.youtube.com/watch?v=Lo6iZ9EgKlo&feature=youtu.be")

---

### Post by mc4man on 2012-04-05
On **12.04 **- easiest way to fill deps
```
sudo apt-get update
```
```
sudo apt-get build-dep gimp
```
```
sudo apt-get remove libgegl-0.0-dev libbabl-0.0-0-dev
```
```
sudo apt-get install libavformat-dev libavcodec-dev valac-0.16 \
graphviz ruby1.9.1-dev liblua5.1-0-dev

```
additionally if desired
```
sudo apt-get install libopenexr-dev libopenraw-dev libexiv2-dev \
libsdl1.2-dev libgs-dev libjasper-dev
```

optional
```
sudo apt-get install checkinstall
```

---

### Post by davidvandoren on 2012-04-06
Ok here is the complete tutorial combining all the different recourses on how to compile / install gimp 2.8 in Ubuntu 12.04 from source.

or watch my video tutorial [http://www.youtube.com/watch?v=k4Um8tvHcgk&feature=youtu.be](http://www.youtube.com/watch?v=k4Um8tvHcgk&feature=youtu.be)
 
first open your update manager and update you Ubuntu to the latest kernel and state. 

then 
1) ```
sudo apt-get update
```2) ```
sudo apt-get install cvs subversion git-core mercurial
```3) ```
sudo apt-get build-dep gimp
```4) ```
sudo apt-get remove libgegl-0.0-dev libbabl-0.0-0-dev
```5) ```
sudo apt-get install libavformat-dev libavcodec-dev valac-0.16 \
graphviz ruby1.9.1-dev liblua5.1-0-dev
```6) ```
sudo apt-get install libopenexr-dev libopenraw-dev libexiv2-dev \
libsdl1.2-dev libgs-dev libjasper-dev
```7) ```
sudo apt-get install checkinstall
```8) ```
cd /tmp
```9) ```
mkdir gimp_build && cd gimp_build
```the following three are only valid for that session if you for any reason restart the terminal, you'll have to execute them again
10) ```
export PATH=/opt/gimp-2.8/bin:$PATH
```11) ```
export PKG_CONFIG_PATH=/opt/gimp-2.8/lib/pkgconfig
```12) ```
export LD_LIBRARY_PATH=/opt/gimp-2.8/lib
```Remember 10, 11 and 12 have to be executed again if you restart your session. 
13) ```
git clone git://git.gnome.org/babl
```14) ```
cd babl
```15) ```
./autogen.sh --prefix=/opt/gimp-2.8
```16) ```
make
```17) ```
sudo make install
```18) ```
cd ..
```19) ```
git clone git://git.gnome.org/gegl
```20) ```
cd gegl
```21) ```
./autogen.sh --prefix=/opt/gimp-2.8
```22) ```
make
```23) ```
sudo make install
```Now take the gimp-2.8.0-RC1.tar.bz2 and drag and drop it into /tmp/gimp_build


[COLOR=Red]**______________________________________________________________________________**
 or type
 ```
cd ..
```  and execute this one to download gimp```
wget ftp://ftp.gimp.org/pub/gimp/v2.8/gimp-2.8.0-RC1.tar.bz2
```
skip 24 if you did this!
**_______________________________________________________________________________**
[/COLOR]


24) ```
cd ..
```25) ```
tar -xjf gimp-2.8.0-RC1.tar.bz2
```26) ```
cd gimp-2.8.0-RC1
```27) ```
./configure --prefix=/opt/gimp-2.8
```28) ```
make
```29) ```
sudo make install
```Now execute gimp in this window and gimp 2.8 should open
30) ```
gimp
```Last thing a nice shortcut 
open a new terminal session
31) ```
sudo apt-get install --no-install-recommends gnome-panel
```32) ```
gnome-desktop-item-edit ~/Desktop/ --create-new
```you'll see a pop up 
under command brows to /opt/gimp 2.8/ bin and select gimp2.8
click on the icon and find the gimp icon select it 
Done

You can drag and drop that launcher to the sidebar.

---

### Post by Flywaver on 2012-04-10
> **davidvandoren said:**
> Ok here is the complete tutorial combining all the different recourses on how to compile / install gimp 2.8 in Ubuntu 12.04 from source.


Awesome tutorial many thanks!!! =D>

One small thing, I can't drag-drop the icon to gnome-shell sidebar and once gimp is opened I can't right-click on it's icon and select "Add to Favorites" :(

---

### Post by davidvandoren on 2012-04-10
> **Flywaver said:**
> Awesome tutorial many thanks!!! =D>

One small thing, I can't drag-drop the icon to gnome-shell sidebar and once gimp is opened I can't right-click on it's icon and select "Add to Favorites" :(


31)      Code:
     sudo apt-get install --no-install-recommends gnome-panel 
32)      Code:
     gnome-desktop-item-edit ~/Desktop/ --create-new 
you'll see a pop up to create a launcher on the desktop. 
You can drag that one over the side-panel and you have to move it a little bit around till it takes same space to be dropped onto. Worked on my 12.04. Maybe you can try to pull from the application menu gimp as resent used to pull onto it.


sorry for adding this a little late you may try this one as described at the bottom of  the page 
[http://ubuntuforums.org/showpost.php?p=11818686&postcount=4](http://ubuntuforums.org/showpost.php?p=11818686&postcount=4)

---

### Post by Flywaver on 2012-04-10
> **davidvandoren said:**
> 31)      Code:
     sudo apt-get install --no-install-recommends gnome-panel 
32)      Code:
     gnome-desktop-item-edit ~/Desktop/ --create-new 
you'll see a pop up to create a launcher on the desktop. 
You can drag that one over the side-panel and you have to move it a little bit around till it takes same space to be dropped onto. Worked on my 12.04. Maybe you can try to pull from the application menu gimp as resent used to pull onto it.


sorry for adding this a little late you may try this one as described at the bottom of  the page 
[http://ubuntuforums.org/showpost.php?p=11818686&postcount=4](http://ubuntuforums.org/showpost.php?p=11818686&postcount=4)

Thanks but I am using gnome-shell...sorry if I haven't mentioned it before. so all these tips don't work in gnome-shell :(

---

### Post by davidvandoren on 2012-04-10
> **Flywaver said:**
> Thanks but I am using gnome-shell...sorry if I haven't mentioned it before. so all these tips don't work in gnome-shell :(

If you already have alacarte installed open terminal and type alacarte.

If not ```
sudo apt-get install alacarte
``` and then type alacarte.

---

### Post by Flywaver on 2012-04-10
> **davidvandoren said:**
> If you already have alacarte installed open terminal and type alacarte.

If not ```
sudo apt-get install alacarte
``` and then type alacarte.

Awesome! Thans a lot...I just edited gimp-2.6 to gimp-2.8 and I was able to add to favorites! :)

---

### Post by Ishimaru Chiaki on 2012-04-10
Hello

@David : Have you tried the tip on 10.04 ?

Because I just can't get any clear information on wether I can or not install GIMP 2.8-rc1 on Ubuntu 10.04, for I would like to test it in order to write a news in French about GIMP 2.8 release, but I usually don't upgrade Ubuntu before a few weeks after a new LTS*release.
I askod on…
- ubuntu-fr
- a blog where I discovered Matt Walker's repo
- Emailed Matt Walker
- Posted on Diaspora

… but still no clear answer…

Thanks in advance.

---

### Post by eulu on 2012-04-10
Awesome! Thanks so much for this tutorial! It worked without a hitch.. I'd been looking and trying to upgrade from 2.6 since I ventured from windows into the linux/ubuntu world a couple months ago... 

It's funny because while I was stuck back in 2.6, I discovered the fx foundry script package, which I had never had on my windows load. Now I will be trying to figure out how to get that into this 2.8 install.. I'm looking to figure out how to get pspi installed on ubuntu too..

---

### Post by dnelub on 2012-04-23
```
root@bt:~/tmp/gimp# sudo apt-get build-dep gimp
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to find a source package for gimp

```

I have been trying to install gimp 2.8 on Ubuntu Lucid. I have not made it yet. As far as I see I need to add a source. Definitely there is no such source in the source of software. I downloaded the source and gave the command in the source folder. 

So, can someone please help me what I should do? thanks in advance.

---

### Post by nmriahi on 2012-05-17
> **davidvandoren said:**
> Ok here is the complete tutorial combining all the different recourses on how to compile / install gimp 2.8 in Ubuntu 12.04 from source.

or watch my video tutorial [http://www.youtube.com/watch?v=k4Um8tvHcgk&feature=youtu.be](http://www.youtube.com/watch?v=k4Um8tvHcgk&feature=youtu.be)
 
first open your update manager and update you Ubuntu to the latest kernel and state. 

then ... 

Thanks a bunch,
It worked for me.
Really nice tutorial :-)

---

### Post by shreepads on 2012-05-20
> **dnelub said:**
> ```
root@bt:~/tmp/gimp# sudo apt-get build-dep gimp
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to find a source package for gimp

```

I have been trying to install gimp 2.8 on Ubuntu Lucid. I have not made it yet. As far as I see I need to add a source. Definitely there is no such source in the source of software. I downloaded the source and gave the command in the source folder. 

So, can someone please help me what I should do? thanks in advance.

Have a look at your "Software Sources" that have been enabled (universe, multiverse, sources, partners, independent etc in Ubuntu Software Centre -> Edit -> Software Sources). I would guess that you need to enable one or more of these.

I've had no problems getting GIMP 2.8 on Lucid and have put together a little (!) how-to here: [How to use GIMP 2.8 on Lucid 10.04.4 LTS]("http://ubuntuforums.org/showthread.php?t=1982183")

---

### Post by warp4ever on 2012-05-25
I too have this problem, I made all the repos available, and the response remains:

> 
/drive/gimp-2.8.0: sudo apt-get build-dep gimp 
Reading package lists... Done 
Building dependency tree        
Reading state information... Done 
E: Unable to find a source package for gimp

---

### Post by shreepads on 2012-05-28
> **warp4ever said:**
> I too have this problem, I made all the repos available, and the response remains:

Do you have any GIMP PPAs enabled? They may be causing the problem..

---

### Post by ardhiesta on 2012-07-20
> **warp4ever said:**
> I too have this problem, I made all the repos available, and the response remains:

I had the same problem as yours
I activated **Source code** repository and it was resolve my problem

[IMG]http://img204.imageshack.us/img204/6935/synapticf.png[/IMG]

sorry if there was any mistake in my grammar, I'm not native speaker

---

### Post by Macr237 on 2012-07-22
> **davidvandoren said:**
> 27) ```
./configure --prefix=/opt/gimp-2.8
```I keep dying at this step.

This is what I get

checking for headers required to compile python extensions... not found
configure: error: 
*** Could not find Python headers.
*** Please install them, or skip building the python scripting extension by
*** passing --disable-python to configure (but then you will not be able
*** to use scripts for GIMP that are written in Python).

I had another error earlier with libtiff, IIRC I just got the developers version. But after that, I got the above error. I tried reloading Python 2.7 and even 3 dev, but to no avail. Any idea how I can proceed?

---

### Post by Macr237 on 2012-07-22
Don't worry. I have sorted it out. It took a while and a number of packages had to be downloaded.

Anyway, thanks for the tutorial, now to see if I can get my plug-ins back.

---

### Post by jimstar79 on 2012-09-10
Hi guys, 

I am interested in getting Gimp 2.8 working on Ubuntu 10.04. I thought this thread might help. 

A lot of the stuff here goes a bit (read, way) over my head. I am correct in thinking that a lot of these instructions are for Ubuntu 12.04? And are not worth attempting in 10.04?

cheers!

---

