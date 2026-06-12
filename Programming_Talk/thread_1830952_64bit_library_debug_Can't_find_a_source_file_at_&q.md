---
title: "64bit library debug Can't find a source file at &quot;ioputs.c&quot;"
date: 2011-08-22
forum: Programming Talk
---

### Post by Uk Meterman on 2011-08-22
Hi,
I am just starting with eclipse, and have a 64 bit version of Ubuntu installed. When I try to step into puts("!!!Hello World!!!") I get the error Can't find a source file at "ioputs.c" 
Locate the file or edit the source lookup path to include its location.

Which libraries or includes am I missing?

Thanks

---

### Post by Bachstelze on 2011-08-22
It's probably in the libc6 source, but why are you stepping into puts anyway?

---

### Post by Uk Meterman on 2011-08-22
Hi,
Just stepping in to puts for interest at the moment. Will soon be considering writeing my own device drivers so need to start somewhere.

---

### Post by Bachstelze on 2011-08-22
Well then just

```
apt-get source libc6
```

and you can use e.g. [font=monospace]find[/font] to locate the file you want. Then just copy it in the same dir you're running gdb in.

---

