---
title: "C director search strange problem (recursion)"
date: 2010-09-15
forum: Programming Talk
---

### Post by Xender1 on 2010-09-15
Trying to write juts a simple C program that will start at the current directory, then just goes through the directory and when it sees another directory it says here is a directory then enters it and does the same. 

The problem with the following code is that it does not enter the right directory only enters the last one in the one it starts with and then from there does not find directories. So i think its because of pointers but it also may be because i am not fulling understanding opendir/readdir. 

```

#include <stdio.h>
#include <stdlib.h>
#include <dirent.h>
#include <sys/types.h>
#include <sys/stat.h>
#include <string.h>
unsigned char isDir = 0x4;
void directorysearch(char name[]) {
    DIR *mydir;
    struct dirent *entry = NULL;
    struct stat st;

    mydir = opendir(name);
    if (mydir!= NULL) {
        printf("entering %s\n",name);
        while ((entry = readdir(mydir))) {
            stat(entry->d_name,&st);

            if (entry->d_type == isDir) { //is directory
                if (strcmp(entry->d_name,".") != 0 & strcmp(entry->d_name,"..") != 0) {
                    printf("%s is a directory\n",entry->d_name);
                    directorysearch(entry->d_name);
                }
            }
        }
    }
}

```

Any tips / pointers (hehe) would be appreciated, thanks!

edit update
 changed my test to see if its a directory to:

```

//this is global
unsigned char isDir = 0x4;
//then the if statement
if (entry->d_type == isDir) {

```

now it is recursing into the directory yay! but it only seems to see the directories in the current directory (it gets all of them) but only seems to go into them one level

---

### Post by schauerlich on 2010-09-15
In this line:

```
if (strcmp(entry->d_name,".") != 0 **&** strcmp(entry->d_name,"..") != 0) {
```

You have a bitwise AND (&) instead of a boolean AND (&&).

---

### Post by Some Penguin on 2010-09-15
Use the reentrant version of readdir.  readdir() implementations are permitted to use statically allocated memory to store results.

---

### Post by spjackson on 2010-09-15
There are 2 faults that don't actually affect the outcome.
1. You have & when you mean &&.
2. You don't call closedir() before returning from the function.

The reason it fails, though, is that entry->d_name only has the file  *name*, not a path to that file, and your current working directory does  not change.

So if you have a path ./a/b/c , and you call your function with ".". You  readdir on "."  and find "a", you then readdir on "a" and find "b" but  your opendir on "b" fails because "b" isn't in your current directory.  

You could put in a diagnostic (e.g. call perror()) when openddir fails.  stat() will also be failing, but you are not using its results.

---

