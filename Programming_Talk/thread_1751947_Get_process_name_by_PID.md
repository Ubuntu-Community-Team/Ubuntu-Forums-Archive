---
title: "Get process name by PID"
date: 2011-05-07
forum: Programming Talk
---

### Post by zobayer1 on 2011-05-07
I want to get process name and other options from a given PID using C/C++. I am doing it by checking /proc directory entries.
```

#include <stdio.h>
#include <string.h>

char buff[1048576];

int main(int argc, char **argv) {
    char fname[128];
    sprintf(fname, "/proc/%s/status", argv[1]);
    FILE *fp = fopen(fname, "r");
    if(fp == NULL) return printf("Process not found.\n");
    while(fgets(buff, 1048576, fp)) {
        //if(!strncmp(buff, "State:", 6))
        printf("%s\n", buff);
    }
    fclose(fp);
    return 0;
}

```Here, If I can't open the file, then I assume that the process doesn't exist. Is this correct? Or any easy way to do this?
:popcorn:

---

