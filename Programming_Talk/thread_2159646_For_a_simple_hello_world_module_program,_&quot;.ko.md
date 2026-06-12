---
title: "For a simple hello world module program, &quot;.ko&quot; file not created !"
date: 2013-07-03
forum: Programming Talk
---

### Post by rdhanunjayaraju on 2013-07-03
Hello  friends... i wrote a simple hello world module and  compiled the code.  Code compiled successfully without any errors. But ".ko" file not created. What might be the reason?

```
obj:=hello.o

KDIR = /lib/modules/$(shell uname -r)/build
PWD = $(shell pwd)

all:
 $(MAKE) -C $(KDIR) SUBDIRS=$(PWD) modules

```
Additional Information:
OS: Ubuntu 12.10
Kernel: 3.5.0-34-generic


thanks,
Dhanu

---

### Post by Bucky Ball on 2013-07-04
*Thread moved to **Programming Talk**.*

Welcome to the forums. Hopefully you'll have more luck here.

---

### Post by xb12x on 2013-07-04
Your Makefile is not correct. Try this Makefile.

Note the := (colon equal) for ***obj-m*** and ***KDIR*** and ***PWD***

Note that there is a tab (not spaces) at the begining of the command under ***all:*** 
and a tab at the begining of the command under ***clean:***


```

obj-m := hello.o 

KDIR := /lib/modules/$(shell uname -r)/build

PWD := $(shell pwd)

all:
    $(MAKE) -C $(KDIR) M=$(PWD) modules

clean:
    ${MAKE} -C ${KDIR} M=${PWD} clean    

```

---

