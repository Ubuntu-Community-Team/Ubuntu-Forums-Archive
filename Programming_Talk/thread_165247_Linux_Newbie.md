---
title: "Linux Newbie"
date: 2006-04-24
forum: Programming Talk
---

### Post by HAL98 SE on 2006-04-24
I'm attempted to extract and build wxWidgets-2.6.3 in order to use it to complete installing Xara XS, but when i attempt to build the following occurs


```
root@ubuntu:/usr/local/wxWidgets-2.6.3# ./configure --enable-unicode checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking target system type... i686-pc-linux-gnu
loading argument cache configarg.cache
checking for --enable-gui... yes
checking for --enable-monolithic... no
checking for --enable-plugins... no
checking for --enable-universal... no
checking for --enable-nanox... no
checking for --enable-gpe... no
checking for --with-libpng... yes
checking for --with-libjpeg... yes
checking for --with-libtiff... yes
checking for --with-libxpm... yes
checking for --with-libmspack... yes
checking for --with-sdl... no
checking for --with-gnomeprint... no
checking for --with-hildon... no
checking for --with-opengl... no
checking for --with-dmalloc... no
checking for --with-regex... yes
checking for --with-zlib... yes
checking for --with-odbc... no
checking for --with-expat... yes
checking for --enable-shared... yes
checking for --enable-optimise... yes
checking for --enable-debug... no
checking for --enable-stl... no
checking for --enable-debug_flag... no
checking for --enable-debug_info... no
checking for --enable-debug_gdb... no
checking for --enable-debug_cntxt... no
checking for --enable-mem_tracing... no
checking for --enable-profile... no
checking for --enable-no_rtti... no
checking for --enable-no_exceptions... no
checking for --enable-permissive... no
checking for --enable-no_deps... no
checking for --enable-universal_binary... no
checking for --enable-compat22... no
checking for --disable-compat24... no
checking for --enable-rpath... yes
checking for --enable-intl... yes
checking for --enable-config... yes
checking for --enable-protocols... yes
checking for --enable-ftp... yes
checking for --enable-http... yes
checking for --enable-fileproto... yes
checking for --enable-sockets... yes
checking for --enable-ole... yes
checking for --enable-dataobj... yes
checking for --enable-ipc... yes
checking for --enable-apple_ieee... yes
checking for --enable-arcstream... yes
checking for --enable-backtrace... yes
checking for --enable-catch_segvs... yes
checking for --enable-cmdline... yes
checking for --enable-datetime... yes
checking for --enable-debugreport... yes
checking for --enable-dialupman... yes
checking for --enable-dynlib... yes
checking for --enable-dynamicloader... yes
checking for --enable-exceptions... yes
checking for --enable-ffile... yes
checking for --enable-file... yes
checking for --enable-filesystem... yes
checking for --enable-fontmap... yes
checking for --enable-fs_inet... yes
checking for --enable-fs_zip... yes
checking for --enable-geometry... yes
checking for --enable-log... yes
checking for --enable-longlong... yes
checking for --enable-mimetype... no
checking for --enable-mslu... yes
checking for --enable-snglinst... yes
checking for --enable-std_iostreams... yes
checking for --enable-std_string... yes
checking for --enable-stdpaths... yes
checking for --enable-stopwatch... yes
checking for --enable-streams... yes
checking for --enable-system_options... yes
checking for --enable-textbuf... yes
checking for --enable-textfile... yes
checking for --enable-timer... yes
checking for --enable-unicode... yes
checking for --enable-sound... yes
checking for --enable-mediactrl... no
checking for --enable-wxprintfv... no
checking for --enable-zipstream... yes
checking for --enable-url... yes
checking for --enable-protocol... yes
checking for --enable-protocol_http... yes
checking for --enable-protocol_ftp... yes
checking for --enable-protocol_file... yes
checking for --enable-threads... yes
checking for --enable-docview... yes
checking for --enable-help... yes
checking for --enable-mshtmlhelp... yes
checking for --enable-html... yes
checking for --enable-htmlhelp... yes
checking for --enable-xrc... yes
checking for --enable-constraints... yes
checking for --enable-printarch... yes
checking for --enable-mdi... yes
checking for --enable-mdidoc... yes
checking for --enable-loggui... yes
checking for --enable-logwin... yes
checking for --enable-logdialog... yes
checking for --enable-webkit... yes
checking for --enable-postscript... yes
checking for --enable-prologio... no
checking for --enable-resources... no
checking for --enable-clipboard... yes
checking for --enable-dnd... yes
checking for --enable-metafile... yes
checking for --enable-controls... no
checking for --enable-accel... yes
checking for --enable-button... yes
checking for --enable-bmpbutton... yes
checking for --enable-calendar... yes
checking for --enable-caret... yes
checking for --enable-checkbox... yes
checking for --enable-checklst... yes
checking for --enable-choice... yes
checking for --enable-choicebook... yes
checking for --enable-combobox... yes
checking for --enable-datepick... yes
checking for --enable-display... yes
checking for --enable-gauge... yes
checking for --enable-grid... yes
checking for --enable-imaglist... yes
checking for --enable-listbook... yes
checking for --enable-listbox... yes
checking for --enable-listctrl... yes
checking for --enable-notebook... yes
checking for --enable-radiobox... yes
checking for --enable-radiobtn... yes
checking for --enable-sash... yes
checking for --enable-scrollbar... yes
checking for --enable-slider... yes
checking for --enable-spinbtn... yes
checking for --enable-spinctrl... yes
checking for --enable-splitter... yes
checking for --enable-statbmp... yes
checking for --enable-statbox... yes
checking for --enable-statline... yes
checking for --enable-stattext... yes
checking for --enable-statusbar... yes
checking for --enable-tabdialog... no
checking for --enable-textctrl... yes
checking for --enable-togglebtn... yes
checking for --enable-toolbar... yes
checking for --enable-tbarnative... yes
checking for --enable-tbarsmpl... yes
checking for --enable-treectrl... yes
checking for --enable-tipwindow... yes
checking for --enable-popupwin... yes
checking for --enable-commondlg... yes
checking for --enable-choicedlg... yes
checking for --enable-coldlg... yes
checking for --enable-filedlg... yes
checking for --enable-finddlg... yes
checking for --enable-fontdlg... yes
checking for --enable-dirdlg... yes
checking for --enable-msgdlg... yes
checking for --enable-numberdlg... yes
checking for --enable-splash... yes
checking for --enable-textdlg... yes
checking for --enable-tipdlg... yes
checking for --enable-progressdlg... yes
checking for --enable-wizarddlg... yes
checking for --enable-menus... yes
checking for --enable-miniframe... yes
checking for --enable-tooltips... yes
checking for --enable-splines... yes
checking for --enable-mousewheel... yes
checking for --enable-validators... yes
checking for --enable-busyinfo... yes
checking for --enable-joystick... yes
checking for --enable-metafile... yes
checking for --enable-dragimage... yes
checking for --enable-accessibility... no
checking for --enable-palette... yes
checking for --enable-image... yes
checking for --enable-gif... yes
checking for --enable-pcx... yes
checking for --enable-iff... no
checking for --enable-pnm... yes
checking for --enable-xpm... yes
checking for --enable-ico_cur... yes
checking for --enable-official_build... no
saving argument cache configarg.cache
checking for toolkit... gtk
checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables...
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ANSI C... none needed
checking whether we are using the Intel C compiler... no
checking how to run the C preprocessor... gcc -E
checking for egrep... grep -E
checking whether gcc needs -traditional... no
checking for g++... no
checking for c++... no
checking for gpp... no
checking for aCC... no
checking for CC... no
checking for cxx... no
checking for cc++... no
checking for cl... no
checking for FCC... no
checking for KCC... no
checking for RCC... no
checking for xlC_r... no
checking for xlC... no
checking whether we are using the GNU C++ compiler... no
checking whether g++ accepts -g... no
checking whether we are using the Intel C++ compiler... no
checking for ranlib... ranlib
checking for ar... ar
checking for a BSD-compatible install... /usr/bin/install -c
checking for strip... strip
checking if make is GNU make... yes
checking whether ln -s works... yes
checking for strcasecmp() in string.h... no
checking for strcasecmp() in strings.h... no
**configure: error: No case-insensitive string comparison function found.**
root@ubuntu:/usr/local/wxWidgets-2.6.3# make
make: *** No targets specified and no makefile found.  Stop.
root@ubuntu:/usr/local/wxWidgets-2.6.3# make wxWidgets-2.6.3
make: *** No rule to make target `wxWidgets-2.6.3'.  Stop.
root@ubuntu:/usr/local/wxWidgets-2.6.3# dir
acinclude.m4     COPYING.LIB        Makefile.in        utils
aclocal.m4       demos              misc               version-script.in
art              descrip.mms        mkinstalldirs      wxBase.spec
autoconf_inc.m4  distrib            README-MAC.txt     wx-config.in
autogen.sh       docs               README-MGL.txt     wx-config-inplace.in
build            include            README-MOTIF.txt   wxGTK_RR.spec
BuildCVS.txt     INSTALL-MAC.txt    README-PALMOS.txt  wxGTK.spec
CHANGES.txt      INSTALL-MGL.txt    README.txt         wxMGL.spec
configarg.cache  INSTALL-MOTIF.txt  README-X11.txt     wxMotif.spec
config.guess     INSTALL-OS2.txt    regen              wxWINE.spec
config.log       install-sh         samples            wxwin.m4
config.sub       INSTALL-X11.txt    setup.h.in         wxX11.spec
configure        lib                setup.h_vms
configure.in     LICENCE.txt        src
contrib          locale             tests

```

i have checked synaptic packages and Make is there, am I missing something? I have highlighted in bold the line which i assume to be the issue.

any response would be welcome

thanx

---

### Post by skinnygmg on 2006-04-24
this belongs here

[http://www.ubuntuforums.org/forumdisplay.php?f=73](http://www.ubuntuforums.org/forumdisplay.php?f=73)

---

### Post by kh4nh on 2006-04-24
"configure: error: No case-insensitive string comparison function found."

./configure process did not go through succesfully. Have you installed build-essential? If not, you might wanna do this first: 
       sudo apt-get install build-essential

---

