---
title: "Distro for developement"
date: 2007-06-15
forum: Programming Talk
---

### Post by gizmoarena on 2007-06-15
I am doing my thesis on device drivers. No need to say that I am using linux for my thesis.
But the problem is, I'm confused which linux is better for development jobs.

I personally use and love ubuntu fiesty. but when I tried to code my first module programming. I realized ubuntu isn't ready for that. My thesis supervisor told me developers usually use debian or fedora. But I don't want to leave ubuntu.

Guys, help me. Tell me if anyone else is using ubuntu for device driver coding. 
Let me know.

---

### Post by justin whitaker on 2007-06-15
> **gizmoarena said:**
> I am doing my thesis on device drivers. No need to say that I am using linux for my thesis.
But the problem is, I'm confused which linux is better for development jobs.

I personally use and love ubuntu fiesty. but when I tried to code my first module programming. I realized ubuntu isn't ready for that. My thesis supervisor asked me to use either debian or fedora. But I don't want to leave ubuntu.

Guys, help me. Tell me if anyone else is using ubuntu for device driver coding. 
Let me know.

Ubuntu is a perfectly fine development environment, although many of the kernel dudes use Debian or RH/Fedora.

---

### Post by Majorix on 2007-06-15
You could use Debian. After all, it is the "father" of Ubuntu, so you won't feel far away from home :)

---

### Post by pmasiar on 2007-06-15
ubuntu *is* debian. You just need to install developer's packages, which are not installed by default.

What are you missing in ubuntu?

---

### Post by gizmoarena on 2007-06-16
kernel modules

when I try to compile a program with #include </linux/module.h> it says that there's no such directory

but at university lab, where pc's are powered by fedora 5. it gets compiled without any problem.

---

### Post by gizmoarena on 2007-06-16
not to mention: I just installed fedora 7 ... and it totally sucks. [sorry Fed lovers]
I'll be getting back to ubuntu 6.06 as I dont have the 7.04 DVD.

Can anyone tell me, would I be able to add debian DVD's ar repo on my ubuntu 6.06?

---

### Post by Ramses de Norre on 2007-06-16
Install the kernel headers, they should have all the headers you need.
I think the package is something like kernel-headers-version or linux-headers-version, search with apt.
You'll also want build-essential if that isn't installed yet.

---

### Post by gizmoarena on 2007-06-16
**build-essential** was installed
**kernel-headers** was installed 
I had linux-headers installed. I manually checked that **module.h** was in the folder **/usr/src/linux-headers-2.6.20-15/include/linux**

still I had the problem ... any solution? or alternative??

---

### Post by danhm on 2007-06-16
I think you want **#include <linux/module.h>**, not #include <**/**linux/module.h>.

---

### Post by kknd on 2007-06-16
Ubuntu is a good distro for developing. Until now, I could compile everything that I needed (I tried 5 other distros, including openSUSE, Debian Etch and Mandriva)

---

### Post by gizmoarena on 2007-06-17
well, help me here ... i tried to compile this code 
> 
#define MODULE
#include <linux/module.h>

int init_module (void) /* Loads a module in the kernel */
{
printk("Hello kernel n");
return 0;
}

void cleanup_module(void) /* Removes module from kernel */
{
printk("GoodBye Kerneln");
}

and GCC shows this error> 
gizmo@ubuntu:~/driver$ sudo gcc -c hello.c
hello.c:2:26: error: linux/module.h: No such file or directory

**when I had build-essentials and linux-headers install.**

what could be the problem? any solution?


Consider I have only Fiesty installed by CD. So, I have nothin installed for developement.
At this point what should I install for developing?

---

### Post by daxumaming on 2007-06-17
I'm currently using Kubuntu and Xubuntu.. I've used Puppy LInux, Damn Small Linux, Vector Linux, Fedora Core, CentOS, Scientific Linux, and Slackware.. All of them are appropriate for development. 

Development isn't and shouldn't be based on what distro you're using, but the tools your using... Kate, Anjuta, KDevelop, Qt, NetBeans, Eclipse... those IDEs that would make your coding life simple. And the most important is your brain.. are you prepared for software development?

If you can install those IDE's, if you have a text editor, then the distro you're currently on is appropriate for development. What matters now is your preference, are you happy with your distro? If you are, then you code on that.

---

### Post by kknd on 2007-06-17
sudo aptitude install build-essential should give you enough libs to make kernel modules, since with only this nvidia driver installer was capable of compiling a kernel module.

P.S: I now see that you got build-essential instaled.

---

### Post by xtacocorex on 2007-06-17
You shouldn't need to compile with sudo.  As far as everything else goes, I don't have a clue.

---

### Post by alex0o0 on 2007-06-17
```

alex@nop:~$ cat Makefile
obj-m += hello.o

all:
        make -C /lib/modules/$(shell uname -r)/build M=$(PWD) modules

        clean:
                make -C /lib/modules/$(shell uname -r)/build M=$(PWD) clean

```

```

alex@nop:~$ make
make -C /lib/modules/2.6.20-16-generic/build M=/home/alex modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.20-16-generic'
  CC [M]  /home/alex/hello.o
  Building modules, stage 2.
  MODPOST 1 modules
  CC      /home/alex/hello.mod.o
  LD [M]  /home/alex/hello.ko
make[1]: Leaving directory `/usr/src/linux-headers-2.6.20-16-generic'

```

You really need to read a book on driver development first. Distribution does not really matter, Ubuntu is as good as any for development. Its the kernel sources/headers you build your modules against that is important.

---

### Post by Majorix on 2007-06-18
> **danhm said:**
> I think you want **#include <linux/module.h>**, not #include <**/**linux/module.h>.

Agreed. / refers to the root of the file system and there is no "linux" folder there. Only folders like usr, etc, var and so on.

---

### Post by the_unforgiven on 2007-06-18
> **gizmoarena said:**
> well, help me here ... i tried to compile this code 


and GCC shows this error

**when I had build-essentials and linux-headers install.**

what could be the problem? any solution?


Consider I have only Fiesty installed by CD. So, I have nothin installed for developement.
At this point what should I install for developing?
That's wrong way of compiling kernel modules - it was used for the 2.4.x kernels.
For compiling kernel modules for 2.6.x kernels, you need to use the kernel build system as pointed out by alex0o0.

You might want to refer to [The Linux Kernel Module Programmer's Guide (for 2.6 kernels)]("http://en.tldp.org/LDP/lkmpg/2.6/html/index.html").

As far as distros go, any distro that ships a build system (compiler, make, libraries, headers etc.) is good enough for development of kernel modules (actually, libraries are not required for kernel modules :P).

HTH ;)

---

### Post by gizmoarena on 2007-06-20
thanks a lot guyz :D you guyz really helped me.

now I'm sticking with ubuntu fiesty. The problem was with the inlcuding header file.
using a makefile solved it. :D

thanks again.

---

