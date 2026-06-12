---
title: "make: Nothing to be done for `all'. while compiling my first hello world kernel modul"
date: 2011-07-02
forum: Packaging and Compiling Programs
---

### Post by sunandi on 2011-07-02
Hi All,

I am following the basic tutorial to learn to compile my first hello-world kernel module.
========================
/*
   first_mod.c
   My first kernel module.
*/

#include <linux/module.h> /* Needed by all modules */
#include <linux/kernel.h> /* Needed for KERN_INFO*/
int init_module(void)
{
   printk(KERN_INFO "Hello world 1.\n");

   /* 
    * A non 0 return means init_module failed; module can't be loaded. 
    */
   return 0;
}

void cleanup_module(void)
{
   printk(KERN_INFO "Goodbye world 1.\n");
}

========================

and Makefile:
=========================
obj-m += first_mod.o

all:
        make -C /lib/modules/$(shell uname -r)/build M=$(PWD) modules

clean:
        make -C /lib/modules/$(shell uname -r)/build M=$(PWD) clean
=========================

but when i do make it gives me this error:
sudipto@sudipto-ThinkPad-T61p:~/kernel_workspace/Development/module_development$ ll
total 16
drwxr-xr-x 2 sudipto sudipto 4096 2011-07-02 20:47 ./
drwxr-xr-x 4 sudipto sudipto 4096 2011-07-02 19:52 ../
-rw-r--r-- 1 sudipto sudipto  396 2011-07-02 20:13 first_mod.c
-rw-r--r-- 1 sudipto sudipto  173 2011-07-02 20:47 Makefile
sudipto@sudipto-ThinkPad-T61p:~/kernel_workspace/Development/module_development$ make
make: Nothing to be done for `all'.
sudipto@sudipto-ThinkPad-T61p:~/kernel_workspace/Development/module_development$

Help will be heavily appreciated

---

### Post by gmargo on 2011-07-03
Inside a Makefile, the TAB character is critical.  On the line after your "all:", with the "make", there must be a TAB before the "make".  Without a TAB (for instance if you just used spaces) you will receive that error.

---

### Post by sunandi on 2011-07-03
Super!!!!!! Its working 
Thanks to You and Toz :-)

---

### Post by hackintoshrao on 2012-08-08
Thanks a lot !! I too had encountered the same problem ...Your suggestion worked

---

### Post by shaaraddalvi on 2013-02-09
Knowledge of makefile is vital..thanks for your suggestion...worked! :)

---

### Post by mahanew on 2013-04-23
Hi,
I want to install the package build-essential .So I've downloaded it from ubuntu packages build-essential_11.5ubuntu3.tar.gz .My first question is it the right version of build-essential(I'm using ubunu 12.04lts)?
In addition,when i tried to compile :
./configure
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking whether to enable maintainer-specific portions of Makefiles... no
checking for dpkg-architecture... yes
checking for Debian architecture... i386
configure: creating ./config.status
config.status: creating Makefile

But ,when I taped make :
make: Nothing to be done for `all'.

Can anyone help me please? I'm too blocked.
Thank you so much.

---

### Post by schragge on 2013-04-23
Please start a new thread for your question rather than hijacking this.

The right version for precise is *11.5ubuntu2.1*. But you don't need to compile *build-essential*. To install it, just
```
sudo apt-get install build-essential
```

---

