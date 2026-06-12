---
title: "Help to compile the WaveWatch3 code"
date: 2017-06-26
forum: Packaging and Compiling Programs
---

### Post by doum2 on 2017-06-26
Hello, everyone and thank's for help
i'm using ubuntu 16.04 LTS in my portable PC, and i try to compile source code of Wavewatch3 model (oceanographic model developed by NOAA) using Fortran code
i folow the steps to compile code from this siteweb "https://forge.ifremer.fr/plugins/mediawiki/wiki/ww3/index.php/En:installation" , the are 2 scripts called (comp and link) that need to be editing before executing the make script but unfortunatly i have error in log file saying (w3iogrmd.F90 :229: Error: Can't open included file 'mpif.h'

so if you can help me pleasss

---

### Post by howefield on 2017-06-26
Thread moved to the "*Packaging and Compiling Programs*" forum.

---

### Post by steeldriver on 2017-06-27
It looks like it is expecting to find an MPI development subsystem (libopenmpi-dev or libmpich-dev) - however my google-fu fails to find any documentation that suggests which is preferred

Alternatively, there may be a way to configure it to build without MPI if you don't need that?

---

### Post by doum2 on 2017-06-27
hello, finaly i find the solution to probleme when configure the comp file choose mpif90 compiler

---

### Post by doum2 on 2017-06-28
Hello, thank's for reply, i found how to fix that, all compilation work fine ;)  thank you

---

