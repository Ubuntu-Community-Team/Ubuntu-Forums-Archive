---
title: "Compiling conky with xmms2 support = no dice"
date: 2011-04-16
forum: Packaging and Compiling Programs
---

### Post by Ranko Kohime on 2011-04-16
I'm attempting to compile conky with xmms2 support, but it's failing.  :(

configure appears to run ok, at least it doesn't give me any obvious errors, but here's the output just in case:

```
ranko@Greybox:~/Downloads/conky-1.8.1$ ./configure --prefix=/opt/conky --enable-xmms2 --disable-mpd --enable-curl
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
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
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
checking for /usr/bin/ld option to reload object files... -r
checking for objdump... objdump
checking how to recognize dependent libraries... pass_all
checking for ar... ar
checking for strip... strip
checking for ranlib... ranlib
checking command to parse /usr/bin/nm -B output from gcc object... ok
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
checking whether stripping libraries is possible... yes
checking if libtool supports shared libraries... yes
checking whether to build shared libraries... yes
checking whether to build static libraries... yes
checking whether gcc and cc understand -c and -o together... yes
checking for pkg-config... yes
checking for pkg-config... /usr/bin/pkg-config
checking pkg-config is at least version 0.19... yes
checking for fopencookie... yes
checking for funopen... no
checking for XMMS2... yes
checking for X11... yes
checking for LUA... no
checking for LUA51... no
checking for LUA51... yes
checking for getnameinfo... yes
checking netdb.h usability... yes
checking netdb.h presence... yes
checking for netdb.h... yes
checking netinet/in.h usability... yes
checking netinet/in.h presence... yes
checking for netinet/in.h... yes
checking netinet/tcp.h usability... yes
checking netinet/tcp.h presence... yes
checking for netinet/tcp.h... yes
checking sys/socket.h usability... yes
checking sys/socket.h presence... yes
checking for sys/socket.h... yes
checking arpa/inet.h usability... yes
checking arpa/inet.h presence... yes
checking for arpa/inet.h... yes
checking for ld used by GCC... /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... yes
checking for shared library run path origin... done
checking for iconv... yes
checking for working iconv... yes
checking for iconv declaration... 
         extern size_t iconv (iconv_t cd, char * *inbuf, size_t *inbytesleft, char * *outbuf, size_t *outbytesleft);
checking for Xext... yes
checking for XDamage... yes
checking for Xft... yes
checking for GLib2... yes
checking for libcurl... yes
checking alsa/asoundlib.h usability... yes
checking alsa/asoundlib.h presence... yes
checking for alsa/asoundlib.h... yes
checking for snd_pcm_open in -lasound... yes
checking signal.h usability... yes
checking signal.h presence... yes
checking for signal.h... yes
checking for unistd.h... (cached) yes
checking sys/utsname.h usability... yes
checking sys/utsname.h presence... yes
checking for sys/utsname.h... yes
checking for sys/stat.h... (cached) yes
checking linux/soundcard.h usability... yes
checking linux/soundcard.h presence... yes
checking for linux/soundcard.h... yes
checking for alsa/asoundlib.h... (cached) yes
checking dirent.h usability... yes
checking dirent.h presence... yes
checking for dirent.h... yes
checking mcheck.h usability... yes
checking mcheck.h presence... yes
checking for mcheck.h... yes
checking sys/statfs.h usability... yes
checking sys/statfs.h presence... yes
checking for sys/statfs.h... yes
checking sys/param.h usability... yes
checking sys/param.h presence... yes
checking for sys/param.h... yes
checking pthread.h usability... yes
checking pthread.h presence... yes
checking for pthread.h... yes
checking semaphore.h usability... yes
checking semaphore.h presence... yes
checking for semaphore.h... yes
checking assert.h usability... yes
checking assert.h presence... yes
checking for assert.h... yes
checking errno.h usability... yes
checking errno.h presence... yes
checking for errno.h... yes
checking time.h usability... yes
checking time.h presence... yes
checking for time.h... yes
checking for sys/mount.h... yes
checking sys/inotify.h usability... yes
checking sys/inotify.h presence... yes
checking for sys/inotify.h... yes
checking for calloc... yes
checking for malloc... yes
checking for free... yes
checking for popen... yes
checking for sysinfo... yes
checking for getloadavg... yes
checking for memrchr... yes
checking for strndup... yes
checking for gethostbyname_r... yes
checking for library containing clock_gettime... -lrt
checking for struct statfs.f_fstypename... no
checking zlib.h usability... yes
checking zlib.h presence... yes
checking for zlib.h... yes
checking for db2x_xsltproc... no
checking for db2x_manxml... no
checking for xsltproc... xsltproc
checking if /usr/bin/ld accepts -O1... yes
configure: creating ./config.status
config.status: creating Makefile
config.status: creating data/Makefile
config.status: creating doc/Makefile
config.status: creating src/Makefile
config.status: creating src/build.h
config.status: creating lua/Makefile
config.status: creating src/config.h
config.status: executing depfiles commands
config.status: executing libtool commands

conky 1.8.1 configured successfully:

 Installing into:   /opt/conky
 System config dir: ${prefix}/etc
 C compiler flags:   -I/usr/include/xmms2      -I/usr/include/lua5.1       -I/usr/include/freetype2   -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include     -Wall -W
 Libraries:          -lncurses -lm -lxmmsclient   -lX11    -llua5.1    -lXext   -lXdamage -lXfixes   -lXft   -lglib-2.0   -lcurl   -lasound -lrt 
 Linker flags:       -Wl,-O1

 * X11:
  X11 support:      yes
  XDamage support:  yes
  XDBE support:     yes
  Xft support:      yes
  ARGB support      yes

 * Music detection:
  Audacious:        no
  BMPx:             no
  MPD:              no
  MOC:              yes
  XMMS2:            yes

 * General:
  math:             yes
  hddtemp:          yes
  portmon:          yes
  RSS:              no
  Curl:             yes
  Weather
    METAR:          no
    XOAP:           no
  wireless:         no
  IBM:              no
  nvidia:           no
  eve-online:       no
  config-output:    yes
  Imlib2:           no
  ALSA mixer:       yes
  apcupsd:          yes
  I/O stats:        yes
  ncurses:          yes

 * Lua (yes) bindings:
  Cairo:            no
  Imlib2:           no
```
Compiling fails during make, exactly on the xmms2.c file.  Attempting to compile after configuring WITHOUT xmms2, results in a successful build.

Output of make:
```
ranko@Greybox:~/Downloads/conky-1.8.1$ make
Making all in src
make[1]: Entering directory `/home/ranko/Downloads/conky-1.8.1/src'
make  all-am
make[2]: Entering directory `/home/ranko/Downloads/conky-1.8.1/src'
gcc -DHAVE_CONFIG_H -I. -DSYSTEM_CONFIG_FILE=\"/opt/conky/etc/conky/conky.conf\" -DPACKAGE_LIBDIR=\"/opt/conky/lib/conky\"   -I/usr/include/xmms2      -I/usr/include/lua5.1       -I/usr/include/freetype2   -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include     -Wall -W  -MT conky-conf_cookie.o -MD -MP -MF .deps/conky-conf_cookie.Tpo -c -o conky-conf_cookie.o `test -f 'conf_cookie.c' || echo './'`conf_cookie.c
mv -f .deps/conky-conf_cookie.Tpo .deps/conky-conf_cookie.Po
gcc -DHAVE_CONFIG_H -I. -DSYSTEM_CONFIG_FILE=\"/opt/conky/etc/conky/conky.conf\" -DPACKAGE_LIBDIR=\"/opt/conky/lib/conky\"   -I/usr/include/xmms2      -I/usr/include/lua5.1       -I/usr/include/freetype2   -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include     -Wall -W  -MT conky-moc.o -MD -MP -MF .deps/conky-moc.Tpo -c -o conky-moc.o `test -f 'moc.c' || echo './'`moc.c
mv -f .deps/conky-moc.Tpo .deps/conky-moc.Po
gcc -DHAVE_CONFIG_H -I. -DSYSTEM_CONFIG_FILE=\"/opt/conky/etc/conky/conky.conf\" -DPACKAGE_LIBDIR=\"/opt/conky/lib/conky\"   -I/usr/include/xmms2      -I/usr/include/lua5.1       -I/usr/include/freetype2   -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include     -Wall -W  -MT conky-xmms2.o -MD -MP -MF .deps/conky-xmms2.Tpo -c -o conky-xmms2.o `test -f 'xmms2.c' || echo './'`xmms2.c
xmms2.c: In function ‘handle_playback_state_change’:
xmms2.c:226: error: ‘struct xmms2_s’ has no member named ‘percent’
make[2]: *** [conky-xmms2.o] Error 1
make[2]: Leaving directory `/home/ranko/Downloads/conky-1.8.1/src'
make[1]: *** [all] Error 2
make[1]: Leaving directory `/home/ranko/Downloads/conky-1.8.1/src'
make: *** [all-recursive] Error 1
```
And here's the specific part of xmms2.c where it's failing:

```
int handle_playback_state_change(xmmsv_t *value, void *p)
{
	struct information *ptr = p;
	int pb_state = 0;
	const char *errbuf;

	if (xmmsv_get_error(value, &errbuf)) {
		fprintf(stderr,"XMMS2 server error. %s\n", errbuf);
		return TRUE;
	}

	if (ptr->xmms2.status == NULL) {
		ptr->xmms2.status = malloc(text_buffer_size);
		ptr->xmms2.status[0] = '\0';
	}

	if (xmmsv_get_int(value, &pb_state)) {
		switch (pb_state) {
			case XMMS_PLAYBACK_STATUS_PLAY:
				strncpy(ptr->xmms2.status, "Playing", text_buffer_size - 1);
				break;
			case XMMS_PLAYBACK_STATUS_PAUSE:
				strncpy(ptr->xmms2.status, "Paused", text_buffer_size - 1);
				break;
			case XMMS_PLAYBACK_STATUS_STOP:
				strncpy(ptr->xmms2.status, "Stopped", text_buffer_size - 1);
				ptr->xmms2.elapsed = ptr->xmms2.progress = ptr->xmms2.percent = 0;
				break;
			default:
				strncpy(ptr->xmms2.status, "Unknown", text_buffer_size - 1);
		}
	}
	return TRUE;
}

```
Does anyone see the problem?  I can troubleshoot code slightly, but I'm nowhere near fluent in C, unfortunately.

---

### Post by SevenMachines on 2011-04-16
This has been fixed in conky git. You may just need to add
int percent;
to  struct xmms2_s in src/xmms2.h 
if that isnt enough have a look at the full [commit]("http://git.omp.am/?p=conky.git;a=commitdiff;h=c00e7b0a42c03a261dab38bcc89b8bd0adf7b394;hp=29f833ee05916b3ea58b3d81aa119638ddf946ba")

---

### Post by Ranko Kohime on 2011-04-16
> **SevenMachines said:**
> This has been fixed in conky git. You may just need to add
int percent;
to  struct xmms2_s in src/xmms2.h 
if that isnt enough have a look at the full [commit]("http://git.omp.am/?p=conky.git;a=commitdiff;h=c00e7b0a42c03a261dab38bcc89b8bd0adf7b394;hp=29f833ee05916b3ea58b3d81aa119638ddf946ba")
Yeah, no dice.  Not even with any of the .c and .h files from the git.  :(

```
ranko@Greybox:~/Downloads/conky-1.8.1$ make
Making all in src
make[1]: Entering directory `/home/ranko/Downloads/conky-1.8.1/src'
make  all-am
make[2]: Entering directory `/home/ranko/Downloads/conky-1.8.1/src'
gcc -DHAVE_CONFIG_H -I. -DSYSTEM_CONFIG_FILE=\"/opt/conky/etc/conky/conky.conf\" -DPACKAGE_LIBDIR=\"/opt/conky/lib/conky\"   -I/usr/include/xmms2      -I/usr/include/lua5.1       -I/usr/include/freetype2   -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include     -Wall -W  -MT conky-xmms2.o -MD -MP -MF .deps/conky-xmms2.Tpo -c -o conky-xmms2.o `test -f 'xmms2.c' || echo './'`xmms2.c
xmms2.c: In function ‘connection_lost’:
xmms2.c:90: error: ‘struct xmms2_s’ has no member named ‘conn_state’
xmms2.c: At top level:
xmms2.c:256: error: conflicting types for ‘update_xmms2’
xmms2.h:54: note: previous declaration of ‘update_xmms2’ was here
xmms2.c: In function ‘update_xmms2’:
xmms2.c:261: error: ‘struct xmms2_s’ has no member named ‘conn_state’
xmms2.c:274: error: ‘struct xmms2_s’ has no member named ‘conn_state’
xmms2.c:281: error: ‘struct xmms2_s’ has no member named ‘conn_state’
xmms2.c:287: error: ‘struct xmms2_s’ has no member named ‘conn_state’
xmms2.c:311: error: ‘struct xmms2_s’ has no member named ‘conn_state’
xmms2.c:315: error: ‘struct xmms2_s’ has no member named ‘conn_state’
make[2]: *** [conky-xmms2.o] Error 1
make[2]: Leaving directory `/home/ranko/Downloads/conky-1.8.1/src'
make[1]: *** [all] Error 2
make[1]: Leaving directory `/home/ranko/Downloads/conky-1.8.1/src'
make: *** [all-recursive] Error 1
```

---

### Post by Ranko Kohime on 2011-04-16
Correction: I apparently grabbed the wrong files from the git.  Now I can successfully compile, but conky crashes if any xmms2 commands are used in .conkyrc

Results of make:
```
ranko@Greybox:~/Downloads/conky-1.8.1$ make
Making all in src
make[1]: Entering directory `/home/ranko/Downloads/conky-1.8.1/src'
make  all-am
make[2]: Entering directory `/home/ranko/Downloads/conky-1.8.1/src'
gcc -DHAVE_CONFIG_H -I. -DSYSTEM_CONFIG_FILE=\"/usr/local/etc/conky/conky.conf\" -DPACKAGE_LIBDIR=\"/usr/local/lib/conky\"   -I/usr/include/xmms2      -I/usr/include/lua5.1       -I/usr/include/freetype2   -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include   -Wall -W  -MT conky-conf_cookie.o -MD -MP -MF .deps/conky-conf_cookie.Tpo -c -o conky-conf_cookie.o `test -f 'conf_cookie.c' || echo './'`conf_cookie.c
mv -f .deps/conky-conf_cookie.Tpo .deps/conky-conf_cookie.Po
gcc -DHAVE_CONFIG_H -I. -DSYSTEM_CONFIG_FILE=\"/usr/local/etc/conky/conky.conf\" -DPACKAGE_LIBDIR=\"/usr/local/lib/conky\"   -I/usr/include/xmms2      -I/usr/include/lua5.1       -I/usr/include/freetype2   -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include   -Wall -W  -MT conky-moc.o -MD -MP -MF .deps/conky-moc.Tpo -c -o conky-moc.o `test -f 'moc.c' || echo './'`moc.c
mv -f .deps/conky-moc.Tpo .deps/conky-moc.Po
gcc -DHAVE_CONFIG_H -I. -DSYSTEM_CONFIG_FILE=\"/usr/local/etc/conky/conky.conf\" -DPACKAGE_LIBDIR=\"/usr/local/lib/conky\"   -I/usr/include/xmms2      -I/usr/include/lua5.1       -I/usr/include/freetype2   -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include   -Wall -W  -MT conky-xmms2.o -MD -MP -MF .deps/conky-xmms2.Tpo -c -o conky-xmms2.o `test -f 'xmms2.c' || echo './'`xmms2.c
mv -f .deps/conky-xmms2.Tpo .deps/conky-xmms2.Po
gcc -DHAVE_CONFIG_H -I. -DSYSTEM_CONFIG_FILE=\"/usr/local/etc/conky/conky.conf\" -DPACKAGE_LIBDIR=\"/usr/local/lib/conky\"   -I/usr/include/xmms2      -I/usr/include/lua5.1       -I/usr/include/freetype2   -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include   -Wall -W  -MT conky-linux.o -MD -MP -MF .deps/conky-linux.Tpo -c -o conky-linux.o `test -f 'linux.c' || echo './'`linux.c
mv -f .deps/conky-linux.Tpo .deps/conky-linux.Po
gcc -DHAVE_CONFIG_H -I. -DSYSTEM_CONFIG_FILE=\"/usr/local/etc/conky/conky.conf\" -DPACKAGE_LIBDIR=\"/usr/local/lib/conky\"   -I/usr/include/xmms2      -I/usr/include/lua5.1       -I/usr/include/freetype2   -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include   -Wall -W  -MT conky-users.o -MD -MP -MF .deps/conky-users.Tpo -c -o conky-users.o `test -f 'users.c' || echo './'`users.c
mv -f .deps/conky-users.Tpo .deps/conky-users.Po
gcc -DHAVE_CONFIG_H -I. -DSYSTEM_CONFIG_FILE=\"/usr/local/etc/conky/conky.conf\" -DPACKAGE_LIBDIR=\"/usr/local/lib/conky\"   -I/usr/include/xmms2      -I/usr/include/lua5.1       -I/usr/include/freetype2   -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include   -Wall -W  -MT conky-sony.o -MD -MP -MF .deps/conky-sony.Tpo -c -o conky-sony.o `test -f 'sony.c' || echo './'`sony.c
mv -f .deps/conky-sony.Tpo .deps/conky-sony.Po
gcc -DHAVE_CONFIG_H -I. -DSYSTEM_CONFIG_FILE=\"/usr/local/etc/conky/conky.conf\" -DPACKAGE_LIBDIR=\"/usr/local/lib/conky\"   -I/usr/include/xmms2      -I/usr/include/lua5.1       -I/usr/include/freetype2   -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include   -Wall -W  -MT conky-i8k.o -MD -MP -MF .deps/conky-i8k.Tpo -c -o conky-i8k.o `test -f 'i8k.c' || echo './'`i8k.c
mv -f .deps/conky-i8k.Tpo .deps/conky-i8k.Po
gcc -DHAVE_CONFIG_H -I. -DSYSTEM_CONFIG_FILE=\"/usr/local/etc/conky/conky.conf\" -DPACKAGE_LIBDIR=\"/usr/local/lib/conky\"   -I/usr/include/xmms2      -I/usr/include/lua5.1       -I/usr/include/freetype2   -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include   -Wall -W  -MT conky-libtcp-portmon.o -MD -MP -MF .deps/conky-libtcp-portmon.Tpo -c -o conky-libtcp-portmon.o `test -f 'libtcp-portmon.c' || echo './'`libtcp-portmon.c
mv -f .deps/conky-libtcp-portmon.Tpo .deps/conky-libtcp-portmon.Po
gcc -DHAVE_CONFIG_H -I. -DSYSTEM_CONFIG_FILE=\"/usr/local/etc/conky/conky.conf\" -DPACKAGE_LIBDIR=\"/usr/local/lib/conky\"   -I/usr/include/xmms2      -I/usr/include/lua5.1       -I/usr/include/freetype2   -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include   -Wall -W  -MT conky-tcp-portmon.o -MD -MP -MF .deps/conky-tcp-portmon.Tpo -c -o conky-tcp-portmon.o `test -f 'tcp-portmon.c' || echo './'`tcp-portmon.c
mv -f .deps/conky-tcp-portmon.Tpo .deps/conky-tcp-portmon.Po
gcc -DHAVE_CONFIG_H -I. -DSYSTEM_CONFIG_FILE=\"/usr/local/etc/conky/conky.conf\" -DPACKAGE_LIBDIR=\"/usr/local/lib/conky\"   -I/usr/include/xmms2      -I/usr/include/lua5.1       -I/usr/include/freetype2   -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include   -Wall -W  -MT conky-x11.o -MD -MP -MF .deps/conky-x11.Tpo -c -o conky-x11.o `test -f 'x11.c' || echo './'`x11.c
mv -f .deps/conky-x11.Tpo .deps/conky-x11.Po
gcc -DHAVE_CONFIG_H -I. -DSYSTEM_CONFIG_FILE=\"/usr/local/etc/conky/conky.conf\" -DPACKAGE_LIBDIR=\"/usr/local/lib/conky\"   -I/usr/include/xmms2      -I/usr/include/lua5.1       -I/usr/include/freetype2   -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include   -Wall -W  -MT conky-fonts.o -MD -MP -MF .deps/conky-fonts.Tpo -c -o conky-fonts.o `test -f 'fonts.c' || echo './'`fonts.c
mv -f .deps/conky-fonts.Tpo .deps/conky-fonts.Po
gcc -DHAVE_CONFIG_H -I. -DSYSTEM_CONFIG_FILE=\"/usr/local/etc/conky/conky.conf\" -DPACKAGE_LIBDIR=\"/usr/local/lib/conky\"   -I/usr/include/xmms2      -I/usr/include/lua5.1       -I/usr/include/freetype2   -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include   -Wall -W  -MT conky-hddtemp.o -MD -MP -MF .deps/conky-hddtemp.Tpo -c -o conky-hddtemp.o `test -f 'hddtemp.c' || echo './'`hddtemp.c
mv -f .deps/conky-hddtemp.Tpo .deps/conky-hddtemp.Po
gcc -DHAVE_CONFIG_H -I. -DSYSTEM_CONFIG_FILE=\"/usr/local/etc/conky/conky.conf\" -DPACKAGE_LIBDIR=\"/usr/local/lib/conky\"   -I/usr/include/xmms2      -I/usr/include/lua5.1       -I/usr/include/freetype2   -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include   -Wall -W  -MT conky-llua.o -MD -MP -MF .deps/conky-llua.Tpo -c -o conky-llua.o `test -f 'llua.c' || echo './'`llua.c
llua.c:43: warning: "MIN" redefined
/usr/include/glib-2.0/glib/gmacros.h:201: note: this is the location of the previous definition
mv -f .deps/conky-llua.Tpo .deps/conky-llua.Po
gcc -DHAVE_CONFIG_H -I. -DSYSTEM_CONFIG_FILE=\"/usr/local/etc/conky/conky.conf\" -DPACKAGE_LIBDIR=\"/usr/local/lib/conky\"   -I/usr/include/xmms2      -I/usr/include/lua5.1       -I/usr/include/freetype2   -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include   -Wall -W  -MT conky-apcupsd.o -MD -MP -MF .deps/conky-apcupsd.Tpo -c -o conky-apcupsd.o `test -f 'apcupsd.c' || echo './'`apcupsd.c
mv -f .deps/conky-apcupsd.Tpo .deps/conky-apcupsd.Po
gcc -DHAVE_CONFIG_H -I. -DSYSTEM_CONFIG_FILE=\"/usr/local/etc/conky/conky.conf\" -DPACKAGE_LIBDIR=\"/usr/local/lib/conky\"   -I/usr/include/xmms2      -I/usr/include/lua5.1       -I/usr/include/freetype2   -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include   -Wall -W  -MT conky-iconv_tools.o -MD -MP -MF .deps/conky-iconv_tools.Tpo -c -o conky-iconv_tools.o `test -f 'iconv_tools.c' || echo './'`iconv_tools.c
mv -f .deps/conky-iconv_tools.Tpo .deps/conky-iconv_tools.Po
gcc -DHAVE_CONFIG_H -I. -DSYSTEM_CONFIG_FILE=\"/usr/local/etc/conky/conky.conf\" -DPACKAGE_LIBDIR=\"/usr/local/lib/conky\"   -I/usr/include/xmms2      -I/usr/include/lua5.1       -I/usr/include/freetype2   -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include   -Wall -W  -MT conky-colours.o -MD -MP -MF .deps/conky-colours.Tpo -c -o conky-colours.o `test -f 'colours.c' || echo './'`colours.c
mv -f .deps/conky-colours.Tpo .deps/conky-colours.Po
gcc -DHAVE_CONFIG_H -I. -DSYSTEM_CONFIG_FILE=\"/usr/local/etc/conky/conky.conf\" -DPACKAGE_LIBDIR=\"/usr/local/lib/conky\"   -I/usr/include/xmms2      -I/usr/include/lua5.1       -I/usr/include/freetype2   -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include   -Wall -W  -MT conky-combine.o -MD -MP -MF .deps/conky-combine.Tpo -c -o conky-combine.o `test -f 'combine.c' || echo './'`combine.c
mv -f .deps/conky-combine.Tpo .deps/conky-combine.Po
gcc -DHAVE_CONFIG_H -I. -DSYSTEM_CONFIG_FILE=\"/usr/local/etc/conky/conky.conf\" -DPACKAGE_LIBDIR=\"/usr/local/lib/conky\"   -I/usr/include/xmms2      -I/usr/include/lua5.1       -I/usr/include/freetype2   -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include   -Wall -W  -MT conky-common.o -MD -MP -MF .deps/conky-common.Tpo -c -o conky-common.o `test -f 'common.c' || echo './'`common.c
mv -f .deps/conky-common.Tpo .deps/conky-common.Po
gcc -DHAVE_CONFIG_H -I. -DSYSTEM_CONFIG_FILE=\"/usr/local/etc/conky/conky.conf\" -DPACKAGE_LIBDIR=\"/usr/local/lib/conky\"   -I/usr/include/xmms2      -I/usr/include/lua5.1       -I/usr/include/freetype2   -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include   -Wall -W  -MT conky-conky.o -MD -MP -MF .deps/conky-conky.Tpo -c -o conky-conky.o `test -f 'conky.c' || echo './'`conky.c
mv -f .deps/conky-conky.Tpo .deps/conky-conky.Po
gcc -DHAVE_CONFIG_H -I. -DSYSTEM_CONFIG_FILE=\"/usr/local/etc/conky/conky.conf\" -DPACKAGE_LIBDIR=\"/usr/local/lib/conky\"   -I/usr/include/xmms2      -I/usr/include/lua5.1       -I/usr/include/freetype2   -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include   -Wall -W  -MT conky-core.o -MD -MP -MF .deps/conky-core.Tpo -c -o conky-core.o `test -f 'core.c' || echo './'`core.c
core.c: In function ‘construct_text_object’:
core.c:955: warning: passing argument 1 of ‘add_update_callback’ from incompatible pointer type
common.h:14: note: expected ‘int (*)(void)’ but argument is of type ‘void (*)(void)’
core.c:956: warning: passing argument 1 of ‘add_update_callback’ from incompatible pointer type
common.h:14: note: expected ‘int (*)(void)’ but argument is of type ‘void (*)(void)’
core.c:957: warning: passing argument 1 of ‘add_update_callback’ from incompatible pointer type
common.h:14: note: expected ‘int (*)(void)’ but argument is of type ‘void (*)(void)’
core.c:958: warning: passing argument 1 of ‘add_update_callback’ from incompatible pointer type
common.h:14: note: expected ‘int (*)(void)’ but argument is of type ‘void (*)(void)’
core.c:959: warning: passing argument 1 of ‘add_update_callback’ from incompatible pointer type
common.h:14: note: expected ‘int (*)(void)’ but argument is of type ‘void (*)(void)’
core.c:960: warning: passing argument 1 of ‘add_update_callback’ from incompatible pointer type
common.h:14: note: expected ‘int (*)(void)’ but argument is of type ‘void (*)(void)’
core.c:961: warning: passing argument 1 of ‘add_update_callback’ from incompatible pointer type
common.h:14: note: expected ‘int (*)(void)’ but argument is of type ‘void (*)(void)’
core.c:962: warning: passing argument 1 of ‘add_update_callback’ from incompatible pointer type
common.h:14: note: expected ‘int (*)(void)’ but argument is of type ‘void (*)(void)’
core.c:963: warning: passing argument 1 of ‘add_update_callback’ from incompatible pointer type
common.h:14: note: expected ‘int (*)(void)’ but argument is of type ‘void (*)(void)’
core.c:964: warning: passing argument 1 of ‘add_update_callback’ from incompatible pointer type
common.h:14: note: expected ‘int (*)(void)’ but argument is of type ‘void (*)(void)’
core.c:965: warning: passing argument 1 of ‘add_update_callback’ from incompatible pointer type
common.h:14: note: expected ‘int (*)(void)’ but argument is of type ‘void (*)(void)’
core.c:966: warning: passing argument 1 of ‘add_update_callback’ from incompatible pointer type
common.h:14: note: expected ‘int (*)(void)’ but argument is of type ‘void (*)(void)’
core.c:967: warning: passing argument 1 of ‘add_update_callback’ from incompatible pointer type
common.h:14: note: expected ‘int (*)(void)’ but argument is of type ‘void (*)(void)’
core.c:968: warning: passing argument 1 of ‘add_update_callback’ from incompatible pointer type
common.h:14: note: expected ‘int (*)(void)’ but argument is of type ‘void (*)(void)’
core.c:969: warning: passing argument 1 of ‘add_update_callback’ from incompatible pointer type
common.h:14: note: expected ‘int (*)(void)’ but argument is of type ‘void (*)(void)’
core.c:970: warning: passing argument 1 of ‘add_update_callback’ from incompatible pointer type
common.h:14: note: expected ‘int (*)(void)’ but argument is of type ‘void (*)(void)’
core.c:972: warning: passing argument 1 of ‘add_update_callback’ from incompatible pointer type
common.h:14: note: expected ‘int (*)(void)’ but argument is of type ‘void (*)(void)’
core.c:973: warning: passing argument 1 of ‘add_update_callback’ from incompatible pointer type
common.h:14: note: expected ‘int (*)(void)’ but argument is of type ‘void (*)(void)’
core.c:974: warning: passing argument 1 of ‘add_update_callback’ from incompatible pointer type
common.h:14: note: expected ‘int (*)(void)’ but argument is of type ‘void (*)(void)’
core.c:975: warning: passing argument 1 of ‘add_update_callback’ from incompatible pointer type
common.h:14: note: expected ‘int (*)(void)’ but argument is of type ‘void (*)(void)’
mv -f .deps/conky-core.Tpo .deps/conky-core.Po
gcc -DHAVE_CONFIG_H -I. -DSYSTEM_CONFIG_FILE=\"/usr/local/etc/conky/conky.conf\" -DPACKAGE_LIBDIR=\"/usr/local/lib/conky\"   -I/usr/include/xmms2      -I/usr/include/lua5.1       -I/usr/include/freetype2   -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include   -Wall -W  -MT conky-diskio.o -MD -MP -MF .deps/conky-diskio.Tpo -c -o conky-diskio.o `test -f 'diskio.c' || echo './'`diskio.c
mv -f .deps/conky-diskio.Tpo .deps/conky-diskio.Po
gcc -DHAVE_CONFIG_H -I. -DSYSTEM_CONFIG_FILE=\"/usr/local/etc/conky/conky.conf\" -DPACKAGE_LIBDIR=\"/usr/local/lib/conky\"   -I/usr/include/xmms2      -I/usr/include/lua5.1       -I/usr/include/freetype2   -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include   -Wall -W  -MT conky-entropy.o -MD -MP -MF .deps/conky-entropy.Tpo -c -o conky-entropy.o `test -f 'entropy.c' || echo './'`entropy.c
mv -f .deps/conky-entropy.Tpo .deps/conky-entropy.Po
gcc -DHAVE_CONFIG_H -I. -DSYSTEM_CONFIG_FILE=\"/usr/local/etc/conky/conky.conf\" -DPACKAGE_LIBDIR=\"/usr/local/lib/conky\"   -I/usr/include/xmms2      -I/usr/include/lua5.1       -I/usr/include/freetype2   -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include   -Wall -W  -MT conky-exec.o -MD -MP -MF .deps/conky-exec.Tpo -c -o conky-exec.o `test -f 'exec.c' || echo './'`exec.c
mv -f .deps/conky-exec.Tpo .deps/conky-exec.Po
gcc -DHAVE_CONFIG_H -I. -DSYSTEM_CONFIG_FILE=\"/usr/local/etc/conky/conky.conf\" -DPACKAGE_LIBDIR=\"/usr/local/lib/conky\"   -I/usr/include/xmms2      -I/usr/include/lua5.1       -I/usr/include/freetype2   -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include   -Wall -W  -MT conky-fs.o -MD -MP -MF .deps/conky-fs.Tpo -c -o conky-fs.o `test -f 'fs.c' || echo './'`fs.c
mv -f .deps/conky-fs.Tpo .deps/conky-fs.Po
gcc -DHAVE_CONFIG_H -I. -DSYSTEM_CONFIG_FILE=\"/usr/local/etc/conky/conky.conf\" -DPACKAGE_LIBDIR=\"/usr/local/lib/conky\"   -I/usr/include/xmms2      -I/usr/include/lua5.1       -I/usr/include/freetype2   -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include   -Wall -W  -MT conky-mail.o -MD -MP -MF .deps/conky-mail.Tpo -c -o conky-mail.o `test -f 'mail.c' || echo './'`mail.c
mv -f .deps/conky-mail.Tpo .deps/conky-mail.Po
gcc -DHAVE_CONFIG_H -I. -DSYSTEM_CONFIG_FILE=\"/usr/local/etc/conky/conky.conf\" -DPACKAGE_LIBDIR=\"/usr/local/lib/conky\"   -I/usr/include/xmms2      -I/usr/include/lua5.1       -I/usr/include/freetype2   -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include   -Wall -W  -MT conky-mixer.o -MD -MP -MF .deps/conky-mixer.Tpo -c -o conky-mixer.o `test -f 'mixer.c' || echo './'`mixer.c
mv -f .deps/conky-mixer.Tpo .deps/conky-mixer.Po
gcc -DHAVE_CONFIG_H -I. -DSYSTEM_CONFIG_FILE=\"/usr/local/etc/conky/conky.conf\" -DPACKAGE_LIBDIR=\"/usr/local/lib/conky\"   -I/usr/include/xmms2      -I/usr/include/lua5.1       -I/usr/include/freetype2   -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include   -Wall -W  -MT conky-net_stat.o -MD -MP -MF .deps/conky-net_stat.Tpo -c -o conky-net_stat.o `test -f 'net_stat.c' || echo './'`net_stat.c
mv -f .deps/conky-net_stat.Tpo .deps/conky-net_stat.Po
gcc -DHAVE_CONFIG_H -I. -DSYSTEM_CONFIG_FILE=\"/usr/local/etc/conky/conky.conf\" -DPACKAGE_LIBDIR=\"/usr/local/lib/conky\"   -I/usr/include/xmms2      -I/usr/include/lua5.1       -I/usr/include/freetype2   -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include   -Wall -W  -MT conky-template.o -MD -MP -MF .deps/conky-template.Tpo -c -o conky-template.o `test -f 'template.c' || echo './'`template.c
mv -f .deps/conky-template.Tpo .deps/conky-template.Po
gcc -DHAVE_CONFIG_H -I. -DSYSTEM_CONFIG_FILE=\"/usr/local/etc/conky/conky.conf\" -DPACKAGE_LIBDIR=\"/usr/local/lib/conky\"   -I/usr/include/xmms2      -I/usr/include/lua5.1       -I/usr/include/freetype2   -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include   -Wall -W  -MT conky-timed_thread.o -MD -MP -MF .deps/conky-timed_thread.Tpo -c -o conky-timed_thread.o `test -f 'timed_thread.c' || echo './'`timed_thread.c
mv -f .deps/conky-timed_thread.Tpo .deps/conky-timed_thread.Po
gcc -DHAVE_CONFIG_H -I. -DSYSTEM_CONFIG_FILE=\"/usr/local/etc/conky/conky.conf\" -DPACKAGE_LIBDIR=\"/usr/local/lib/conky\"   -I/usr/include/xmms2      -I/usr/include/lua5.1       -I/usr/include/freetype2   -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include   -Wall -W  -MT conky-mboxscan.o -MD -MP -MF .deps/conky-mboxscan.Tpo -c -o conky-mboxscan.o `test -f 'mboxscan.c' || echo './'`mboxscan.c
mv -f .deps/conky-mboxscan.Tpo .deps/conky-mboxscan.Po
gcc -DHAVE_CONFIG_H -I. -DSYSTEM_CONFIG_FILE=\"/usr/local/etc/conky/conky.conf\" -DPACKAGE_LIBDIR=\"/usr/local/lib/conky\"   -I/usr/include/xmms2      -I/usr/include/lua5.1       -I/usr/include/freetype2   -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include   -Wall -W  -MT conky-read_tcp.o -MD -MP -MF .deps/conky-read_tcp.Tpo -c -o conky-read_tcp.o `test -f 'read_tcp.c' || echo './'`read_tcp.c
mv -f .deps/conky-read_tcp.Tpo .deps/conky-read_tcp.Po
gcc -DHAVE_CONFIG_H -I. -DSYSTEM_CONFIG_FILE=\"/usr/local/etc/conky/conky.conf\" -DPACKAGE_LIBDIR=\"/usr/local/lib/conky\"   -I/usr/include/xmms2      -I/usr/include/lua5.1       -I/usr/include/freetype2   -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include   -Wall -W  -MT conky-scroll.o -MD -MP -MF .deps/conky-scroll.Tpo -c -o conky-scroll.o `test -f 'scroll.c' || echo './'`scroll.c
mv -f .deps/conky-scroll.Tpo .deps/conky-scroll.Po
gcc -DHAVE_CONFIG_H -I. -DSYSTEM_CONFIG_FILE=\"/usr/local/etc/conky/conky.conf\" -DPACKAGE_LIBDIR=\"/usr/local/lib/conky\"   -I/usr/include/xmms2      -I/usr/include/lua5.1       -I/usr/include/freetype2   -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include   -Wall -W  -MT conky-specials.o -MD -MP -MF .deps/conky-specials.Tpo -c -o conky-specials.o `test -f 'specials.c' || echo './'`specials.c
specials.c: In function ‘scan_graph’:
specials.c:222: warning: suggest parentheses around assignment used as truth value
mv -f .deps/conky-specials.Tpo .deps/conky-specials.Po
gcc -DHAVE_CONFIG_H -I. -DSYSTEM_CONFIG_FILE=\"/usr/local/etc/conky/conky.conf\" -DPACKAGE_LIBDIR=\"/usr/local/lib/conky\"   -I/usr/include/xmms2      -I/usr/include/lua5.1       -I/usr/include/freetype2   -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include   -Wall -W  -MT conky-tailhead.o -MD -MP -MF .deps/conky-tailhead.Tpo -c -o conky-tailhead.o `test -f 'tailhead.c' || echo './'`tailhead.c
mv -f .deps/conky-tailhead.Tpo .deps/conky-tailhead.Po
gcc -DHAVE_CONFIG_H -I. -DSYSTEM_CONFIG_FILE=\"/usr/local/etc/conky/conky.conf\" -DPACKAGE_LIBDIR=\"/usr/local/lib/conky\"   -I/usr/include/xmms2      -I/usr/include/lua5.1       -I/usr/include/freetype2   -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include   -Wall -W  -MT conky-temphelper.o -MD -MP -MF .deps/conky-temphelper.Tpo -c -o conky-temphelper.o `test -f 'temphelper.c' || echo './'`temphelper.c
mv -f .deps/conky-temphelper.Tpo .deps/conky-temphelper.Po
gcc -DHAVE_CONFIG_H -I. -DSYSTEM_CONFIG_FILE=\"/usr/local/etc/conky/conky.conf\" -DPACKAGE_LIBDIR=\"/usr/local/lib/conky\"   -I/usr/include/xmms2      -I/usr/include/lua5.1       -I/usr/include/freetype2   -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include   -Wall -W  -MT conky-text_object.o -MD -MP -MF .deps/conky-text_object.Tpo -c -o conky-text_object.o `test -f 'text_object.c' || echo './'`text_object.c
mv -f .deps/conky-text_object.Tpo .deps/conky-text_object.Po
gcc -DHAVE_CONFIG_H -I. -DSYSTEM_CONFIG_FILE=\"/usr/local/etc/conky/conky.conf\" -DPACKAGE_LIBDIR=\"/usr/local/lib/conky\"   -I/usr/include/xmms2      -I/usr/include/lua5.1       -I/usr/include/freetype2   -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include   -Wall -W  -MT conky-timeinfo.o -MD -MP -MF .deps/conky-timeinfo.Tpo -c -o conky-timeinfo.o `test -f 'timeinfo.c' || echo './'`timeinfo.c
mv -f .deps/conky-timeinfo.Tpo .deps/conky-timeinfo.Po
gcc -DHAVE_CONFIG_H -I. -DSYSTEM_CONFIG_FILE=\"/usr/local/etc/conky/conky.conf\" -DPACKAGE_LIBDIR=\"/usr/local/lib/conky\"   -I/usr/include/xmms2      -I/usr/include/lua5.1       -I/usr/include/freetype2   -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include   -Wall -W  -MT conky-algebra.o -MD -MP -MF .deps/conky-algebra.Tpo -c -o conky-algebra.o `test -f 'algebra.c' || echo './'`algebra.c
mv -f .deps/conky-algebra.Tpo .deps/conky-algebra.Po
gcc -DHAVE_CONFIG_H -I. -DSYSTEM_CONFIG_FILE=\"/usr/local/etc/conky/conky.conf\" -DPACKAGE_LIBDIR=\"/usr/local/lib/conky\"   -I/usr/include/xmms2      -I/usr/include/lua5.1       -I/usr/include/freetype2   -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include   -Wall -W  -MT conky-proc.o -MD -MP -MF .deps/conky-proc.Tpo -c -o conky-proc.o `test -f 'proc.c' || echo './'`proc.c
mv -f .deps/conky-proc.Tpo .deps/conky-proc.Po
gcc -DHAVE_CONFIG_H -I. -DSYSTEM_CONFIG_FILE=\"/usr/local/etc/conky/conky.conf\" -DPACKAGE_LIBDIR=\"/usr/local/lib/conky\"   -I/usr/include/xmms2      -I/usr/include/lua5.1       -I/usr/include/freetype2   -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include   -Wall -W  -MT conky-user.o -MD -MP -MF .deps/conky-user.Tpo -c -o conky-user.o `test -f 'user.c' || echo './'`user.c
mv -f .deps/conky-user.Tpo .deps/conky-user.Po
gcc -DHAVE_CONFIG_H -I. -DSYSTEM_CONFIG_FILE=\"/usr/local/etc/conky/conky.conf\" -DPACKAGE_LIBDIR=\"/usr/local/lib/conky\"   -I/usr/include/xmms2      -I/usr/include/lua5.1       -I/usr/include/freetype2   -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include   -Wall -W  -MT conky-top.o -MD -MP -MF .deps/conky-top.Tpo -c -o conky-top.o `test -f 'top.c' || echo './'`top.c
mv -f .deps/conky-top.Tpo .deps/conky-top.Po
/bin/bash ../libtool --tag=CC   --mode=link gcc -I/usr/include/xmms2      -I/usr/include/lua5.1       -I/usr/include/freetype2   -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include   -Wall -W  -lpthread -lm  -o conky  conky-conf_cookie.o     conky-moc.o conky-xmms2.o conky-linux.o conky-users.o conky-sony.o conky-i8k.o   conky-libtcp-portmon.o conky-tcp-portmon.o conky-x11.o conky-fonts.o conky-hddtemp.o     conky-llua.o   conky-apcupsd.o conky-iconv_tools.o conky-colours.o conky-combine.o conky-common.o conky-conky.o conky-core.o conky-diskio.o conky-entropy.o conky-exec.o conky-fs.o conky-mail.o conky-mixer.o conky-net_stat.o conky-template.o conky-timed_thread.o conky-mboxscan.o conky-read_tcp.o conky-scroll.o conky-specials.o conky-tailhead.o conky-temphelper.o conky-text_object.o conky-timeinfo.o conky-algebra.o conky-proc.o conky-user.o conky-top.o  -lncurses -lm -lxmmsclient   -lX11    -llua5.1    -lXext   -lXdamage -lXfixes   -lXft   -lglib-2.0   -lasound -lrt 
libtool: link: gcc -I/usr/include/xmms2 -I/usr/include/lua5.1 -I/usr/include/freetype2 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -Wall -W -o conky conky-conf_cookie.o conky-moc.o conky-xmms2.o conky-linux.o conky-users.o conky-sony.o conky-i8k.o conky-libtcp-portmon.o conky-tcp-portmon.o conky-x11.o conky-fonts.o conky-hddtemp.o conky-llua.o conky-apcupsd.o conky-iconv_tools.o conky-colours.o conky-combine.o conky-common.o conky-conky.o conky-core.o conky-diskio.o conky-entropy.o conky-exec.o conky-fs.o conky-mail.o conky-mixer.o conky-net_stat.o conky-template.o conky-timed_thread.o conky-mboxscan.o conky-read_tcp.o conky-scroll.o conky-specials.o conky-tailhead.o conky-temphelper.o conky-text_object.o conky-timeinfo.o conky-algebra.o conky-proc.o conky-user.o conky-top.o  -lpthread -lncurses -lm -lxmmsclient -lX11 /usr/lib/liblua5.1.so -lXext -lXdamage -lXfixes -lXft /usr/lib/libglib-2.0.so /usr/lib/libasound.so -lrt
make[2]: Leaving directory `/home/ranko/Downloads/conky-1.8.1/src'
make[1]: Leaving directory `/home/ranko/Downloads/conky-1.8.1/src'
Making all in doc
make[1]: Entering directory `/home/ranko/Downloads/conky-1.8.1/doc'
make[1]: Nothing to be done for `all'.
make[1]: Leaving directory `/home/ranko/Downloads/conky-1.8.1/doc'
Making all in lua
make[1]: Entering directory `/home/ranko/Downloads/conky-1.8.1/lua'
make  all-am
make[2]: Entering directory `/home/ranko/Downloads/conky-1.8.1/lua'
make[2]: Nothing to be done for `all-am'.
make[2]: Leaving directory `/home/ranko/Downloads/conky-1.8.1/lua'
make[1]: Leaving directory `/home/ranko/Downloads/conky-1.8.1/lua'
Making all in data
make[1]: Entering directory `/home/ranko/Downloads/conky-1.8.1/data'
make[1]: Nothing to be done for `all'.
make[1]: Leaving directory `/home/ranko/Downloads/conky-1.8.1/data'
make[1]: Entering directory `/home/ranko/Downloads/conky-1.8.1'
make[1]: Nothing to be done for `all-am'.
make[1]: Leaving directory `/home/ranko/Downloads/conky-1.8.1'
```
Conky leaves no error messages in the terminal when started, when started in a window, the window flashes up for half a second, then disappears.  Conky does not then continue to run.

```
ranko@Greybox:~/Downloads/conky-1.8.1$ conky -o
Conky: forked to background, pid is 10755
Conky: desktop window (11b) is root window
Conky: window type - normal
Conky: drawing to created window (0x1600001)
Conky: drawing to double buffer
```
At that point, conky has exited.  I'm stumped.  :(

---

