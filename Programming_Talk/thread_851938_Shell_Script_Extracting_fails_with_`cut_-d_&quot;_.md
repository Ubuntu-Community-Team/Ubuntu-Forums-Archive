---
title: "Shell Script: Extracting fails with `cut -d &quot; &quot; -f 14`"
date: 2008-07-07
forum: Programming Talk
---

### Post by jo.angel on 2008-07-07
Hello everyone out there. I am trying to extract the Source IP from my logfiles for further use. My logfile looks something like this:
```
Jul  6 11:34:58 test kernel: [ 1234.56789 ] 
DROP IN=ppp0 OUT= MAC= SRC=77.777.77.787 
DST=88.888.88.878 LEN=52 TOS=0x00 PREC=0x00 
TTL=62 ID=10941 DF PROTO=TCP SPT=12345 
DPT=23456 WINDOW=60352 RES=0x00 SYN URGP=0 
```
As I am not very experienced I did the following
Extracting the string SRC=whatever and then removing the first 4 bits with:
```
(...)    cut -d " " -f 13 | cut -c 5-19`
```Now this might not be from the book, but it basically seemed to work, but:

Every now and then I have to amend the field number (example above: 13), otherwise I get "DST=whatever" or even "MAC=whatever". My solution just cant grab the wanted string reliably. I assume this is, because the entries do not follow exactly the same pattern of fields..?

I would be very greatful for a solution, which allows me to extract any given string, which starts with a certain pattern (here: SRC=), and ends with a certain pattern (here: " " or TAB)

Thanks a lot, my researches just did not lead to any solution.

---

### Post by Xavieran on 2008-07-07
You could try using a scripting language like Python or Perl (python is best though).

You could also use the sed command to extract it (man sed or search google).

Emmanuel

---

### Post by ghostdog74 on 2008-07-07
cut is not the correct tool to do such tasks
if SRC is not at a specific position everytime 
```

awk '/SRC/{
  for(i=1;i<=NF;i++) {
   if ( $i ~ /SRC/ ){
     n=split($i,a,"=")
     print "SRC is " a[2]     
   }
  }
}' file

```

---

### Post by gnusci on 2008-07-07
Try

```
fmt -s | cut -d" " -f5 | cut -c 5-9

```

EDIT: I used as input the single line

> DROP IN=ppp0 OUT= MAC= SRC=77.777.77.787

---

### Post by WW on 2008-07-07
Or
```

egrep -o 'SRC=[0-9.]+' | cut -d '=' -f 2

```
E.g.
```

$ cat logfile.txt 
Jul  6 11:34:58 test kernel: [ 1234.56789 ] 
DROP IN=ppp0 OUT= MAC= SRC=77.777.77.787 
DST=88.888.88.878 LEN=52 TOS=0x00 PREC=0x00 
TTL=62 ID=10941 DF PROTO=TCP SPT=12345 
DPT=23456 WINDOW=60352 RES=0x00 SYN URGP=0
$ egrep -o 'SRC=[0-9.]+' logfile.txt                  
SRC=77.777.77.787
$ egrep -o 'SRC=[0-9.]+' logfile.txt | cut -d '=' -f 2
77.777.77.787
$ 

```

---

### Post by jo.angel on 2008-07-07
Thanks for all your replies. I am just comin ghome and have given a quick try to

```
egrep -o 'SRC=[0-9.]+' | cut -d '=' -f 2
```This works fine.

Nevertheless I will check out the other suggestions, especially sed.
awk seems a bit tricky for my level of skills.

```
fmt -s | cut -d" " -f5 | cut -c 5-9
``` I am not sure if this will work reliably, as SRC MUST always be in the 5th position, which was my problem in the first time. My makes hift siolution assumed similar, that SRC was in the 13th position and that didn't work reliable. 

Thanks anyway to all of you. The egrep solution works fine, and I am familiar with grepping stuff.

---

### Post by ghostdog74 on 2008-07-07
> **jo.angel said:**
> Thanks for all your replies. I am just comin ghome and have given a quick try to

```
egrep -o 'SRC=[0-9.]+' | cut -d '=' -f 2
```This works fine.

Nevertheless I will check out the other suggestions, especially sed.
awk seems a bit tricky for my level of skills.

the awk solution is just the longer equivalent of -o option of egrep. use the egrep solution if it satisfy your requirement.

> 
```
fmt -s | cut -d" " -f5 | cut -c 5-9
``` I am not sure if this will work reliably, as SRC MUST always be in the 5th position, which was my problem in the first time. My makes hift siolution assumed similar, that SRC was in the 13th position and that didn't work reliable. 

no, it will not work correctly.

---

