---
title: "Problem with compiling Ubuntu module"
date: 2011-03-16
forum: Packaging and Compiling Programs
---

### Post by Fanatico on 2011-03-16
I need to port some network driver module from other distribution to Ubuntu 10.04.

I've downloaded Ubuntu kernel with git and rebuilt it. Then I've added sources
of module to ubuntu-lucid-src/drivers/net/my_gbe folder.

I've added the following entry to ubuntu-lucid-src/drivers/net/Kconfig file:

config MY_GBE
        tristate "My Gigabit Ethernet"
	select MII
        ---help---
          This is an gigabit ethernet driver for xxx.


I've added the following line to ubuntu-lucid-src/drivers/net/Makefile file:

obj-$(CONFIG_MY_GBE) += my_gbe/

I also configured to build it as separate module via make xconfig command.

Now when I rebuild kernel with "make j 2 bzImage" command, the object files
(.o) are created  for all .c file as well as new built-in.o file.
However no my_gbe.ko kernel object file is created as I expected.

Can anyone explain what I did wrong?

Thanks.

---

### Post by Fanatico on 2011-03-18
Bump. Nobody knows answer???

I also notice today that if I run the following command, then ko file is created:

make drivers/net/my_gbe/my_gbe.ko

The above command also triggered rebuilding all other modules, what is strange.

I probably did some mistake while adding the module sources to kernel.

Any advise?

---

