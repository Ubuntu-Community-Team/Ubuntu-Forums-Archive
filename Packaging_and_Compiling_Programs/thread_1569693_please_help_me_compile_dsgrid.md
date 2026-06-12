---
title: "please help me compile dsgrid"
date: 2010-09-07
forum: Packaging and Compiling Programs
---

### Post by Gozu-san on 2010-09-07
I'm attempting to compile CleaverSafe's dsgrid-core-src-alpha4.1.3 (downloaded some years ago from SourceForge).  AFAIK, no newer versions are freely available, and I doubt that I'd get support on this alpha.  Please note that the software I'm using was released under the GNU GPL.

Also, this is my first attempt at compiling -- and I am totally snowed!

Anyway, I extracted the contents of dsgrid-core-src-alpha4.1.3.tar.gz to /usr/local/src on a Ubuntu 10.04 Desktop x86 VM in Oracle VM VirtualBox, with g++ installed, and executed make install.  After considerable thrashing, I get "make: *** [install] Error 2".  I also have a 223-line log file, which I will attach shortly.

Please point out the obvious, recommend sources, tell me which manuals to read, and/or help.  Thank you.

---

### Post by stevebu56 on 2010-09-07
You chose a tough one for your first compile.  Based on a quick look at the source makefiles there needs to be a "dsthirdparty" directory at the same level as the dsgrid-core-src-alpha4.1.3 directory. It needs to contain the following directories ace, boost, bzip, gcodefac, openssl, xerces.  

```
dsgrid-core-src-alpha4.1.3/
dsthirdparty/
|-- [sburke          4096]  ace
|-- [sburke          4096]  boost
|-- [sburke          4096]  bzip
|-- [sburke          4096]  gcodefac
|-- [sburke          4096]  openssl
`-- [sburke          4096]  xerces

```

So you would need to download & compile those dependencies.  Also, some of the old project websites that are still available mentioned that it was tested on CentOS 5.1.  I would recommend building on that OS if you can since it will be closer to their build environment & things may go smoother for you if you continue.  

Also, you probably want to run 'make', then 'make install'.  Running make install first without a make may fail depending on how they set up the makefiles.  Good luck!

---

### Post by Gozu-san on 2010-09-07
Thank you, stevebu56.  Although I knew it'd be tough, it's what I want.  Perhaps I'll experiment with something simple first.

---

