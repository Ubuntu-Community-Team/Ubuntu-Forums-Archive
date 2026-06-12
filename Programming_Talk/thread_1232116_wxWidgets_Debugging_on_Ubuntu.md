---
title: "wxWidgets Debugging on Ubuntu"
date: 2009-08-05
forum: Programming Talk
---

### Post by igi_ubu on 2009-08-05
[FONT=Tahoma][SIZE=3]Hello, 

I have recently switched my PC to Ubuntu (9.04), so I am trying to convert my code to wxGTK (preliminary migration to wxWin was in progress, in early alfa-version). 

Now the problem is that I am able to build my app with "debug" switch on, but can't make it run or start the debugger. 

I use CodeBlocks 8.02, wxgtk 2.8. The debugger is gdb 6.8. 

The debugger log I get is the following: [/SIZE][/FONT]        
 > LD_LIBRARY_PATH=.:
Command-line: /usr/bin/gdb -nx -fullname  -quiet -args ./Debug_GTK/bilancio
Working dir : /media/Documenti/Documenti/Programmazione/Bilancio_3-0/
> set prompt >>>>>>cb_gdb:
(gdb) >>>>>>cb_gdb:
> show version
GNU gdb 6.8-debian
Copyright (C) 2008 Free Software Foundation, Inc.
License GPLv3+: GNU GPL version 3 or later <http://gnu.org/licenses/gpl.html>
This is free software: you are free to change and redistribute it.
There is NO WARRANTY, to the extent permitted by law.  Type "show copying"
and "show warranty" for details.
This GDB was configured as "i486-linux-gnu".
>>>>>>cb_gdb:
> set confirm off
>>>>>>cb_gdb:
> set width 0
>>>>>>cb_gdb:
> set height 0
>>>>>>cb_gdb:
> set breakpoint pending on
>>>>>>cb_gdb:
> set print asm-demangle on
>>>>>>cb_gdb:
> set unwindonsignal on
>>>>>>cb_gdb:
> set disassembly-flavor intel
>>>>>>cb_gdb:
> cd ./Debug_GTK
>>>>>>cb_gdb:
> directory /media/Documenti/Documenti/Programmazione/Bilancio_3-0/
>>>>>>cb_gdb:
> break "/media/Documenti/Documenti/Programmazione/Bilancio_3-0/bilancio.cpp:70"
Breakpoint 1 at 0x805ba7e: file /media/Documenti/Documenti/Programmazione/Bilancio_3-0/bilancio.cpp, line 70.
>>>>>>cb_gdb:
> run
/bin/bash: /media/Documenti/Documenti/Programmazione/Bilancio_3-0/Debug_GTK/bilancio: Permesso negato
/bin/bash: /media/Documenti/Documenti/Programmazione/Bilancio_3-0/Debug_GTK/bilancio: Riuscito
Program exited with code 01.
You can't do that without a process to debug.
>>>>>>cb_gdb:
> quit
[FONT=Tahoma][SIZE=3]Can anybody advice me? 

Thank you very much! 

igi[/SIZE][/FONT]

---

### Post by jero3n on 2009-08-05
> /bin/bash: /media/Documenti/Documenti/Programmazione/Bilancio_3-0/Debug_GTK/bilancio: Permesso negato
Permission Denied?
Try moving your source project to your home directory, rebuild and retry.

---

### Post by igi_ubu on 2009-08-05
> **jero3n said:**
> Permission Denied?
Try moving your source project to your home directory, rebuild and retry.
Thank you jero!

I had this suspect also... I tried to edit permissions many times. Moving the project made it work.

---

