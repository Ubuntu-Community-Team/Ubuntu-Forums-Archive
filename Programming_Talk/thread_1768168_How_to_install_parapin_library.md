---
title: "How to install parapin library"
date: 2011-05-26
forum: Programming Talk
---

### Post by kirill578 on 2011-05-26
I have been trying to install parapin library on my Ubuntu 11.04

i downloaded it here, but i can't figure out how to install it
[http://parapin.sourceforge.net/](http://parapin.sourceforge.net/)

---

### Post by Smart Viking on 2011-05-26
The library doesn't have to be installed, you just gotta include the stuff you needs in the header file of your program like
#include "whatever.h"
And then you create and compile.

---

### Post by kirill578 on 2011-05-26
> **Smart Viking said:**
> The library doesn't have to be installed, you just gotta include the stuff you needs in the header file of your program like
#include "whatever.h"
And then you create and compile.

may you explain a bit more? When I did it in windows it was quite simple i just included the liberty (for windows) and used outp();

I've some how managed to make it work.
i used this like to complie files
```

cc -O2 -g -Wall  -I. -L. <File_HERE> -o <FILE_HERE> -lparapin
```

---

