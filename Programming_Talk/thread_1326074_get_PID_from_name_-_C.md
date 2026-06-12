---
title: "get PID from name - C"
date: 2009-11-14
forum: Programming Talk
---

### Post by dread22 on 2009-11-14
I need a way to get the PID of another program through a C program. Is there a way to do this?

If the only way is through a /proc search... how do I open all the file in one directory one by one?

---

### Post by dwhitney67 on 2009-11-14
EDIT:  I must've glanced over the word "another" in your OP.

To open a directory, use opendir().  To read the directory contents, use readdir().  The latter function requires a handle to a DIR object, which is returned by opendir().

Read the manpage for these functions.

---

### Post by dread22 on 2009-11-14
> **dwhitney67 said:**
> EDIT:  I must've glanced over the word "another" in your OP.

To open a directory, use opendir().  To read the directory contents, use readdir().  The latter function requires a handle to a DIR object, which is returned by opendir().

Read the manpage for these functions.

Yeah I got to that part and have the list of files in the directory but I don't know how to open the struct dirent * variable. Usually to open a file it's fopen(char*)/open(char*) so I have no clue what to do next once I get the struct dirent *.

---

### Post by dwhitney67 on 2009-11-14
EDIT...

Here's a C implementation of how to find if a particular process is running...

findtask.c:
```

#include <dirent.h>
#include <string.h>
#include <stdlib.h>
#include <stdio.h>

int main(int argc, char** argv)
{
   if (argc < 2)
   {
      fprintf(stderr, "Usage: %s <process name>\n", argv[0]);
      return 1;
   }

   const char* directory = "/proc";
   size_t      taskNameSize = 1024;
   char*       taskName = calloc(1, taskNameSize);

   DIR* dir = opendir(directory);

   if (dir)
   {
      struct dirent* de = 0;

      while ((de = readdir(dir)) != 0)
      {
         if (strcmp(de->d_name, ".") == 0 || strcmp(de->d_name, "..") == 0)
            continue;

         int pid = -1;
         int res = sscanf(de->d_name, "%d", &pid);

         if (res == 1)
         {
            // we have a valid pid

            // open the cmdline file to determine what's the name of the process running
            char cmdline_file[1024] = {0};
            sprintf(cmdline_file, "%s/%d/cmdline", directory, pid);

            FILE* cmdline = fopen(cmdline_file, "r");

            if (getline(&taskName, &taskNameSize, cmdline) > 0)
            {
               // is it the process we care about?
               if (strstr(taskName, argv[1]) != 0)
               {
                  fprintf(stdout, "A %s process, with PID %d, has been detected.\n", argv[1], pid);
               }
            }

            fclose(cmdline);
         }
      }

      closedir(dir);
   }

   // just let the OS free this process' memory!
   //free(taskName);

   return 0;
}

```
To build:
```

gcc -std=gnu99 findtask.c -o findtask

```
To use:
```

./findtask bash

```

---

### Post by dread22 on 2009-11-15
Thanks.

I was hoping there was a quicker way to open directly using the return value from readdir but will use this.

---

### Post by apmcd47 on 2009-11-16
how about this as a template?

[PHP]char com[160];
char *oprog;   // pointer to name of other prog you want PID of
char *tmpfile = "/tmp/sysoutput";   // name of file to put output of pgrep
int status, pid;
FILE *fff;

// get oprog (left to you)
(void) sprintf com, "pgrep %s > %s", oprog, tmpfile);
status = system(com);
// check status - read the manpage for that
fff = fopen(tmpfile, "r");
fscanf(fff, "%d\n", &pid);
[/PHP]

more work has to be done. I'm not getting the name of the program you are searching for or checking the status. Also, the tmpfile name is not unique and what if there are several processes?. But this must be better than reading /proc.

Andrew

---

### Post by dwhitney67 on 2009-11-16
> **dread22 said:**
> Thanks.

I was hoping there was a quicker way to open directly using the return value from readdir but will use this.

Incredible!  It's not like you have to do it; the computer will do it.

---

### Post by riskwill on 2012-09-19
I didn't find a simpler solution on the internet, so I solved with a system call "pidof <process_name>"...

```

#include <stdio.h>
#include <stdlib.h>
#include <unistd.h>
#include <sys/types.h>
#include <string.h>

int GetPIDbyName(char* pidName)
{
    FILE *fp;
    char pidofCmd[50]={0};
    int pidValue=-1;
        
    if(pidName != 0) {
        strcpy(pidofCmd, "pidof ");
        strcat(pidofCmd, pidName);
        strcat(pidofCmd,  "> /tmp/pidof");
        system(pidofCmd); 
        fp = fopen("/tmp/pidof", "r");
        fscanf(fp, "%d", &pidValue);
        fclose(fp);
    }
    return pidValue;
}

int main() 
{
      int eclipsePid = GetPIDbyName("eclipse") ; 
      if(eclipsePid < 0) {
          printf("error on get eclipse pid\n");
      } else {
          printf("eclipse pid: %d\n", eclipsePid);
      }
      return 0;
}


```

---

### Post by dwhitney67 on 2012-09-19
Um... this is a very old thread.  I doubt the OP is still looking for a solution.

As for your solution, it is not the best.  Here's evidence of that: instead of searching for the PID of "eclipse", search for the PID of this application... "foo; rm -rf /".

Just kidding... don't run your program with my suggestion above.

---

### Post by ofnuts on 2012-09-19
Also, run  ```
pidof getty
``` to see another problem with your solution.

---

