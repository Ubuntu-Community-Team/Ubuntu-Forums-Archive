---
title: "[SOLVED] no rule to make target"
date: 2008-08-20
forum: Packaging and Compiling Programs
---

### Post by ssam on 2008-08-20
I am having lots of fun trying to compile SDDSToolkit. a piece of scientific software from argonne national lab. I think it is writen with Redhat systems in mind.

I am usually fairly proficient at compiling things, and have written my own simple makefiles for projects. but this time i am stumped.

```

make -C SDDSaps/sddsplots install
make[1]: Entering directory `/tmp/t1/epics_build/epics/extensions/SDDS/SDDSaps/sddsplots'
make -C O.linux-x86 -f ../Makefile TOP=../../../../.. T_A=linux-x86 install
make[2]: Entering directory `/tmp/t1/epics_build/epics/extensions/SDDS/SDDSaps/sddsplots/O.linux-x86'
**make[2]: *** No rule to make target `../../../../../lib/linux-x86/libXaw.a', needed by `sddsplot'. Stop.**
make[2]: Leaving directory `/tmp/t1/epics_build/epics/extensions/SDDS/SDDSaps/sddsplots/O.linux-x86'
make[1]: *** [install.linux-x86] Error 2
make[1]: Leaving directory `/tmp/t1/epics_build/epics/extensions/SDDS/SDDSaps/sddsplots'
make: *** [SDDSaps/sddsplots.install] Error 2

```

I have libxaw7 and the -dev package installed, so thats not the problem. and its not saying that it can't find the library.

I am not completely sure of the relation between .a files and .so files, but i have both in my /usr/lib.

If libxaw is installed on the system, why would i need a rule to make it?

Looking through the make files i have, the only references to libxaw are
```

$ f Makefile | xargs grep -i xaw
./extensions/SDDS/SDDSaps/sddsplots/Makefile.OAG:#PROD_LIBS_DEFAULT = mdbplt mdbcommon SDDS1 mdbmth mdblib Xaw Xmu Xt Xext X11
./extensions/SDDS/SDDSaps/sddsplots/Makefile.OAG:PROD_LIBS_Darwin = mdbplt mdbcommon SDDS1 mdbmth mdblib Xaw Xmu Xt Xext X11
./extensions/SDDS/SDDSaps/sddsplots/Makefile.OAG:PROD_LIBS_solaris = mdbplt mdbcommon SDDS1 mdbmth mdblib Xaw Xmu Xext
./extensions/SDDS/SDDSaps/sddsplots/Makefile.OAG:OP_SYS_LDLIBS = -Wl,-Bdynamic -lXaw -lXmu -lXt -lXext -lX11 -Wl,-Bstatic
./extensions/SDDS/SDDSaps/sddsplots/Makefile.OAG:PROD_LIBS_Linux += Xaw Xmu Xt Xext X11
./extensions/SDDS/SDDSaps/sddsplots/Makefile.OAG:Xaw_DIR = $(X11_LIB)
./extensions/SDDS/SDDSaps/sddsplots/Makefile.OAG~:PROD_LIBS_DEFAULT = mdbplt mdbcommon SDDS1 mdbmth mdblib Xaw Xmu Xt Xext X11
./extensions/SDDS/SDDSaps/sddsplots/Makefile.OAG~:PROD_LIBS_Darwin = mdbplt mdbcommon SDDS1 mdbmth mdblib Xaw Xmu Xt Xext X11
./extensions/SDDS/SDDSaps/sddsplots/Makefile.OAG~:PROD_LIBS_solaris = mdbplt mdbcommon SDDS1 mdbmth mdblib Xaw Xmu Xext
./extensions/SDDS/SDDSaps/sddsplots/Makefile.OAG~:OP_SYS_LDLIBS = -Wl,-Bdynamic -lXaw -lXmu -lXt -lXext -lX11 -Wl,-Bstatic
./extensions/SDDS/SDDSaps/sddsplots/Makefile.OAG~:#PROD_LIBS_Linux += Xaw Xmu Xt Xext X11
./extensions/SDDS/SDDSaps/sddsplots/Makefile.OAG~:Xaw_DIR = $(X11_LIB)

```

so adding Xaw to a PROD_LIBS list, and adding -lXaw to the build flags. The PROD_LIBS seems to go into the attached RULES.Host script.

Any ideas what I can do to get around this.

Thanks

---
PS the site make it difficult to download the files, but the licence says I can redistribute them, so they are at [http://www.hep.manchester.ac.uk/u/sam/pub/SDDS/SDDS.2.4.tar.gz](http://www.hep.manchester.ac.uk/u/sam/pub/SDDS/SDDS.2.4.tar.gz) and [http://www.hep.manchester.ac.uk/u/sam/pub/SDDS/epics.base.configure.tar.gz](http://www.hep.manchester.ac.uk/u/sam/pub/SDDS/epics.base.configure.tar.gz) if you want to have a proper look

---

### Post by ssam on 2008-08-21
i found the answer :-)
I needed to set the correct library directories in epics/extensions/configure/os/CONFIG_SITE.linux-x86.linux-x86

```
X11_LIB=/usr/lib
X11_INC=/usr/include/X11
MOTIF_LIB=/usr/lib
MOTIF_INC=/usr/include/Xm/
```

---

