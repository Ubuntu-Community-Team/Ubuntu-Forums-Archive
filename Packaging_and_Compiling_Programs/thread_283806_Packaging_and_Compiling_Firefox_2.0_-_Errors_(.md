---
title: "Packaging and Compiling Firefox 2.0 - Errors :("
date: 2006-10-24
forum: Packaging and Compiling Programs
---

### Post by Treviño on 2006-10-24
Hello I'm trying to build firefox 2.0 both using ubuntu (edgy) repositories patched sources and the official sources...

```
nsStackFrameUnix.cpp: In function 'void DumpStackToFile(FILE*)':
nsStackFrameUnix.cpp:110: error: 'Dl_info' was not declared in this scope
nsStackFrameUnix.cpp:110: error: expected `;' before 'info'
nsStackFrameUnix.cpp:111: error: 'info' was not declared in this scope
nsStackFrameUnix.cpp:111: error: 'dladdr' was not declared in this scope
```The file with problems is [FONT=Courier New]./xpcom/base/nsStackFrameUnix.cpp[/FONT], anyway also adding to it the instruction [FONT=Courier New]#include <dlfcn.h>[/FONT] (the [FONT=Courier New]Dl_info[/FONT] struct is definied there...) then, I get a linking error...

Anyone has/had this problem?

I had tried to do this also some time ago, but it didn't work anyway! :(

Any fix?

Thanks!

---

### Post by americux on 2006-11-03
Why don´t you use Synaptic or apt-get or aptitude?
I´d do it if I wanted the package installed in my system. If you´re doing it for practising... I don´t know how to help you with your issue. Regards and good luck, a.

---

### Post by Treviño on 2006-11-27
I wanted to rebuild firefox with my optimizations.....

---

