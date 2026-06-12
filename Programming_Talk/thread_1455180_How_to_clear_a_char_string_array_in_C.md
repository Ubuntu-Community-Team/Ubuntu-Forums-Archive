---
title: "How to clear a char* string array in C"
date: 2010-04-15
forum: Programming Talk
---

### Post by rchan0021 on 2010-04-15
Given that

char *string = (char*)malloc(500);

how would I go about clearing *string?

In java for example if I wanted to make a string empty I would just say,

String var = "";

What would be the C equivalent?

Thanks in advance.

---

### Post by lisati on 2010-04-15
A couple of ways come to mind. Given that strings in C are usually terminated by an ASCII zero, the easiest would be to set the first byte to zero.
Another way might be to use memset() to set the whole string to zeros.

---

### Post by MindSz on 2010-04-15
if you want to "empty" a string 'name' just do ```
name[0] = '\0';
```
Now this doesn't erase all the characters in the string, but since the first character is now a termination character the string looks empty to your program.

If you want to erase all the characters in the string then you need to use a loop.

---

### Post by Simian Man on 2010-04-15
The ways above are valid, but I usually do:
```

strcpy(str, "");

```

Which does the same thing, but conveys the meaning a little better I think.

---

### Post by rchan0021 on 2010-04-15
I tried both methods, but no go. Let me better explain what I am trying to do. I need to make a program that given a directory, i.e. /home/ , the program will list all files within that directory and also any sub directories. My problem is that when using my recursive function printDir(), my char* curFileFullPath doesn't clear between calls to printDir(). So the program works only for the first file, after that curFileFullPath should clear so that a new path can be put in it, but it doesn't clear so if i said /home/ the first time, the second time around it would be /home/home/..., instead of /home/...

Please help, lol.
____________________________________________________________________
```
#include <stdio.h>
#include <stdlib.h>
#include <string.h>
#include <sys/types.h>
#include <sys/stat.h>
#include <dirent.h>

void printDir(char *dirPath);

int main(void)
{
    char *directory = (char*)malloc(500);

    printf("Enter a directory to list (must have tailend / , i.e. /home/): ");
    scanf("%s", directory);

    printDir(directory);

    free(directory);

    return 0;
}

void printDir(char *dirPath) /* dirPath MUST have a tailend / else code won't work, i.e. /home/ */
{
    struct dirent *entry = NULL;
    struct stat s;

    char *curFileFullPath = (char*)malloc(500);

    DIR *mydir = opendir(dirPath);

    while ((entry = readdir(mydir))) /* If we get EOF, the expression is 0 and the loop stops. */
    {
        if (strcmp(entry->d_name, "..") == 0 || strcmp(entry->d_name, ".") == 0)
        {
            continue;
        }
        printf("content of curFileFullPath: %s\n\n",curFileFullPath );
        strcat(curFileFullPath, dirPath);
        strcat(curFileFullPath, entry->d_name);

        if ( stat(curFileFullPath,&s) == 0 )
        {
            if ( s.st_mode & S_IFDIR )
            {
                printf("[Dir]\t%s\n", entry->d_name);
                strcat(curFileFullPath, "/");
                printDir(curFileFullPath);
            }
            else
            {
                printf("%s\n", entry->d_name);
            }
        }
        else
        {
            printf("stat read error\n");
        }
    }
}

```

---

### Post by MindSz on 2010-04-15
you could maybe try to loop through your string (until strlen() or size-of-array) and set all characters to '\0' before storing the new name?

---

### Post by lisati on 2010-04-15
> **MindSz said:**
> you could maybe try to loop through your string (until strlen() or size-of-array) and set all characters to '\0' before storing the new name?

This can be done with [memset]("http://www.elook.org/programming/c/memset.html")

---

### Post by MadCow108 on 2010-04-15
the problem goes beyond simple clearing (string[0] = 0 is the best solution when one only handles normal c style strings)

to fix your program move the strcat(..., dirPath) before the while loop and save the length there
and then just always reset after this length in the loop:
curFileFullPath[len] = 0;
printf("content of curFileFullPath: %s\n\n",curFileFullPath );
strcat(curFileFullPath, entry->d_name);


but you still have memory and resource leaks
use free and closedir

if the original buffer is big enough you technically don't even need the copy of the path
replace curFileFullPath with dirPath, remove the malloc and first strcat in printDir and you only have a resource leak left

---

### Post by cb951303 on 2010-04-15
or you could use "calloc" instead of "malloc" and get a zero initialized array?

---

### Post by falconindy on 2010-04-15
Rather than using strcat twice, just use snprintf:

```
snprintf(curFileFullPath, strlen(dirPath) + strlen(entry->d_name) + 1, "%s%s", dirPath, entry->d_name);
```

This will overwrite the contents of the string, and neatly append a \0 to the end of the format.

---

### Post by rchan0021 on 2010-04-15
Thank Everyone! With your advice I finally got my program working.

---

