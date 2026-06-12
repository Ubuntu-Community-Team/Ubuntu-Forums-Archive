---
title: "Building Nautilus 2.91 from source"
date: 2011-01-30
forum: Packaging and Compiling Programs
---

### Post by towheedm on 2011-01-30
I'm trying to build nautilus 2.91.  When I run the configure script I get the following error

configure: error: glib-compile-schemas not found.

I've checked and glib-compile-schemas exist under the /usr/lib/glib-2.0 directory.  I've tried adding the directory to my path but that does not help.

This is the output of the configure script:

```
towheed@GA1A4CH:~/nautilus-2.91.7$ ./configure --prefix=/usr/
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for a thread-safe mkdir -p... /bin/mkdir -p
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking how to create a ustar tar archive... gnutar
checking whether to enable maintainer-specific portions of Makefiles... no
checking for style of include used by make... GNU
checking for gcc... gcc
checking whether the C compiler works... yes
checking for C compiler default output file name... a.out
checking for suffix of executables... 
checking whether we are cross compiling... no
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ISO C89... none needed
checking dependency style of gcc... gcc3
checking how to run the C preprocessor... gcc -E
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
checking whether byte ordering is bigendian... no
checking for an ANSI C-conforming const... yes
checking for gcc... (cached) gcc
checking whether we are using the GNU C compiler... (cached) yes
checking whether gcc accepts -g... (cached) yes
checking for gcc option to accept ISO C89... (cached) none needed
checking dependency style of gcc... (cached) gcc3
checking how to run the C preprocessor... gcc -E
checking whether ln -s works... yes
checking whether make sets $(MAKE)... (cached) yes
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking how to print strings... printf
checking for a sed that does not truncate output... /bin/sed
checking for fgrep... /bin/grep -F
checking for ld used by gcc... /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... yes
checking for BSD- or MS-compatible name lister (nm)... /usr/bin/nm -B
checking the name lister (/usr/bin/nm -B) interface... BSD nm
checking the maximum length of command line arguments... 1572864
checking whether the shell understands some XSI constructs... yes
checking whether the shell understands "+="... yes
checking how to convert i686-pc-linux-gnu file names to i686-pc-linux-gnu format... func_convert_file_noop
checking how to convert i686-pc-linux-gnu file names to toolchain format... func_convert_file_noop
checking for /usr/bin/ld option to reload object files... -r
checking for objdump... objdump
checking how to recognize dependent libraries... pass_all
checking for dlltool... dlltool
checking how to associate runtime and link libraries... printf %s\n
checking for ar... ar
checking for archiver @FILE support... @
checking for strip... strip
checking for ranlib... ranlib
checking command to parse /usr/bin/nm -B output from gcc object... ok
checking for sysroot... no
checking for mt... mt
checking if mt is a manifest tool... no
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
checking whether stripping libraries is possible... yes
checking if libtool supports shared libraries... yes
checking whether to build shared libraries... yes
checking whether to build static libraries... no
checking for pkg-config... /usr/bin/pkg-config
checking for floor in -lm... yes
checking locale.h usability... yes
checking locale.h presence... yes
checking for locale.h... yes
checking for LC_MESSAGES... yes
checking libintl.h usability... yes
checking libintl.h presence... yes
checking for libintl.h... yes
checking for ngettext in libc... yes
checking for dgettext in libc... yes
checking for bind_textdomain_codeset... yes
checking for msgfmt... /usr/bin/msgfmt
checking for dcgettext... yes
checking if msgfmt accepts -c... yes
checking for gmsgfmt... /usr/bin/msgfmt
checking for xgettext... /usr/bin/xgettext
checking pkg-config is at least version 0.16... yes
configure: error: glib-compile-schemas not found.

```Any help with solving this is greatly appreciated.
NOTE:  I'm building this for Maverick.

---

### Post by mc4man on 2011-01-30
Well your libglib version may be too old, (min. 2.27.5), anyway that would only be first of several.
You'd need some gnome3 (gnome-desktop) and gtk3 libs as well that I don't believe are avail. in the default maverick repo's

---

### Post by towheedm on 2011-01-30
Quite so.  Got past the first problem after installing some -dev packages.  Then got the glib and gtk+3 errors.  Does this mean I now have to build glib and gtk from source first, or are there some ppa out there with .deb packages of these.

Thanks.

---

### Post by towheedm on 2011-02-01
So I have built the required glib and gtk+ libraries.  Now configure reports the following error:

```
configure: error: Package requirements (
    gail-3.0
    gnome-desktop-3.0 >= 2.91.2
    libxml-2.0 >= 2.4.7
    x11
) were not met:

No package 'gnome-desktop-3.0' found
```

pkg-config returns:

```
pkg-config --modversion libxml-2.0 gail-3.0 x11
2.7.7
2.99.2
1.3.3
```

I'm a noob at building packages from source so any help is appreciated.

Thanks

---

### Post by LanoxxthShaddow on 2011-02-03
hi towheedm,

I am also trying to compile nautilus. I got as far as you and when i  tried to compile gnome-desktop i got some strange errors about autoconf  makros:

```
Please add the files
  codeset.m4 gettext.m4 glibc21.m4 iconv.m4 isc-posix.m4 lcmessage.m4
  progtest.m4
from the /aclocal directory to your autoconf macro directory
or directly to your aclocal.m4 file.
You will also need config.guess and config.sub, which you can get from
ftp://ftp.gnu.org/pub/gnu/config/.
```

and then later:
```
libgnome-desktop/Makefile.am:73: HAVE_INTROSPECTION does not appear in AM_CONDITIONAL
```

Did you perhaps come across these errors too?

---

### Post by towheedm on 2011-02-03
I eventually got it built successfully 2 nites ago, just after my previous post.  I built 2.91.8. The files [COLOR=Blue]config.guess[/COLOR] and [COLOR=Blue]config.sub[/COLOR] is already included in the source.  Did you download from [COLOR=Red]ftp.gnome.org[/COLOR] or from some other place?

Did you try to rebuild the automake and autoconf files?

If you're interested, this is what I did to build nautilus.  This was done in Maverick.

1.  Install the gconf2 development libs package:
```
sudo apt-get install libgconf2-dev
```2.  Download nautilus
```
wget --output-document=~/Downloads/nautilus-2.91.8.tar.gz ftp.gnome.org/../pub/gnome/sources/nautilus/2.91/nautilus-2.91.8.tar.gz
```3.  Download glib 2.27.93
```
wget --output-document=~/Downloads/glib-2.9.6.tar.gz ftp.gnome.org/../pub/gnome/sources/glib/2.9/glib-2.9.6.tar.gz

```4.  Download GTK+-3.0
```
wget --output-document=~/Downloads/gtk+-2.99.3.tar.gz ftp.gnome.org/../pub/gnome/sources/gtk+/2.99/gtk+-2.99.3.tar.gz
```5.  Download gnome-desktop-3.0
```
wget --output-document=~/Downloads/gnome-desktop-2.91.6.tar.gz ftp.gnome.org/../pub/gnome/sources/gnome-desktop/2.91/gnome-desktop-2.91.6.tar.gz

```6.  Download gsettings-desktop-schemas:
```
wget --output-document=~/Downloads/gsettings-desktop-schemas-0.1.5.tar.gz ftp.gnome.org/../pub/gnome/sources/gsettings-desktop-schemas/0.1/gsettings-desktop-schemas-0.1.5.tar.gz

```6.  Extract archives
```
tar xfv ~/Downloads/nautilus-2.91.8.tar.gz &&
tar xvf ~/Downloads/glib-2.9.6.tar.gz &&
tar xvf ~/Downloads/gtk+-2.99.3.tar.gz &&
tar xvf ~/Downloads/gnome-desktop-2.91.6.tar.gz &&
tar xvf ~/Downloads/gsettings-desktop-schemas-0.1.5.tar.gz 

```7.  Install the gettext package
```
sudo apt-get install gettext
```8.  Build Glib
```
cd ~/glib-2.9.6
./configure
make
sudo make install
sudo ldconfig -v

```9.  Install pango and gail
```
sudo apt-get install libpango1.0-dev libgail-dev
```10.  Build gtk+-3.0:
```
cd ~/gtk+-2.99.3
./configure
make
sudo make install
sudo ldconfig -v

```11.  Install the intltool package
```
sudo apt-get install intltool libgconf2-dev

```12.  Build gsettings-desktop-schemas
```
cd ~/gsettings-desktop-schemas-0.1.5
./configure
make
sudo make install

```13.  Build gnome-desktop-3.0
```
cd ~/gnome-desktop-2.91.6
./configure
make
sudo make install
sudo ldconfig -v

```14.  Install the libxml2.0 development libs
```
sudo apt-get install libxml2-dev

```15.  Build nautilus:
```
cd ~/nautilus-2.91.8
./configure
make
make install
sudo ldconfig -v

```Notice I've built everything to the /usr/local directory.  When I tried building to the /usr/ directory there were conflicts between the old and the new packages.  I have not tried to sorting these out to build to the /usr/ directory.  If you do please let me kmow.

I've tried this just as a learning exercise for myself.

---

### Post by LanoxxthShaddow on 2011-02-03
towheedm,

thank you for this detailed post. I also got nautilus to work using JHBuild yesterday. I had given up on building it manually due to several errors I had gotten. Like you I used a different build directory, the difference however is that I am using the latest git sources. However from your code samples I can not see where you set the build destination? Also you dont seem to use autogen.sh but configure instead, when I tried to build manually I used something like this:
```
#One time on starting the shell:
export PKG_CONFIG_PATH=/home/MyDocuments/usr/local/lib/pkgconfig/
export LD_LIBRARY_PATH=/home/MyDocuments/usr/local/lib/
``````

#Then for each package: glib, gtk+, gnome-desktop, etc, I ran:
./autogen.sh --prefix=/home/MyDocuments/usr/local
make
make install #no sudo required as im building to /home/...

```When I tried to build gnome-desktop I suddently got that error I described below and then I gave up and went to use JHBuild, which also gave me a lot of headaces but eventually it build nautilus fine.

The only thing that I wonder about now is that nautilus is only shown with simple X graphics, it doesnt use the Maverick themes. Does that happen for you too?

Oh, I would not try to build to /usr, because then it will try to overwrite your Maverick packages, and you might end up with a broken system. That happended to me once when I compiled glib.

---

### Post by towheedm on 2011-02-04
If you built some of the libs to your home dir, then you may need to add that path to the PK_CONFIG_PATH variable so that it finds the .pc files there.

As for the theme, yes I also got the same simple theme.  It does not use the Maverick themes I set.

Also, there are a host of other thimgs I don't like.  When I clik on Network, it gives a 'Nautilus does not work with network:///' error.  I also miss my volume icons on the left pane which I could simply click on and mount or unmount.

My primary OS is Karmic so if Maverick gets broken no probs for me.  I'll still give it a shot at building to /usr.

Oh, and I used the ./configure script which defaults to --prefix=/usr/local.  To build to a different destination you would need to specify --prefix=/builddir.

I susspect if you built from the git source, you would have to generate the .am and .in files yourself.

---

