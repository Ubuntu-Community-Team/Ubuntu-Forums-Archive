---
title: "C dup2 append to file"
date: 2010-09-26
forum: Programming Talk
---

### Post by Xender1 on 2010-09-26
Im writing a small program in C and I am trying to redirect STDOUT to append a file. Currently I am overwriting the entire contents of the file and I am unsure why this is happening especially when specifying the O_APPEND flag.
```

int file = open("outfile",O_RDWR | O_APPEND| S_IRUSR | S_IRGRP | S_IWGRP | S_IWUSR);
dup2(file,1); 
close(file);
int ret = execl("/bin/ls","ls","-1",(char *)0);

```

Lets the the file outfile already has two lines in it that both say "blah blah", when this code runs instead of adding the ls result after blah blah, it replaces the whole thing.
Thanks!

---

### Post by dwhitney67 on 2010-09-26
I think you would have better luck using fopen().

```

#include <unistd.h>   // for dup2 and execl
#include <stdio.h>    // for everything else

int main(void)
{
   FILE* file = fopen("outfile", "a+");

   dup2(fileno(file), fileno(stdout));

   fclose(file);

   return execl("/bin/ls", "ls", "-1", NULL);
}

```

---

### Post by gmargo on 2010-09-26
You need to add an **O_CREAT** bit to the flag for **open()**.  If you were checking the return code from the **open()** system call, you would have figured this out yourself.

EDIT: There's a little more to it.  You're missing a comma separating the **flags** from the **mode** in the **open()** call, and missing write permission.  This example program works:
```

#include <stdio.h>
#include <sys/types.h>
#include <sys/stat.h>
#include <fcntl.h>
#include <unistd.h>
#include <stdlib.h>
#include <errno.h>
#include <string.h>

int main(argc, argv)
int argc;
char **argv;
{
    int file = open("outfile",
        O_CREAT | O_RDWR | O_APPEND,
        S_IRUSR | S_IWUSR | S_IRGRP | S_IWGRP | S_IROTH | S_IWOTH );
    if (file < 0)
    {
        fprintf(stderr, "open error: %d [%s]\n", errno, strerror(errno));
        exit(1);
    }
    dup2(file,1);
    close(file);
    int ret = execl("/bin/ls","ls","-1",(char *)0);

    return 0;
}

```

---

### Post by dumbsnake on 2010-09-27
> **gmargo said:**
> You need to add an **O_CREAT** bit to the flag for **open()**.  If you were checking the return code from the **open()** system call, you would have figured this out yourself.

EDIT: There's a little more to it.  You're missing a comma separating the **flags** from the **mode** in the **open()** call, and missing write permission.  This example program works:
```

#include <stdio.h>
#include <sys/types.h>
#include <sys/stat.h>
#include <fcntl.h>
#include <unistd.h>
#include <stdlib.h>
#include <errno.h>
#include <string.h>

int main(argc, argv)
int argc;
char **argv;
{
    int file = open("outfile",
        O_CREAT | O_RDWR | O_APPEND,
        S_IRUSR | S_IWUSR | S_IRGRP | S_IWGRP | S_IROTH | S_IWOTH );
    if (file < 0)
    {
        fprintf(stderr, "open error: %d [%s]\n", errno, strerror(errno));
        exit(1);
    }
    dup2(file,1);
    close(file);
    int ret = execl("/bin/ls","ls","-1",(char *)0);

    return 0;
}

```

This solution will work perfectly, but I would also mention that you should probably use O_WRONLY instead of O_RDWR when opening the file. If, for some reason, you make outfile a pipe or restrict permission in a special way in the future, you'll prefer to have it this way. Kind of nit-picky I guess.

---

