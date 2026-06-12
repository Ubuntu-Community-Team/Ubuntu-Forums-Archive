---
title: "How to upgrade new Kernel"
date: 2011-12-25
forum: New to Ubuntu
---

### Post by cropicko on 2011-12-25
Hi I need help,how can i install ubuntu linux kernel 3.2.rc7 PLS REPLY

---

### Post by BC59 on 2011-12-25
Go here to download it:
[http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.2-rc7-precise/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.2-rc7-precise/)

---

### Post by cropicko on 2011-12-25
So i donwloaded i386 images for my 32 bit system and how to install?

---

### Post by fdrake on 2011-12-25
> **cropicko said:**
> Hi I need help,how can i install ubuntu linux kernel 3.2.rc7 PLS REPLY
it's not available in the repo yet you have to build it from source:
[http://kernel.org/](http://kernel.org/)

ps. if your system is fully function there is not need to install a new kernel unless you need some new functionality that YOU KNOW that this kernel can provide, since it is not considered stable !
Don't come back and complain that something is not working then...

---

### Post by cropicko on 2011-12-25
I dont know how to build it is there any software i am newbie.

---

### Post by BC59 on 2011-12-25
Look here:
[http://www.howopensource.com/2011/08/how-to-compile-and-install-linux-kernel-3-0-in-ubuntu-11-04-10-10-and-10-04/](http://www.howopensource.com/2011/08/how-to-compile-and-install-linux-kernel-3-0-in-ubuntu-11-04-10-10-and-10-04/)

---

### Post by fdrake on 2011-12-25
> **cropicko said:**
> I dont know how to build it is there any software i am newbie.
download & doubleclick/run the *.deb file. file manager should start up!

think twice before installing it, unless there is a GOOOD Reason to install a not stable kernel!

---

### Post by Lars Noodén on 2011-12-25
You can get the latest kernels here:
[list]
[*][https://wiki.ubuntu.com/Kernel/MainlineBuilds](https://wiki.ubuntu.com/Kernel/MainlineBuilds)
[*][http://kernel.ubuntu.com/~kernel-ppa/mainline/daily/current/](http://kernel.ubuntu.com/~kernel-ppa/mainline/daily/current/)
[/list]

You won't need to compile.  Just download and then install using [dpkg](http://manpages.ubuntu.com/manpages/oneiric/en/man1/dpkg.1.html)

e.g.

```

sudo dpkg -i *linux-image-3.2.0-999-generic_3.2.0-999.201112250405_amd64.deb*

```

---

### Post by cropicko on 2011-12-25
OK i will try it and thanks for fast reply

---

