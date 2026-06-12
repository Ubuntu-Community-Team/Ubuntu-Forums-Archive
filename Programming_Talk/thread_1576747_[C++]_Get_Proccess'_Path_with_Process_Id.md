---
title: "[C++] Get Proccess' Path with Process Id"
date: 2010-09-17
forum: Programming Talk
---

### Post by dodle on 2010-09-17
I've been trying to figure out how to get an executable/process' path using the pid.  What I have read has told me that I need to do something with "/proc/<pid>/exe", but I don't know where to go from there.  

Here are some pages I have been reading:
[http://stackoverflow.com/questions/143174/c-c-how-to-obtain-the-full-path-of-current-directory](http://stackoverflow.com/questions/143174/c-c-how-to-obtain-the-full-path-of-current-directory)
[http://www.flipcode.com/archives/Path_To_Executable_On_Linux.shtml](http://www.flipcode.com/archives/Path_To_Executable_On_Linux.shtml)

Here is the code I have come up with so far:
[php]#include <iostream>
#include <string.h>
#include <sstream>

int main()
{
    std::string process;

    std::ostringstream ss;

    // Get the process id
    pid_t pid = getpid();

    // Retrieve "/proc/<pid>/exe"
    ss << pid; // Send pid_t to stringstream
    process = "/proc/" + ss.str() + "/exe"; // Convert stringstream to string

    std::cout << process << std::endl;

    return 0;
}[/php]

It looks like I have to use [color=red]readlink()[/color] somehow.  Am I on the right path :?:

---

### Post by MadCow108 on 2010-09-17
man proc
> 
/proc/[pid]/exe:
... this file is a symbolic link containing the actual pathname of the executed command.
This symbolic link can be dereferenced normally; attempting to open it  will open the executable
...


```

char buf[512]
ssize_t ret = readlink("/proc/some-pid/exe", buf, 512);
if (ret > 0)
  buf[ret] = 0;
  printf("%s\n", buf)
}
else
  perror("readlink");

```

---

### Post by dodle on 2010-09-17
Yes, that's it.  I understand now.  Thanks madcow!

[php]#include <iostream>
#include <stdio.h>

int main()
{
    char linkname[512]; /* /proc/<pid>/exe */
    char buf[512];
    pid_t pid;
    int ret;

    /* Get our PID and build the name of the link in /proc */
    pid = getpid();

    snprintf(linkname, sizeof(linkname), "/proc/%i/exe", pid);

    /* Now read the symbolic link */
    ret = readlink(linkname, buf, 512);
    buf[ret] = 0;


    std::cout << buf << std::endl;

    return 0;
}[/php]

**Edit:** I was also trying to see if I could do this without using stdio.

---

