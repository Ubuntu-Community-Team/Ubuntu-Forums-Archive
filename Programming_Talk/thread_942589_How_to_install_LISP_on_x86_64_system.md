---
title: "How to install LISP on x86_64 system"
date: 2008-10-09
forum: Programming Talk
---

### Post by irate.turtle on 2008-10-09
Hi,

I have a Dell Studio laptop with following installation

SYSTEM INFORMATION
        Running Ubuntu Linux, the Ubuntu 8.04 (hardy) release.
        GNOME: 2.22.3 (Ubuntu 2008-07-09)
        Kernel version: 2.6.24-19-generic (#1 SMP Wed Aug 20 17:53:40 UTC 2008)
        GCC: 4.2.3 (x86_64-linux-gnu)
        Xorg: unknown (13 June 2008  01:10:57AM) (13 June 2008  01:10:57AM)
        Hostname: xxxxxxx
        Uptime: 0 days 1 h 18 min

CPU INFORMATION
        GenuineIntel, Intel(R) Core(TM)2 Duo CPU     T5750  @ 2.00GHz

Now when I try to install LISP (downloaded from [http://common-lisp.net/project/lispbox/#linux](http://common-lisp.net/project/lispbox/#linux)) on my system

>/tmp/lispbox$ ./setup 
Install in directory (default /home/uname/LispBox): 
creating cache ./config.cache
checking host system type... x86_64-unknown-linux-gnu
configure: error: Emacs hasn't been ported to `x86_64-unknown-linux-gnu' systems.
Check `etc/MACHINES' for recognized configuration names.
executing /tmp/lispbox/clisp-2.33/src/configure --prefix=/home/uname/LispBox --cache-file=config.cache
configure: creating cache config.cache
configure: * checks for programs
checking for gcc... gcc
checking for C compiler default output file name... configure: error: C compiler cannot create executables
See `config.log' for more details.
./setup: 26: ./makemake: not found
make: *** No rule to make target `config.lisp'.  Stop.

******************************************************



How do I install LISP on my system.

Is there a way I could install LISP on my system using the

"apt-get install lisp_xyz_verson"

method?

With thanks and regards,

---

### Post by CptPicard on 2008-10-09
Try Steel Bank Common Lisp instead, and emacs for editing.

```

sudo apt-get install sbcl emacs

```

Then, you want the SLIME package for Emacs, but don't use the one from the repositories, it has issues. Download from the net instead and install as per instructions, it's easy.

---

### Post by indecisive on 2008-10-09
Or this:

sudo apt-get install build-essential

---

### Post by irate.turtle on 2008-10-09
Is the SBCL good? I am beginning programming in LISP, so I am not aware of the options. I got my tip about 'LISP in the box' from Practical Common Lisp ([http://www.gigamonkeys.com/book/](http://www.gigamonkeys.com/book/) , [http://www.gigamonkeys.com/book/lather-rinse-repeat-a-tour-of-the-repl.html](http://www.gigamonkeys.com/book/lather-rinse-repeat-a-tour-of-the-repl.html))

Comments?

---

### Post by irate.turtle on 2008-10-09
Hi,

Mind if I ask what all does this build-essential include. As the name suggests all the essential stuff. I would like to know the contents. Any links?

Thanks and regards,

---

### Post by CptPicard on 2008-10-09
No, build-essential doesn't include anything Lisp-related, it's essentially GCC and dev libs.

[http://packages.ubuntu.com/hardy/build-essential](http://packages.ubuntu.com/hardy/build-essential)

SBCL is good, it's probably the most actively developed and capable Lisp implementation for Linux these days.

---

