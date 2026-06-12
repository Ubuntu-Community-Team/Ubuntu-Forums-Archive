---
title: "Fail to build vlc-1.2 git missing dependency 'libdvbpsi' on ubuntu lucid 10.04 LTS"
date: 2011-04-08
forum: Packaging and Compiling Programs
---

### Post by CMatomic on 2011-04-08
I'm trying to compile vlc 1.2 but got an error

[CENTER]```
Setting up libidl0 (0.8.13-1) ...
Setting up libnspr4-0d (4.8.6-0ubuntu0.10.04.2) ...
Setting up libnss3-1d (3.12.9+ckbi-1.82-0ubuntu0.10.04.1) ...
Setting up libxcb-aux0 (0.3.6-1build1) ...
Setting up libxcb-event1 (0.3.6-1build1) ...
Setting up libstartup-notification0 (0.10-1build1) ...
Setting up xulrunner-1.9.2 (1.9.2.16+build1+nobinonly-0ubuntu0.10.04.1) ...
update-alternatives: using /usr/bin/xulrunner-1.9.2 to provide /usr/bin/xulrunner (xulrunner) in auto mode.
Setting up libnspr4-dev (4.8.6-0ubuntu0.10.04.2) ...
Setting up libnss3-dev (3.12.9+ckbi-1.82-0ubuntu0.10.04.1) ...
Setting up libiw30 (30~pre9-3ubuntu4) ...
Setting up libiw-dev (30~pre9-3ubuntu4) ...
Setting up xulrunner-1.9.2-dev (1.9.2.16+build1+nobinonly-0ubuntu0.10.04.1) ...
Setting up xulrunner-dev (1.9.2.16+build1+nobinonly-0ubuntu0.10.04.1) ...
Setting up yasm (0.8.0-1) ...
Setting up libva-x11-1 (1:1.0.8~ppa10) ...
Setting up libva1 (1:1.0.8~ppa10) ...
Setting up libavcodec52 (4:0.6.1-5ubuntu2) ...
Setting up libavcodec-dev (4:0.6.1-5ubuntu2) ...
Setting up libavformat52 (4:0.6.1-5ubuntu2) ...
Setting up libavformat-dev (4:0.6.1-5ubuntu2) ...
Setting up libva-tpi1 (1:1.0.8~ppa10) ...
Setting up libva-glx1 (1:1.0.8~ppa10) ...
Setting up libva-dev (1:1.0.8~ppa10) ...
Setting up pbuilder-satisfydepends-dummy (0.invalid.0) ...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
Reading package lists... Done             
Building dependency tree       
Reading state information... Done
Reading extended state information       
Initializing package states... Done
Writing extended state information... Done

Current status: 0 broken [-1].
 -> Finished parsing the build-deps
Reading package lists...
Building dependency tree...
Reading state information...
aptitude is already the newest version.
The following NEW packages will be installed:
  fakeroot
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/101kB of archives.
After this operation, 381kB of additional disk space will be used.
Selecting previously deselected package fakeroot.
(Reading database ... 33500 files and directories currently installed.)
Unpacking fakeroot (from .../fakeroot_1.14.4-1ubuntu1_amd64.deb) ...
Processing triggers for man-db ...
Setting up fakeroot (1.14.4-1ubuntu1) ...
update-alternatives: using /usr/bin/fakeroot-sysv to provide /usr/bin/fakeroot (fakeroot) in auto mode.
I: Copying back the cached apt archive contents
I: Copying source file
I: copying [vlc_1.2+git20110408.dsc]
I: copying [./vlc_1.2+git20110408.tar.gz]
I: Extracting source
gpgv: Signature made Fri Apr  8 16:15:38 2011 UTC using RSA key ID 35F963B1
gpgv: Can't check signature: public key not found
dpkg-source: warning: failed to verify signature on ./vlc_1.2+git20110408.dsc
dpkg-source: info: extracting vlc in vlc-1.2+git20110408
dpkg-source: info: unpacking vlc_1.2+git20110408.tar.gz
I: Building the package
I: Running cd tmp/buildd/*/ && dpkg-buildpackage -us -uc  -rfakeroot
dpkg-buildpackage: export CFLAGS from dpkg-buildflags (origin: vendor): -g -O2
dpkg-buildpackage: export CPPFLAGS from dpkg-buildflags (origin: vendor): 
dpkg-buildpackage: export CXXFLAGS from dpkg-buildflags (origin: vendor): -g -O2
dpkg-buildpackage: export FFLAGS from dpkg-buildflags (origin: vendor): -g -O2
dpkg-buildpackage: export LDFLAGS from dpkg-buildflags (origin: vendor): -Wl,-Bsymbolic-functions
dpkg-buildpackage: source package vlc
dpkg-buildpackage: source version 1.2+git20110408
dpkg-buildpackage: source changed by CMatomic <cmatomic@gmail.com>
dpkg-buildpackage: host architecture amd64
 dpkg-source --before-build vlc-1.2+git20110408
dpkg-source: info: using options from vlc-1.2+git20110408/debian/source/local-options: --unapply-patches --abort-on-upstream-changes
dpkg-source: warning: --unapply-patches is not a valid option for Dpkg::Source::Package::V1
 fakeroot debian/rules clean
dh clean --parallel
   dh_testdir -O--parallel
   debian/rules override_dh_auto_clean
make[1]: Entering directory `/tmp/buildd/vlc-1.2+git20110408'
[ ! -f debian/vlc-nox.install.bak ] || mv -f debian/vlc-nox.install.bak \
		debian/vlc-nox.install
rm -f debian/vlc-nox.install.kfreebsd
rm -f debian/vlc-nox.install.hurd
rm -rf tmp/
dh_auto_clean
make[1]: Leaving directory `/tmp/buildd/vlc-1.2+git20110408'
   dh_clean -O--parallel
 dpkg-source -b vlc-1.2+git20110408
dpkg-source: info: using options from vlc-1.2+git20110408/debian/source/local-options: --unapply-patches --abort-on-upstream-changes
dpkg-source: warning: no source format specified in debian/source/format, see dpkg-source(1)
dpkg-source: warning: --unapply-patches is not a valid option for Dpkg::Source::Package::V1
dpkg-source: info: using source format `1.0'
dpkg-source: info: building vlc in vlc_1.2+git20110408.tar.gz
dpkg-source: info: building vlc in vlc_1.2+git20110408.dsc
 debian/rules build
dh build --parallel
   dh_testdir -O--parallel
   debian/rules override_dh_auto_configure
make[1]: Entering directory `/tmp/buildd/vlc-1.2+git20110408'
# We need to build the static library apart
# Else it's a mess when we build the modules
./configure --enable-static --build=x86_64-linux-gnu --config-cache --disable-maintainer-mode --disable-silent-rules --disable-update-check --enable-fast-install --prefix=/usr --docdir=/usr/share/doc/vlc-nox --sysconfdir=/etc --with-binary-version=  --enable-a52 --enable-aa --enable-bonjour --enable-caca --enable-dca --enable-dirac --enable-dvb --enable-dvbpsi --enable-dvdnav --enable-faad --enable-flac --enable-fluidsynth --enable-freetype --enable-fribidi --enable-ggi --enable-gnutls --enable-jack --enable-kate --enable-libass --enable-libmpeg2 --enable-libproxy --enable-libxml2 --enable-lirc --enable-live555 --enable-mad --enable-mkv --enable-mod --enable-mozilla --enable-mpc --enable-mtp --enable-mux_ogg --enable-ncurses --enable-notify --enable-ogg --enable-pulse --enable-qt4 --enable-realrtsp --enable-schroedinger --enable-sdl --enable-shout --enable-skins2 --enable-smb --enable-speex --enable-svg --enable-taglib --enable-theora --enable-twolame --enable-upnp --enable-vcd --enable-vcdx --enable-vorbis --enable-zvbi --with-kde-solid=/usr/share/kde4/apps/solid/actions/ --with-mozilla-pkg=libxul  --disable-dxva2 --disable-gnomevfs --disable-goom --disable-osso_screensaver --disable-portaudio --disable-projectm --disable-sqlite --disable-telx --disable-x264  --enable-alsa --enable-atmo --enable-dc1394 --enable-dv --enable-libva --enable-pvr --enable-udev --enable-v4l2  --enable-svgalib
configure: WARNING: unrecognized options: --enable-dvb, --enable-ggi, --enable-mozilla, --with-mozilla-pkg, --enable-svgalib
configure: creating cache config.cache
checking build system type... x86_64-pc-linux-gnu
checking host system type... x86_64-pc-linux-gnu
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
checking for gcc option to accept ISO C99... -std=gnu99
checking how to run the C preprocessor... gcc -std=gnu99 -E
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
checking minix/config.h usability... no
checking minix/config.h presence... no
checking for minix/config.h... no
checking whether it is safe to define __EXTENSIONS__... yes
checking whether gcc -std=gnu99 and cc understand -c and -o together... yes
checking for g++... g++
checking whether we are using the GNU C++ compiler... yes
checking whether g++ accepts -g... yes
checking dependency style of g++... gcc3
checking how to run the C preprocessor... gcc -std=gnu99 -E
checking for gcc... gcc
checking whether we are using the GNU Objective C compiler... no
checking whether gcc accepts -g... no
checking dependency style of gcc... gcc3
checking dependency style of gcc... (cached) gcc3
checking for egrep... (cached) /bin/grep -E
checking whether make sets $(MAKE)... (cached) yes
checking dependency style of gcc -std=gnu99... gcc3
checking for ranlib... ranlib
checking for strip... strip
checking for ar... ar
checking for ld... ld
checking for dlltool... no
checking for an ANSI C-conforming const... yes
checking for inline... inline
checking for C/C++ restrict keyword... __restrict
checking for libs in /tmp/buildd/vlc-1.2+git20110408/./extras/contrib/hosts/x86_64-linux-gnu... no
checking for a sed that does not truncate output... /bin/sed
checking for fgrep... /bin/grep -F
checking for ld used by gcc -std=gnu99... ld
checking if the linker (ld) is GNU ld... yes
checking for BSD- or MS-compatible name lister (nm)... /usr/bin/nm -B
checking the name lister (/usr/bin/nm -B) interface... BSD nm
checking whether ln -s works... yes
checking the maximum length of command line arguments... 3458764513820540925
checking whether the shell understands some XSI constructs... yes
checking whether the shell understands "+="... yes
checking for ld option to reload object files... -r
checking for objdump... objdump
checking how to recognize dependent libraries... (cached) pass_all
checking for ar... (cached) ar
checking for strip... (cached) strip
checking for ranlib... (cached) ranlib
checking command to parse /usr/bin/nm -B output from gcc -std=gnu99 object... ok
checking for dlfcn.h... yes
checking whether we are using the GNU C++ compiler... (cached) yes
checking whether g++ accepts -g... (cached) yes
checking dependency style of g++... (cached) gcc3
checking how to run the C++ preprocessor... g++ -E
checking for objdir... .libs
checking if gcc -std=gnu99 supports -fno-rtti -fno-exceptions... no
checking for gcc -std=gnu99 option to produce PIC... -fPIC -DPIC
checking if gcc -std=gnu99 PIC flag -fPIC -DPIC works... yes
checking if gcc -std=gnu99 static flag -static works... yes
checking if gcc -std=gnu99 supports -c -o file.o... yes
checking if gcc -std=gnu99 supports -c -o file.o... (cached) yes
checking whether the gcc -std=gnu99 linker (ld -m elf_x86_64) supports shared libraries... yes
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
checking whether to build static libraries... yes
checking for ld used by g++... ld -m elf_x86_64
checking if the linker (ld -m elf_x86_64) is GNU ld... yes
checking whether the g++ linker (ld -m elf_x86_64) supports shared libraries... yes
checking for g++ option to produce PIC... -fPIC -DPIC
checking if g++ PIC flag -fPIC -DPIC works... yes
checking if g++ static flag -static works... yes
checking if g++ supports -c -o file.o... yes
checking if g++ supports -c -o file.o... (cached) yes
checking whether the g++ linker (ld -m elf_x86_64) supports shared libraries... yes
checking dynamic linker characteristics... GNU/Linux ld.so
checking how to hardcode library paths into programs... immediate
checking whether NLS is requested... yes
checking for msgfmt... /usr/bin/msgfmt
checking for gmsgfmt... /usr/bin/msgfmt
checking for xgettext... /usr/bin/xgettext
checking for msgmerge... /usr/bin/msgmerge
checking for ld used by GCC... ld -m elf_x86_64
checking if the linker (ld -m elf_x86_64) is GNU ld... yes
checking for shared library run path origin... done
checking for CFPreferencesCopyAppValue... no
checking for CFLocaleCopyCurrent... no
checking for GNU gettext in libc... yes
checking whether to use NLS... yes
checking where the gettext function comes from... libc
checking for iconv... yes
checking for working iconv... yes
checking for iconv declaration... 
         extern size_t iconv (iconv_t cd, char * *inbuf, size_t *inbytesleft, char * *outbuf, size_t *outbytesleft);
checking for buggy GNU/libc versions... not present
checking for shared objects suffix... .so
checking for daemon... yes
checking for fcntl... yes
checking for fdopendir... yes
checking for fstatvfs... yes
checking for fork... yes
checking for getenv... yes
checking for getpwuid_r... yes
checking for gettimeofday... yes
checking for isatty... yes
checking for lstat... yes
checking for memalign... yes
checking for mmap... yes
checking for openat... yes
checking for pread... yes
checking for posix_fadvise... yes
checking for posix_madvise... yes
checking for posix_memalign... yes
checking for setlocale... yes
checking for stricmp... no
checking for strnicmp... no
checking for uselocale... yes
checking for asprintf... yes
checking for atof... yes
checking for atoll... yes
checking for dirfd... yes
checking for getcwd... yes
checking for getdelim... yes
checking for getpid... yes
checking for gmtime_r... yes
checking for lldiv... yes
checking for localtime_r... yes
checking for nrand48... yes
checking for rewind... yes
checking for setenv... yes
checking for strcasecmp... yes
checking for strcasestr... yes
checking for strdup... yes
checking for strlcpy... no
checking for strncasecmp... yes
checking for strndup... yes
checking for strnlen... yes
checking for strsep... yes
checking for strtof... yes
checking for strtok_r... yes
checking for strtoll... yes
checking for swab... yes
checking for tdestroy... yes
checking for vasprintf... yes
checking for fdatasync... yes
checking for working strcoll... yes
checking for accept4... yes
checking for pipe2... yes
checking for eventfd... yes
checking for vmsplice... yes
checking for sched_getaffinity... yes
checking for connect... yes
checking for send... yes
checking for socklen_t in sys/socket.h... yes
checking for struct sockaddr_storage... yes
checking for library containing getaddrinfo... none required
checking for va_copy... yes
checking for __va_copy... yes
checking for inet_aton... yes
checking for getopt_long... yes
checking for cos in -lm... yes
checking for pow in -lm... yes
checking for sqrt in -lm... yes
checking for ceil in -lm... yes
checking for exp in -lm... yes
checking for round in -lm... yes
checking for sqrtf in -lm... yes
checking for lrintf in -lm... yes
checking dl.h usability... no
checking dl.h presence... no
checking for dl.h... no
checking for shl_load... (cached) no
checking for dlfcn.h... (cached) yes
checking sys/dl.h usability... no
checking sys/dl.h presence... no
checking for sys/dl.h... no
checking for dlopen... (cached) no
checking for dlopen in -ldl... (cached) yes
checking for main in -lpthread... yes
checking for clock_nanosleep in -lrt... yes
checking for nanosleep... yes
checking for strncasecmp in strings.h... yes
checking search.h usability... yes
checking search.h presence... yes
checking for search.h... yes
checking getopt.h usability... yes
checking getopt.h presence... yes
checking for getopt.h... yes
checking for strings.h... (cached) yes
checking locale.h usability... yes
checking locale.h presence... yes
checking for locale.h... yes
checking xlocale.h usability... yes
checking xlocale.h presence... yes
checking for xlocale.h... yes
checking fcntl.h usability... yes
checking fcntl.h presence... yes
checking for fcntl.h... yes
checking sys/time.h usability... yes
checking sys/time.h presence... yes
checking for sys/time.h... yes
checking sys/ioctl.h usability... yes
checking sys/ioctl.h presence... yes
checking for sys/ioctl.h... yes
checking for sys/stat.h... (cached) yes
checking arpa/inet.h usability... yes
checking arpa/inet.h presence... yes
checking for arpa/inet.h... yes
checking netinet/in.h usability... yes
checking netinet/in.h presence... yes
checking for netinet/in.h... yes
checking netinet/udplite.h usability... no
checking netinet/udplite.h presence... no
checking for netinet/udplite.h... no
checking sys/eventfd.h usability... yes
checking sys/eventfd.h presence... yes
checking for sys/eventfd.h... yes
checking for net/if.h... yes
checking for sys/mount.h... yes
checking machine/param.h usability... no
checking machine/param.h presence... no
checking for machine/param.h... no
checking sys/shm.h usability... yes
checking sys/shm.h presence... yes
checking for sys/shm.h... yes
checking linux/version.h usability... yes
checking linux/version.h presence... yes
checking for linux/version.h... yes
checking linux/dccp.h usability... yes
checking linux/dccp.h presence... yes
checking for linux/dccp.h... yes
checking scsi/scsi.h usability... yes
checking scsi/scsi.h presence... yes
checking for scsi/scsi.h... yes
checking linux/magic.h usability... yes
checking linux/magic.h presence... yes
checking for linux/magic.h... yes
checking syslog.h usability... yes
checking syslog.h presence... yes
checking for syslog.h... yes
checking for ssize_t... yes
checking for library containing poll... none required
checking for nanosleep in time.h... yes
checking for timespec in sys/time.h... yes
checking pthread.h usability... yes
checking pthread.h presence... yes
checking for pthread.h... yes
checking for pkg-config... /usr/bin/pkg-config
checking pkg-config is at least version 0.9.0... yes
checking zlib.h usability... yes
checking zlib.h presence... yes
checking for zlib.h... yes
checking for MINIZIP... no
checking unzip.h usability... no
checking unzip.h presence... no
checking for unzip.h... no
checking for DBUS... yes
checking for ntohl in sys/param.h... no
checking if gcc -std=gnu99 accepts -Wall... yes
checking if gcc -std=gnu99 accepts -Wextra... yes
checking if gcc -std=gnu99 accepts -Wsign-compare... yes
checking if gcc -std=gnu99 accepts -Wundef... yes
checking if gcc -std=gnu99 accepts -Wpointer-arith... yes
checking if gcc -std=gnu99 accepts -Wbad-function-cast... yes
checking if gcc -std=gnu99 accepts -Wwrite-strings... yes
checking if gcc -std=gnu99 accepts -Wmissing-prototypes... yes
checking if gcc -std=gnu99 accepts -Wvolatile-register-var... yes
checking if gcc -std=gnu99 accepts -Werror-implicit-function-declaration... yes
checking if gcc -std=gnu99 accepts -pipe... yes
checking if $CC accepts -Os... yes
checking if $CC accepts -O4... yes
checking if $CC accepts -O3... yes
checking if $CC accepts -O2... yes
checking if $CC accepts -O0... yes
checking if $CC accepts -ffast-math... yes
checking if $CC accepts -funroll-loops... yes
checking if $CC accepts -fomit-frame-pointer... yes
checking if $CC accepts -bundle -undefined error... no
checking __attribute__ ((aligned ())) support... 64
checking for __attribute__((packed))... yes
checking execinfo.h usability... yes
checking execinfo.h presence... yes
checking for execinfo.h... yes
checking for backtrace... yes
checking if gcc -std=gnu99 groks MMX intrinsics... yes
checking if gcc -std=gnu99 groks MMX inline assembly... yes
checking if gcc -std=gnu99 groks MMX EXT inline assembly... yes
checking if gcc -std=gnu99 groks SSE2 intrinsics... yes
checking if gcc -std=gnu99 groks SSE inline assembly... yes
checking if gcc -std=gnu99 groks SSE2 inline assembly... yes
checking if gcc -std=gnu99 groks SSE3 inline assembly... yes
checking if gcc -std=gnu99 groks SSSE3 inline assembly... yes
checking if gcc -std=gnu99 groks SSE4.1 inline assembly... yes
checking if gcc -std=gnu99 groks SSE4.2 inline assembly... yes
checking if gcc -std=gnu99 groks SSE4A inline assembly... yes
checking if gcc -std=gnu99 groks 3D Now! inline assembly... yes
checking whether gcc -std=gnu99 accepts -mtune=athlon64... yes
checking for LUA... yes
checking for luac... /usr/bin/luac
checking for LIBPROXY... yes
checking for NOTIFY... yes
checking for TAGLIB... yes
checking taglib/mp4coverart.h usability... yes
checking taglib/mp4coverart.h presence... yes
checking for taglib/mp4coverart.h... yes
checking liveMedia_version.hh usability... yes
checking liveMedia_version.hh presence... yes
checking for liveMedia_version.hh... yes
checking for liveMedia version >= 1275091200 ... yes
checking for main in -lliveMedia_pic... yes
checking for DC1394... yes
checking for DV... yes
checking for LINSYS_SDI... yes
checking for DVDREAD... yes
checking for DVDNAV... yes
checking for dvdnav_get_video_resolution in -ldvdnav... no
checking for dvdnav_describe_title_chapters in -ldvdnav... yes
checking for BLURAY... no
configure: WARNING: Library libbluray >= 0.2  needed for bluray was not found
checking libsmbclient.h usability... yes
checking libsmbclient.h presence... yes
checking for libsmbclient.h... yes
checking linux/videodev2.h usability... yes
checking linux/videodev2.h presence... yes
checking for linux/videodev2.h... yes
checking sys/videoio.h usability... no
checking sys/videoio.h presence... no
checking for sys/videoio.h... no
checking for LIBV4L2... yes
checking DeckLinkAPIDispatch.cpp usability... no
checking DeckLinkAPIDispatch.cpp presence... no
checking for DeckLinkAPIDispatch.cpp... no
configure: WARNING: Blackmagic DeckLink SDI include files not found
checking for LIBCDIO... yes
checking for LIBVCDINFO... yes
checking for cdrom_msf0 in linux/cdrom.h... yes
checking for scsireq in sys/scsiio.h... no
checking for ioc_toc_header in sys/cdio.h... no
checking for LIBCDDB... yes
checking for DVBPSI... configure: error: Package requirements (libdvbpsi) were not met:

No package 'libdvbpsi' found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables DVBPSI_CFLAGS
and DVBPSI_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.

make[1]: *** [override_dh_auto_configure] Error 1
make[1]: Leaving directory `/tmp/buildd/vlc-1.2+git20110408'
make: *** [build] Error 2
dpkg-buildpackage: error: debian/rules build gave error exit status 2
E: Failed autobuilding of package
I: unmounting dev/pts filesystem
I: unmounting proc filesystem
I: cleaning the build env 
I: removing directory /var/cache/pbuilder/build//25802 and its subdirectories
codexlibre@tonignome-laptop:~/CodigosFonte/vlcDEBIAN$ 
```[/CENTER]

 my control for vlc 1.2 git 

[CENTER]```
Source: vlc
Section: video
Priority: optional
Maintainer: Debian multimedia packages maintainers <pkg-multimedia-maintainers@lists.alioth.debian.org>
Uploaders: Sam Hocevar (Debian packages) <sam+deb@zoy.org>,
           Clément Stenac <zorglub@debian.org>,
           Loic Minier <lool@dooz.org>,
           Christophe Mutricy <xtophe@videolan.org>,
           Mohammed Adnène Trojette <adn+deb@diwi.org>,
           Reinhard Tartler <siretart@tauware.de>,
           Benjamin Drung <bdrung@debian.org>
Build-Depends: debhelper (>= 7.2.3~),
               dh-buildinfo,
               gettext,
               liba52-0.7.4-dev,
               libaa1-dev,
               libasound2-dev (>= 0.9.0beta10a) [!kfreebsd-i386 !kfreebsd-amd64 !hurd-i386],
               libass-dev (>= 0.9.6),
               libavahi-client-dev,
               libavc1394-dev [!kfreebsd-i386 !kfreebsd-amd64 !hurd-i386],
               libavcodec-dev (>= 4:0.6),
               libavformat-dev (>= 4:0.6),
               libcaca-dev (>= 0.99.beta4),
               libcddb2-dev,
               libcdio-dev (>= 0.78.2),
               libdc1394-22-dev (>= 2.1.0) [!kfreebsd-i386 !kfreebsd-amd64 !hurd-i386],
               libdca-dev,
               libdirac-dev,
               **libdvbpsi-dev | libdvbpsi5-dev,**
               libdvdnav-dev,
               libdvdread-dev (>= 0.9.5),
               libfaad-dev,
               libflac-dev (>= 1.1.2-3),
               libfluidsynth-dev,
               libfreetype6-dev,
               libfribidi-dev,
               libggi2-dev,
               libgl1-mesa-dev,
               libglib2.0-0,
               libgnutls-dev (>= 1.7.4),
               libgtk2.0-dev,
               libjack-dev,
               libkate-dev (>= 0.1.5),
               liblircclient-dev,
               liblivemedia-dev (>= 2009.11.27),
               liblua5.1-0-dev,
               libmad0-dev,
               libmatroska-dev (>= 0.8.0),
               libmodplug-dev (>= 1:0.8.8.1),
               libmpcdec-dev,
               libmpeg2-4-dev,
               libmtp-dev (>= 1.0.0),
               libncursesw5-dev,
               libnotify-dev,
               libogg-dev,
               libpng12-dev,
               libpostproc-dev (>= 4:0.6),
               libproxy-dev,
               libpulse-dev (>= 0.9.11),
               libqt4-dev (>= 4.4.0),
               libraw1394-dev (>= 2.0.1) [!kfreebsd-i386 !kfreebsd-amd64 !hurd-i386],
               librsvg2-dev,
               libschroedinger-dev (>= 1.0.10),
               libsdl-image1.2-dev,
               libsdl1.2-dev (>= 1.2.10),
               libshout3-dev,
               libsmbclient-dev,
               libspeex-dev,
               libsvga1-dev [amd64 i386],
               libswscale-dev (>= 4:0.6),
               libtag1-dev (>= 1.5),
               libtar-dev,
               libtheora-dev,
               libtwolame-dev (>= 0.3.8),
               libudev-dev [!kfreebsd-i386 !kfreebsd-amd64 !hurd-i386],
               libupnp3-dev,
               libv4l-dev [!kfreebsd-i386 !kfreebsd-amd64 !hurd-i386],
               libva-dev [!kfreebsd-i386 !kfreebsd-amd64 !hurd-i386],
               libvcdinfo-dev (>= 0.7.22),
               libvorbis-dev,
               libx11-dev,
               libx11-xcb-dev,
               libxcb-keysyms1-dev (>= 0.3.4),
               libxcb-randr0-dev (>= 1.3),
               libxcb-shm0-dev,
               libxcb-xv0-dev (>= 1.1.90.1),
               libxcb1-dev,
               libxext-dev,
               libxml2-dev,
               libxpm-dev,
               libxt-dev,
               libzvbi-dev (>= 0.2.28),
               lua5.1,
               nasm,
               pkg-config,
               xulrunner-dev (>= 1.9.1),
               yasm [amd64 kfreebsd-amd64],
               zlib1g-dev
Standards-Version: 3.9.1
Homepage: http://www.videolan.org/vlc/
Vcs-Git: git://git.debian.org/git/pkg-multimedia/vlc.git
Vcs-Browser: http://git.debian.org/?p=pkg-multimedia/vlc.git;a=summary

Package: libvlc-dev
Section: libdevel
Architecture: any
Depends: libvlc5 (= ${binary:Version}),
         libvlccore-dev,
         pkg-config,
         ${misc:Depends}
Replaces: libvlc0-dev
Description: development files for libvlc
 This package contains headers and a static library required to build
 standalone applications that use VLC features.
 .
 VLC is the VideoLAN project's media player. It plays MPEG, MPEG2, MPEG4,
 DivX, MOV, WMV, QuickTime, mp3, Ogg/Vorbis files, DVDs, VCDs, and multimedia
 streams from various network sources.

Package: libvlc5
Section: libs
Architecture: any
Depends: ${misc:Depends}, ${shlibs:Depends}
Replaces: vlc (<< 0.8.6.c-6)
Description: multimedia player and streamer library
 This package contains the shared library required by applications using VLC
 features.
 .
 VLC is the VideoLAN project's media player. It plays MPEG, MPEG2, MPEG4,
 DivX, MOV, WMV, QuickTime, mp3, Ogg/Vorbis files, DVDs, VCDs, and multimedia
 streams from various network sources.

Package: libvlccore-dev
Section: libdevel
Architecture: any
Depends: libvlccore4 (= ${binary:Version}), pkg-config, ${misc:Depends}
Description: development files for libvlccore
 This package contains headers and a static library required to build plugins
 for VLC.
 .
 VLC is the VideoLAN project's media player. It plays MPEG, MPEG2, MPEG4,
 DivX, MOV, WMV, QuickTime, mp3, Ogg/Vorbis files, DVDs, VCDs, and multimedia
 streams from various network sources.

Package: libvlccore4
Section: libs
Architecture: any
Depends: vlc-data (= ${source:Version}), ${misc:Depends}, ${shlibs:Depends}
Description: base library for VLC and its modules
 This package contains the shared library required by VLC modules and libvlc.
 .
 VLC is the VideoLAN project's media player. It plays MPEG, MPEG2, MPEG4,
 DivX, MOV, WMV, QuickTime, mp3, Ogg/Vorbis files, DVDs, VCDs, and multimedia
 streams from various network sources.

Package: mozilla-plugin-vlc
Architecture: any
Depends: vlc, vlc-nox (= ${binary:Version}), ${misc:Depends}, ${shlibs:Depends}
Xb-Npp-Applications: 92650c4d-4b8e-4d2a-b7eb-24ecf4f6b63a,
                     ec8030f7-c20a-464f-9b0e-13a3a9e97384
Xb-Npp-Name: VLC Multimedia Plugin
Xb-Npp-Description: play video and audio in Firefox using the VLC Multimedia Player
Xb-Npp-File: libvlcplugin.so
Xb-Npp-MimeType: application/mpeg4-iod,
                 application/mpeg4-muxcodetable,
                 application/ogg,
                 application/x-google-vlc-plugin,
                 application/x-mplayer2,
                 application/x-ogg,
                 application/x-vlc-plugin,
                 audio/3gpp,
                 audio/3gpp2,
                 audio/mpeg,
                 audio/mpeg4,
                 audio/wav,
                 audio/x-mpeg,
                 audio/x-wav,
                 video/3gpp,
                 video/3gpp2,
                 video/mpeg,
                 video/mpeg-system,
                 video/mpeg4,
                 video/quicktime,
                 video/x-mpeg,
                 video/x-mpeg-system,
                 video/x-ms-asf,
                 video/x-ms-asf-plugin,
                 video/x-ms-wmv,
                 video/x-msvideo
Description: multimedia plugin for web browsers based on VLC
 This plugin adds support for MPEG, MPEG2, DVD, DivX, Ogg/Vorbis and many
 more formats to your Gecko-based web browser (Firefox, Galeon, etc.). The
 decoding process is done by VLC and the output window is embedded in a
 webpage or directly in the browser window. There is also support for
 fullscreen display and javascript control.
 .
 VLC is the VideoLAN project's media player. It plays MPEG, MPEG2, MPEG4,
 DivX, MOV, WMV, QuickTime, mp3, Ogg/Vorbis files, DVDs, VCDs, and multimedia
 streams from various network sources.

Package: vlc
Architecture: any
Depends: ttf-freefont,
         vlc-nox (= ${binary:Version}),
         ${misc:Depends},
         ${shlibs:Depends}
Recommends: vlc-plugin-notify (= ${binary:Version}),
            vlc-plugin-pulse (= ${binary:Version}),
            xdg-utils
Suggests: mozilla-plugin-vlc, videolan-doc
Breaks: vlc-nox (<< 1.1.5-1)
Replaces: vlc-nox (<< 1.1.5-1)
Provides: mp3-decoder
Description: multimedia player and streamer
 VLC is the VideoLAN project's media player. It plays MPEG, MPEG2, MPEG4,
 DivX, MOV, WMV, QuickTime, mp3, Ogg/Vorbis files, DVDs, VCDs, and multimedia
 streams from various network sources.
 .
 VLC can also be used as a streaming server that duplicates the stream it
 reads and multicasts them through the network to other clients, or serves
 them through HTTP.
 .
 VLC has support for on-the-fly transcoding of audio and video formats, either
 for broadcasting purposes or for movie format transformations. Support for
 most output methods is provided by this package, but features can be added
 by installing additional audio plugins (vlc-plugin-pulse, vlc-plugin-sdl)
 or video plugins (vlc-plugin-sdl, vlc-plugin-ggi, vlc-plugin-svgalib). There
 is also a web browser plugin in the mozilla-plugin-vlc package.

Package: vlc-data
Depends: ${misc:Depends}
Architecture: all
Replaces: mozilla-plugin-vlc (<< 0.9.2-1),
          vlc (<< 0.9.2-1),
          vlc-nox (<< 0.9.2-1)
Description: Common data for VLC
 Localisations, HTTP interface files, Lua scripts for VLC media player
 .
 VLC is the VideoLAN project's media player. It plays MPEG, MPEG2, MPEG4,
 DivX, MOV, WMV, QuickTime, mp3, Ogg/Vorbis files, DVDs, VCDs, and multimedia
 streams from various network sources.

Package: vlc-dbg
Section: debug
Priority: extra
Architecture: any
Depends: vlc-nox (= ${binary:Version}), ${misc:Depends}
Description: debugging symbols for vlc
 VLC is the VideoLAN project's media player. It plays MPEG, MPEG2, MPEG4,
 DivX, MOV, WMV, QuickTime, mp3, Ogg/Vorbis files, DVDs, VCDs, and multimedia
 streams from various network sources.
 .
 This package contains the debugging symbols for vlc.

Package: vlc-nox
Architecture: any
Depends: ${misc:Depends}, ${shlibs:Depends}
Replaces: vlc (<< 1.1.0)
Provides: mp3-decoder
Description: multimedia player and streamer (without X support)
 VLC is the VideoLAN project's media player. It plays MPEG, MPEG2, MPEG4,
 DivX, MOV, WMV, QuickTime, mp3, Ogg/Vorbis files, DVDs, VCDs, and multimedia
 streams from various network sources.
 .
 VLC can also be used as a streaming server that duplicates the stream it
 reads and multicasts them through the network to other clients, or serves
 them through HTTP.
 .
 VLC has support for on-the-fly transcoding of audio and video formats, either
 for broadcasting purposes or for movie format transformations. Support for
 most output methods is provided by this package, but features can be added
 by installing additional audio plugins (vlc-plugin-pulse, vlc-plugin-sdl,
 vlc-plugin-jack) or video plugins (vlc-plugin-sdl, vlc-plugin-ggi,
 vlc-plugin-svgalib). There is also a web browser plugin in  the
 mozilla-plugin-vlc package.
 .
 This package contains a version of VLC that does not require X and that is
 thus suitable for headless servers.

Package: vlc-plugin-fluidsynth
Architecture: any
Depends: vlc-nox (= ${binary:Version}), ${misc:Depends}, ${shlibs:Depends}
Description: FluidSynth plugin for VLC
 This plugin adds support for playing MIDI file via the FluidSynth software
 synthesizer to the VLC media player.
 .
 VLC is the VideoLAN project's media player. It plays MPEG, MPEG2, MPEG4,
 DivX, MOV, WMV, QuickTime, mp3, Ogg/Vorbis files, DVDs, VCDs, and multimedia
 streams from various network sources.

Package: vlc-plugin-ggi
Architecture: any
Depends: vlc-nox, ${misc:Depends}, ${shlibs:Depends}
Description: GGI video output plugin for VLC
 This is a GGI plugin for the VLC media player.  To activate it, use
 the `--vout ggi' flag or select the `ggi' video output plugin from the
 preferences menu.
 .
 VLC is the VideoLAN project's media player. It plays MPEG, MPEG2, MPEG4,
 DivX, MOV, WMV, QuickTime, mp3, Ogg/Vorbis files, DVDs, VCDs, and multimedia
 streams from various network sources.

Package: vlc-plugin-jack
Architecture: any
Depends: vlc-nox (= ${binary:Version}), ${misc:Depends}, ${shlibs:Depends}
Description: Jack audio plugins for VLC
 These plugins add support for JACK to the VLC media player. To
 activate the audio output module, use the `--aout jack' flag or
 select the `jack' audio output plugin from the preferences menu.
 For the jack input, use `vlc jack://channels=...:ports=...'
 .
 VLC is the VideoLAN project's media player. It plays MPEG, MPEG2, MPEG4,
 DivX, MOV, WMV, QuickTime, mp3, Ogg/Vorbis files, DVDs, VCDs, and multimedia
 streams from various network sources.

Package: vlc-plugin-notify
Architecture: any
Depends: vlc-nox (= ${binary:Version}), ${misc:Depends}, ${shlibs:Depends}
Breaks: vlc-nox (<< 1.1.2)
Replaces: vlc-nox (<< 1.1.2)
Description: LibNotify plugin for VLC
 This plugin adds support for libnotify track change notification to the
 VLC media player.
 .
 VLC is the VideoLAN project's media player. It plays MPEG, MPEG2, MPEG4,
 DivX, MOV, WMV, QuickTime, mp3, Ogg/Vorbis files, DVDs, VCDs, and multimedia
 streams from various network sources.

Package: vlc-plugin-pulse
Architecture: any
Depends: vlc-nox (= ${binary:Version}), ${misc:Depends}, ${shlibs:Depends}
Description: PulseAudio plugin for VLC
 This plugin adds support for PulseAudio to the VLC media player. To
 activate the audio output module, use the `--aout pulse' flag or
 select the `pulse' audio output plugin from the preferences menu.
 .
 VLC is the VideoLAN project's media player. It plays MPEG, MPEG2, MPEG4,
 DivX, MOV, WMV, QuickTime, mp3, Ogg/Vorbis files, DVDs, VCDs, and multimedia
 streams from various network sources.

Package: vlc-plugin-sdl
Architecture: any
Depends: vlc-nox, ${misc:Depends}, ${shlibs:Depends}
Description: SDL video and audio output plugin for VLC
 This plugin adds support for the Simple DirectMedia Layer library to
 the VLC media player. To activate it, use the `--vout sdl' or
 `--aout sdl' flags or select the `sdl' video or audio output plugin
 from the preferences menu.
 .
 VLC is the VideoLAN project's media player. It plays MPEG, MPEG2, MPEG4,
 DivX, MOV, WMV, QuickTime, mp3, Ogg/Vorbis files, DVDs, VCDs, and multimedia
 streams from various network sources.

Package: vlc-plugin-svg
Architecture: any
Depends: vlc-nox (= ${binary:Version}), ${misc:Depends}, ${shlibs:Depends}
Description: SVG plugin for VLC
 This plugin allows you to render SVG graphics on top of the video. It is a text
 renderer, and must be activated through the '--text-renderer svg' option. When
 sent non-SVG data, it will convert it to SVG using a template that can be
 specified by the svg-template-file option.
 .
 VLC is the VideoLAN project's media player. It plays MPEG, MPEG2, MPEG4,
 DivX, MOV, WMV, QuickTime, mp3, Ogg/Vorbis files, DVDs, VCDs, and multimedia
 streams from various network sources.

Package: vlc-plugin-svgalib
Architecture: amd64 i386
Depends: vlc-nox (= ${binary:Version}), ${misc:Depends}, ${shlibs:Depends}
Description: SVGAlib video output plugin for VLC
 This plugin adds support for SVGAlib to the VLC media player. To
 activate it, use the `--vout svgalib' flag or select the `svgalib' video
 output plugin from the preferences menu. Note that you will need root
 permissions to use SVGAlib.
 .
 VLC is the VideoLAN project's media player. It plays MPEG, MPEG2, MPEG4,
 DivX, MOV, WMV, QuickTime, mp3, Ogg/Vorbis files, DVDs, VCDs, and multimedia
 streams from various network sources.

Package: vlc-plugin-zvbi
Architecture: any
Depends: vlc-nox (= ${binary:Version}), ${misc:Depends}, ${shlibs:Depends}
Description: VBI teletext plugin for VLC
 This plugin adds support for VBI teletext to the VLC media player.
 .
 VLC is the VideoLAN project's media player. It plays MPEG, MPEG2, MPEG4,
 DivX, MOV, WMV, QuickTime, mp3, Ogg/Vorbis files, DVDs, VCDs, and multimedia
 streams from various network sources.
```[/CENTER]

How can I solve this problem ?

Thanks

---

### Post by MadCow108 on 2011-04-08
libdvbpsi-dev is not available for lucid.
but it seems to build fine:
```

#requires devscripts and equivs installed
dget -ux https://launchpad.net/ubuntu/+archive/primary/+files/libdvbpsi_0.1.7-1.dsc
cd libdvbpsi_0.1.7
sudo mk-build-dep -i -r
debuild -us -uc
ls -ltr ../*deb

```
install both debs and retry vlc build

---

