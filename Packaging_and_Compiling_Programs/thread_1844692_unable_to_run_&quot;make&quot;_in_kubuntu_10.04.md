---
title: "unable to run &quot;make&quot; in kubuntu 10.04"
date: 2011-09-15
forum: Packaging and Compiling Programs
---

### Post by shaktiman1234 on 2011-09-15
hi all, i m trying to install kpicosim ([http://marksix.home.xs4all.nl/kpicosim.html](http://marksix.home.xs4all.nl/kpicosim.html)) on my machine.
after using .[FONT=Comic Sans MS]/configure[/FONT], when i try to [FONT=Comic Sans MS]make[/FONT] it gives following error.
i am posting the log here:

/bin/bash ./config.status --recheck
running /bin/bash ./configure  --without-arts  --no-create --no-recursion
configure: WARNING: unrecognized options: --without-arts
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking target system type... i686-pc-linux-gnu
./configure: line 2019: syntax error near unexpected token `kpicosim,'
./configure: line 2019: `AM_INIT_AUTOMAKE(kpicosim, 0.1)'
make: *** [config.status] Error 2


please help me . i am stuck here.
thanks in advance.

---

### Post by Nutria on 2011-09-16
> **shaktiman1234 said:**
> hi all, i m trying to install kpicosim ([http://marksix.home.xs4all.nl/kpicosim.html](http://marksix.home.xs4all.nl/kpicosim.html)) on my machine.
after using ./configure, when i try to [FONT=Comic Sans MS]make[/FONT] it gives following error.
i am posting the log here:

/bin/bash ./config.status --recheck
running /bin/bash ./configure  --without-arts  --no-create --no-recursion
configure: WARNING: unrecognized options: --without-arts
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking target system type... i686-pc-linux-gnu
./configure: line 2019: syntax error near unexpected token `kpicosim,'
./configure: line 2019: `AM_INIT_AUTOMAKE(kpicosim, 0.1)'
make: *** [config.status] Error 2


please help me . i am stuck here.
thanks in advance.


Presumably the ./configure showed no errors or warnings?

(Note, though, that "Desktop Environments" probably isn't the best place to ask this question...)

---

### Post by sumski on 2011-09-20
./configure didn't go all the way, it first needs to be succesfully finished, then you can use make

> running /bin/bash ./configure --without-arts --no-create --no-recursion
configure: **WARNING: unrecognized options: --without-arts**
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking target system type... i686-pc-linux-gnu
./configure: line 2019: **syntax error** near unexpected token `kpicosim,'
./configure: line 2019: `AM_INIT_AUTOMAKE(kpicosim, 0.1)'
make: *** [config.status] Error 2

---

### Post by oldos2er on 2011-09-20
Moved to Packaging & Compiling programs.

---

### Post by SevenMachines on 2011-09-21
Take it this is 0.7? Not seeing the issue here, try
$ autoreconf -fi
and retry

---

