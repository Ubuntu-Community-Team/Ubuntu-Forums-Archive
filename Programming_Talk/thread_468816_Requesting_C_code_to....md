---
title: "Requesting C code to..."
date: 2007-06-09
forum: Programming Talk
---

### Post by Sockerdrickan on 2007-06-09
...create a .Dir in the current user home dir :) Thanks :p

---

### Post by ruy_lopez on 2007-06-09
The fragment below should get you started, try the manpages for the individual functions shown,

```

#include <sys/stat.h> /* for */
#include <sys/types.h> /* mkdir */
#include <stdlib.h> /* for getenv */
#include <sys/param.h> /* for MAXPATHLEN */
#include <stdio.h>

int main()
{
        char *homedir, path[MAXPATHLEN];
        char *dir = "folder_to_create";
        mode_t mode = (S_IRWXU | S_IRGRP | S_IXGRP | S_IROTH | S_IXOTH);

        homedir = getenv("HOME");
        snprintf(path, MAXPATHLEN, "%s/%s", homedir, dir);
        mkdir(path, mode);

}

```

In fact, replacing snprintf(...) with chdir(homedir), then using mkdir(dir, mode), is probably simpler. In that case, include <unistd.h>.

---

### Post by Sockerdrickan on 2007-06-09
Edit: It works :D

```
#include <sys/stat.h> /* for */
#include <sys/types.h> /* mkdir */
#include <stdlib.h> /* for getenv */
#include <sys/param.h> /* for MAXPATHLEN */
#include <stdio.h>

int main()
{
        char *homedir, path[MAXPATHLEN];
        char *dir = ".unknown";
        mode_t mode = (S_IRWXU | S_IRGRP | S_IXGRP | S_IROTH | S_IXOTH);

        homedir = getenv("HOME");
        chdir(homedir);
        mkdir(dir, mode);
}
```

---

