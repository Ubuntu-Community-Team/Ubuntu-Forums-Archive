---
title: "Problem compiling c script (driver example: hello world)"
date: 2013-06-29
forum: Packaging and Compiling Programs
---

### Post by johanngomes on 2013-06-29
Hi, i am following a driver example of 'Hello World', by [http://www.linuxdevcenter.com/pub/a/linux/2007/07/05/devhelloworld-a-simple-introduction-to-device-drivers-under-linux.html](http://www.linuxdevcenter.com/pub/a/linux/2007/07/05/devhelloworld-a-simple-introduction-to-device-drivers-under-linux.html)

 The file is: [http://www.linuxdevcenter.com/linux/2007/07/05/examples/hello_printk.tar.gz](http://www.linuxdevcenter.com/linux/2007/07/05/examples/hello_printk.tar.gz)

When i do make in Terminal in the folder:

[COLOR=#003366]$ make
[/COLOR]
This is being showed as result:

```
make -C /lib/modules/3.5.0-34-generic/build M=/home/johann/Dropbox/BSI UFRPE/8º Período/Infra-Estrutura de Software/driver-linuxdevcenter/hello_printk modules
make[1]: Entering directory `/usr/src/linux-headers-3.5.0-34-generic'
make[1]: *** No rule to make target `UFRPE/8º'.  Stop.
make[1]: Leaving directory `/usr/src/linux-headers-3.5.0-34-generic'
make: *** [default] Error 2

```

What happened? I can't figure out... rule? 

I'm a beginner in the linux universe, i never compiled C files before in this OS.

Thanks you very much!

---

### Post by MG&amp;TL on 2013-06-29
It is failing to build because of the path the file is in:

```
M=/home/johann/Dropbox/BSI UFRPE/8º Período/Infra-Estrutura de Software/driver-linuxdevcenter/hello_printk
```

Will be interpreted by the shell as several arguments, because of the spaces:

```
M=/home/johann/Dropbox/BSI
UFRPE/8º
Período/Infra-Estrutura
de
Software/driver-linuxdevcenter/hello_printk

```

To fix this, use a path without spaces in, or edit the Makefile to quote the output of ```
$(shell pwd)
```

I suggest getting used to *make* before trying to build a kernel module. Here's the *make* manual: [http://www.gnu.org/software/make/manual/make.html](http://www.gnu.org/software/make/manual/make.html)

---

### Post by johanngomes on 2013-06-29
> **MG&TL said:**
> It is failing to build because of the path the file is in:

```
M=/home/johann/Dropbox/BSI UFRPE/8º Período/Infra-Estrutura de Software/driver-linuxdevcenter/hello_printk
```

Will be interpreted by the shell as several arguments, because of the spaces:

```
M=/home/johann/Dropbox/BSI
UFRPE/8º
Período/Infra-Estrutura
de
Software/driver-linuxdevcenter/hello_printk

```

To fix this, use a path without spaces in, or edit the Makefile to quote the output of ```
$(shell pwd)
```

I suggest getting used to *make* before trying to build a kernel module. Here's the *make* manual: [http://www.gnu.org/software/make/manual/make.html](http://www.gnu.org/software/make/manual/make.html)

Thank you [COLOR=#000000]MG&TL[/COLOR]! 
It was that! :DD[COLOR=#000000]
[/COLOR]

---

