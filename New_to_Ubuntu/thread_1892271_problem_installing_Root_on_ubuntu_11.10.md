---
title: "problem installing Root on ubuntu 11.10"
date: 2011-12-07
forum: New to Ubuntu
---

### Post by daroox on 2011-12-07
hi guys,
i want to install the cern software called root ./configure went well but make gives the following error massage
```

g++ -m64 -D_ALL_SOURCE -D_REENTRANT -D_GNU_SOURCE -fPIC -rdynamic -Wall -Wno-deprecated -D__linux__ -O2 ../../obj/XrdFrmConfig.o ../../obj/XrdFrmMigrate.o ../../obj/XrdFrmReqBoss.o ../../obj/XrdFrmTransfer.o ../../obj/XrdFrmXfrAgent.o ../../obj/XrdFrmXfrDaemon.o ../../obj/XrdFrmXfrMain.o ../../obj/XrdFrmXfrQueue.o ../../lib/libXrdOss.a -lnsl -lpthread -lrt -ldl -lc -L../../lib -lXrdFrm -lXrdNet -lXrdOuc -lXrdNetUtil -lXrdSys -o ../../bin/frm_xfrd ../../lib/libXrdSys.a(XrdSysPlugin.o): In function `XrdSysPlugin::getPlugin(char const*, int, bool)': XrdSysPlugin.cc:(.text+0x77): undefined reference to `dlsym' XrdSysPlugin.cc:(.text+0xec): undefined reference to `dlerror' XrdSysPlugin.cc:(.text+0x115): undefined reference to `dlopen' XrdSysPlugin.cc:(.text+0x12a): undefined reference to `dlerror' ../../lib/libXrdSys.a(XrdSysPlugin.o): In function `XrdSysPlugin::~XrdSysPlugin()': XrdSysPlugin.cc:(.text+0xa): undefined reference to `dlclose' 
```i found a patch  on the cern website [https://savannah.cern.ch/bugs/?81355](https://savannah.cern.ch/bugs/?81355) but i have totally no idea what to do 

```

This patch fixes them: 
Index: net/xrootd/src/xrootd/src/XrdFrm/GNUmakefile 
=================================================================== 
--- net/xrootd/src/xrootd/src/XrdFrm/GNUmakefile    (revision 39269) 
+++ net/xrootd/src/xrootd/src/XrdFrm/GNUmakefile    (working copy) 
@@ -4,7 +4,7 @@ 

     include ../GNUmake.env 

  -BINLIBS = -L$(LIBDIR) -lXrdFrm -lXrdNet -lXrdOuc -lXrdNetUtil -lXrdSys \ 
+BINLIBS = -L$(LIBDIR) -lXrdFrm -lXrdNet -lXrdOuc -lXrdNetUtil -lXrdSys -ldl \ 
             $(TYPELIBSF) 

--- net/xrootd/src/xrootd/src/XrdFrm/GNUmakefile    (revision 39269) 
+++ net/xrootd/src/xrootd/src/XrdFrm/GNUmakefile    (working copy) 
@@ -4,7 +4,7 @@ 

     include ../GNUmake.env 

  -BINLIBS = -L$(LIBDIR) -lXrdFrm -lXrdNet -lXrdOuc -lXrdNetUtil -lXrdSys \ 
+BINLIBS = -L$(LIBDIR) -lXrdFrm -lXrdNet -lXrdOuc -lXrdNetUtil -lXrdSys -ldl \ 
             $(TYPELIBSF) 

```

---

### Post by yeats on 2011-12-10
You can create a patch file by copying the text into an empty file and call it something like "GNUmakefile.patch".  Then cd into the directory where GNUmakefile is located and do:

```
patch -p0 < /path/to/GNUmakefile.patch
```

where "/path/to/GNUmakefile.patch" is the actual location of the patch file you created.

---

