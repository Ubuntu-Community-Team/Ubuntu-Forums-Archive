---
title: "Compiling emacs 22.2 with gtk from source"
date: 2008-04-25
forum: Packaging and Compiling Programs
---

### Post by bluehue on 2008-04-25
Hello everyone,

I need some help compiling the latest version of emacs (22.2) with gtk so that I may run emacs with attractive menus, scrollbars, and so forth. The version of emacs22-gtk on the repositories is 22.1 and I would very much prefer installing the latest and greatest instead. Here was my attempt:
```

spiral@spiral-desktop:~/Desktop/emacs-22.2$ ./configure --with-x-toolkit=gtk --with-pkg-config-prog=/usr/bin/pkg-config
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables... 
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ISO C89... none needed
checking how to run the C preprocessor... gcc -E
checking for grep that handles long lines and -e... /bin/grep
checking for egrep... /bin/grep -E
checking for AIX... no
checking whether gcc understands -Wno-pointer-sign... yes
checking whether ln -s works... yes
checking how to run the C preprocessor... gcc -E
checking for a BSD-compatible install... /usr/bin/install -c
checking for ranlib... ranlib
checking for install-info... /usr/sbin/install-info
checking for install-info... (cached) /usr/sbin/install-info
checking for install-info... (cached) /usr/sbin/install-info
checking for gzip... /bin/gzip
checking for -znocombreloc... yes
configure: checking the machine- and system-dependent files to find out
 - which libraries the lib-src programs will want, and
 - whether the GNU malloc routines are usable...
checking for special C compiler options needed for large files... no
checking for _FILE_OFFSET_BITS value needed for large files... 64
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
checking machine/soundcard.h usability... no
checking machine/soundcard.h presence... no
checking for machine/soundcard.h... no
checking sys/soundcard.h usability... yes
checking sys/soundcard.h presence... yes
checking for sys/soundcard.h... yes
checking soundcard.h usability... no
checking soundcard.h presence... no
checking for soundcard.h... no
checking for _oss_ioctl in -lossaudio... no
checking for alsa >= 1.0.0... no
checking sys/select.h usability... yes
checking sys/select.h presence... yes
checking for sys/select.h... yes
checking sys/timeb.h usability... yes
checking sys/timeb.h presence... yes
checking for sys/timeb.h... yes
checking sys/time.h usability... yes
checking sys/time.h presence... yes
checking for sys/time.h... yes
checking for unistd.h... (cached) yes
checking utime.h usability... yes
checking utime.h presence... yes
checking for utime.h... yes
checking linux/version.h usability... yes
checking linux/version.h presence... yes
checking for linux/version.h... yes
checking sys/systeminfo.h usability... no
checking sys/systeminfo.h presence... no
checking for sys/systeminfo.h... no
checking termios.h usability... yes
checking termios.h presence... yes
checking for termios.h... yes
checking limits.h usability... yes
checking limits.h presence... yes
checking for limits.h... yes
checking for string.h... (cached) yes
checking for stdlib.h... (cached) yes
checking termcap.h usability... no
checking termcap.h presence... no
checking for termcap.h... no
checking stdio_ext.h usability... yes
checking stdio_ext.h presence... yes
checking for stdio_ext.h... yes
checking fcntl.h usability... yes
checking fcntl.h presence... yes
checking for fcntl.h... yes
checking for strings.h... (cached) yes
checking coff.h usability... no
checking coff.h presence... no
checking for coff.h... no
checking pty.h usability... yes
checking pty.h presence... yes
checking for pty.h... yes
checking sys/mman.h usability... yes
checking sys/mman.h presence... yes
checking for sys/mman.h... yes
checking sys/param.h usability... yes
checking sys/param.h presence... yes
checking for sys/param.h... yes
checking sys/vlimit.h usability... yes
checking sys/vlimit.h presence... yes
checking for sys/vlimit.h... yes
checking sys/resource.h usability... yes
checking sys/resource.h presence... yes
checking for sys/resource.h... yes
checking locale.h usability... yes
checking locale.h presence... yes
checking for locale.h... yes
checking sys/_mbstate_t.h usability... no
checking sys/_mbstate_t.h presence... no
checking for sys/_mbstate_t.h... no
checking sys/utsname.h usability... yes
checking sys/utsname.h presence... yes
checking for sys/utsname.h... yes
checking pwd.h usability... yes
checking pwd.h presence... yes
checking for pwd.h... yes
checking if personality LINUX32 can be set... yes
checking for term.h... no
checking for ANSI C header files... (cached) yes
checking whether time.h and sys/time.h may both be included... yes
checking whether sys_siglist is declared... no
checking whether __sys_siglist is declared... no
checking for sys/wait.h that is POSIX.1 compatible... yes
checking for struct utimbuf... yes
checking return type of signal handlers... void
checking for speed_t... yes
checking for struct timeval... yes
checking for struct exception... yes
checking sys/socket.h usability... yes
checking sys/socket.h presence... yes
checking for sys/socket.h... yes
checking for net/if.h... yes
checking whether struct tm is in sys/time.h or time.h... time.h
checking for struct tm.tm_zone... yes
checking for struct tm.tm_gmtoff... yes
checking for struct ifreq.ifr_flags... yes
checking for struct ifreq.ifr_hwaddr... yes
checking for struct ifreq.ifr_netmask... yes
checking for struct ifreq.ifr_broadaddr... yes
checking for struct ifreq.ifr_addr... yes
checking for function prototypes... yes
checking for working volatile... yes
checking for an ANSI C-conforming const... yes
checking for void * support... yes
checking whether make sets $(MAKE)... yes
checking for long file names... yes
checking for X... no
checking Carbon/Carbon.h usability... no
checking Carbon/Carbon.h presence... no
checking for Carbon/Carbon.h... no
checking for malloc_get_state... yes
checking for malloc_set_state... yes
checking whether __after_morecore_hook exists... yes
checking for stdlib.h... (cached) yes
checking for unistd.h... (cached) yes
checking for getpagesize... yes
checking for working mmap... yes
checking for dnet_ntoa in -ldnet... no
checking for main in -lXbsd... no
checking for cma_open in -lpthreads... no
checking for XFree86 in /usr/X386... no
checking malloc/malloc.h usability... no
checking malloc/malloc.h presence... no
checking for malloc/malloc.h... no
checking whether netdb declares h_errno... yes
checking for working alloca.h... yes
checking for alloca... yes
checking for sqrt in -lm... yes
checking for maillock in -lmail... no
checking for maillock in -llockfile... no
checking for liblockfile.so... no
checking for touchlock... no
checking maillock.h usability... no
checking maillock.h presence... no
checking for maillock.h... no
checking for gethostname... yes
checking for getdomainname... yes
checking for dup2... yes
checking for rename... yes
checking for closedir... yes
checking for mkdir... yes
checking for rmdir... yes
checking for sysinfo... yes
checking for getrusage... yes
checking for get_current_dir_name... yes
checking for random... yes
checking for lrand48... yes
checking for bcopy... yes
checking for bcmp... yes
checking for logb... yes
checking for frexp... yes
checking for fmod... yes
checking for rint... yes
checking for cbrt... yes
checking for ftime... yes
checking for res_init... no
checking for setsid... yes
checking for strerror... yes
checking for fpathconf... yes
checking for select... yes
checking for mktime... yes
checking for euidaccess... yes
checking for getpagesize... (cached) yes
checking for tzset... yes
checking for setlocale... yes
checking for utimes... yes
checking for setrlimit... yes
checking for setpgid... yes
checking for getcwd... yes
checking for getwd... yes
checking for shutdown... yes
checking for getaddrinfo... yes
checking for __fpending... yes
checking for mblen... yes
checking for mbrlen... yes
checking for mbsinit... yes
checking for strsignal... yes
checking for setitimer... yes
checking for ualarm... yes
checking for index... yes
checking for rindex... yes
checking for sendto... yes
checking for recvfrom... yes
checking for getsockopt... yes
checking for setsockopt... yes
checking for getsockname... yes
checking for getpeername... yes
checking for gai_strerror... yes
checking for mkstemp... yes
checking for getline... yes
checking for getdelim... yes
checking for mremap... yes
checking for memmove... yes
checking for fsync... yes
checking for sync... yes
checking for bzero... yes
checking for memset... yes
checking for memcmp... yes
checking for difftime... yes
checking for memcpy... yes
checking for mempcpy... yes
checking for mblen... (cached) yes
checking for mbrlen... (cached) yes
checking for posix_memalign... yes
checking sys/un.h usability... yes
checking sys/un.h presence... yes
checking for sys/un.h... yes
checking for sys/time.h... (cached) yes
checking for unistd.h... (cached) yes
checking for alarm... yes
checking for working mktime... yes
checking for getloadavg... yes
checking for pstat_getdynamic... no
checking for kstat_open in -lkstat... no
checking for getloadavg... yes
checking whether getloadavg requires setgid... no
checking for _LARGEFILE_SOURCE value needed for large files... no
checking getopt.h usability... yes
checking getopt.h presence... yes
checking for getopt.h... yes
checking for getopt_long_only... yes
checking whether optreset is declared... no
checking for working GNU getopt function... yes
checking whether getpgrp requires zero arguments... yes
checking for strftime... yes
checking for grantpt... yes
checking for getpt... yes
checking for tparm in -lncurses... no
checking for dgettext in -lintl... no
checking whether localtime caches TZ... no
checking for gettimeofday... yes
checking whether gettimeofday can accept two arguments... yes
checking for socket... yes
checking netinet/in.h usability... yes
checking netinet/in.h presence... yes
checking for netinet/in.h... yes
checking arpa/inet.h usability... yes
checking arpa/inet.h presence... yes
checking for arpa/inet.h... yes
checking sys/ioctl.h usability... yes
checking sys/ioctl.h presence... yes
checking for sys/ioctl.h... yes
checking whether system supports dynamic ptys... yes
checking for pid_t... yes
checking vfork.h usability... no
checking vfork.h presence... no
checking for vfork.h... no
checking for fork... yes
checking for vfork... yes
checking for working fork... yes
checking for working vfork... (cached) yes
checking for nl_langinfo and CODESET... yes
checking for size_t... yes
checking for mbstate_t... yes
checking for C restrict keyword... __restrict
checking for C restricted array declarations... yes

Configured for `i686-pc-linux-gnu'.

  Where should the build process find the source code?    /home/spiral/Desktop/emacs-22.2
  What operating system and machine description files should Emacs use?
        `s/gnu-linux.h' and `m/intel386.h'
  What compiler should emacs be built with?               gcc -g -O2 -Wno-pointer-sign 
  Should Emacs use the GNU version of malloc?             yes
      (Using Doug Lea's new malloc from the GNU C Library.)
  Should Emacs use a relocating allocator for buffers?    yes
  Should Emacs use mmap(2) for buffer allocation?         no
  What window system should Emacs use?                    none
  What toolkit should Emacs use?                          none
  Where do we find X Windows header files?                NONE
  Where do we find X Windows libraries?                   NONE
  Does Emacs use -lXaw3d?                                 no
  Does Emacs use -lXpm?                                   no
  Does Emacs use -ljpeg?                                  no
  Does Emacs use -ltiff?                                  no
  Does Emacs use -lungif?                                 no
  Does Emacs use -lpng?                                   no
  Does Emacs use X toolkit scroll bars?                   no

configure: creating ./config.status
config.status: creating Makefile
config.status: creating lib-src/Makefile.c
config.status: creating oldXMenu/Makefile
config.status: creating man/Makefile
config.status: creating lwlib/Makefile
config.status: creating src/Makefile.c
config.status: creating lisp/Makefile
config.status: creating lispref/Makefile
config.status: creating lispintro/Makefile
config.status: creating leim/Makefile
config.status: creating src/config.h
config.status: executing default commands
creating src/epaths.h
creating lib-src/Makefile
creating src/Makefile
spiral@spiral-desktop:~/Desktop/emacs-22.2$ 
```
The compile status information near the bottom lends me to believe that I made a mistake somewhere as it indicates that the build contains no X toolkit support, and thus no gtk, which means no fancy menus and the rest of the eye candy.

Can someone walk me through the process of compiling it correctly with gtk support?

---

### Post by bluehue on 2008-04-26
Welp, figured it out. First, get libgtk2.0-dev from the repos. 

Next, execute:
```

./configure --with-gtk
```

Output:
```

spiral@spiral-desktop:~/Desktop/emacs-22.2$ ./configure --with-gtk
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables... 
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ISO C89... none needed
checking how to run the C preprocessor... gcc -E
checking for grep that handles long lines and -e... /bin/grep
checking for egrep... /bin/grep -E
checking for AIX... no
checking whether gcc understands -Wno-pointer-sign... yes
checking whether ln -s works... yes
checking how to run the C preprocessor... gcc -E
checking for a BSD-compatible install... /usr/bin/install -c
checking for ranlib... ranlib
checking for install-info... /usr/sbin/install-info
checking for install-info... (cached) /usr/sbin/install-info
checking for install-info... (cached) /usr/sbin/install-info
checking for gzip... /bin/gzip
checking for -znocombreloc... yes
configure: checking the machine- and system-dependent files to find out
 - which libraries the lib-src programs will want, and
 - whether the GNU malloc routines are usable...
checking for special C compiler options needed for large files... no
checking for _FILE_OFFSET_BITS value needed for large files... 64
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
checking machine/soundcard.h usability... no
checking machine/soundcard.h presence... no
checking for machine/soundcard.h... no
checking sys/soundcard.h usability... yes
checking sys/soundcard.h presence... yes
checking for sys/soundcard.h... yes
checking soundcard.h usability... no
checking soundcard.h presence... no
checking for soundcard.h... no
checking for _oss_ioctl in -lossaudio... no
checking for pkg-config... /usr/bin/pkg-config
checking for alsa >= 1.0.0... no
checking sys/select.h usability... yes
checking sys/select.h presence... yes
checking for sys/select.h... yes
checking sys/timeb.h usability... yes
checking sys/timeb.h presence... yes
checking for sys/timeb.h... yes
checking sys/time.h usability... yes
checking sys/time.h presence... yes
checking for sys/time.h... yes
checking for unistd.h... (cached) yes
checking utime.h usability... yes
checking utime.h presence... yes
checking for utime.h... yes
checking linux/version.h usability... yes
checking linux/version.h presence... yes
checking for linux/version.h... yes
checking sys/systeminfo.h usability... no
checking sys/systeminfo.h presence... no
checking for sys/systeminfo.h... no
checking termios.h usability... yes
checking termios.h presence... yes
checking for termios.h... yes
checking limits.h usability... yes
checking limits.h presence... yes
checking for limits.h... yes
checking for string.h... (cached) yes
checking for stdlib.h... (cached) yes
checking termcap.h usability... no
checking termcap.h presence... no
checking for termcap.h... no
checking stdio_ext.h usability... yes
checking stdio_ext.h presence... yes
checking for stdio_ext.h... yes
checking fcntl.h usability... yes
checking fcntl.h presence... yes
checking for fcntl.h... yes
checking for strings.h... (cached) yes
checking coff.h usability... no
checking coff.h presence... no
checking for coff.h... no
checking pty.h usability... yes
checking pty.h presence... yes
checking for pty.h... yes
checking sys/mman.h usability... yes
checking sys/mman.h presence... yes
checking for sys/mman.h... yes
checking sys/param.h usability... yes
checking sys/param.h presence... yes
checking for sys/param.h... yes
checking sys/vlimit.h usability... yes
checking sys/vlimit.h presence... yes
checking for sys/vlimit.h... yes
checking sys/resource.h usability... yes
checking sys/resource.h presence... yes
checking for sys/resource.h... yes
checking locale.h usability... yes
checking locale.h presence... yes
checking for locale.h... yes
checking sys/_mbstate_t.h usability... no
checking sys/_mbstate_t.h presence... no
checking for sys/_mbstate_t.h... no
checking sys/utsname.h usability... yes
checking sys/utsname.h presence... yes
checking for sys/utsname.h... yes
checking pwd.h usability... yes
checking pwd.h presence... yes
checking for pwd.h... yes
checking if personality LINUX32 can be set... yes
checking for term.h... no
checking for ANSI C header files... (cached) yes
checking whether time.h and sys/time.h may both be included... yes
checking whether sys_siglist is declared... no
checking whether __sys_siglist is declared... no
checking for sys/wait.h that is POSIX.1 compatible... yes
checking for struct utimbuf... yes
checking return type of signal handlers... void
checking for speed_t... yes
checking for struct timeval... yes
checking for struct exception... yes
checking sys/socket.h usability... yes
checking sys/socket.h presence... yes
checking for sys/socket.h... yes
checking for net/if.h... yes
checking whether struct tm is in sys/time.h or time.h... time.h
checking for struct tm.tm_zone... yes
checking for struct tm.tm_gmtoff... yes
checking for struct ifreq.ifr_flags... yes
checking for struct ifreq.ifr_hwaddr... yes
checking for struct ifreq.ifr_netmask... yes
checking for struct ifreq.ifr_broadaddr... yes
checking for struct ifreq.ifr_addr... yes
checking for function prototypes... yes
checking for working volatile... yes
checking for an ANSI C-conforming const... yes
checking for void * support... yes
checking whether make sets $(MAKE)... yes
checking for long file names... yes
checking for X... libraries , headers 
checking Carbon/Carbon.h usability... no
checking Carbon/Carbon.h presence... no
checking for Carbon/Carbon.h... no
checking for malloc_get_state... yes
checking for malloc_set_state... yes
checking whether __after_morecore_hook exists... yes
checking for stdlib.h... (cached) yes
checking for unistd.h... (cached) yes
checking for getpagesize... yes
checking for working mmap... yes
checking for dnet_ntoa in -ldnet... no
checking for main in -lXbsd... no
checking for cma_open in -lpthreads... no
checking for XFree86 in /usr/X386... no
checking whether X on GNU/Linux needs -b to link... no
checking for Xkb... yes
checking for XrmSetDatabase... yes
checking for XScreenResourceString... yes
checking for XScreenNumberOfScreen... yes
checking for XSetWMProtocols... yes
checking X11 version 6... 6 or newer
checking X11 version 5... 5 or newer
checking for gtk+-2.0 >= 2.6 glib-2.0 >= 2.6... yes
checking GTK_CFLAGS... -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/freetype2 -I/usr/include/libpng12 -I/usr/include/pixman-1  
checking GTK_LIBS... -lgtk-x11-2.0 -lgdk-x11-2.0 -latk-1.0 -lgdk_pixbuf-2.0 -lm -lpangocairo-1.0 -lpango-1.0 -lcairo -lgobject-2.0 -lgmodule-2.0 -ldl -lglib-2.0  
checking for gtk_main... yes
checking for gdk_display_open... yes
checking for gtk_file_selection_new... yes
checking for gtk_file_chooser_dialog_new... yes
checking pthread.h usability... yes
checking pthread.h presence... yes
checking for pthread.h... yes
checking for pthread_self in -lpthread... yes
checking for xft >= 0.13.0... yes
checking XFT_CFLAGS... -I/usr/include/freetype2  
checking XFT_LIBS... -lXft -lfontconfig  
checking X11/Xft/Xft.h usability... yes
checking X11/Xft/Xft.h presence... yes
checking for X11/Xft/Xft.h... yes
checking for XftFontOpen in -lXft... yes
checking X11/xpm.h usability... no
checking X11/xpm.h presence... no
checking for X11/xpm.h... no
checking jerror.h usability... no
checking jerror.h presence... no
checking for jerror.h... no


checking png.h usability... yes
checking png.h presence... yes
checking for png.h... yes
checking libpng/png.h usability... yes
checking libpng/png.h presence... yes
checking for libpng/png.h... yes
checking for png_get_channels in -lpng... yes
checking tiffio.h usability... no
checking tiffio.h presence... no
checking for tiffio.h... no
checking gif_lib.h usability... no
checking gif_lib.h presence... no
checking for gif_lib.h... no
checking malloc/malloc.h usability... no
checking malloc/malloc.h presence... no
checking for malloc/malloc.h... no
checking X11/SM/SMlib.h usability... yes
checking X11/SM/SMlib.h presence... yes
checking for X11/SM/SMlib.h... yes
checking for SmcOpenConnection in -lSM... yes
checking whether netdb declares h_errno... yes
checking for working alloca.h... yes
checking for alloca... yes
checking for sqrt in -lm... yes
checking for maillock in -lmail... no
checking for maillock in -llockfile... no
checking for liblockfile.so... no
checking for touchlock... no
checking maillock.h usability... no
checking maillock.h presence... no
checking for maillock.h... no
checking for gethostname... yes
checking for getdomainname... yes
checking for dup2... yes
checking for rename... yes
checking for closedir... yes
checking for mkdir... yes
checking for rmdir... yes
checking for sysinfo... yes
checking for getrusage... yes
checking for get_current_dir_name... yes
checking for random... yes
checking for lrand48... yes
checking for bcopy... yes
checking for bcmp... yes
checking for logb... yes
checking for frexp... yes
checking for fmod... yes
checking for rint... yes
checking for cbrt... yes
checking for ftime... yes
checking for res_init... no
checking for setsid... yes
checking for strerror... yes
checking for fpathconf... yes
checking for select... yes
checking for mktime... yes
checking for euidaccess... yes
checking for getpagesize... (cached) yes
checking for tzset... yes
checking for setlocale... yes
checking for utimes... yes
checking for setrlimit... yes
checking for setpgid... yes
checking for getcwd... yes
checking for getwd... yes
checking for shutdown... yes
checking for getaddrinfo... yes
checking for __fpending... yes
checking for mblen... yes
checking for mbrlen... yes
checking for mbsinit... yes
checking for strsignal... yes
checking for setitimer... yes
checking for ualarm... yes
checking for index... yes
checking for rindex... yes
checking for sendto... yes
checking for recvfrom... yes
checking for getsockopt... yes
checking for setsockopt... yes
checking for getsockname... yes
checking for getpeername... yes
checking for gai_strerror... yes
checking for mkstemp... yes
checking for getline... yes
checking for getdelim... yes
checking for mremap... yes
checking for memmove... yes
checking for fsync... yes
checking for sync... yes
checking for bzero... yes
checking for memset... yes
checking for memcmp... yes
checking for difftime... yes
checking for memcpy... yes
checking for mempcpy... yes
checking for mblen... (cached) yes
checking for mbrlen... (cached) yes
checking for posix_memalign... yes
checking sys/un.h usability... yes
checking sys/un.h presence... yes
checking for sys/un.h... yes
checking for sys/time.h... (cached) yes
checking for unistd.h... (cached) yes
checking for alarm... yes
checking for working mktime... yes
checking for getloadavg... yes
checking for pstat_getdynamic... no
checking for kstat_open in -lkstat... no
checking for getloadavg... yes
checking whether getloadavg requires setgid... no
checking for _LARGEFILE_SOURCE value needed for large files... no
checking getopt.h usability... yes
checking getopt.h presence... yes
checking for getopt.h... yes
checking for getopt_long_only... yes
checking whether optreset is declared... no
checking for working GNU getopt function... yes
checking whether getpgrp requires zero arguments... yes
checking for strftime... yes
checking for grantpt... yes
checking for getpt... yes
checking for tparm in -lncurses... no
checking for dgettext in -lintl... no
checking whether localtime caches TZ... no
checking for gettimeofday... yes
checking whether gettimeofday can accept two arguments... yes
checking for socket... yes
checking netinet/in.h usability... yes
checking netinet/in.h presence... yes
checking for netinet/in.h... yes
checking arpa/inet.h usability... yes
checking arpa/inet.h presence... yes
checking for arpa/inet.h... yes
checking sys/ioctl.h usability... yes
checking sys/ioctl.h presence... yes
checking for sys/ioctl.h... yes
checking whether system supports dynamic ptys... yes
checking for pid_t... yes
checking vfork.h usability... no
checking vfork.h presence... no
checking for vfork.h... no
checking for fork... yes
checking for vfork... yes
checking for working fork... yes
checking for working vfork... (cached) yes
checking for nl_langinfo and CODESET... yes
checking for size_t... yes
checking for mbstate_t... yes
checking for C restrict keyword... __restrict
checking for C restricted array declarations... yes

Configured for `i686-pc-linux-gnu'.

  Where should the build process find the source code?    /home/spiral/Desktop/emacs-22.2
  What operating system and machine description files should Emacs use?
        `s/gnu-linux.h' and `m/intel386.h'
  What compiler should emacs be built with?               gcc -g -O2 -Wno-pointer-sign 
  Should Emacs use the GNU version of malloc?             yes
      (Using Doug Lea's new malloc from the GNU C Library.)
  Should Emacs use a relocating allocator for buffers?    yes
  Should Emacs use mmap(2) for buffer allocation?         no
  What window system should Emacs use?                    x11
  What toolkit should Emacs use?                          GTK
  Where do we find X Windows header files?                Standard dirs
  Where do we find X Windows libraries?                   Standard dirs
  Does Emacs use -lXaw3d?                                 no
  Does Emacs use -lXpm?                                   no
  Does Emacs use -ljpeg?                                  no
  Does Emacs use -ltiff?                                  no
  Does Emacs use -lungif?                                 no
  Does Emacs use -lpng?                                   yes
  Does Emacs use X toolkit scroll bars?                   yes

configure: creating ./config.status
config.status: creating Makefile
config.status: creating lib-src/Makefile.c
config.status: creating oldXMenu/Makefile
config.status: creating man/Makefile
config.status: creating lwlib/Makefile
config.status: creating src/Makefile.c
config.status: creating lisp/Makefile
config.status: creating lispref/Makefile
config.status: creating lispintro/Makefile
config.status: creating leim/Makefile
config.status: creating src/config.h
config.status: executing default commands
creating src/epaths.h
creating lib-src/Makefile
creating src/Makefile
spiral@spiral-desktop:~/Desktop/emacs-22.2$
```
Note how emacs is now using gtk as the toolkit. Done! :)

---

