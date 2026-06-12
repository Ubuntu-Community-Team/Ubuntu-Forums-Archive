---
title: "Getpid in C Newbie"
date: 2010-06-24
forum: Programming Talk
---

### Post by cristiangarofalo on 2010-06-24
Hi Guys, 
Is there any way to do, Something like this? I need to get a variable with the Pid of a process that is currently running.. (or not) this is on Posix C language.
Obviously what I'm sending below doesn't work. But essentially its kind-of what I'm looking for.

int pid ;
pid = system("pidof myprocess_in_memory");

---

### Post by MadCow108 on 2010-06-24
man 2 getpid

---

### Post by dwhitney67 on 2010-06-24
The code below isn't 100% bullet-proof, but it works for basic purposes:
```

#include <stdio.h>
#include <unistd.h>


int main(int argc, char** argv)
{
   char cmd[256];

   snprintf(cmd, sizeof(cmd) - 1, "pidof %s", argv[1]);

   FILE* fp = popen(cmd, "r");

   if (fp)
   {
      pid_t pid;

      if (fscanf(fp, "%d", &pid) == 1)
      {
         fprintf(stdout, "Process %s is assigned a pid of %d.\n", argv[1], pid);
      }
      else
      {
         fprintf(stderr, "Error acquiring pid.\n");
      }

      pclose(fp);
   }
   else
   {
      fprintf(stderr, "Cannot determine pid for process %s.\n", argv[1]);
   }

   return 0;
}

```

---

