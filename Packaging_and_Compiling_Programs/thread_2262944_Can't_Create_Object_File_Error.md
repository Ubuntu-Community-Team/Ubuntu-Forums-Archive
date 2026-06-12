---
title: "Can't Create Object File Error"
date: 2015-01-28
forum: Packaging and Compiling Programs
---

### Post by cranberries2 on 2015-01-28
[SIZE=2][FONT=comic sans ms]Hi, 
I am new to open source development. And, I am getting the following error in the path which I compile for arm; 

Assembler messages:
Fatal error: can't create bin/arm1176/blabla.o: No such file or directory
*** Error code 1
clearmake: Error: Build script failed for "bin/arm1176/blabla.o"

I've checked the related makefile. And it includes the following rules for blabla ; [/FONT][/SIZE]

[COLOR=#666666]# Libraries[/COLOR][COLOR=green]
[/COLOR][COLOR=green]

[OBJECTS]("http://devices-dev.global-ad.net:8080/openstage_v3r3/s?refs=OBJECTS") = [/COLOR]$([TESTOBJS]("http://devices-dev.global-ad.net:8080/openstage_v3r3/xref/Opera_Platform_Linux/GPAL/USB/makefile#TESTOBJS"))$([COLOR=#990099]LIBOBJS[/COLOR])[COLOR=green]
[/COLOR][COLOR=green]
[LIBOBJS_arm]("http://devices-dev.global-ad.net:8080/openstage_v3r3/s?refs=LIBOBJS_arm") = \
    [/COLOR]$([BIN]("http://devices-dev.global-ad.net:8080/openstage_v3r3/xref/Opera_Platform_Linux/GPAL/USB/makefile#BIN"))[COLOR=green]/[blabla.o]("http://devices-dev.global-ad.net:8080/openstage_v3r3/s?path=StringTokenizer.o") \
[/COLOR]
[SIZE=2][FONT=comic sans ms]Could you please mention about the possible causes of the problem ?[/FONT][/SIZE][COLOR=green]
[SIZE=2][FONT=comic sans ms]Thanks in advance for the replies, [/FONT][/SIZE]

[/COLOR]

---

### Post by pal4 on 2015-02-03
[FONT=arial]It seems the directory [COLOR=#000000]bin/arm1176/ does not exist. Assembler wants to put the output file there, but the directory was not created. Something is wrong in the makefile... [/COLOR][/FONT]

---

