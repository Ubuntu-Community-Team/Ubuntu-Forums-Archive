---
title: "/usr/bin/ld: cannot find -lncursesw"
date: 2013-02-06
forum: New to Ubuntu
---

### Post by sachin0091 on 2013-02-06
hey currently 'm working with some developmental issues of powertop
but 'm having trouble in "make"ing the code
and the error report from terminal is as shown below..
'm in need of some help... 'm glad if u do so..

THE STARRED LINES ARE  SPOTS OF ERRORS

sac@sac-pc$ make -w
make: Entering directory `/home/student/powertop-1.13'
cc -O1 -g -Wall -Wshadow -W -Wformat -Wimplicit-function-declaration -Wimplicit-int -D VERSION=\"1.13\"  powertop.o config.o process.o misctips.o bluetooth.o display.o suggestions.o wireless.o cpufreq.o sata.o xrandr.o ethernet.o cpufreqstats.o usb.o urbnum.o intelcstates.o wifi-new.o perf.o alsa-power.o ahci-alpm.o dmesg.o devicepm.o -lncursesw -o powertop
/usr/bin/ld: cannot find -lncursesw:KS
collect2: ld returned 1 exit status:KS:KS
make: *** [powertop] Error 1:KS:KS:KS
make: Leaving directory `/home/student/powertop-1.13'

kindly help me

---

### Post by schragge on 2013-02-06
```
sudo apt-get install libncursesw5-dev
```

---

### Post by sachin0091 on 2013-02-06
actually i want to remove tat libaray an make my code run wit out it..
how to know where exactly the error is coming from
mean to say which of the file o lines lik that..
 I DONT WANT MY FILE TO RUN USING NCURSES

---

### Post by schragge on 2013-02-06
PowerTop's README states
> 
in addition to that, PowerTOP requires the following components:

pciutils-devel (is only required if you have PCI) 
ncurses-devel  (required) 
libnl-devel    (required)
kernel version => 2.6.38

But if you're sure that it's not needed then you can try
```
make NCURSES_LIBS=
```

---

### Post by sachin0091 on 2013-02-07
the same error pop up again...
any other ways...???

---

### Post by MG&amp;TL on 2013-02-07
> **sachin0091 said:**
> the same error pop up again...
any other ways...???
 
You're trying to build a source tree that either a) requires curses or b) thinks that it does, hence the -lncurses flag.
 
Solutions:
 
a) Install ncurses.
b) Remove that flag from the makefile (or whichever build system you're using)

---

### Post by sachin0091 on 2013-02-08
how to remove it from make file:confused::confused:

---

### Post by MG&amp;TL on 2013-02-08
> **sachin0091 said:**
> how to remove it from make file:confused::confused:
 
What build system does powertop use? (If you don't know, what files are in the top-level directory?)

---

### Post by schragge on 2013-02-08
GNU Autotools: [https://github.com/fenrus75/powertop](https://github.com/fenrus75/powertop)

---

### Post by MG&amp;TL on 2013-02-09
> **schragge said:**
> GNU Autotools: [https://github.com/fenrus75/powertop](https://github.com/fenrus75/powertop)
 
Tbh I have no clue how to do that, and no wish to find out either. I suggest the OP reads up on autoconf.

---

### Post by r-senior on 2013-02-09
It's not a trivial job to remove ncurses support from a program like that. It's not just a matter of tinkering with the makefiles because the code expects to link to ncurses libraries. I picked one random .cpp file and it has references to curses all over it.

You'd have to remove the ncurses package and header checks in configure.ac and run autoreconf to regenerate the configure script. Then you'd run configure, which runs automake to regenerate the makefiles. Then you'd type make and get loads of errors, which you'd have to go and fix by removing the ncurses code. Apart from all of this being a painful process, you would probably introduce all sorts of bugs unless you understand the code intimately.

---

### Post by sachin0091 on 2013-02-11
how yo get to knw tat,that file which u reffered have ncurses dependencies all over it..
how to get to know tat...
i saw conf.c but found none dependencies related to ncurses in it...:popcorn:

---

### Post by schragge on 2013-02-11
> **sachin0091 said:**
> i saw conf.c but found none dependencies related to ncurses in it...
You probably mean *configure.ac*? The check for ncurses is there:
```

AC_SEARCH_LIBS([delwin], [ncursesw ncurses], [], AC_MSG_ERROR([ncurses is required but was not found]), [])

```

---

### Post by MG&amp;TL on 2013-02-11
> **sachin0091 said:**
> how yo get to knw tat,that file which u reffered have ncurses dependencies all over it..
how to get to know tat...
 
If you've programmed in *ncurses* before, you tend to get to know the library functions quite well,so you'll recognise them in cases like this.

---

### Post by schragge on 2013-02-12
Sorry, but why are you so wary of using ncurses? Look, it's not some obscure library used exclusively by PowerTop. It's very common, used by lots of packages, including nano, python, procps, and aptitude. Most probably, it's already installed on your system. Moreover, it's among *depends* of Ubuntu's [required seed]("http://people.canonical.com/%7Eubuntu-archive/germinate-output/ubuntu.precise/required"), and thus present on pretty much every Ubuntu installation.

---

### Post by sachin0091 on 2013-02-19
ITS BEEN SOLVED

all u need is go to the make file an remove -lncursesw5 in the linkage

all works fine

THANX to  1 an all who have helped me here

THANK U ALL my forum mates

'm glad to u all):P:D

---

