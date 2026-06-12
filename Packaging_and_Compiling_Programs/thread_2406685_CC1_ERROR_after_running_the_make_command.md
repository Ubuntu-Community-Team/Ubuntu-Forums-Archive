---
title: "CC1 ERROR after running the make command"
date: 2018-11-24
forum: Packaging and Compiling Programs
---

### Post by ziflinger on 2018-11-24
Hey, im building a kernel module and for some reason after a few times that it worked i get the following error:

"cc1: error: code model kernel does not support PIC mode."

i looked around tried all kinds of things and nothing seems to work, even installed ubuntu again because i thought i courrupted some files, help please! thank you.

---

### Post by jeremy31 on 2018-11-24
[https://askubuntu.com/a/999983/300665](https://askubuntu.com/a/999983/300665)
Does that fix it?

---

### Post by ziflinger on 2018-11-24
i tried to add the EXTRA_FLAGS line it didnt work. 
about the comment with the patch - i didnt understand so idk ..

i wierd stuff that i already build modules before and it suddenly happend.
thanks for the quick replay!

---

### Post by jeremy31 on 2018-11-24
Can you paste the contents of Makefile at paste.ubuntu.com and post a link?

---

### Post by ziflinger on 2018-11-24
its the simplest module ever: 


obj-m += x.o

all:
     make -C /lib/modules/$(shell uname -r)/build M=$(PWD) modules

clean:
     make -C /lib/modules/$(shell uname -r)/build M=$(PWD) modules

------------------------------------------------------------------------------------

---

### Post by jeremy31 on 2018-11-24
What kernel and Ubuntu version?  Also check
```
cat /usr/src/linux-headers-$(uname -r)/Makefile | grep -i pie
```

---

### Post by ziflinger on 2018-11-24
ok i have no idea how it happend but it fixed itself, thank for the help!

---

