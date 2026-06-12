---
title: "Running Multiple Process"
date: 2009-11-10
forum: Programming Talk
---

### Post by nebu on 2009-11-10
Say i create a c program like

```

#include <stdlib.h>

int main(){
int i;
for(i=0;i<5;i++)
fork();

//Some code

return 0;
}


```how do i make the parent process finish only after all the 5 children have terminated?

---

### Post by Arndt on 2009-11-10
> **nebu said:**
> Say i create a c program like

```

#include <stdlib.h>

int main(){
int i;
for(i=0;i<5;i++)
fork();

//Some code

return 0;
}


```how do i make the parent process finish only after all the 5 children have terminated?

You use 'wait' or one of the other functions described on the same manual page.

---

### Post by nebu on 2009-11-10
could u elaborate with some code....

i am not getting very far with the manual pages

---

### Post by dwhitney67 on 2009-11-10
It amounts to something as simple as...
```

man 2 wait

```

In case you find yourself dazed/confused/deer-in-headlights, here's a basic example...
```

#include <unistd.h>
#include <stdlib.h>
#include <stdio.h>

void childDoSomething();

int main()
{
   pid_t chld_pid[5] = {0};
   int   num_chld    = 0;

   for (int i = 0; i < 5; ++i)
   {
      chld_pid[i] = fork();

      if (chld_pid[i] == 0)
      {
         // we are the child; do something very unconstructive
         childDoSomething();
         exit(0);
      }
      else if (chld_pid[i] > 0)
      {
         ++num_chld;
      }
   }

   while (num_chld--)
   {
      sleep(1);
      printf("Waiting for children to die...\n");

      for (int i = 0; i < 5; ++i)
      {
         int status;
         waitpid(chld_pid[i], &status, 0);
      }
   }
   printf("All children are dead... dead I tell you!\n");

   return 0;
}

void childDoSomething()
{
   for (int i = 0; i < 5; ++i)
   {
      sleep(1);
      if (i == 0)
         printf("The child is running.\n");
      else
         printf("The child is still running.\n");
   }
   printf("The child is done.\n");
}

```

---

### Post by MindSz on 2009-11-10
You can also use threads.

[http://www.cs.cf.ac.uk/Dave/C/node32.html](http://www.cs.cf.ac.uk/Dave/C/node32.html)

---

