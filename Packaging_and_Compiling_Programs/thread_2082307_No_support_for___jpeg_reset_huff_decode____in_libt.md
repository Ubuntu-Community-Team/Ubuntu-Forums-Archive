---
title: "No support for   jpeg_reset_huff_decode    in libtiff ?"
date: 2012-11-09
forum: Packaging and Compiling Programs
---

### Post by akazia on 2012-11-09
Hello 

I am compiling an old private program on ubuntu 12.10.
While doing this I get the following error message:

/usr/lib/libtiff.so.3: undefined reference to `jpeg_reset_huff_decode'

I have googled all sources up and down but I did not find a workable solution. 
I seams that the ojepg support fails. Did any one come across this problem,
or even better any hint to solve this prob??

Thank in advance
Michael

---

### Post by Bachstelze on 2012-11-09
Please provide the complete output of your compilation command (including the command itself), not just a small piece of it.

---

### Post by akazia on 2012-11-09
Hello, 

this is the output I get:

src$ make
cc bem.o chip.o konto.o main.o zahl.o makro.o suchen.o stamm1.o stamm2.o brief.o pkas.o abr.o plancom.o antrag.o beleg.o plan.o scan.o listen.o termin.o vergabe.o warten.o blz.o leist.o labor.o punkt.o kasse.o erin.o scriber.o fliste.o addr.o konf.o abr_utils.o formulare.o xray.o indikation.o hand.o kennw.o befund01.o ip1.o zahnstatus.o todo.o fax.o zaster.o vorlage.o appmain.o wichtig.o wochen.o weriswo.o kig.o stamm3.o autoarchiv.o postit.o rate.o news.o ooexport.o knr-12.fpo sms.o laborxml.o planlabor.o -Llib -L/opt/lib -L/usr/X11R6/lib -L/opt/gnome/lib -lpost -lxml2 -lXmt -ltab -lXbae -lXpm -ljpeg -lXm  -lXt -lXmu -lXext -lX11 -lSM -lICE -lImlib -lpost -lpq -lm -lcrypt -o /opt/db/bin/abr
/usr/lib/libtiff.so.3: undefined reference to `jpeg_reset_huff_decode'
collect2: Fehler: ld gab 1 als Ende-Status zurück
make: *** [/opt/db/bin/abr] Fehler 1

Hope this is what provides further information
Michael

---

### Post by MadCow108 on 2012-11-09
there is no packaged /usr/lib/libtiff.so.3 in 12.10
its probably a remnant from an upgrade
install libtiff-dev (which points to libtiff5-dev) or libtiff4-dev

---

### Post by akazia on 2012-11-10
Hi there,

after renaming the libtiff.so.3  the compile went much further unfortunately the program requires the libtiff.so.3 is there any simple way to keep  the libtiff.s0.3 

apt-fiel does not provide any info that the libtiff3 ist availabe 

Thanks a lot
Michael

/usr/bin/ld: warning: libtiff.so.3, needed by /usr/lib//libImlib.so, not found (try using -rpath or -rpath-link)
/usr/lib//libImlib.so: undefined reference to `TIFFReadRGBAImage'
/usr/lib//libImlib.so: undefined reference to `TIFFGetField'
/usr/lib//libImlib.so: undefined reference to `TIFFScanlineSize'
/usr/lib//libImlib.so: undefined reference to `TIFFSetField'
/usr/lib//libImlib.so: undefined reference to `_TIFFfree'
/usr/lib//libImlib.so: undefined reference to `_TIFFmalloc'
/usr/lib//libImlib.so: undefined reference to `TIFFFdOpen'
/usr/lib//libImlib.so: undefined reference to `TIFFWriteScanline'
/usr/lib//libImlib.so: undefined reference to `TIFFOpen'
/usr/lib//libImlib.so: undefined reference to `TIFFClose'
/usr/lib//libImlib.so: undefined reference to `TIFFDefaultStripSize'
collect2: Fehler: ld gab 1 als Ende-Status zurück
make: *** [/opt/db/bin/abr] Fehler 1

---

