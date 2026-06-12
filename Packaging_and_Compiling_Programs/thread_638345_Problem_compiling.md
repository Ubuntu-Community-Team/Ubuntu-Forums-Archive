---
title: "Problem compiling"
date: 2007-12-11
forum: Packaging and Compiling Programs
---

### Post by wrparks on 2007-12-11
To start with, the program I want to compile can be found here under "C source and pyton scripts" at the top [http://www.stats.ox.ac.uk/~lyngsoe/beagle/](http://www.stats.ox.ac.uk/~lyngsoe/beagle/)  .  It's a population genetic analysis program.

So, I have a Mepis system, and recently set up a ubuntu system.  In order to get these to compile in Mepis, i had to install Flex, Bison, and upgrade Python.  I did this through the package manager for Mepis (I think it was apt, but can't remember for sure).  Once I did all that "make greven" worked perfect and the program has been running since the day before thanksgiving.  Yes, these take forever to run, which is why I have set up another PC.

On the Ubuntu system, I have not been able to get it to compile no matter what I do.  I'm certain it's a problem with one of the languages, but I'm am a biologist with some computer knowledge who likes linux, not a programmer.  Any ideas.  When I get to the lab tomorrow I'll post the actual error message produced.

I did manage to get it to run by copying the compiled mepis folder to Ubuntu via flash drive, but now I want to know what I did wrong.  I know, I could set up another Mepis system, but I want to play with Ubuntu for a while on the governments dime.
thanks.

---

### Post by wrparks on 2007-12-12
Here are the error logs:

ryan@ryan-desktop:~/Desktop/Pop_genetics/test$ make greven
gcc -O3 -DHAPLOTYPE_BLOCKS -DBEAGLE_HAPLOTYPEHEURISTIC -DBEAGLE_DONOTSTORELEAVES -DENUMERATE_DONOTSTORELEAVES -DENUMERATE_HAPLOTYPEHEURISTIC   -c -o greven.o greven.c
greven.c:7:19: error: stdio.h: No such file or directory
greven.c:8:20: error: stdlib.h: No such file or directory
greven.c:9:20: error: unistd.h: No such file or directory
In file included from greven.c:11:
gene.h:70: error: expected declaration specifiers or ‘...’ before ‘FILE’
gene.h:71: error: expected declaration specifiers or ‘...’ before ‘FILE’
gene.h:72: error: expected declaration specifiers or ‘...’ before ‘FILE’
gene.h:103: error: expected declaration specifiers or ‘...’ before ‘FILE’
gene.h:104: error: expected declaration specifiers or ‘...’ before ‘FILE’
In file included from common.h:8,
                 from greven.c:13:
arg.h:73: error: expected declaration specifiers or ‘...’ before ‘FILE’
In file included from greven.c:13:
common.h:40: error: expected ‘)’ before ‘*’ token
common.h:41: error: expected ‘)’ before ‘*’ token
greven.c:15: error: expected ‘)’ before ‘*’ token
greven.c:34: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
greven.c: In function ‘print_state’:
greven.c:38: error: ‘state_file’ undeclared (first use in this function)
greven.c:38: error: (Each undeclared identifier is reported only once
greven.c:38: error: for each function it appears in.)
greven.c:38: error: ‘NULL’ undeclared (first use in this function)
greven.c:38: error: too many arguments to function ‘output_genes’
greven.c:39: warning: incompatible implicit declaration of built-in function ‘fprintf’
greven.c: In function ‘main’:
greven.c:62: error: ‘stdout’ undeclared (first use in this function)
greven.c:63: warning: incompatible implicit declaration of built-in function ‘exit’
greven.c:66: error: ‘stderr’ undeclared (first use in this function)
greven.c:70: warning: incompatible implicit declaration of built-in function ‘sscanf’
greven.c:70: error: ‘optarg’ undeclared (first use in this function)
greven.c:71: warning: incompatible implicit declaration of built-in function ‘fprintf’
greven.c:80: warning: incompatible implicit declaration of built-in function ‘fprintf’
greven.c:106: error: ‘state_file’ undeclared (first use in this function)
greven.c:106: error: ‘NULL’ undeclared (first use in this function)
greven.c:111: warning: incompatible implicit declaration of built-in function ‘fprintf’
greven.c:130: error: ‘optind’ undeclared (first use in this function)
greven.c:132: warning: incompatible implicit declaration of built-in function ‘fprintf’
greven.c:133: warning: incompatible implicit declaration of built-in function ‘exit’
greven.c:138: warning: incompatible implicit declaration of built-in function ‘fprintf’
greven.c:139: warning: incompatible implicit declaration of built-in function ‘exit’
greven.c:148: error: too many arguments to function ‘output_annotatedgenes’
greven.c:159: error: ‘free’ undeclared (first use in this function)
greven.c:171: warning: incompatible implicit declaration of built-in function ‘printf’
greven.c:176: warning: incompatible implicit declaration of built-in function ‘printf’
make: *** [greven.o] Error 1
ryan@ryan-desktop:~/Desktop/Pop_genetics/test$

---

### Post by meatpan on 2007-12-12
Compilation utilities and development libraries/headers are not bundled with the default ubuntu installations, so you need to install them manually.   The following command should install everything you need to get started:
```
 sudo apt-get install build-essential
```

Does this help?

---

### Post by wrparks on 2007-12-12
It did indeed it, thanks a lot.  I have another question, but I'll start another post.

Thanks again.

---

