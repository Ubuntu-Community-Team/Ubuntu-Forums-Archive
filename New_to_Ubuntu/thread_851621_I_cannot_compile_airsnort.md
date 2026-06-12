---
title: "I cannot compile airsnort"
date: 2008-07-06
forum: New to Ubuntu
---

### Post by Vossibear on 2008-07-06
I want to show my father how easy it is to crack our network.

So I wanted to install airsnort und I downloaded the source code.

Then I wanted to compile and started qith configure but there were a mistake but I do not know where.

> 
vossi@helmut:~/tmp/airsnort-0.2.7e$ ./configure
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking whether to enable maintainer-specific portions of Makefiles... no
checking for style of include used by make... GNU
checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables... 
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ANSI C... none needed
checking dependency style of gcc... gcc3
checking for library containing strerror... none required
checking for gcc... (cached) gcc
checking whether we are using the GNU C compiler... (cached) yes
checking whether gcc accepts -g... (cached) yes
checking for gcc option to accept ANSI C... (cached) none needed
checking dependency style of gcc... (cached) gcc3
checking for gcc... (cached) gcc
checking whether we are using the GNU C compiler... (cached) yes
checking whether gcc accepts -g... (cached) yes
checking for gcc option to accept ANSI C... (cached) none needed
checking dependency style of gcc... (cached) gcc3
checking how to run the C preprocessor... gcc -E
checking for egrep... grep -E
checking for ANSI C header files... yes
checking for pkg-config... /usr/bin/pkg-config
checking for gtk+-2.0 >= 2.0.0... yes
checking PACKAGE_CFLAGS... -DPNG_NO_MMX_CODE -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/freetype2 -I/usr/include/libpng12 -I/usr/include/pixman-1  
checking PACKAGE_LIBS... -lgtk-x11-2.0 -lgdk-x11-2.0 -latk-1.0 -lgdk_pixbuf-2.0 -lm -lpangocairo-1.0 -lpango-1.0 -lcairo -lgobject-2.0 -lgmodule-2.0 -ldl -lglib-2.0  
configure: creating ./config.status
config.status: creating Makefile
config.status: creating src/Makefile
config.status: creating man/Makefile
config.status: creating config.h
config.status: executing depfiles commands


---

### Post by Dissident85 on 2008-07-06
I would suggest getting yourself a copy of backtrack... it makes life a lot easier as they already have all the apps and a lot of the drivers already set up... what can be easily done it backtrack can at times be quite a daunting and difficult task in other distros of linux...

---

### Post by unutbu on 2008-07-06
There is also
```

sudo apt-get install airsnort
```

---

### Post by Vossibear on 2008-07-06
But it would not solve my compile problem.

I have the same problems when I want to compile other programs ... and airsnort is more comfortable than backtrack, because it is an program and I have not to restart, when I understood you that I have to work with JtR.

---

### Post by Vossibear on 2008-07-06
> **unutbu said:**
> There is also
```

sudo apt-get install airsnort
```

Which source I must write in the source.list for that? It doesn't find airsnort

---

### Post by unutbu on 2008-07-06
Hm. It appears there is a package for Gutsy but not a package for Hardy:
[http://packages.ubuntu.com/search?suite=gutsy&searchon=names&keywords=airsnort](http://packages.ubuntu.com/search?suite=gutsy&searchon=names&keywords=airsnort)

You can find the Gutsy deb here:
[http://security.ubuntu.com/ubuntu/pool/universe/a/airsnort/](http://security.ubuntu.com/ubuntu/pool/universe/a/airsnort/)

But altonbr says the Gutsy package does not work under Hardy
[http://ubuntuforums.org/showthread.php?p=5127915](http://ubuntuforums.org/showthread.php?p=5127915)

It would be easy to install the deb and remove it if it doesn't work. And if it doesn't then maybe compiling is the best way.

In case you need to compile:

You don't show any error messages in your first post. What's wrong?

In general, when compiling stuff under Ubuntu, I think it is best to link /bin/sh to /bin/bash instead of /bin/dash (Ubuntu's default). Some configure scripts are written by developers on non-Ubuntu systems and they put bashisms in their scripts which break when run by /bin/dash. So to re-link /bin/sh to /bin/bash, do
```

sudo ln -sf /bin/bash /bin/sh
```

Also, make sure you have installed build-essential:
```
sudo apt-get install build-essential
```

---

### Post by Vossibear on 2008-07-06
I did the two things you said

But after the make there are more mistakes:

> 
vossi@helmut:~/tmp/airsnort-0.2.7e$ sudo make
make  all-recursive

make[1]: Betrete Verzeichnis '/home/vossi/tmp/airsnort-0.2.7e'
Making all in src
make[2]: Betrete Verzeichnis '/home/vossi/tmp/airsnort-0.2.7e/src'
if gcc -DHAVE_CONFIG_H -I. -I. -I.. -DPACKAGE_DATA_DIR=\""/usr/local/share"\" -DPACKAGE_LOCALE_DIR=\""/usr/local//locale"\" -DPNG_NO_MMX_CODE -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/freetype2 -I/usr/include/libpng12 -I/usr/include/pixman-1      -g -O2 -MT main.o -MD -MP -MF ".deps/main.Tpo" -c -o main.o main.c; \
	then mv -f ".deps/main.Tpo" ".deps/main.Po"; else rm -f ".deps/main.Tpo"; exit 1; fi
if gcc -DHAVE_CONFIG_H -I. -I. -I.. -DPACKAGE_DATA_DIR=\""/usr/local/share"\" -DPACKAGE_LOCALE_DIR=\""/usr/local//locale"\" -DPNG_NO_MMX_CODE -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/freetype2 -I/usr/include/libpng12 -I/usr/include/pixman-1      -g -O2 -MT support.o -MD -MP -MF ".deps/support.Tpo" -c -o support.o support.c; \
	then mv -f ".deps/support.Tpo" ".deps/support.Po"; else rm -f ".deps/support.Tpo"; exit 1; fi
if gcc -DHAVE_CONFIG_H -I. -I. -I.. -DPACKAGE_DATA_DIR=\""/usr/local/share"\" -DPACKAGE_LOCALE_DIR=\""/usr/local//locale"\" -DPNG_NO_MMX_CODE -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/freetype2 -I/usr/include/libpng12 -I/usr/include/pixman-1      -g -O2 -MT interface.o -MD -MP -MF ".deps/interface.Tpo" -c -o interface.o interface.c; \
	then mv -f ".deps/interface.Tpo" ".deps/interface.Po"; else rm -f ".deps/interface.Tpo"; exit 1; fi
if gcc -DHAVE_CONFIG_H -I. -I. -I.. -DPACKAGE_DATA_DIR=\""/usr/local/share"\" -DPACKAGE_LOCALE_DIR=\""/usr/local//locale"\" -DPNG_NO_MMX_CODE -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/freetype2 -I/usr/include/libpng12 -I/usr/include/pixman-1      -g -O2 -MT callbacks.o -MD -MP -MF ".deps/callbacks.Tpo" -c -o callbacks.o callbacks.c; \
	then mv -f ".deps/callbacks.Tpo" ".deps/callbacks.Po"; else rm -f ".deps/callbacks.Tpo"; exit 1; fi
callbacks.c:9:18: Fehler: pcap.h: No such file or directory
In file included from PacketSource.h:31,
                 from callbacks.c:24:
/usr/include/linux/wireless.h:660: Fehler: expected specifier-qualifier-list before »__s32«
/usr/include/linux/wireless.h:673: Fehler: expected specifier-qualifier-list before »__u16«
/usr/include/linux/wireless.h:687: Fehler: expected specifier-qualifier-list before »__s32«
/usr/include/linux/wireless.h:698: Fehler: expected specifier-qualifier-list before »__u8«
/usr/include/linux/wireless.h:714: Fehler: expected specifier-qualifier-list before »__u32«
/usr/include/linux/wireless.h:727: Fehler: expected specifier-qualifier-list before »__u32«
/usr/include/linux/wireless.h:754: Fehler: expected specifier-qualifier-list before »__u8«
/usr/include/linux/wireless.h:816: Fehler: expected specifier-qualifier-list before »__u32«
/usr/include/linux/wireless.h:830: Fehler: expected specifier-qualifier-list before »__u16«
/usr/include/linux/wireless.h:844: Fehler: expected specifier-qualifier-list before »__u32«
/usr/include/linux/wireless.h:852: Fehler: expected specifier-qualifier-list before »__u32«
/usr/include/linux/wireless.h:861: Fehler: expected specifier-qualifier-list before »__u32«
/usr/include/linux/wireless.h:873: Fehler: expected specifier-qualifier-list before »__u16«
/usr/include/linux/wireless.h:896: Fehler: »IFNAMSIZ« ist hier nicht deklariert (nicht in einer Funktion)
/usr/include/linux/wireless.h:911: Fehler: expected specifier-qualifier-list before »__u32«
/usr/include/linux/wireless.h:955: Fehler: expected specifier-qualifier-list before »__u32«
/usr/include/linux/wireless.h:1059: Fehler: expected specifier-qualifier-list before »__u32«
/usr/include/linux/wireless.h:1077: Fehler: expected specifier-qualifier-list before »__u16«
In file included from callbacks.c:24:
PacketSource.h:153: Fehler: expected specifier-qualifier-list before »pcap_t«
PacketSource.h:178: Warnung: »struct pcap_pkthdr« innerhalb Parameterliste deklariert
PacketSource.h:178: Warnung: sein Gültigkeitsbereich umfasst nur diese Definition bzw. Deklaration, was Sie wahrscheinlich nicht wollten
PacketSource.h:179: Warnung: »struct pcap_pkthdr« innerhalb Parameterliste deklariert
callbacks.c:79: Fehler: »PCAP_ERRBUF_SIZE« ist hier nicht deklariert (nicht in einer Funktion)
callbacks.c: In Funktion »fillDeviceList«:
callbacks.c:121: Fehler: Speichergröße von »ir« ist unbekannt
callbacks.c:129: Fehler: »IFF_LOOPBACK« nicht deklariert (erste Benutzung in dieser Funktion)
callbacks.c:129: Fehler: (Jeder nicht deklarierte Bezeichner wird nur einmal aufgeführt
callbacks.c:129: Fehler: für jede Funktion in der er auftritt.)
make[2]: *** [callbacks.o] Fehler 1
make[2]: Verlasse Verzeichnis '/home/vossi/tmp/airsnort-0.2.7e/src'
make[1]: *** [all-recursive] Fehler 1
make[1]: Verlasse Verzeichnis '/home/vossi/tmp/airsnort-0.2.7e'
make: *** [all] Fehler 2


But the problem is, that the language in my terminal is German and I do not know how I can change. Sry for that

---

### Post by tjwoosta on 2008-07-06
first you need build-essential to compile anything

(although i also would recommend backtrack, or Knoppix STD they both come with about everything you need to crack your network preinstalled)

EDIT: wish i could speak German, sry

---

### Post by unutbu on 2008-07-06
Here is google's ([http://translate.google.com/translate_t?sl=de&tl=en](http://translate.google.com/translate_t?sl=de&tl=en)) translation of the error message.

```

make [1]: Enter the directory '/ home/vossi/tmp/airsnort-0.2.7e'
Making all in SRC
make [2]: Enter the directory '/ home/vossi/tmp/airsnort-0.2.7e/src'
if gcc-DHAVE_CONFIG_H-I. - I. I .. - DPACKAGE_DATA_DIR = \ "" / usr / local / share "\" DPACKAGE_LOCALE_DIR = \ "" / usr / local / / locale \ "-DPNG_NO_MMX_CODE -I/usr/include/gtk-2.0 -I/usr/lib / gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/glib-2.0 -I/usr/lib / glib-2.0/include -I/usr/include/freetype2 -I/usr/include/libpng12 -I/usr/include/pixman-1-g-O2-MT main.o-MD-MP-MF ". deps / main.Tpo "-c-o main.o main.c \
then mv-f ".deps / main.Tpo" ".deps / main.Po"; else rm-f ".deps / main.Tpo"; exit 1; fi
if gcc-DHAVE_CONFIG_H-I. - I. I .. - DPACKAGE_DATA_DIR = \ "" / usr / local / share "\" DPACKAGE_LOCALE_DIR = \ "" / usr / local / / locale \ "-DPNG_NO_MMX_CODE -I/usr/include/gtk-2.0 -I/usr/lib / gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/glib-2.0 -I/usr/lib / glib-2.0/include -I/usr/include/freetype2 -I/usr/include/libpng12 -I/usr/include/pixman-1-g-O2-MT support.o-MD-MP-MF ". deps / support.Tpo "-c-o support.o support.c \
then mv-f ".deps / support.Tpo" ".deps / support.Po"; else rm-f ".deps / support.Tpo"; exit 1; fi
if gcc-DHAVE_CONFIG_H-I. - I. I .. - DPACKAGE_DATA_DIR = \ "" / usr / local / share "\" DPACKAGE_LOCALE_DIR = \ "" / usr / local / / locale \ "-DPNG_NO_MMX_CODE -I/usr/include/gtk-2.0 -I/usr/lib / gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/glib-2.0 -I/usr/lib / glib-2.0/include -I/usr/include/freetype2 -I/usr/include/libpng12 -I/usr/include/pixman-1-g-O2-MT interface.o-MD-MP-MF ". deps / interface.Tpo "-c-o interface.o interface.c \
then mv-f ".deps / interface.Tpo" ".deps / interface.Po"; else rm-f ".deps / interface.Tpo"; exit 1; fi
if gcc-DHAVE_CONFIG_H-I. - I. I .. - DPACKAGE_DATA_DIR = \ "" / usr / local / share "\" DPACKAGE_LOCALE_DIR = \ "" / usr / local / / locale \ "-DPNG_NO_MMX_CODE -I/usr/include/gtk-2.0 -I/usr/lib / gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/glib-2.0 -I/usr/lib / glib-2.0/include -I/usr/include/freetype2 -I/usr/include/libpng12 -I/usr/include/pixman-1-g-O2-MT callbacks.o-MD-MP-MF ". deps / callbacks.Tpo "-c-o callbacks.o callbacks.c \
then mv-f ".deps / callbacks.Tpo" ".deps / callbacks.Po"; else rm-f ".deps / callbacks.Tpo"; exit 1; fi
callbacks.c: 9:18: Error: pcap.h: No such file or directory
In file included from PacketSource.h: 31,
from callbacks.c: 24:
/ usr / include / linux / wireless.h: 660: Error: expected specifier-qualifier-list before "__s32"
/ usr / include / linux / wireless.h: 673: Error: expected specifier-qualifier-list before "__u16"
/ usr / include / linux / wireless.h: 687: Error: expected specifier-qualifier-list before "__s32"
/ usr / include / linux / wireless.h: 698: Error: expected specifier-qualifier-list before "__u8"
/ usr / include / linux / wireless.h: 714: Error: expected specifier-qualifier-list before "__u32"
/ usr / include / linux / wireless.h: 727: Error: expected specifier-qualifier-list before "__u32"
/ usr / include / linux / wireless.h: 754: Error: expected specifier-qualifier-list before "__u8"
/ usr / include / linux / wireless.h: 816: Error: expected specifier-qualifier-list before "__u32"
/ usr / include / linux / wireless.h: 830: Error: expected specifier-qualifier-list before "__u16"
/ usr / include / linux / wireless.h: 844: Error: expected specifier-qualifier-list before "__u32"
/ usr / include / linux / wireless.h: 852: Error: expected specifier-qualifier-list before "__u32"
/ usr / include / linux / wireless.h: 861: Error: expected specifier-qualifier-list before "__u32"
/ usr / include / linux / wireless.h: 873: Error: expected specifier-qualifier-list before "__u16"
/ usr / include / linux / wireless.h: 896: Error: 'IFNAMSIZ "is not declared (not in a position)
/ usr / include / linux / wireless.h: 911: Error: expected specifier-qualifier-list before "__u32"
/ usr / include / linux / wireless.h: 955: Error: expected specifier-qualifier-list before "__u32"
/ usr / include / linux / wireless.h: 1059: Error: expected specifier-qualifier-list before "__u32"
/ usr / include / linux / wireless.h: 1077: Error: expected specifier-qualifier-list before "__u16"
In file included from callbacks.c: 24:
PacketSource.h: 153: Error: expected specifier-qualifier-list before "pcap_t"
PacketSource.h: 178: Warning: 'struct pcap_pkthdr "within parameters declared list
PacketSource.h: 178: Warning: its scope covers only this definition or declaration, which you probably did not want
PacketSource.h: 179: Warning: 'struct pcap_pkthdr "within parameters declared list
callbacks.c: 79: error: 'PCAP_ERRBUF_SIZE "is not declared (not in a position)
callbacks.c: deactivated fillDeviceList ":
callbacks.c: 121: Error: Memory size of "ir" is unknown
callbacks.c: 129: Error: "IFF_LOOPBACK" not declared (first use in this function)
callbacks.c: 129: Error: (Each name is declared not only repeated
callbacks.c: 129: error: for each function in which it occurs.)
make [2]: *** [callbacks.o] Error 1
make [2]: Leave directory '/ home/vossi/tmp/airsnort-0.2.7e/src'
make [1]: *** [all-recursive] Error 1
make [1]: Leave directory '/ home/vossi/tmp/airsnort-0.2.7e'
make: *** [all] Error 2

```

It appears the first error message is 

> callbacks.c: 9:18: Error: pcap.h: No such file or directory

`apt-file search pcap.h`  lists libpcap0.8-dev. (See [http://packages.ubuntu.com/hardy/libpcap0.8-dev](http://packages.ubuntu.com/hardy/libpcap0.8-dev)) So it looks like you need to 
```

sudo apt-get install libpcap0.8-dev
```

---

### Post by Vossibear on 2008-07-07
Ou I thought it would be installed.

build-essential is installed :)

So after installtion of libpcap0.8 there is the following print (Google translation)

> 
vossi helmut @: ~ / tmp/airsnort-0.2.7e $ sudo. / configure 
[sudo] password for vossi: 
checking for a BSD-compatible install ... / usr / bin / install-c 
checking whether build environment is sane ... Yes 
Checking for gawk ... No. 
Checking for mawk ... mawk 
checking whether make sets $ (MAKE) ... Yes 
checking whether to enable maintainer-specific portions of Makefiles ... No. 
checking for style of include used by make ... GNU 
Checking for GCC ... GCC 
checking for C compiler default output file name ... a.out 
checking whether the C compiler works ... Yes 
checking whether we are cross compiling ... No. 
checking for suffix of executables ... 
checking for suffix of object files ... o 
checking whether we are using the GNU C compiler ... Yes 
checking whether accepts gcc-g ... Yes 
checking for gcc option to accept ANSI C. .. none needed 
checking dependency style of gcc ... gcc3 
checking for library containing strerror ... none required 
Checking for GCC ... (cached) GCC 
checking whether we are using the GNU C compiler ... (cached) Yes 
checking whether accepts gcc-g ... (cached) Yes 
checking for gcc option to accept ANSI C. .. (cached) none needed 
checking dependency style of gcc ... (cached) gcc3 
Checking for GCC ... (cached) GCC 
checking whether we are using the GNU C compiler ... (cached) Yes 
checking whether accepts gcc-g ... (cached) Yes 
checking for gcc option to accept ANSI C. .. (cached) none needed 
checking dependency style of gcc ... (cached) gcc3 
checking how to run the C preprocessor ... GCC-E 
Checking for egrep ... grep-E 
checking for ANSI C header files ... Yes 
checking for pkg-config ... / usr / bin / pkg-config 
checking for gtk + -2.0> = 2.0.0 ... Yes 
Checking PACKAGE_CFLAGS ... - DPNG_NO_MMX_CODE -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango -1.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/freetype2 -I/usr/include/libpng12 -I/usr/include/pixman-1 
Checking PACKAGE_LIBS ... - lgtk-x11-2.0-lgdk-x11-2.0-latk-1.0-lgdk_pixbuf-2.0-lm-lpangocairo-1.0-lpango-1.0-lcairo-lgobject 2.0 lgmodule 2.0 ldl-lglib-2.0 
configure: creating. / config.status 
config.status: creating Makefile 
config.status: creating src / Makefile 
config.status: creating man / Makefile 
config.status: creating config.h 
config.status: executing depfiles commands 
vossi helmut @: ~ / $ sudo make tmp/airsnort-0.2.7e 
Make all-recursive 
make [1]: Enter the directory '/ home/vossi/tmp/airsnort-0.2.7e' 
Making all in SRC 
make [2]: Enter the directory '/ home/vossi/tmp/airsnort-0.2.7e/src' 
if gcc-DHAVE_CONFIG_H-I. - I. I .. - DPACKAGE_DATA_DIR = \ "" / usr / local / share "\" DPACKAGE_LOCALE_DIR = \ "" / usr / local / / locale \ "-DPNG_NO_MMX_CODE -I/usr/include/gtk-2.0 -I/usr/lib / gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/glib-2.0 -I/usr/lib / glib-2.0/include -I/usr/include/freetype2 -I/usr/include/libpng12 -I/usr/include/pixman-1-g-O2-MT main.o-MD-MP-MF ". deps / main.Tpo "-c-o main.o main.c \ 
then mv-f ".deps / main.Tpo" ".deps / main.Po"; else rm-f ".deps / main.Tpo"; exit 1; fi 
if gcc-DHAVE_CONFIG_H-I. - I. I .. - DPACKAGE_DATA_DIR = \ "" / usr / local / share "\" DPACKAGE_LOCALE_DIR = \ "" / usr / local / / locale \ "-DPNG_NO_MMX_CODE -I/usr/include/gtk-2.0 -I/usr/lib / gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/glib-2.0 -I/usr/lib / glib-2.0/include -I/usr/include/freetype2 -I/usr/include/libpng12 -I/usr/include/pixman-1-g-O2-MT support.o-MD-MP-MF ". deps / support.Tpo "-c-o support.o support.c \ 
then mv-f ".deps / support.Tpo" ".deps / support.Po"; else rm-f ".deps / support.Tpo"; exit 1; fi 
if gcc-DHAVE_CONFIG_H-I. - I. I .. - DPACKAGE_DATA_DIR = \ "" / usr / local / share "\" DPACKAGE_LOCALE_DIR = \ "" / usr / local / / locale \ "-DPNG_NO_MMX_CODE -I/usr/include/gtk-2.0 -I/usr/lib / gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/glib-2.0 -I/usr/lib / glib-2.0/include -I/usr/include/freetype2 -I/usr/include/libpng12 -I/usr/include/pixman-1-g-O2-MT interface.o-MD-MP-MF ". deps / interface.Tpo "-c-o interface.o interface.c \ 
then mv-f ".deps / interface.Tpo" ".deps / interface.Po"; else rm-f ".deps / interface.Tpo"; exit 1; fi 
if gcc-DHAVE_CONFIG_H-I. - I. I .. - DPACKAGE_DATA_DIR = \ "" / usr / local / share "\" DPACKAGE_LOCALE_DIR = \ "" / usr / local / / locale \ "-DPNG_NO_MMX_CODE -I/usr/include/gtk-2.0 -I/usr/lib / gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/glib-2.0 -I/usr/lib / glib-2.0/include -I/usr/include/freetype2 -I/usr/include/libpng12 -I/usr/include/pixman-1-g-O2-MT callbacks.o-MD-MP-MF ". deps / callbacks.Tpo "-c-o callbacks.o callbacks.c \ 
then mv-f ".deps / callbacks.Tpo" ".deps / callbacks.Po"; else rm-f ".deps / callbacks.Tpo"; exit 1; fi 
In file included from PacketSource.h: 31, 
                  from callbacks.c: 24: 
/ usr / include / linux / wireless.h: 660: Error: expected specifier-qualifier-list before "__s32" 
/ usr / include / linux / wireless.h: 673: Error: expected specifier-qualifier-list before "__u16" 
/ usr / include / linux / wireless.h: 687: Error: expected specifier-qualifier-list before "__s32" 
/ usr / include / linux / wireless.h: 698: Error: expected specifier-qualifier-list before "__u8" 
/ usr / include / linux / wireless.h: 714: Error: expected specifier-qualifier-list before "__u32" 
/ usr / include / linux / wireless.h: 727: Error: expected specifier-qualifier-list before "__u32" 
/ usr / include / linux / wireless.h: 754: Error: expected specifier-qualifier-list before "__u8" 
/ usr / include / linux / wireless.h: 816: Error: expected specifier-qualifier-list before "__u32" 
/ usr / include / linux / wireless.h: 830: Error: expected specifier-qualifier-list before "__u16" 
/ usr / include / linux / wireless.h: 844: Error: expected specifier-qualifier-list before "__u32" 
/ usr / include / linux / wireless.h: 852: Error: expected specifier-qualifier-list before "__u32" 
/ usr / include / linux / wireless.h: 861: Error: expected specifier-qualifier-list before "__u32" 
/ usr / include / linux / wireless.h: 873: Error: expected specifier-qualifier-list before "__u16" 
/ usr / include / linux / wireless.h: 896: Error: 'IFNAMSIZ "is not declared (not in a position) 
/ usr / include / linux / wireless.h: 911: Error: expected specifier-qualifier-list before "__u32" 
/ usr / include / linux / wireless.h: 955: Error: expected specifier-qualifier-list before "__u32" 
/ usr / include / linux / wireless.h: 1059: Error: expected specifier-qualifier-list before "__u32" 
/ usr / include / linux / wireless.h: 1077: Error: expected specifier-qualifier-list before "__u16" 
callbacks.c: deactivated fillDeviceList ": 
callbacks.c: 121: Error: Memory size of "ir" is unknown 
callbacks.c: 129: Error: "IFF_LOOPBACK" not declared (first use in this function) 
callbacks.c: 129: Error: (Each name is declared not only repeated 
callbacks.c: 129: error: for each function in which it occurs.) 
make [2]: *** [callbacks.o] Error 1 
make [2]: Leave directory '/ home/vossi/tmp/airsnort-0.2.7e/src' 
make [1]: *** [all-recursive] Error 1 
make [1]: Leave directory '/ home/vossi/tmp/airsnort-0.2.7e' 
make: *** [all] Error 2


I want to install airsnort if it is possible ... I would be very happy ... but I don't understand the Errormessage

Thx

---

### Post by unutbu on 2008-07-07
(1) You are not alone. If you google your error message, many people are reporting the same compile error.
(2) The fix seems to be to use a patch to include <linux/types.h> and <linux/wireless.h> in various places. 
(3) A debian developer, Noèl Köthe <noel@debian.org> says

> Date: Sun, 23 Mar 2008 14:40:51 +0100
Hello,

I'm closing all bugs from the Debian airsnort package because it is
removed from Debian since some time.
There is no upstream activity in more than 3 years and there is a better
and active maintained alternative aircrack-ng:

[http://sf.net/projects/airsnort](http://sf.net/projects/airsnort)
[http://www.aircrack-ng.org](http://www.aircrack-ng.org)
[http://packages.debian.org/aircrack-ng](http://packages.debian.org/aircrack-ng)


See
[http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=425958](http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=425958)

---

### Post by Vossibear on 2008-07-07
Big Thanks for that ...

OK no qirsnort ... I will try vmware and backtrack ... I hope it will works ... THANX

---

### Post by kevdog on 2008-07-07
What's wrong with aircrack-ng?  I can verify this works.  If you are using this to crack WEP, I can verify it works.

---

### Post by Vossibear on 2008-07-07
OK
So I will try this and for practise I will try to install BT on VMware

---

### Post by dracayr on 2008-07-07
to change a language in a terminal to english:

```

set LANG=en_US.UTF-8

```

---

### Post by Vossibear on 2008-07-07
I have downloaded the Backtrack version for VMware ... and I have installed VMware and there a virtual machine with Linux 64bit. 

So what I have to do now? When I copy Backtrack in the folder of the virtual machine is it searching for a bootable device ...

---

