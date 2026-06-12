---
title: "[64-bit] F-Prot (anti-virus) for Ubuntu 64-bit"
date: 2007-11-26
forum: Outdated Tutorials &amp; Tips
---

### Post by Perfect Storm on 2007-11-26
**Tested:** Ubuntu 7.10 | 8.04 64 bit - Gnome

This guide show you how to install F-prot with gui for Ubuntu 64-bit

1.  F.A.Q. - Please read - Important
2. Guide - F-prot for Ubuntu 64-bit
3. Links


**[size=5]1. - F.A.Q.[/size]**

Q: **Is viruses, trojans and malware a threat to a linux system as in Windows?**

A: No, there's a very few viruses to linux and the few are not out in the wild. The way a Linux/unix is build up makes it difficult to do any serious damage to the system, in fact I've never heard from people who got their Linux/unix system infected.

Q: **So why install an anti-virus application/program?**

A: For an ordinary Linux Home user with only one OS system their's no need for Anti-virus, but people who's running network, server or dual booting with win OS this tool can be very handy to scan for virus.

Q: **I'm a home user only running Linux do I need it?**

A: No, a firewall is way better as protection in that case.


_Please also read;_ [[color=red] Ubuntu Security[/color]](http://ubuntuforums.org/showthread.php?t=510812) and [[color=red] Are firestarter and clamav really necessary ??[/color]](http://ubuntuforums.org/showthread.php?t=131616)



**[size=5]2. F-Prot for Ubuntu 64-bit[/size]**

**Before Installation**

First you need some tool to edit/build .deb packages. To the terminal;

```
sudo aptitude update && sudo aptitude upgrade
sudo aptitude install ia32-libs build-essential dpkg-dev fakeroot
```



**Installation**

Grab F-prot [here]("http://www.f-prot.com/products/home_use/linux/")  and pick the debian/gnu file. (4.6.8 ) and save it to your Desktop
Download XFPROT-1.22 [here]("http://web.tiscali.it/sharp/xfprot/") and save it to your Desktop. 

Installation of F-prot;
```
cd ~/Desktop
sudo dpkg -i fp-linux-ws.deb
```


Installation of xf-prot (gui to F-prot);

```
cd ~/Desktop
mkdir xf-prot
dpkg-deb --extract xfprot_1.25-1_i386.deb xf-prot
dpkg-deb --control xfprot_1.25-1_i386.deb xf-prot/DEBIAN
nano xf-prot/DEBIAN/control
```

change **Architecture: i386** to **Architecture: amd64**

Save [ctrl]+[o]
Exit [ctrl]+[x]

```
dpkg --build xf-prot
sudo dpkg -i xf-prot.deb

```



**Launcher**

```
sudo nano /usr/share/applications/fprot.desktop
```

add the following;

```
[Desktop Entry]
Name=F-Prot
Comment=Anti-Virus Application
Exec=xfprot
Icon=/usr/local/xfprot/icons/antivirus-48x48.png
Terminal=false
Type=Application
Categories=Application;System;
```

Save [ctrl]+[o]
Exit [ctrl]+[x]

**NOTE:** If you want to run xf-prot (f-prot) with administration permission change **Exec=xfprot** to **Exec=gksudo xfprot**



**[size=5]3. Links[/size]**

[Install AVG free and pro anti-virus for Ubuntu 64-bit](http://ubuntuforums.org/showthread.php?p=3836317)
[Build the  latest of Pidgin + Plugins](http://ubuntuforums.org/showthread.php?p=4072317)
[Build the latest of Audacious](http://ubuntuforums.org/showthread.php?p=4072585)

---

### Post by bosesubhasis on 2007-12-27
i am a newbee in ubuntu. i followed everything as u said.the whole installation was ok without any problem. but xfprot is not seems to be running. it's listed in there Applications>>System Tools both F-prot and Xfprot.none of them r running upon execution.pls help me.
i also tried command line
gksudo xfprot >>> nothing happened
sudo xfprot >>>gives an error message >>>xfprot: error while loading shared libraries: libgtk-x11-2.0.so.0: cannot open shared object file: No such file or directory

---

### Post by Perfect Storm on 2007-12-27
Try installing libgtkextra-x11-2.0-1
If that doesn't help check if you have installed 32 bit layers


Edit: yup, you need to install 32-bit layer.
Do a
```
sudo aptitude install ia32-libs
```

Should do it.
To check what's missing (application are using);
```
cd /usr/local/xfprot
ldd xfprot-gtk
```

---

### Post by bosesubhasis on 2007-12-27
thanks a bunch. Installing 32-bit layer solved my problem totally. F-prot executed normally.
thanks again 4 all ur help.

---

### Post by bosesubhasis on 2007-12-28
> **Artificial Intelligence said:**
> 
**NOTE:** If you want to run xf-prot (f-prot) with administration permission change **Exec=xfprot** to **Exec=gksudo xfprot**


and last thing i want to know "where should i change the command"?
thank u in advance

---

### Post by Perfect Storm on 2007-12-28
When you make the launcher, if you take a look at it

[Desktop Entry]
Name=F-Prot
Comment=Anti-Virus Application
Exec=xfprot
Icon=/usr/local/xfprot/icons/antivirus-48x48.png
Terminal=false
Type=Application
Categories=Application;System;

change Exec=xfprot to Exec=gksudo xfprot

---

### Post by bosesubhasis on 2007-12-28
ok thank u. i configured it.

---

### Post by Perfect Storm on 2008-04-10
Now tested on Ubuntu 8.04

---

### Post by Perfect Storm on 2008-08-16
Guide updated.

---

### Post by chammi on 2009-05-14
Hi there, I started with Ubuntu back during the Breezy days and used it for about a year and now I'm back after a long hiatus.  So I'm rusty. 

Anyway, it looks like with F-prot 6, there is only a tarball (not a deb version) I tried following the tarball install directions, but it's not working. 


I think the actual f-prot part was installed.  fpscan is where it is supposed to be, at least.  When I click on it in the menu (using the launcher we created, I get some activity.  It starts a thing on the taskbar/bottom panel that says "starting adminit...." and then it goes away.  There is no visible result. 

This the part for xfprot.  It was truncated because I ran out of buffer space in my terminal, but maybe it's enough info to work with.  I looks like I am missing a library, but I dunno what I need. 

32 bit compatibility is installed, as is fakeroot--basically, anything that was recommended in the directions.  The only diff is that I skipped the part where we depackage and work with the .deb file because there was no deb file.

===========================
about_window.c:67: error: ‘menubar’ undeclared (first use in this function)
about_window.c:68: error: ‘table’ undeclared (first use in this function)
about_window.c:69: error: ‘frame’ undeclared (first use in this function)
about_window.c:70: error: ‘label’ undeclared (first use in this function)
about_window.c:71: error: ‘bbox’ undeclared (first use in this function)
about_window.c:72: error: ‘check_button’ undeclared (first use in this function)
about_window.c:73: error: ‘button’ undeclared (first use in this function)
about_window.c:74: error: ‘option_menu’ undeclared (first use in this function)
about_window.c:75: error: ‘options’ undeclared (first use in this function)
about_window.c:76: error: ‘toggle_wrap’ undeclared (first use in this function)
about_window.c:77: error: ‘GtkAccelGroup’ undeclared (first use in this function)
about_window.c:77: error: ‘accel_group’ undeclared (first use in this function)
about_window.c:87: error: ‘about_window’ undeclared (first use in this function)
about_window.c:87: warning: implicit declaration of function ‘window_create’
about_window.c:88: warning: implicit declaration of function ‘gtk_accel_group_new’
about_window.c:89: warning: implicit declaration of function ‘gtk_window_add_accel_group’
about_window.c:89: warning: implicit declaration of function ‘GTK_WINDOW’
about_window.c:90: warning: implicit declaration of function ‘find_toplevel_set_transient’
about_window.c:91: warning: implicit declaration of function ‘table_create’
about_window.c:93: warning: implicit declaration of function ‘gtk_menu_bar_new’
about_window.c:94: warning: implicit declaration of function ‘gtk_table_attach_defaults’
about_window.c:94: warning: implicit declaration of function ‘GTK_TABLE’
about_window.c:94: warning: implicit declaration of function ‘GTK_WIDGET’
about_window.c:96: warning: implicit declaration of function ‘gtk_menu_new’
about_window.c:97: warning: implicit declaration of function ‘gtk_image_menu_item_new_with_mnemonic’
about_window.c:98: warning: implicit declaration of function ‘gtk_image_menu_item_set_image’
about_window.c:98: warning: implicit declaration of function ‘GTK_IMAGE_MENU_ITEM’
about_window.c:98: warning: implicit declaration of function ‘gtk_image_new_from_stock’
about_window.c:98: error: ‘GTK_STOCK_PREFERENCES’ undeclared (first use in this function)
about_window.c:98: error: ‘GTK_ICON_SIZE_MENU’ undeclared (first use in this function)
about_window.c:100: warning: implicit declaration of function ‘gtk_check_menu_item_new_with_label’
about_window.c:101: warning: implicit declaration of function ‘gtk_widget_add_accelerator’
about_window.c:101: error: ‘GDK_w’ undeclared (first use in this function)
about_window.c:101: error: ‘GDK_CONTROL_MASK’ undeclared (first use in this function)
about_window.c:101: error: ‘GTK_ACCEL_VISIBLE’ undeclared (first use in this function)
about_window.c:102: warning: implicit declaration of function ‘g_signal_connect’
about_window.c:102: warning: implicit declaration of function ‘G_OBJECT’
about_window.c:102: warning: implicit declaration of function ‘G_CALLBACK’
about_window.c:103: warning: implicit declaration of function ‘gtk_check_menu_item_set_active’
about_window.c:103: warning: implicit declaration of function ‘GTK_CHECK_MENU_ITEM’
about_window.c:105: warning: implicit declaration of function ‘gtk_menu_item_set_submenu’
about_window.c:105: warning: implicit declaration of function ‘GTK_MENU_ITEM’
about_window.c:106: warning: implicit declaration of function ‘gtk_menu_shell_append’
about_window.c:106: warning: implicit declaration of function ‘GTK_MENU_SHELL’
about_window.c:109: warning: implicit declaration of function ‘frame_create_on_table’
about_window.c:111: warning: implicit declaration of function ‘g_markup_printf_escaped’
about_window.c:117: warning: assignment makes pointer from integer without a cast
about_window.c:118: warning: implicit declaration of function ‘gtk_label_new’
about_window.c:119: warning: implicit declaration of function ‘gtk_label_set_markup’
about_window.c:119: warning: implicit declaration of function ‘GTK_LABEL’
about_window.c:121: warning: implicit declaration of function ‘label_create’
about_window.c:123: warning: implicit declaration of function ‘gtk_label_set_justify’
about_window.c:123: error: ‘GTK_JUSTIFY_CENTER’ undeclared (first use in this function)
about_window.c:124: warning: implicit declaration of function ‘gtk_container_add’
about_window.c:124: warning: implicit declaration of function ‘GTK_CONTAINER’
about_window.c:125: error: ‘about_text’ undeclared (first use in this function)
about_window.c:125: warning: implicit declaration of function ‘textpad_create_on_table’
about_window.c:126: warning: implicit declaration of function ‘default_button_box_create_on_table’
about_window.c:127: warning: implicit declaration of function ‘button_create_in_container’
about_window.c:127: error: ‘GTK_STOCK_OK’ undeclared (first use in this function)
about_window.c:130: warning: implicit declaration of function ‘check_create_on_table’
about_window.c:131: error: ‘license_callback’ undeclared (first use in this function)
about_window.c:135: warning: implicit declaration of function ‘gtk_widget_show_all’
about_window.c:139: warning: implicit declaration of function ‘read_from_stream_and_display_text’
about_window.c:143: warning: implicit declaration of function ‘main_loop’
make[1]: *** [xfprot-about_window.o] Error 1
make[1]: Leaving directory `/home/ubuntu/Desktop/xfprot-2.2/src'
make: *** [install-recursive] Error 1
ubuntu@ubuntu:~/Desktop/xfprot-2.2$ sudo make clean
Making clean in icons
make[1]: Entering directory `/home/ubuntu/Desktop/xfprot-2.2/icons'
make[1]: Nothing to be done for `clean'.
make[1]: Leaving directory `/home/ubuntu/Desktop/xfprot-2.2/icons'
Making clean in src
make[1]: Entering directory `/home/ubuntu/Desktop/xfprot-2.2/src'
test -z "xfprot" || rm -f xfprot
rm -f *.o
make[1]: Leaving directory `/home/ubuntu/Desktop/xfprot-2.2/src'
Making clean in po
make[1]: Entering directory `/home/ubuntu/Desktop/xfprot-2.2/po'
rm -f *.pox xfprot.pot *.old.po cat-id-tbl.tmp
rm -f .intltool-merge-cache
make[1]: Leaving directory `/home/ubuntu/Desktop/xfprot-2.2/po'
Making clean in .
make[1]: Entering directory `/home/ubuntu/Desktop/xfprot-2.2'
make[1]: Nothing to be done for `clean-am'.
make[1]: Leaving directory `/home/ubuntu/Desktop/xfprot-2.2'
ubuntu@ubuntu:~/Desktop/xfprot-2.2$ sudo ./configure
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for a thread-safe mkdir -p... /bin/mkdir -p
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking for sudo... /usr/bin/sudo
checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables... 
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ISO C89... none needed
checking for style of include used by make... GNU
checking dependency style of gcc... gcc3
checking whether gcc and cc understand -c and -o together... yes
checking for a BSD-compatible install... /usr/bin/install -c
checking whether make sets $(MAKE)... (cached) yes
checking for intltool-update... /usr/bin/intltool-update
checking for intltool-merge... /usr/bin/intltool-merge
checking for intltool-extract... /usr/bin/intltool-extract
checking for xgettext... /usr/bin/xgettext
checking for msgmerge... /usr/bin/msgmerge
checking for msgfmt... /usr/bin/msgfmt
checking for perl... /usr/bin/perl
checking for XML::Parser... ok
checking how to run the C preprocessor... gcc -E
checking for grep that handles long lines and -e... /bin/grep
checking for egrep... /bin/grep -E
checking for ANSI C header files... yes
checking for pkg-config... /usr/bin/pkg-config
checking for GTK+ - version >= 2.8.0... no
*** Could not run GTK+ test program, checking why...
*** The test program failed to compile or link. See the file config.log for the
*** exact error that occured. This usually means GTK+ is incorrectly installed.
Package gtk+-2.0 was not found in the pkg-config search path.
Perhaps you should add the directory containing `gtk+-2.0.pc'
to the PKG_CONFIG_PATH environment variable
No package 'gtk+-2.0' found
Package gtk+-2.0 was not found in the pkg-config search path.
Perhaps you should add the directory containing `gtk+-2.0.pc'
to the PKG_CONFIG_PATH environment variable
No package 'gtk+-2.0' found
Package gtk+-2.0 was not found in the pkg-config search path.
Perhaps you should add the directory containing `gtk+-2.0.pc'
to the PKG_CONFIG_PATH environment variable
No package 'gtk+-2.0' found
checking for gtk_widget_set_tooltip_text in -lgtk-x11-2.0... no
checking for prctl... yes
checking for kde-config... no
configure: WARNING: kde-config............not found.
Setting kdeprefix to default /usr, use --with-kdeprefix=PATH to override."
checking for sys/types.h... yes
checking for sys/stat.h... yes
checking for stdlib.h... yes
checking for string.h... yes
checking for memory.h... yes
checking for strings.h... yes
checking for inttypes.h... yes
checking for stdint.h... yes
checking for unistd.h... yes
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
checking for msgfmt... (cached) /usr/bin/msgfmt
checking for dcgettext... yes
checking if msgfmt accepts -c... yes
checking for gmsgfmt... /usr/bin/msgfmt
checking for xgettext... (cached) /usr/bin/xgettext
checking for catalogs to be installed...  it_IT.UTF-8 de_DE.UTF-8 fr_FR.UTF-8 es_ES.UTF-8 pt_BR.UTF-8 pl_PL.UTF-8 ru_RU.UTF-8
configure: creating ./config.status
config.status: creating Makefile
config.status: creating src/Makefile
config.status: creating src/xfprot.desktop
config.status: creating src/xfprot_scan.desktop
config.status: creating po/Makefile.in
config.status: creating icons/Makefile
config.status: creating src/config.h
config.status: src/config.h is unchanged
config.status: executing depfiles commands
config.status: executing default-1 commands
config.status: executing po/stamp-it commands

  XFPROT 2.2

  Build target . . . . . . . . . . . . . . . . . . .: release
  Install prefix . . . . . . . . . . . . . . . . . .: /usr/local
  Datarootdir  . . . . . . . . . . . . . . . . . . .: /usr/local/share
  Gtk+ library version . . . . . . . . . . . . . . .: ..
  Preferred command to become superuser. . . . . . .: sudo
  Core dumps . . . . . . . . . . . . . . . . . . . .: not allowed
  KDE3 prefix for desktop integration  . . . . . . .: /usr

Now type 'make', followed by 'make install' as root.

ubuntu@ubuntu:~/Desktop/xfprot-2.2$ sudo make
Making all in po
make[1]: Entering directory `/home/ubuntu/Desktop/xfprot-2.2/po'
make[1]: Nothing to be done for `all'.
make[1]: Leaving directory `/home/ubuntu/Desktop/xfprot-2.2/po'
Making all in src
make[1]: Entering directory `/home/ubuntu/Desktop/xfprot-2.2/src'
make  all-am
make[2]: Entering directory `/home/ubuntu/Desktop/xfprot-2.2/src'
gcc -DHAVE_CONFIG_H -I.    -DG_DISABLE_DEPRECATED -DGDK_DISABLE_DEPRECATED -DGDK_PIXBUF_DISABLE_DEPRECATED -DGTK_DISABLE_DEPRECATED  -include config.h -include xfprot.h -std=c99 -D_XOPEN_SOURCE=500 -DNDEBUG -O3 -pipe -fomit-frame-pointer -fno-builtin -MT xfprot-about_window.o -MD -MP -MF .deps/xfprot-about_window.Tpo -c -o xfprot-about_window.o `test -f 'about_window.c' || echo './'`about_window.c
about_window.c:29:21: error: gtk/gtk.h: No such file or directory
about_window.c:30:28: error: gdk/gdkkeysyms.h: No such file or directory
In file included from about_window.c:33:
mygtk.h:101: error: expected ‘)’ before ‘*’ token
mygtk.h:102: error: expected ‘)’ before ‘*’ token
mygtk.h:104: error: expected ‘)’ before ‘*’ token
mygtk.h:107: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
mygtk.h:108: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
mygtk.h:110: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
mygtk.h:117: error: expected ‘)’ before ‘*’ token
mygtk.h:122: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
mygtk.h:129: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
mygtk.h:141: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
mygtk.h:142: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
mygtk.h:152: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
mygtk.h:158: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
mygtk.h:165: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
mygtk.h:171: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
mygtk.h:173: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
mygtk.h:175: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
mygtk.h:177: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
mygtk.h:185: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
mygtk.h:193: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
mygtk.h:199: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
mygtk.h:208: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
mygtk.h:215: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
mygtk.h:217: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
mygtk.h:224: error: expected specifier-qualifier-list before ‘GtkWidget’
mygtk.h:239: error: expected declaration specifiers or ‘...’ before ‘GtkFileChooserAction’
mygtk.h:239: error: expected declaration specifiers or ‘...’ before ‘gboolean’
mygtk.h:239: error: expected declaration specifiers or ‘...’ before ‘gboolean’
mygtk.h:241: error: expected declaration specifiers or ‘...’ before ‘GtkFileChooserAction’
mygtk.h:297: error: expected declaration specifiers or ‘...’ before ‘GtkTextBuffer’
mygtk.h:298: error: expected ‘)’ before ‘*’ token
mygtk.h:299: error: expected ‘)’ before ‘*’ token
mygtk.h:305: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
mygtk.h:306: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
mygtk.h:323: error: expected specifier-qualifier-list before ‘gpointer’
mygtk.h:331: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
mygtk.h:345: error: expected specifier-qualifier-list before ‘GtkWidget’
mygtk.h:355: error: expected declaration specifiers or ‘...’ before ‘GtkWidget’
mygtk.h:405: error: expected ‘)’ before ‘*’ token
about_window.c:37: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
about_window.c:38: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
about_window.c: In function ‘about_wrap_text’:
about_window.c:42: warning: implicit declaration of function ‘gtk_text_view_set_wrap_mode’
about_window.c:42: warning: implicit declaration of function ‘GTK_TEXT_VIEW’
about_window.c:42: error: ‘about_text’ undeclared (first use in this function)
about_window.c:42: error: (Each undeclared identifier is reported only once
about_window.c:42: error: for each function it appears in.)
about_window.c:43: warning: implicit declaration of function ‘gtk_text_view_get_wrap_mode’
about_window.c:43: error: ‘GTK_WRAP_NONE’ undeclared (first use in this function)
about_window.c:45: error: ‘GTK_WRAP_WORD’ undeclared (first use in this function)
about_window.c: At top level:
about_window.c:48: error: expected ‘)’ before ‘*’ token
about_window.c: In function ‘about_quit’:
about_window.c:61: warning: implicit declaration of function ‘gtk_main_quit’
about_window.c:62: warning: implicit declaration of function ‘gtk_widget_destroy’
about_window.c:62: error: ‘about_window’ undeclared (first use in this function)
about_window.c: In function ‘about_window_create’:
about_window.c:67: error: ‘GtkWidget’ undeclared (first use in this function)
about_window.c:67: error: ‘menubar’ undeclared (first use in this function)
about_window.c:68: error: ‘table’ undeclared (first use in this function)
about_window.c:69: error: ‘frame’ undeclared (first use in this function)
about_window.c:70: error: ‘label’ undeclared (first use in this function)
about_window.c:71: error: ‘bbox’ undeclared (first use in this function)
about_window.c:72: error: ‘check_button’ undeclared (first use in this function)
about_window.c:73: error: ‘button’ undeclared (first use in this function)
about_window.c:74: error: ‘option_menu’ undeclared (first use in this function)
about_window.c:75: error: ‘options’ undeclared (first use in this function)
about_window.c:76: error: ‘toggle_wrap’ undeclared (first use in this function)
about_window.c:77: error: ‘GtkAccelGroup’ undeclared (first use in this function)
about_window.c:77: error: ‘accel_group’ undeclared (first use in this function)
about_window.c:87: error: ‘about_window’ undeclared (first use in this function)
about_window.c:87: warning: implicit declaration of function ‘window_create’
about_window.c:88: warning: implicit declaration of function ‘gtk_accel_group_new’
about_window.c:89: warning: implicit declaration of function ‘gtk_window_add_accel_group’
about_window.c:89: warning: implicit declaration of function ‘GTK_WINDOW’
about_window.c:90: warning: implicit declaration of function ‘find_toplevel_set_transient’
about_window.c:91: warning: implicit declaration of function ‘table_create’
about_window.c:93: warning: implicit declaration of function ‘gtk_menu_bar_new’
about_window.c:94: warning: implicit declaration of function ‘gtk_table_attach_defaults’
about_window.c:94: warning: implicit declaration of function ‘GTK_TABLE’
about_window.c:94: warning: implicit declaration of function ‘GTK_WIDGET’
about_window.c:96: warning: implicit declaration of function ‘gtk_menu_new’
about_window.c:97: warning: implicit declaration of function ‘gtk_image_menu_item_new_with_mnemonic’
about_window.c:98: warning: implicit declaration of function ‘gtk_image_menu_item_set_image’
about_window.c:98: warning: implicit declaration of function ‘GTK_IMAGE_MENU_ITEM’
about_window.c:98: warning: implicit declaration of function ‘gtk_image_new_from_stock’
about_window.c:98: error: ‘GTK_STOCK_PREFERENCES’ undeclared (first use in this function)
about_window.c:98: error: ‘GTK_ICON_SIZE_MENU’ undeclared (first use in this function)
about_window.c:100: warning: implicit declaration of function ‘gtk_check_menu_item_new_with_label’
about_window.c:101: warning: implicit declaration of function ‘gtk_widget_add_accelerator’
about_window.c:101: error: ‘GDK_w’ undeclared (first use in this function)
about_window.c:101: error: ‘GDK_CONTROL_MASK’ undeclared (first use in this function)
about_window.c:101: error: ‘GTK_ACCEL_VISIBLE’ undeclared (first use in this function)
about_window.c:102: warning: implicit declaration of function ‘g_signal_connect’
about_window.c:102: warning: implicit declaration of function ‘G_OBJECT’
about_window.c:102: warning: implicit declaration of function ‘G_CALLBACK’
about_window.c:103: warning: implicit declaration of function ‘gtk_check_menu_item_set_active’
about_window.c:103: warning: implicit declaration of function ‘GTK_CHECK_MENU_ITEM’
about_window.c:105: warning: implicit declaration of function ‘gtk_menu_item_set_submenu’
about_window.c:105: warning: implicit declaration of function ‘GTK_MENU_ITEM’
about_window.c:106: warning: implicit declaration of function ‘gtk_menu_shell_append’
about_window.c:106: warning: implicit declaration of function ‘GTK_MENU_SHELL’
about_window.c:109: warning: implicit declaration of function ‘frame_create_on_table’
about_window.c:111: warning: implicit declaration of function ‘g_markup_printf_escaped’
about_window.c:117: warning: assignment makes pointer from integer without a cast
about_window.c:118: warning: implicit declaration of function ‘gtk_label_new’
about_window.c:119: warning: implicit declaration of function ‘gtk_label_set_markup’
about_window.c:119: warning: implicit declaration of function ‘GTK_LABEL’
about_window.c:121: warning: implicit declaration of function ‘label_create’
about_window.c:123: warning: implicit declaration of function ‘gtk_label_set_justify’
about_window.c:123: error: ‘GTK_JUSTIFY_CENTER’ undeclared (first use in this function)
about_window.c:124: warning: implicit declaration of function ‘gtk_container_add’
about_window.c:124: warning: implicit declaration of function ‘GTK_CONTAINER’
about_window.c:125: error: ‘about_text’ undeclared (first use in this function)
about_window.c:125: warning: implicit declaration of function ‘textpad_create_on_table’
about_window.c:126: warning: implicit declaration of function ‘default_button_box_create_on_table’
about_window.c:127: warning: implicit declaration of function ‘button_create_in_container’
about_window.c:127: error: ‘GTK_STOCK_OK’ undeclared (first use in this function)
about_window.c:130: warning: implicit declaration of function ‘check_create_on_table’
about_window.c:131: error: ‘license_callback’ undeclared (first use in this function)
about_window.c:135: warning: implicit declaration of function ‘gtk_widget_show_all’
about_window.c:139: warning: implicit declaration of function ‘read_from_stream_and_display_text’
about_window.c:143: warning: implicit declaration of function ‘main_loop’
make[2]: *** [xfprot-about_window.o] Error 1
make[2]: Leaving directory `/home/ubuntu/Desktop/xfprot-2.2/src'
make[1]: *** [all] Error 2
make[1]: Leaving directory `/home/ubuntu/Desktop/xfprot-2.2/src'
make: *** [all-recursive] Error 1
ubuntu@ubuntu:~/Desktop/xfprot-2.2$ sudo make install
Making install in po
make[1]: Entering directory `/home/ubuntu/Desktop/xfprot-2.2/po'
/bin/sh /home/ubuntu/Desktop/xfprot-2.2/install-sh -d /usr/local/share/locale
linguas="it_IT.UTF-8 de_DE.UTF-8 fr_FR.UTF-8 es_ES.UTF-8 pt_BR.UTF-8 pl_PL.UTF-8 ru_RU.UTF-8 "; \
	for lang in $linguas; do \
	  dir=/usr/local/share/locale/$lang/LC_MESSAGES; \
	  /bin/sh /home/ubuntu/Desktop/xfprot-2.2/install-sh -d $dir; \
	  if test -r $lang.gmo; then \
	    /usr/bin/install -c -m 644 $lang.gmo $dir/xfprot.mo; \
	    echo "installing $lang.gmo as $dir/xfprot.mo"; \
	  else \
	    /usr/bin/install -c -m 644 ./$lang.gmo $dir/xfprot.mo; \
	    echo "installing ./$lang.gmo as" \
		 "$dir/xfprot.mo"; \
	  fi; \
	  if test -r $lang.gmo.m; then \
	    /usr/bin/install -c -m 644 $lang.gmo.m $dir/xfprot.mo.m; \
	    echo "installing $lang.gmo.m as $dir/xfprot.mo.m"; \
	  else \
	    if test -r ./$lang.gmo.m ; then \
	      /usr/bin/install -c -m 644 ./$lang.gmo.m \
		$dir/xfprot.mo.m; \
	      echo "installing ./$lang.gmo.m as" \
		   "$dir/xfprot.mo.m"; \
	    else \
	      true; \
	    fi; \
	  fi; \
	done
installing it_IT.UTF-8.gmo as /usr/local/share/locale/it_IT.UTF-8/LC_MESSAGES/xfprot.mo
installing de_DE.UTF-8.gmo as /usr/local/share/locale/de_DE.UTF-8/LC_MESSAGES/xfprot.mo
installing fr_FR.UTF-8.gmo as /usr/local/share/locale/fr_FR.UTF-8/LC_MESSAGES/xfprot.mo
installing es_ES.UTF-8.gmo as /usr/local/share/locale/es_ES.UTF-8/LC_MESSAGES/xfprot.mo
installing pt_BR.UTF-8.gmo as /usr/local/share/locale/pt_BR.UTF-8/LC_MESSAGES/xfprot.mo
installing pl_PL.UTF-8.gmo as /usr/local/share/locale/pl_PL.UTF-8/LC_MESSAGES/xfprot.mo
installing ru_RU.UTF-8.gmo as /usr/local/share/locale/ru_RU.UTF-8/LC_MESSAGES/xfprot.mo
make[1]: Leaving directory `/home/ubuntu/Desktop/xfprot-2.2/po'
Making install in src
make[1]: Entering directory `/home/ubuntu/Desktop/xfprot-2.2/src'
gcc -DHAVE_CONFIG_H -I.    -DG_DISABLE_DEPRECATED -DGDK_DISABLE_DEPRECATED -DGDK_PIXBUF_DISABLE_DEPRECATED -DGTK_DISABLE_DEPRECATED  -include config.h -include xfprot.h -std=c99 -D_XOPEN_SOURCE=500 -DNDEBUG -O3 -pipe -fomit-frame-pointer -fno-builtin -MT xfprot-about_window.o -MD -MP -MF .deps/xfprot-about_window.Tpo -c -o xfprot-about_window.o `test -f 'about_window.c' || echo './'`about_window.c
about_window.c:29:21: error: gtk/gtk.h: No such file or directory
about_window.c:30:28: error: gdk/gdkkeysyms.h: No such file or directory
In file included from about_window.c:33:
mygtk.h:101: error: expected ‘)’ before ‘*’ token
mygtk.h:102: error: expected ‘)’ before ‘*’ token
mygtk.h:104: error: expected ‘)’ before ‘*’ token
mygtk.h:107: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
mygtk.h:108: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
mygtk.h:110: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
mygtk.h:117: error: expected ‘)’ before ‘*’ token
mygtk.h:122: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
mygtk.h:129: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
mygtk.h:141: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
mygtk.h:142: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
mygtk.h:152: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
mygtk.h:158: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
mygtk.h:165: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
mygtk.h:171: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
mygtk.h:173: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
mygtk.h:175: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
mygtk.h:177: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
mygtk.h:185: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
mygtk.h:193: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
mygtk.h:199: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
mygtk.h:208: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
mygtk.h:215: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
mygtk.h:217: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
mygtk.h:224: error: expected specifier-qualifier-list before ‘GtkWidget’
mygtk.h:239: error: expected declaration specifiers or ‘...’ before ‘GtkFileChooserAction’
mygtk.h:239: error: expected declaration specifiers or ‘...’ before ‘gboolean’
mygtk.h:239: error: expected declaration specifiers or ‘...’ before ‘gboolean’
mygtk.h:241: error: expected declaration specifiers or ‘...’ before ‘GtkFileChooserAction’
mygtk.h:297: error: expected declaration specifiers or ‘...’ before ‘GtkTextBuffer’
mygtk.h:298: error: expected ‘)’ before ‘*’ token
mygtk.h:299: error: expected ‘)’ before ‘*’ token
mygtk.h:305: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
mygtk.h:306: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
mygtk.h:323: error: expected specifier-qualifier-list before ‘gpointer’
mygtk.h:331: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
mygtk.h:345: error: expected specifier-qualifier-list before ‘GtkWidget’
mygtk.h:355: error: expected declaration specifiers or ‘...’ before ‘GtkWidget’
mygtk.h:405: error: expected ‘)’ before ‘*’ token
about_window.c:37: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
about_window.c:38: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
about_window.c: In function ‘about_wrap_text’:
about_window.c:42: warning: implicit declaration of function ‘gtk_text_view_set_wrap_mode’
about_window.c:42: warning: implicit declaration of function ‘GTK_TEXT_VIEW’
about_window.c:42: error: ‘about_text’ undeclared (first use in this function)
about_window.c:42: error: (Each undeclared identifier is reported only once
about_window.c:42: error: for each function it appears in.)
about_window.c:43: warning: implicit declaration of function ‘gtk_text_view_get_wrap_mode’
about_window.c:43: error: ‘GTK_WRAP_NONE’ undeclared (first use in this function)
about_window.c:45: error: ‘GTK_WRAP_WORD’ undeclared (first use in this function)
about_window.c: At top level:
about_window.c:48: error: expected ‘)’ before ‘*’ token
about_window.c: In function ‘about_quit’:
about_window.c:61: warning: implicit declaration of function ‘gtk_main_quit’
about_window.c:62: warning: implicit declaration of function ‘gtk_widget_destroy’
about_window.c:62: error: ‘about_window’ undeclared (first use in this function)
about_window.c: In function ‘about_window_create’:
about_window.c:67: error: ‘GtkWidget’ undeclared (first use in this function)
about_window.c:67: error: ‘menubar’ undeclared (first use in this function)
about_window.c:68: error: ‘table’ undeclared (first use in this function)
about_window.c:69: error: ‘frame’ undeclared (first use in this function)
about_window.c:70: error: ‘label’ undeclared (first use in this function)
about_window.c:71: error: ‘bbox’ undeclared (first use in this function)
about_window.c:72: error: ‘check_button’ undeclared (first use in this function)
about_window.c:73: error: ‘button’ undeclared (first use in this function)
about_window.c:74: error: ‘option_menu’ undeclared (first use in this function)
about_window.c:75: error: ‘options’ undeclared (first use in this function)
about_window.c:76: error: ‘toggle_wrap’ undeclared (first use in this function)
about_window.c:77: error: ‘GtkAccelGroup’ undeclared (first use in this function)
about_window.c:77: error: ‘accel_group’ undeclared (first use in this function)
about_window.c:87: error: ‘about_window’ undeclared (first use in this function)
about_window.c:87: warning: implicit declaration of function ‘window_create’
about_window.c:88: warning: implicit declaration of function ‘gtk_accel_group_new’
about_window.c:89: warning: implicit declaration of function ‘gtk_window_add_accel_group’
about_window.c:89: warning: implicit declaration of function ‘GTK_WINDOW’
about_window.c:90: warning: implicit declaration of function ‘find_toplevel_set_transient’
about_window.c:91: warning: implicit declaration of function ‘table_create’
about_window.c:93: warning: implicit declaration of function ‘gtk_menu_bar_new’
about_window.c:94: warning: implicit declaration of function ‘gtk_table_attach_defaults’
about_window.c:94: warning: implicit declaration of function ‘GTK_TABLE’
about_window.c:94: warning: implicit declaration of function ‘GTK_WIDGET’
about_window.c:96: warning: implicit declaration of function ‘gtk_menu_new’
about_window.c:97: warning: implicit declaration of function ‘gtk_image_menu_item_new_with_mnemonic’
about_window.c:98: warning: implicit declaration of function ‘gtk_image_menu_item_set_image’
about_window.c:98: warning: implicit declaration of function ‘GTK_IMAGE_MENU_ITEM’
about_window.c:98: warning: implicit declaration of function ‘gtk_image_new_from_stock’
about_window.c:98: error: ‘GTK_STOCK_PREFERENCES’ undeclared (first use in this function)
about_window.c:98: error: ‘GTK_ICON_SIZE_MENU’ undeclared (first use in this function)
about_window.c:100: warning: implicit declaration of function ‘gtk_check_menu_item_new_with_label’
about_window.c:101: warning: implicit declaration of function ‘gtk_widget_add_accelerator’
about_window.c:101: error: ‘GDK_w’ undeclared (first use in this function)
about_window.c:101: error: ‘GDK_CONTROL_MASK’ undeclared (first use in this function)
about_window.c:101: error: ‘GTK_ACCEL_VISIBLE’ undeclared (first use in this function)
about_window.c:102: warning: implicit declaration of function ‘g_signal_connect’
about_window.c:102: warning: implicit declaration of function ‘G_OBJECT’
about_window.c:102: warning: implicit declaration of function ‘G_CALLBACK’
about_window.c:103: warning: implicit declaration of function ‘gtk_check_menu_item_set_active’
about_window.c:103: warning: implicit declaration of function ‘GTK_CHECK_MENU_ITEM’
about_window.c:105: warning: implicit declaration of function ‘gtk_menu_item_set_submenu’
about_window.c:105: warning: implicit declaration of function ‘GTK_MENU_ITEM’
about_window.c:106: warning: implicit declaration of function ‘gtk_menu_shell_append’
about_window.c:106: warning: implicit declaration of function ‘GTK_MENU_SHELL’
about_window.c:109: warning: implicit declaration of function ‘frame_create_on_table’
about_window.c:111: warning: implicit declaration of function ‘g_markup_printf_escaped’
about_window.c:117: warning: assignment makes pointer from integer without a cast
about_window.c:118: warning: implicit declaration of function ‘gtk_label_new’
about_window.c:119: warning: implicit declaration of function ‘gtk_label_set_markup’
about_window.c:119: warning: implicit declaration of function ‘GTK_LABEL’
about_window.c:121: warning: implicit declaration of function ‘label_create’
about_window.c:123: warning: implicit declaration of function ‘gtk_label_set_justify’
about_window.c:123: error: ‘GTK_JUSTIFY_CENTER’ undeclared (first use in this function)
about_window.c:124: warning: implicit declaration of function ‘gtk_container_add’
about_window.c:124: warning: implicit declaration of function ‘GTK_CONTAINER’
about_window.c:125: error: ‘about_text’ undeclared (first use in this function)
about_window.c:125: warning: implicit declaration of function ‘textpad_create_on_table’
about_window.c:126: warning: implicit declaration of function ‘default_button_box_create_on_table’
about_window.c:127: warning: implicit declaration of function ‘button_create_in_container’
about_window.c:127: error: ‘GTK_STOCK_OK’ undeclared (first use in this function)
about_window.c:130: warning: implicit declaration of function ‘check_create_on_table’
about_window.c:131: error: ‘license_callback’ undeclared (first use in this function)
about_window.c:135: warning: implicit declaration of function ‘gtk_widget_show_all’
about_window.c:139: warning: implicit declaration of function ‘read_from_stream_and_display_text’
about_window.c:143: warning: implicit declaration of function ‘main_loop’
make[1]: *** [xfprot-about_window.o] Error 1
make[1]: Leaving directory `/home/ubuntu/Desktop/xfprot-2.2/src'
make: *** [install-recursive] Error 1

---

