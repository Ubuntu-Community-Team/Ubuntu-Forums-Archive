---
title: "Kernel module package - pbuilder issue"
date: 2007-12-26
forum: Packaging and Compiling Programs
---

### Post by mat087 on 2007-12-26
Hi,

I've made a simple kernel module with a minimal Makefile. 


```

PWD = $(shell pwd)

obj-m += toshlcd.o

all:
        make -C /lib/modules/$(shell uname -r)/build M=$(PWD) modules

install: all
        make -C /lib/modules/$(shell uname -r)/build M=$(PWD) modules_install
        depmod -a

clean:
        make -C /lib/modules/$(shell uname -r)/build M=$(PWD) clean

```


When I'm doing a "make", the  module compiled successfully. **However, when I'm building the ".dsc" with pbuilder.** I've got the following error:

```

make[1]: Entering directory `/tmp/buildd/toshlcd-0.1'
make -C /lib/modules/2.6.22-14-generic/build M=/tmp/buildd/toshlcd-0.1 clean
[B]make: Entering an unknown directory
make: *** /lib/modules/2.6.22-14-generic/build: No such file or directory.  Stop.
make: Leaving an unknown directory[/B]
make[1]: *** [clean] Error 2
make[1]: Leaving directory `/tmp/buildd/toshlcd-0.1'
make: [clean] Error 2 (ignored)

```


I think, it is related to the dependencies of the package. I've tried to add "linux-headers", "linux-source". But it doesn't solve my problem.

Does anyone has a idea ?


Thanks,
Mathieu

---

