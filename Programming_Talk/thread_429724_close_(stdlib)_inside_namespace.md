---
title: "close (stdlib) inside namespace"
date: 2007-05-01
forum: Programming Talk
---

### Post by angustia on 2007-05-01
hi
i 'got a little problem

i got a namespace with a memeber function called close(), that has to call the standard C funcion close():

```

namespace NS {
    int close() {
        ...
        return close(fd);
    }
}

```

the internal close must be the close from stdlib, but the compiler complains about bad number of arguments.

i know there are c++ versions of sandard C libs (cstdlib, cstdio), but those don't cover other libs like fcntl

thanks for any help

---

### Post by WW on 2007-05-01
Use :: with no name in front to refer to the global namespace.

This compiles with g++:
```

#include <unistd.h>

namespace NS {
    int close() {
        int fd;
        return ::close(fd);
    }
}

```

---

