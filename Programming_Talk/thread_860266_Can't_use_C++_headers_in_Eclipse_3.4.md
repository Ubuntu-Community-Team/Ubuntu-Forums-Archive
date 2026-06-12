---
title: "Can't use C++ headers in Eclipse 3.4"
date: 2008-07-15
forum: Programming Talk
---

### Post by AOZ on 2008-07-15
When i make a .cpp file and try to include iostream.h or math.h etc., it gives me an error No include files were found. why is this?

---

### Post by Jessehk on 2008-07-15
Any header files ending in ".h" that are part of the C++ standard are deprecated.

You should be using filenames with no suffix for C++ headers, ie
```

#include <iostream>
#include <string>

```

and C headers (like time.h and math.c) are prepeneded with a "c" and also have no suffix.

```

#include <ctime>
#include <cmath>
#include <cctype>

```

etc.

Since you're using old headers, it's likely you haven't been introduced to namespaces. Do a google search.

I'd also advise dumping whatever learning material you have that teaches you about these headers: it's outdated.

---

