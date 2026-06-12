---
title: "Configure problem library"
date: 2008-08-09
forum: New to Ubuntu
---

### Post by scuba123 on 2008-08-09
Hi,

I downloaded xterm from this link: [http://invisible-island.net/xterm/xterm.html](http://invisible-island.net/xterm/xterm.html)

Once I configure, I received the following error message:
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
Configuring for linux-gnu
checking for gcc... gcc
checking for C compiler default output... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for executable suffix... 
checking for object suffix... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking how to run the C preprocessor... gcc -E
checking whether gcc needs -traditional... no
checking for mawk... mawk
checking for a BSD compatible install... /usr/bin/install -c
checking whether ln -s works... yes
checking for tdlint... no
checking for lint... no
checking for alint... no
checking for AIX... no
checking for POSIXized ISC... no
checking for gcc option to accept ANSI C... -DCC_HAS_PROTOS
checking for gcc option to accept ANSI C... none needed
checking for an ANSI C-conforming const... yes
checking if gcc -U and -D options work together... yes
checking if we must define _GNU_SOURCE... yes
checking if SIGWINCH is defined... yes
checking for ncurses/term.h... no
checking for stdlib.h... yes
checking for sys/ttydefaults.h... yes
checking for term.h... yes
checking for termios.h... yes
checking for unistd.h... yes
checking for wchar.h... yes
checking whether time.h and sys/time.h may both be included... yes
checking for nl_langinfo and CODESET... yes
checking for signal global datatype... volatile sig_atomic_t
checking for size_t in <sys/types.h> or <stdio.h>... yes
checking for ANSI C header files... yes
checking for sys/types.h... yes
checking for sys/stat.h... yes
checking for stdlib.h... (cached) yes
checking for string.h... yes
checking for memory.h... yes
checking for strings.h... yes
checking for inttypes.h... yes
checking for stdint.h... yes
checking for unistd.h... (cached) yes
checking for time_t... yes
checking for mode_t... yes
checking for pid_t... yes
checking for uid_t in sys/types.h... yes
checking for off_t... yes
checking for bcopy... yes
checking for gethostname... yes
checking for getlogin... yes
checking for memmove... yes
checking for putenv... yes
checking for sched_yield... yes
checking for strerror... yes
checking for strftime... yes
checking for tcgetattr... yes
checking for waitpid... yes
checking for wcswidth... yes
checking for wcwidth... yes
checking for memmove... (cached) yes
checking for lastlog.h... yes
checking for paths.h... yes
checking for lastlog path... _PATH_LASTLOG
checking for utmp implementation... utmp
checking if utmp.ut_host is declared... yes
checking if utmp.ut_syslen is declared... no
checking if utmp.ut_name is declared... ut_name
checking for exit-status in utmp... ut_exit.e_exit
checking if utmp.ut_xtime is declared... yes
checking if utmp.ut_session is declared... yes
checking if utmp is SYSV flavor... yes
checking for lastlog.h... (cached) yes
checking for struct lastlog... yes
checking for sys/param.h... yes
checking if POSIX saved-ids are supported... yes
checking if we want full tgetent function... yes
checking for full tgetent function... no
checking for partial tgetent function... -ltermcap
checking for termcap.h... yes
checking for directory to install resource files... '$(exec_prefix)/lib/X11/app-defaults'
checking for directory to install icons... '$(exec_prefix)/share/pixmaps'
checking if you want to install desktop files... yes
checking for desktop-file-install... yes
checking for install-permissions reference... xterm
checking for xterm... /usr/bin/xterm
checking for symbolic link to create to xterm... xterm
checking if you want to disable setuid... no
checking if you want to disable setgid... no
checking if you want to run xterm setuid to a given user... no
checking if you want to run xterm setgid to match utmp/utmpx file... no
checking if you want to link with utempter... no
checking if external errno is declared... yes
checking if external errno exists... no
checking for explicit tty group name... auto...
checking for tty group name... tty
checking if we may use the tty group... yes
checking for sys/wait.h that is POSIX.1 compatible... yes
checking for POSIX wait functions... yes
checking if external sys_nerr is declared... yes
checking if external sys_nerr exists... yes
checking if external sys_errlist is declared... yes
checking if external sys_errlist exists... yes
checking for termios.h... (cached) yes
checking for stdlib.h... (cached) yes
checking for X11/Intrinsic.h... no
checking if we should define SYSV... no
checking for elf_begin in -lelf... no
checking for X... no
checking for XOpenDisplay... no
checking for XOpenDisplay in -lX11... no
checking for XtAppInitialize... no
checking for XtAppInitialize in -lXt... no
configure: WARNING: Unable to successfully link X Toolkit library (-lXt) with
test program.  You will have to check and add the proper libraries by hand
to makefile.
checking for X11/DECkeysym.h... no
checking for X11/Sunkeysym.h... no
checking for X11/XF86keysym.h... no
checking for X11/Xpoll.h... no
checking if you want to link with Xaw 3d library... no
checking if you want to link with neXT Athena library... no
checking if you want to link with Athena-Plus library... no
checking for XextCreateExtension in -lXext... no
checking for X11/Xaw/SimpleMenu.h... no
checking for X11/Xaw/SimpleMenu.h in /usr/contrib/X11R6... no
checking for X11/Xaw/SimpleMenu.h in /usr/contrib/X11R5... no
checking for X11/Xaw/SimpleMenu.h in /usr/lib/X11R5... no
checking for X11/Xaw/SimpleMenu.h in /usr/local... no
configure: WARNING: Unable to successfully find Athena header files with test program
checking for XawSimpleMenuAddGlobalActions in -lXaw -lXmu... no
checking for XawSimpleMenuAddGlobalActions in -lXaw -lXpm -lXmu... no
checking for XawSimpleMenuAddGlobalActions in -lXaw_s -lXmu_s... no
checking for -lXaw -lXmu in /usr/contrib/X11R6... no
checking for -lXaw -lXpm -lXmu in /usr/contrib/X11R6... no
checking for -lXaw_s -lXmu_s in /usr/contrib/X11R6... no
checking for -lXaw -lXmu in /usr/contrib/X11R5... no
checking for -lXaw -lXpm -lXmu in /usr/contrib/X11R5... no
checking for -lXaw_s -lXmu_s in /usr/contrib/X11R5... no
checking for -lXaw -lXmu in /usr/lib/X11R5... no
checking for -lXaw -lXpm -lXmu in /usr/lib/X11R5... no
checking for -lXaw_s -lXmu_s in /usr/lib/X11R5... no
checking for -lXaw -lXmu in /usr/local... no
checking for -lXaw -lXpm -lXmu in /usr/local... no
checking for -lXaw_s -lXmu_s in /usr/local... no
configure: error: Unable to successfully link Athena library (-lXaw) with test program

Could you help please? Thanks.

---

### Post by SZ07 on 2008-08-09
Not too sure what to do here, but from the warning message it seems like you are missing some libraries (though it doesn't say which ones).

---

### Post by oldos2er on 2008-08-09
xterm should already be installed in Ubuntu; if it's not I'm sure it's in the repositories.

 Read the README and INSTALL files that should've come with the source code, they should tell you the dependencies the program needs.

---

### Post by scuba123 on 2008-08-09
Hi Guys,

After I looked at the README and INSTALL, I found out that I needed to have Athena-related libraries in place. So, I went to synaptic package manager and installed any libraries related to Athena. It worked. Thanks.

Regards,

scuba123

---

