---
title: "compiling kernel threads"
date: 2012-11-18
forum: New to Ubuntu
---

### Post by Alivn on 2012-11-18
i was tryin to compile that simple hello-1.c module....
wen i use make command i get this error
make -C /lib/modules/3.2.0-32-generic/build M=/home/alvin/Kernal Modules modules
make[1]: Entering directory `/usr/src/linux-headers-3.2.0-32-generic'
make[1]: *** No rule to make target `Modules'.  Stop.
make[1]: Leaving directory `/usr/src/linux-headers-3.2.0-32-generic'
make: *** [all] Error 2
i referred a few threads over the net and checked the linux headers....installed all of em from the synaptic...and 
wen i run the command 
$ apt-cache search linux-headers-$(uname -r)
i get this.......
linux-headers-3.2.0-32-generic - Linux kernel headers for version 3.2.0 on 64 bit x86 SMP
linux-headers-3.2.0-32-generic-pae - Linux kernel headers for version 3.2.0 on 32 bit x86 SMP
her's my make file....


obj-m += hello-1.o
all:
    make -C /lib/modules/$(shell uname -r)/build M=$(PWD) modules
clean:
    make -C /lib/modules/$(shell uname -r)/build M=$(PWD) clean

---

### Post by steeldriver on 2012-11-18
Welcome

I think the problem is likely that your PWD appears to have a space in its name

```
/home/alvin/Kernal Modules
```You could try quoting the PWD variable in your Makefile - but tbh I don't know if that will work - if not you could rename the directory

```
all:
    make -C /lib/modules/$(shell uname -r)/build M=[COLOR=Red]"[COLOR=Black]$(PWD)[/COLOR]"[/COLOR] modules
clean:
    make -C /lib/modules/$(shell uname -r)/build M=[COLOR=Red]"[/COLOR]$(PWD)[COLOR=Red]"[/COLOR] clean     
```

---

### Post by Alivn on 2012-11-18
naah that dint work

---

