---
title: "unix C api to get pid by passin a process name"
date: 2011-07-01
forum: Programming Talk
---

### Post by Blackbug on 2011-07-01
I am writin an application in c++ in which a thread needs to check whether an another process is runnin or not ( based on this need to do further work ).
is there any c api provided by unix similar to getpid which takes a process name and return me its pid?
 
I dont want to make a system call system( ps -a | grep <process name) since it might slow my application.
 
Do suggest.

---

### Post by dwhitney67 on 2011-07-01
To the best of my knowledge, there is no C library function call that you can use to query whether a process is running.

Of course, you can check using "ps -ef", and have the output directed to a readable stream, say using popen().  However it seems that you wanted to avoid that.

---

### Post by Blackbug on 2011-07-01
well yes..
in that case any other idea how can i check if another process is runnin

---

### Post by slavik on 2011-07-01
Try looking at killall/pgrep/pkill code to see how they do it.

They might be iterating through the /proc file system.

---

### Post by dwhitney67 on 2011-07-01
Typically a process that wants to "advertise" that is running will create a file, containing the process PID, in /var/run.

If the external process is doing such a thing, then your process (thread) would need to check that the file exists.  The existence of the file is no guarantee that the process is running, but if you are willing to take risks, then you could assume if the file is present, then the process is running.  You can check the existence of the file using stat().

Otherwise, as I indicated earlier, you can use popen().
```

#include <cstdio>
#include <sstream>
#include <iostream>

int main()
{
   const char* someapp = "foo";
   std::stringstream cmd;

   cmd << "ps -ef | grep " << someapp << " | grep -v grep -c";

   FILE* app = popen(cmd.str().c_str(), "r");
   char instances = '0';

   if (app)
   {
      fread(&instances, sizeof(instances), 1, app);
      pclose(app);
   }

   std::cout << someapp << " is "
             << (instances == '0' ? "NOT" : "")
             << " running."
             << std::endl;
}

```

---

### Post by johnl on 2011-07-01
You can check the cmdline entries in /proc.

Something like this:

```

#include <stdlib.h>
#include <stdio.h>
#include <string.h>
#include <unistd.h>
#include <dirent.h>
#include <sys/types.h>

pid_t proc_find(const char* name) 
{
    DIR* dir;
    struct dirent* ent;
    char* endptr;
    char buf[512];
    
    if (!(dir = opendir("/proc"))) {
        perror("can't open /proc");
        return -1;
    }

    while((ent = readdir(dir)) != NULL) {
        /* if endptr is not a null character, the directory is not
         * entirely numeric, so ignore it */
        long lpid = strtol(ent->d_name, &endptr, 10);
        if (*endptr != '\0') {
            continue;
        }

        /* try to open the cmdline file */
        snprintf(buf, sizeof(buf), "/proc/%ld/cmdline", lpid);
        FILE* fp = fopen(buf, "r");
        
        if (fp) {
            if (fgets(buf, sizeof(buf), fp) != NULL) {
                /* check the first token in the file, the program name */
                char* first = strtok(buf, " ");
                if (!strcmp(first, name)) {
                    fclose(fp);
                    closedir(dir);
                    return (pid_t)lpid;
                }
            }
            fclose(fp);
        }
        
    }
    
    closedir(dir);
    return -1;
}


int main(int argc, char* argv[]) 
{
    if (argc == 1) {
        fprintf("usage: %s name1 name2 ...\n", argv[0]);
        return 1;
    }
    
    int i;
    for(int i = 1; i < argc; ++i) {
        pid_t pid = proc_find(argv[i]);
        if (pid == -1) {
            printf("%s: not found\n", argv[i]);
        } else {
            printf("%s: %d\n", argv[i], pid);
        }
    }

    return 0;
}

```

Edit:  I see that you are using C++, you can simplify some things by using the C++ fstream and << operator rather than my hackish fgets/strtok.

---

### Post by Arndt on 2011-07-01
> **dwhitney67 said:**
> Typically a process that wants to "advertise" that is running will create a file, containing the process PID, in /var/run.

If the external process is doing such a thing, then your process (thread) would need to check that the file exists.  The existence of the file is no guarantee that the process is running, but if you are willing to take risks, then you could assume if the file is present, then the process is running.  You can check the existence of the file using stat().


If the pid is stored in the file, you should of course use that information. You can use 'kill' to see whether a pid belongs to a running process.

---

