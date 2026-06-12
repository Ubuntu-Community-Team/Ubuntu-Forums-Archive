---
title: "getting a return value from another program in C"
date: 2017-04-13
forum: Programming Talk
---

### Post by jlw2002us on 2017-04-13
How to get return value from another program.  

In program1.c:

```
wait(&status);
printf(%d,status);
```

In program2.c:

```
return 4;
```

But status is not 4?  Is there another way to get return value from program2.c?

---

### Post by howefield on 2017-04-13
Thread moved to the "*Programming Talk*" forum.

---

### Post by dwhitney67 on 2017-04-19
> **jlw2002us said:**
> 
But status is not 4?

What value did you get??

You should read the man-page for *wait* (man 3 wait).

In case you are still stuck, here's a trivial example:
```

#include <unistd.h>
#include <sys/wait.h>
#include <stdio.h>

int main()
{
    if (fork() == 0)
    {
        // child process
        return 4;
    }
    else
    {
        int status;

        wait(&status);

        if (WIFEXITED(status))
        {
            printf("Child Process Status: %d\n", WEXITSTATUS(status));
        }
    }

    return 0;
}

```

---

