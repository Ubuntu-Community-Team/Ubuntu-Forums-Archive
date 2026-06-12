---
title: "Installing xspim errors"
date: 2005-10-18
forum: Programming Talk
---

### Post by sapphirine on 2005-10-18
Hi,

I'm (attempting to) install the SPIM / MIPS R2000 simulator, from [http://www.cs.wisc.edu/~larus/spim.html]("http://www.cs.wisc.edu/~larus/spim.html").

The installation instructions say that I need to give the pathnames of the directory to intall the exception handler (exception.s), the program, and the manual pages.

I'm not sure exactly where to put them, but the default options doesn't work. When I type $ make, (the $ sign is already provided) the following appears:

make[1]: Entering directory `/home/sarah/spim-7.2.1/xspim'
bison -y -d ../CPU/parser.y
/bin/sh: bison: command not found
make[1]: *** [y.tab.c] Error 127
make[1]: Leaving directory `/home/sarah/spim-7.2.1/xspim'
make: *** [xspim] Error 2

Where do I install the files to? I don't want to have to go back to using the Windows version.

I'm running Hoary Hedgehog (V5.04) for AMD64.

Thanks,

Sarah

---

### Post by toojays on 2005-10-18
The error you are seeing is because you don't have bison installed. Install it (e.g. via synaptic package manager) and try again. If you get a different error (I suspect you will need some development libraries installed), come back and we'll try and help you again :)

By the way, there is an older version of spim (6.5) available in Ubuntu's multiverse repository.

---

### Post by jerome bettis on 2005-10-18
yeah you can apt-get spim and xspim i beleive.

---

### Post by rootrhift on 2009-01-19
Installing the packages recommended by:

[http://www.nepherte.be/spim-on-linux/]("http://www.nepherte.be/spim-on-linux/")

got xspim to work for me on Ubuntu 8.04 (2.6.24-23-generic i686).  That site will also walk you through the process of building the program from source if you don't know how.

Just in case the URL ends up failing here are the additional packages that were necessary for me to build xspim:

```
flex bison byacc libx11-dev libxaw7-dev build-essential linux-headers-`uname -r`
```

Good luck.

---

### Post by city-17 on 2009-09-28
Yeah, got it working on Ubuntu 9.04 as well. The instructions provided in the link are pretty neat. Thanks!:guitar:


> **rootrhift said:**
> Installing the packages recommended by:

[http://www.nepherte.be/spim-on-linux/]("http://www.nepherte.be/spim-on-linux/")

got xspim to work for me on Ubuntu 8.04 (2.6.24-23-generic i686).  That site will also walk you through the process of building the program from source if you don't know how.

Just in case the URL ends up failing here are the additional packages that were necessary for me to build xspim:

```
flex bison byacc libx11-dev libxaw7-dev build-essential linux-headers-`uname -r`
```

Good luck.

---

