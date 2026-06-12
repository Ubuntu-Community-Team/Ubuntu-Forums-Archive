---
title: "dd_rescue multiple files with 'for' syntax in bash"
date: 2011-01-04
forum: Programming Talk
---

### Post by randras_lavos on 2011-01-04
[FONT=Times New Roman][SIZE=1]*sorry my english

hello, Ubuntu Forum.. ):P

this is my case,
my sister has a 320GB 3,5" harddisk with bad sectors, windows failed detect it, i've tried almost all of kind- recovery software under windows, and all of those are failed:mad:
So, i installed ubuntu in another harddisk. Lucky me,i have recovered about 82% of all files and directory folders using syntax mix of 'mkisofs','dd', 'dd_rescue' and 'ddrescue' in terminal. 
For the rest 18% (bad sector) i'm going to use .sh script in order to get quick result on folders in bad area sector. 
so my questions are[/SIZE][/FONT] 

[LIST=1]
[*][FONT=Franklin Gothic Medium][SIZE=2]**Could the 'dd' / 'dd_rescue' / 'ddrescue'  handle multiple files in a directory?**[/SIZE][/FONT]
[*][FONT=Franklin Gothic Medium][SIZE=2]**I wanna make a .sh script to 'dd_rescue' of some folders  in "/mnt/disk320/mydata" and files with extension *.docx, *.xls and *.vob _*only*_. In case 'cmd' windows (bat file) like this: **[/SIZE][/FONT]
[/LIST]
[FONT=Lucida Console][SIZE=1]@echo off
title test
for %i in ("d:\mydata\*.docx" "d:\school_data\private\*.xls" "f:\*.vob") do copy %i "c:\backup disk320\" [/SIZE][/FONT][FONT=Lucida Console]
[SIZE=1]exit

[SIZE=2]**[FONT=Franklin Gothic Medium]but replace the 'copy' command with 'dd_rescue' under linux[/FONT]**, [/SIZE][FONT=Franklin Gothic Medium][B][SIZE=2]like this:[/SIZE]
[/B][/FONT][/SIZE][/FONT][INDENT][SIZE=1][FONT=System]#! /bin/bash

for i in $(the kind of files maybe or something ); do 
    dd_rescue -fwrv -s 10 $i "/mnt/backupDisk/"

[/FONT][/SIZE][/INDENT]**[SIZE=2][FONT=Franklin Gothic Medium]syntax above is[/FONT][/SIZE] not finish yet, anyone could help for _advanced syntax_ maybe? (my english is bad, hope you guys understand my post)** :-PTHANK U, 
**Jbu**.

---

