---
title: "sound playback"
date: 2008-10-24
forum: New to Ubuntu
---

### Post by johntravis on 2008-10-24
I know I have been here before but being stuborn makes a person want to learn more. In system/ preference/ sound/ I have sound playback in all but the "sound capture" which I believe is stopping me from hearing the sound tracks when playing dvd movies. I have installed all I can plus the "restricted extras". Any thoughts?

---

### Post by LowSky on 2008-10-24
you need the libdvdcss2 file open a terminal and copy paste these commands

```
wget -c http://packages.medibuntu.org/pool/free/libd/libdvdcss/libdvdcss2_1.2.9-2medibuntu4_i386.deb

sudo dpkg -i libdvdcss2_1.2.9-2medibuntu4_i386.deb

```

then resart X 

Ctrl+Alt=Backspace

your good to go

---

### Post by johntravis on 2008-10-24
Lowsky, you added   then resartx   ctrl+alt+backspace   are these commands, am I suppose to do something else?

---

### Post by johntravis on 2008-10-24
does "then resart x" and "Ctrl+ alt + backspace" have any significance.

---

