---
title: "Kernel problem"
date: 2007-10-31
forum: Programming Talk
---

### Post by Roxxor on 2007-10-31
Hi, I am trying to compile a new vanilla source kernel but I get this error when I type "make oldconfig":

```
root@roxxor-desktop:/usr/src/linux-2.6.23.1# make oldconfig
  HOSTCC  scripts/basic/fixdep
scripts/basic/fixdep.c:107:23: error: sys/types.h: No such file or directory
scripts/basic/fixdep.c:108:22: error: sys/stat.h: No such file or directory
scripts/basic/fixdep.c:109:22: error: sys/mman.h: No such file or directory
scripts/basic/fixdep.c:110:20: error: unistd.h: No such file or directory
scripts/basic/fixdep.c:111:19: error: fcntl.h: No such file or directory
scripts/basic/fixdep.c:112:20: error: string.h: No such file or directory
scripts/basic/fixdep.c:113:20: error: stdlib.h: No such file or directory
scripts/basic/fixdep.c:114:19: error: stdio.h: No such file or directory
In file included from /usr/lib/gcc/i486-linux-gnu/4.1.3/include/syslimits.h:7,
                 from /usr/lib/gcc/i486-linux-gnu/4.1.3/include/limits.h:11,
                 from scripts/basic/fixdep.c:115:
/usr/lib/gcc/i486-linux-gnu/4.1.3/include/limits.h:122:61: error: limits.h: No such file or directory
scripts/basic/fixdep.c:116:19: error: ctype.h: No such file or directory
scripts/basic/fixdep.c:117:23: error: arpa/inet.h: No such file or directory
scripts/basic/fixdep.c: In function &#8216;usage&#8217;:
scripts/basic/fixdep.c:131: warning: implicit declaration of function &#8216;fprintf&#8217;
scripts/basic/fixdep.c:131: warning: incompatible implicit declaration of built-in function &#8216;fprintf&#8217;
scripts/basic/fixdep.c:131: error: &#8216;stderr&#8217; undeclared (first use in this function)
scripts/basic/fixdep.c:131: error: (Each undeclared identifier is reported only once
scripts/basic/fixdep.c:131: error: for each function it appears in.)
scripts/basic/fixdep.c:132: warning: implicit declaration of function &#8216;exit&#8217;
scripts/basic/fixdep.c:132: warning: incompatible implicit declaration of built-in function &#8216;exit&#8217;
scripts/basic/fixdep.c: In function &#8216;print_cmdline&#8217;:
scripts/basic/fixdep.c:140: warning: implicit declaration of function &#8216;printf&#8217;
scripts/basic/fixdep.c:140: warning: incompatible implicit declaration of built-in function &#8216;printf&#8217;
scripts/basic/fixdep.c: At top level:
scripts/basic/fixdep.c:143: error: &#8216;NULL&#8217; undeclared here (not in a function)
scripts/basic/fixdep.c: In function &#8216;grow_config&#8217;:
scripts/basic/fixdep.c:156: warning: implicit declaration of function &#8216;realloc&#8217;
scripts/basic/fixdep.c:156: warning: assignment makes pointer from integer without a cast
scripts/basic/fixdep.c:158: warning: implicit declaration of function &#8216;perror&#8217;
scripts/basic/fixdep.c:158: warning: incompatible implicit declaration of built-in function &#8216;exit&#8217;
scripts/basic/fixdep.c: In function &#8216;is_defined_config&#8217;:
scripts/basic/fixdep.c:174: warning: implicit declaration of function &#8216;memcmp&#8217;
scripts/basic/fixdep.c: In function &#8216;define_config&#8217;:
scripts/basic/fixdep.c:187: warning: implicit declaration of function &#8216;memcpy&#8217;
scripts/basic/fixdep.c:187: warning: incompatible implicit declaration of built-in function &#8216;memcpy&#8217;
scripts/basic/fixdep.c: In function &#8216;use_config&#8217;:
scripts/basic/fixdep.c:206: error: &#8216;PATH_MAX&#8217; undeclared (first use in this function)
scripts/basic/fixdep.c:214: warning: incompatible implicit declaration of built-in function &#8216;memcpy&#8217;
scripts/basic/fixdep.c:220: warning: implicit declaration of function &#8216;tolower&#8217;
scripts/basic/fixdep.c:222: warning: incompatible implicit declaration of built-in function &#8216;printf&#8217;
scripts/basic/fixdep.c:206: warning: unused variable &#8216;s&#8217;
scripts/basic/fixdep.c: At top level:
scripts/basic/fixdep.c:225: error: expected declaration specifiers or &#8216;...&#8217; before &#8216;size_t&#8217;
scripts/basic/fixdep.c: In function &#8216;parse_config_file&#8217;:
scripts/basic/fixdep.c:227: error: &#8216;len&#8217; undeclared (first use in this function)
scripts/basic/fixdep.c:233: warning: implicit declaration of function &#8216;ntohl&#8217;
scripts/basic/fixdep.c:244: warning: implicit declaration of function &#8216;isalnum&#8217;
scripts/basic/fixdep.c: In function &#8216;strrcmp&#8217;:
scripts/basic/fixdep.c:261: warning: implicit declaration of function &#8216;strlen&#8217;
scripts/basic/fixdep.c:261: warning: incompatible implicit declaration of built-in function &#8216;strlen&#8217;
scripts/basic/fixdep.c: In function &#8216;do_config_file&#8217;:
scripts/basic/fixdep.c:272: error: storage size of &#8216;st&#8217; isn&#8217;t known
scripts/basic/fixdep.c:276: warning: implicit declaration of function &#8216;open&#8217;
scripts/basic/fixdep.c:276: error: &#8216;O_RDONLY&#8217; undeclared (first use in this function)
scripts/basic/fixdep.c:278: warning: incompatible implicit declaration of built-in function &#8216;fprintf&#8217;
scripts/basic/fixdep.c:278: error: &#8216;stderr&#8217; undeclared (first use in this function)
scripts/basic/fixdep.c:280: warning: incompatible implicit declaration of built-in function &#8216;exit&#8217;
scripts/basic/fixdep.c:282: warning: implicit declaration of function &#8216;fstat&#8217;
scripts/basic/fixdep.c:284: warning: implicit declaration of function &#8216;close&#8217;
scripts/basic/fixdep.c:287: warning: implicit declaration of function &#8216;mmap&#8217;
scripts/basic/fixdep.c:287: error: &#8216;PROT_READ&#8217; undeclared (first use in this function)
scripts/basic/fixdep.c:287: error: &#8216;MAP_PRIVATE&#8217; undeclared (first use in this function)
scripts/basic/fixdep.c:287: warning: assignment makes pointer from integer without a cast
scripts/basic/fixdep.c:294: error: too many arguments to function &#8216;parse_config_file&#8217;
scripts/basic/fixdep.c:296: warning: implicit declaration of function &#8216;munmap&#8217;
scripts/basic/fixdep.c:272: warning: unused variable &#8216;st&#8217;
scripts/basic/fixdep.c: At top level:
scripts/basic/fixdep.c:301: error: expected declaration specifiers or &#8216;...&#8217; before &#8216;size_t&#8217;
scripts/basic/fixdep.c: In function &#8216;parse_dep_file&#8217;:
scripts/basic/fixdep.c:304: error: &#8216;len&#8217; undeclared (first use in this function)
scripts/basic/fixdep.c:306: error: &#8216;PATH_MAX&#8217; undeclared (first use in this function)
scripts/basic/fixdep.c:308: warning: implicit declaration of function &#8216;strchr&#8217;
scripts/basic/fixdep.c:308: warning: incompatible implicit declaration of built-in function &#8216;strchr&#8217;
scripts/basic/fixdep.c:310: warning: incompatible implicit declaration of built-in function &#8216;fprintf&#8217;
scripts/basic/fixdep.c:310: error: &#8216;stderr&#8217; undeclared (first use in this function)
scripts/basic/fixdep.c:311: warning: incompatible implicit declaration of built-in function &#8216;exit&#8217;
scripts/basic/fixdep.c:313: warning: incompatible implicit declaration of built-in function &#8216;memcpy&#8217;
scripts/basic/fixdep.c:314: warning: incompatible implicit declaration of built-in function &#8216;printf&#8217;
scripts/basic/fixdep.c:306: warning: unused variable &#8216;s&#8217;
scripts/basic/fixdep.c: In function &#8216;print_deps&#8217;:
scripts/basic/fixdep.c:343: error: storage size of &#8216;st&#8217; isn&#8217;t known
scripts/basic/fixdep.c:347: error: &#8216;O_RDONLY&#8217; undeclared (first use in this function)
scripts/basic/fixdep.c:349: warning: incompatible implicit declaration of built-in function &#8216;fprintf&#8217;
scripts/basic/fixdep.c:349: error: &#8216;stderr&#8217; undeclared (first use in this function)
scripts/basic/fixdep.c:351: warning: incompatible implicit declaration of built-in function &#8216;exit&#8217;
scripts/basic/fixdep.c:355: warning: incompatible implicit declaration of built-in function &#8216;fprintf&#8217;
scripts/basic/fixdep.c:359: error: &#8216;PROT_READ&#8217; undeclared (first use in this function)
scripts/basic/fixdep.c:359: error: &#8216;MAP_PRIVATE&#8217; undeclared (first use in this function)
scripts/basic/fixdep.c:359: warning: assignment makes pointer from integer without a cast
scripts/basic/fixdep.c:366: error: too many arguments to function &#8216;parse_dep_file&#8217;
scripts/basic/fixdep.c:343: warning: unused variable &#8216;st&#8217;
scripts/basic/fixdep.c: In function &#8216;traps&#8217;:
scripts/basic/fixdep.c:378: warning: incompatible implicit declaration of built-in function &#8216;fprintf&#8217;
scripts/basic/fixdep.c:378: error: &#8216;stderr&#8217; undeclared (first use in this function)
scripts/basic/fixdep.c:380: warning: incompatible implicit declaration of built-in function &#8216;exit&#8217;
make[1]: *** [scripts/basic/fixdep] Error 1
make: *** [scripts_basic] Error 2
root@roxxor-desktop:/usr/src/linux-2.6.23.1#
```

What goes wrong?

---

### Post by Compyx on 2007-10-31
I'd start off with installing the build-essential package:
```

sudo apt-get install build-essential

```
This should eliminate a few errors concerning the standard libraries.

---

### Post by Roxxor on 2007-10-31
It did not work.

Now I get this:
```
root@roxxor-desktop:/usr/src/linux-2.6.23.1# make menuconfig
  HOSTCC  scripts/kconfig/lxdialog/checklist.o
In file included from scripts/kconfig/lxdialog/checklist.c:24:
scripts/kconfig/lxdialog/dialog.h:32:20: error: curses.h: No such file or directory
In file included from scripts/kconfig/lxdialog/checklist.c:24:
scripts/kconfig/lxdialog/dialog.h:97: error: expected specifier-qualifier-list before &#8216;chtype&#8217;
scripts/kconfig/lxdialog/dialog.h:187: error: expected &#8216;)&#8217; before &#8216;*&#8217; token
scripts/kconfig/lxdialog/dialog.h:194: error: expected &#8216;)&#8217; before &#8216;*&#8217; token
scripts/kconfig/lxdialog/dialog.h:196: error: expected &#8216;)&#8217; before &#8216;*&#8217; token
scripts/kconfig/lxdialog/dialog.h:197: error: expected &#8216;)&#8217; before &#8216;*&#8217; token
scripts/kconfig/lxdialog/dialog.h:198: error: expected &#8216;)&#8217; before &#8216;*&#8217; token
scripts/kconfig/lxdialog/dialog.h:199: error: expected &#8216;)&#8217; before &#8216;*&#8217; token
scripts/kconfig/lxdialog/dialog.h:201: error: expected &#8216;)&#8217; before &#8216;*&#8217; token
scripts/kconfig/lxdialog/checklist.c:31: error: expected &#8216;)&#8217; before &#8216;*&#8217; token
scripts/kconfig/lxdialog/checklist.c:59: error: expected &#8216;)&#8217; before &#8216;*&#8217; token
scripts/kconfig/lxdialog/checklist.c:95: error: expected &#8216;)&#8217; before &#8216;*&#8217; token
scripts/kconfig/lxdialog/checklist.c: In function &#8216;dialog_checklist&#8217;:
scripts/kconfig/lxdialog/checklist.c:116: error: &#8216;WINDOW&#8217; undeclared (first use in this function)
scripts/kconfig/lxdialog/checklist.c:116: error: (Each undeclared identifier is reported only once
scripts/kconfig/lxdialog/checklist.c:116: error: for each function it appears in.)
scripts/kconfig/lxdialog/checklist.c:116: error: &#8216;dialog&#8217; undeclared (first use in this function)
scripts/kconfig/lxdialog/checklist.c:116: error: &#8216;list&#8217; undeclared (first use in this function)
scripts/kconfig/lxdialog/checklist.c:116: warning: left-hand operand of comma expression has no effect
scripts/kconfig/lxdialog/checklist.c:129: warning: implicit declaration of function &#8216;getmaxy&#8217;
scripts/kconfig/lxdialog/checklist.c:129: error: &#8216;stdscr&#8217; undeclared (first use in this function)
scripts/kconfig/lxdialog/checklist.c:130: error: &#8216;KEY_MAX&#8217; undeclared (first use in this function)
scripts/kconfig/lxdialog/checklist.c:131: warning: implicit declaration of function &#8216;getmaxx&#8217;
scripts/kconfig/lxdialog/checklist.c:137: error: &#8216;COLS&#8217; undeclared (first use in this function)
scripts/kconfig/lxdialog/checklist.c:138: error: &#8216;LINES&#8217; undeclared (first use in this function)
scripts/kconfig/lxdialog/checklist.c:140: warning: implicit declaration of function &#8216;draw_shadow&#8217;
scripts/kconfig/lxdialog/checklist.c:142: warning: implicit declaration of function &#8216;newwin&#8217;
scripts/kconfig/lxdialog/checklist.c:143: warning: implicit declaration of function &#8216;keypad&#8217;
scripts/kconfig/lxdialog/checklist.c:143: error: &#8216;TRUE&#8217; undeclared (first use in this function)
scripts/kconfig/lxdialog/checklist.c:145: warning: implicit declaration of function &#8216;draw_box&#8217;
scripts/kconfig/lxdialog/checklist.c:146: error: &#8216;struct dialog_color&#8217; has no member named &#8216;atr&#8217;
scripts/kconfig/lxdialog/checklist.c:146: error: &#8216;struct dialog_color&#8217; has no member named &#8216;atr&#8217;
scripts/kconfig/lxdialog/checklist.c:147: warning: implicit declaration of function &#8216;wattrset&#8217;
scripts/kconfig/lxdialog/checklist.c:147: error: &#8216;struct dialog_color&#8217; has no member named &#8216;atr&#8217;
scripts/kconfig/lxdialog/checklist.c:148: warning: implicit declaration of function &#8216;mvwaddch&#8217;
scripts/kconfig/lxdialog/checklist.c:150: warning: implicit declaration of function &#8216;waddch&#8217;
scripts/kconfig/lxdialog/checklist.c:151: error: &#8216;struct dialog_color&#8217; has no member named &#8216;atr&#8217;
scripts/kconfig/lxdialog/checklist.c:154: warning: implicit declaration of function &#8216;print_title&#8217;
scripts/kconfig/lxdialog/checklist.c:156: error: &#8216;struct dialog_color&#8217; has no member named &#8216;atr&#8217;
scripts/kconfig/lxdialog/checklist.c:157: warning: implicit declaration of function &#8216;print_autowrap&#8217;
scripts/kconfig/lxdialog/checklist.c:164: warning: implicit declaration of function &#8216;subwin&#8217;
scripts/kconfig/lxdialog/checklist.c:171: error: &#8216;struct dialog_color&#8217; has no member named &#8216;atr&#8217;
scripts/kconfig/lxdialog/checklist.c:171: error: &#8216;struct dialog_color&#8217; has no member named &#8216;atr&#8217;
scripts/kconfig/lxdialog/checklist.c:189: warning: implicit declaration of function &#8216;print_item&#8217;
scripts/kconfig/lxdialog/checklist.c:192: warning: implicit declaration of function &#8216;print_arrows&#8217;
scripts/kconfig/lxdialog/checklist.c:195: warning: implicit declaration of function &#8216;print_buttons&#8217;
scripts/kconfig/lxdialog/checklist.c:197: warning: implicit declaration of function &#8216;wnoutrefresh&#8217;
scripts/kconfig/lxdialog/checklist.c:199: warning: implicit declaration of function &#8216;doupdate&#8217;
scripts/kconfig/lxdialog/checklist.c:202: warning: implicit declaration of function &#8216;wgetch&#8217;
scripts/kconfig/lxdialog/checklist.c:210: error: &#8216;KEY_UP&#8217; undeclared (first use in this function)
scripts/kconfig/lxdialog/checklist.c:210: error: &#8216;KEY_DOWN&#8217; undeclared (first use in this function)
scripts/kconfig/lxdialog/checklist.c:220: error: &#8216;FALSE&#8217; undeclared (first use in this function)
scripts/kconfig/lxdialog/checklist.c:221: warning: implicit declaration of function &#8216;scrollok&#8217;
scripts/kconfig/lxdialog/checklist.c:222: warning: implicit declaration of function &#8216;wscrl&#8217;
scripts/kconfig/lxdialog/checklist.c:232: warning: implicit declaration of function &#8216;wrefresh&#8217;
scripts/kconfig/lxdialog/checklist.c:293: warning: implicit declaration of function &#8216;delwin&#8217;
scripts/kconfig/lxdialog/checklist.c:297: error: &#8216;KEY_LEFT&#8217; undeclared (first use in this function)
scripts/kconfig/lxdialog/checklist.c:298: error: &#8216;KEY_RIGHT&#8217; undeclared (first use in this function)
scripts/kconfig/lxdialog/checklist.c:310: warning: implicit declaration of function &#8216;on_key_esc&#8217;
scripts/kconfig/lxdialog/checklist.c:312: error: &#8216;KEY_RESIZE&#8217; undeclared (first use in this function)
make[1]: *** [scripts/kconfig/lxdialog/checklist.o] Error 1
make: *** [menuconfig] Error 2
```

---

### Post by Compyx on 2007-10-31
Just comment out the lines in /etc/apt/sources.list that look something like this:
```

deb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Alpha i386 (20070823)]/ gutsy main restricted

```
Just stick a '#' in front of that line and you should be fine.

Alternatively you can use a GUI: System->Administration->Software Sources, just untick the boxes in front of the "Installable from CD-rom" list in the "Ubuntu Software" tab.

---

### Post by moma on 2007-10-31
See:
[http://ubuntuforums.org/showthread.php?p=3671645#post3671645](http://ubuntuforums.org/showthread.php?p=3671645#post3671645)

I think you lack libncurses5
See step 1) in this [guide...]("http://www.futuredesktop.org/kompilere_kjerne.html")

Ncurses is a UI component library for _text and console based_ applications.

"make oldconfig" and "make menuconfig" uses a text based UI (user interface).

---

### Post by Compyx on 2007-10-31
> **Roxxor said:**
> It did not work.

Now I get this:
```
root@roxxor-desktop:/usr/src/linux-2.6.23.1# make menuconfig
  HOSTCC  scripts/kconfig/lxdialog/checklist.o
In file included from scripts/kconfig/lxdialog/checklist.c:24:
scripts/kconfig/lxdialog/dialog.h:32:20: error: curses.h: No such file or directory

```

```

sudo apt-get install ncurses-dev

```

---

### Post by Roxxor on 2007-10-31
Thanks folks!

I got it working now. 


Why is not ncurses-dev installed by default?

---

### Post by Compyx on 2007-10-31
Probably because a desktop oriented distro such as the default Ubuntu install doesn't need it to work properly.
My biggest issue with Ubuntu is the decision not to install the standard C libraries and manpages, one of the most asked questions is related to " no such file or directory: stdio.h" or something similar. In my humble opinion a Linux/Unix system isn't complete without a C compiler, standard libraries and manpages related to development ("sudo apt-get install manpages-dev manpages-posix-dev" if you want them).

---

### Post by dwhitney67 on 2007-10-31
> **Roxxor said:**
> Thanks folks!

I got it working now. 


Why is not ncurses-dev installed by default?
Because you are dealing with Ubuntu.  Try another distro and it probably is.  On Fedora 7 I also had to install ncurses-dev.

Btw, if you ever wish to run "make xconfig", you will need to install the Qt libraries.  If you are happy running *menuconfig*, then don't worry about it.

---

