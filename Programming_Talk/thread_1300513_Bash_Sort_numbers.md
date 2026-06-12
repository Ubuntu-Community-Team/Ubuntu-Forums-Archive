---
title: "Bash Sort numbers"
date: 2009-10-25
forum: Programming Talk
---

### Post by sh85 on 2009-10-25
Hi everyone.
 
I have a file containing a list of names with a numbers attached, in the following format: 
 
[FONT=Arial][FONT=Verdana][SIZE=1]Francis,CEO,HQ,15000[/SIZE][/FONT][/FONT]
[FONT=Arial][FONT=Verdana][SIZE=1]Janine,CFO,Finance,12000 [/SIZE][/FONT][/FONT]
[FONT=Arial][FONT=Verdana][SIZE=1]Daniel,CIO,IT,12000[/SIZE][/FONT][/FONT]
[FONT=Arial][FONT=Verdana][SIZE=1]Bobby,Manager,IT,7200[/SIZE][/FONT][/FONT]
[FONT=Arial][FONT=Verdana][SIZE=1]Jenny,Secretary,HQ,2000[/SIZE][/FONT][/FONT]
 
[FONT=Arial][FONT=Verdana][SIZE=1][FONT=Arial][FONT=Verdana][SIZE=1][FONT=Arial][FONT=Verdana][SIZE=1]I am trying to make it sort the numbers at the last fields by either ascending or descending[/SIZE][/FONT][/FONT][/SIZE][/FONT][/FONT][/SIZE][/FONT][/FONT]
[FONT=Arial][SIZE=1][FONT=Arial][FONT=Verdana][SIZE=1][FONT=Arial]e.g.[/FONT][/SIZE][/FONT][/FONT][/SIZE][/FONT]
 
[FONT=Arial][FONT=Verdana][SIZE=1]Francis,CEO,HQ,15000[/SIZE][/FONT][/FONT]
[FONT=Arial][FONT=Verdana][SIZE=1]Daniel,CIO,IT,12000[/SIZE][/FONT][/FONT]
[FONT=Arial][FONT=Arial][FONT=Verdana][SIZE=1]Janine,CFO,Finance,12000 [/SIZE][/FONT][/FONT][/FONT]
[FONT=Arial][FONT=Arial][FONT=Verdana][SIZE=1][FONT=Arial][FONT=Verdana][SIZE=1][FONT=Arial][FONT=Verdana][SIZE=1]Bobby,Manager,IT,7200[/SIZE][/FONT][/FONT][/SIZE][/FONT][/FONT][/SIZE][/FONT][/FONT][/FONT]
[FONT=Arial][FONT=Arial][FONT=Verdana][SIZE=1][FONT=Arial][FONT=Verdana][SIZE=1][FONT=Arial][FONT=Verdana][SIZE=1][FONT=Arial][FONT=Verdana][SIZE=1][FONT=Arial][FONT=Verdana][SIZE=1][FONT=Arial][FONT=Verdana][SIZE=1]Jenny,Secretary,HQ,2000[/SIZE][/FONT][/FONT][/SIZE][/FONT][/FONT][/SIZE][/FONT][/FONT][/SIZE][/FONT][/FONT][/SIZE][/FONT][/FONT][/SIZE][/FONT][/FONT][/FONT]
 
 
For ascending i tried sort -t, -k4 file.txt and my results shows
[FONT=Arial][FONT=Verdana][SIZE=1]Daniel,CIO,IT,12000[/SIZE][/FONT][/FONT]
[FONT=Arial][FONT=Verdana][SIZE=1]Janine,CFO,Finance,12000 [/SIZE][/FONT][/FONT]
[FONT=Arial][FONT=Verdana][SIZE=1][FONT=Arial][FONT=Verdana][SIZE=1]Francis,CEO,HQ,15000[/SIZE][/FONT][/FONT]
[FONT=Arial][FONT=Verdana][SIZE=1][FONT=Arial][FONT=Verdana][SIZE=1][FONT=Arial][FONT=Verdana][SIZE=1]Jenny,Secretary,HQ,2000[/SIZE][/FONT][/FONT][/SIZE][/FONT][/FONT][/SIZE][/FONT][/FONT][/SIZE][/FONT][/FONT]
[FONT=Arial][FONT=Verdana][SIZE=1][FONT=Arial][FONT=Verdana][SIZE=1][FONT=Arial][FONT=Verdana][SIZE=1][FONT=Arial][FONT=Verdana][SIZE=1][FONT=Arial][FONT=Verdana][SIZE=1][FONT=Arial][FONT=Verdana][SIZE=1]Bobby,Manager,IT,7200[/SIZE][/FONT][/FONT][/SIZE][/FONT][/FONT][/SIZE][/FONT][/FONT][/SIZE][/FONT][/FONT][/SIZE][/FONT][/FONT][/SIZE][/FONT][/FONT]
 
[FONT=Arial][FONT=Verdana][SIZE=1][FONT=Arial][FONT=Verdana][SIZE=1][FONT=Arial][FONT=Verdana][SIZE=1][FONT=Arial][FONT=Verdana][SIZE=1][FONT=Arial][FONT=Verdana][SIZE=1][FONT=Arial][FONT=Verdana][SIZE=1]what did i do wrong? why does it not sorts the last field?[/SIZE][/FONT][/FONT][/SIZE][/FONT][/FONT][/SIZE][/FONT][/FONT][/SIZE][/FONT][/FONT][/SIZE][/FONT][/FONT][/SIZE][/FONT][/FONT]

---

### Post by ghostdog74 on 2009-10-25
you must make it sort by numeric, add the -n option

---

### Post by sh85 on 2009-10-25
ok. my mistake to overlook the -n option. Thanks anyway ghostdog74

---

