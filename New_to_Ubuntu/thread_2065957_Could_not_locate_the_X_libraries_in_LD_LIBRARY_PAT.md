---
title: "Could not locate the X libraries in LD_LIBRARY_PATH"
date: 2012-10-03
forum: New to Ubuntu
---

### Post by Twar on 2012-10-03
I am trying to run Libero on Ubuntu 12.04.

I have already installed it as well as updated it to latest service pack, and I have started a license server. I still can't get Libero to run at all though. When I try to run it, I get the output:

```
Could not locate the X libraries in LD_LIBRARY_PATH
```I have installed all the X11 libraries I could find, but still no luck. Also installed openmotif4.

Any ideas?

---

### Post by steeldriver on 2012-10-03
what exactly is libero? there seem to be several projects using that name

AFAIK the use of LD_LIBRARY_PATH is pretty much deprecated - unless your installer sets it it will be empty - the system uses ldconfig to find things like X libraries

---

