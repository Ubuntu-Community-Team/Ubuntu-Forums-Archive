---
title: "[c++]how to install iostream.h"
date: 2010-04-24
forum: Programming Talk
---

### Post by testuser01 on 2010-04-24
i installed c++ library by following command

sudo apt-get install libc6-dev

but my computer does not have iostream.h in following directory
/usr/include

let me know how to install iostream.h

---

### Post by _0R10N on 2010-04-24
iostream.h is a pretty standard library, did you installed the build-essential package?? It comes with most of the standard libraries you'll need.

Kind regards!

_0R10N >>

---

### Post by srs5694 on 2010-04-24
On my Ubuntu 9.10 system, there is no standard iostream.h file; however, there is a standard iostream file (with no extension), installed in /usr/include/c++/4.4/. It's part of the libstdc++6-4.4-dev package.

---

### Post by jrothwell97 on 2010-04-24
^^what s/he said.

You should be topping your C++ files with:

```
// C++ header file include
#include <iostream>
```

It's not like C, where you have to do

```
/* Plain C header file include */
#include <stdio.h>
```

---

### Post by ibuclaw on 2010-04-24
iostream.h is a deprecated header, and last time I checked (probably a year ago) was already removed in g++-4.3 and later releases.

Simply use:
```
#include <iostream>
```
instead.

Regards
Iain

---

### Post by km0r3 on 2010-04-25
> **ibuclaw said:**
> iostream.h is a deprecated header, and last time I checked (probably a year ago) was already removed in g++-4.3 and later releases.

Simply use:
```
#include <iostream>
```instead.

Regards
Iain

Yes, I can assert that, too. 

<iostream> and <iostream.h> are _not_ the same. Also read [here]("http://www.devx.com/tips/Tip/14447").

---

