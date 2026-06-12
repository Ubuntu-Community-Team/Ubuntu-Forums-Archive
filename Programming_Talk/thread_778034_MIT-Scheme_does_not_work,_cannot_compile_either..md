---
title: "MIT-Scheme does not work, cannot compile either."
date: 2008-05-01
forum: Programming Talk
---

### Post by thcommj on 2008-05-01
Hi MIT-scheme doesn't seem to work for me on Ubuntu Hardy, like many others who have reported the same issue. So I tried to follow the instructions on [http://www.gnu.org/software/mit-scheme/liarc-build.html](http://www.gnu.org/software/mit-scheme/liarc-build.html) to rebuild from the source but haven't been successful. the whole thing was done in a minute (it is supposed to take hours..)..

EDIT: I figured that it was because I didn't have build-essential installed...

NEW PROBLEM: Now I've compiled it, but it seems to have trouble installing....

> 

thcommj@thcommj-laptop:~/scheme/mit-scheme-c-20080130/src$ make install
/bin/bash ./mkinstalldirs /usr/local/lib/mit-scheme-c
mkdir /usr/local/lib/mit-scheme-c
mkdir: cannot create directory `/usr/local/lib/mit-scheme-c': Permission denied
make: *** [install-auxdir-top] Error 1
thcommj@thcommj-laptop:~/scheme/mit-scheme-c-20080130/src$ gksu make install
/bin/bash ./mkinstalldirs /usr/local/lib/mit-scheme-c
mkdir /usr/local/lib/mit-scheme-c
/usr/bin/install -c --preserve-timestamps -m 644 ./etc/optiondb.scm /usr/local/lib/mit-scheme-c/.
/usr/bin/install -c --preserve-timestamps -m 644 lib/*.com /usr/local/lib/mit-scheme-c/.
make: *** [install-auxdir-top] Error 1
m': No such file or directory


And I tried again..

> 
thcommj@thcommj-laptop:~/scheme/mit-scheme-c-20080130/src$ gksu make install
/bin/bash ./mkinstalldirs /usr/local/lib/mit-scheme-c
/usr/bin/install -c --preserve-timestamps -m 644 ./etc/optiondb.scm /usr/local/lib/mit-scheme-c/.
/usr/bin/install -c --preserve-timestamps -m 644 lib/*.com /usr/local/lib/mit-scheme-c/.
thcommj@thcommj-laptop:~/scheme/mit-scheme-c-20080130/src$



still doesn't work....

---

### Post by LaRoza on 2008-05-01
I did install mit-scheme from source successfully.

Do you have build-essential? 

```

sudo aptitude install build-essential

```

Delete everything but the archive and start over.

I used this package and instruction set: [http://www.gnu.org/software/mit-scheme/liarc-build.html](http://www.gnu.org/software/mit-scheme/liarc-build.html)

---

### Post by thcommj on 2008-05-01
> **LaRoza said:**
> I did install mit-scheme from source successfully.

Do you have build-essential? 

```

sudo aptitude install build-essential

```

Delete everything but the archive and start over.

I used this package and instruction set: [http://www.gnu.org/software/mit-scheme/liarc-build.html](http://www.gnu.org/software/mit-scheme/liarc-build.html)

Yeah! I figured that out as well when waiting for reply. thanks anyway.

---

### Post by LaRoza on 2008-05-01
> **thcommj said:**
> Yeah! I figured that out as well when waiting for reply. thanks anyway.

I hope you have time to kill. Do not watch it once it gets going ;)

---

### Post by thcommj on 2008-05-02
I left it to compile and went to sleep....and tried to make install this morning but it doesn't work....(description at the top)

---

### Post by cphmit on 2008-05-03
This is caused by new AppArmor support in the kernel, blocking MIT Scheme's attempt to grab low memory.  A short-term workaround is to run

    sudo sysctl -w vm.mmap_min_addr=0

To make the change permanent, edit that binding in /etc/sysctl.conf.

I'll modify the next release so that the Scheme memory allocator accounts for this.  Meanwhile, the mit-scheme-c version works correctly since it uses a different memory allocator -- but you'll need at least 1GB of RAM to compile it.

---

### Post by thcommj on 2008-05-06
Thanks....but since my computer is a fairly low-class one, I guess I'll just wait till there's a version that works out-of-the-box... :)

---

### Post by Ruhe on 2008-05-24
> **cphmit said:**
> This is caused by new AppArmor support in the kernel, blocking MIT Scheme's attempt to grab low memory.  A short-term workaround is to run

    sudo sysctl -w vm.mmap_min_addr=0

To make the change permanent, edit that binding in /etc/sysctl.conf.

I'll modify the next release so that the Scheme memory allocator accounts for this.  Meanwhile, the mit-scheme-c version works correctly since it uses a different memory allocator -- but you'll need at least 1GB of RAM to compile it.


Thanks a lot!

---

### Post by dglb on 2008-06-03
This fix also addresses a problem encountered when running on 8.04 the version of Scheme that is distributed through MIT's Open CourseWare 6.001 class, located here:
[http://ocw.mit.edu/OcwWeb/Electrical-Engineering-and-Computer-Science/6-001Spring-2005/Tools/detail/linuxinstall.htm](http://ocw.mit.edu/OcwWeb/Electrical-Engineering-and-Computer-Science/6-001Spring-2005/Tools/detail/linuxinstall.htm)

When following the instructions on that page, the command to run scheme 
```
scheme -large -band 6001.com -edit
```
produces the following error message in Ubuntu 8.04 :
Not enough memory for this configuration.

To work around this problem, run run the command suggested earlier in this thread before attempting to start scheme.
```
sudo sysctl -w vm.mmap_min_addr=0
```

Thanks to the others who suggested this. Hopefully this information will help others avoid some hassle following the instructions on MIT's site.

---

