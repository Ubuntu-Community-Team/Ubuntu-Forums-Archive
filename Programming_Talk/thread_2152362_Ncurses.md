---
title: "Ncurses"
date: 2013-06-07
forum: Programming Talk
---

### Post by DeRpSoN on 2013-06-07
Hello!
So i got this problem: i cant compile programs (.c) that are using ncurses. 
Im programing noob so its probably my bad but still i thought that:
```
gc projekt1.c -o projekt1_done -l ncurses
```
is the way to compile programs with ncurses lib, right?
And the error i get is:
```
gcc: error: lncurses: No such file or directory
```
Could you please tell me what im doing wrong?

---

### Post by steeldriver on 2013-06-07
Hello and welcome to the forum

You probably need to install the ncurses5 development package

```

$ sudo apt-get update
$ sudo apt-get install libncurses5-dev
```

---

### Post by DeRpSoN on 2013-06-07
Did this already, it didnt work.

---

### Post by steeldriver on 2013-06-07
Hmm... I'm a bit surprised the error is coming from gcc itself since missing libraries are usually reported by the linker i.e.

```

$ gcc -o dostuff dostuff.c -l ncurses
/usr/bin/ld: cannot find -lncurses
collect2: ld returned 1 exit status

```

How exactly did you install gcc? what do

```

which ld

dpkg -l binutils

find /usr/lib -name 'libncurses.so'

```

say?

---

### Post by nvteighen on 2013-06-07
> **steeldriver said:**
> Hmm... I'm a bit surprised the error is coming from gcc itself since missing libraries are usually reported by the linker i.e.

```

$ gcc -o dostuff dostuff.c -l ncurses
/usr/bin/ld: cannot find -lncurses
collect2: ld returned 1 exit status

```

How exactly did you install gcc? what do

```

which ld

dpkg -l binutils

find /usr/lib -name 'libncurses.so'

```

say?

There should be no space between -l and ncurses, the flag must be **-lncurses**:

```

gcc -o whatever whatever.c -Wall -lncurses

```

---

### Post by DeRpSoN on 2013-06-08
```
$ which ld
/usr/bin/ld
$ dpkg -l binutils
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name           Version      Architecture Description
+++-==============-============-============-=================================
ii  binutils       2.23.2-2ubun amd64        GNU assembler, linker and binary 
~$ find /usr/lib -name 'libncurses.so'
/usr/lib/x86_64-linux-gnu/libncurses.so

```

Personally i dont know what i just did, but these are the effects of commands you wrote on my pc, if that means anything to you... :D

Also i upgraded ubuntu to the newest version hoping it to fix the problem but unfortunetly it didnt.

Btw:
```
$ sudo apt-get install libncurses5-dev
Reading package lists... Done
Building dependency tree       
Reading state information... Done
libncurses5-dev is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

```
it means that i already got ncurses but the problem remains

---

### Post by DeRpSoN on 2013-06-08
Alright i fixed it! It works :d but still - thank you guys!!!

---

### Post by steeldriver on 2013-06-08
OK that's good - fwiw it *is* conventional to not leave a space between the '-l' and the library name (i.e. [FONT=courier new] -lncurses[/FONT] not [FONT=courier new]-l ncurses[/FONT] like nvteighen says) however both should be acceptable - unless gcc has dropped POSIX support for that feature

From the gcc man page:
```

       -llibrary
       -l library
           Search the library named library when linking.  (The second alternative with the library as a separate argument is only for POSIX compliance and is not recommended.)

```

Both forms work on my system(s) (both 32 bit and 64 bit)

---

