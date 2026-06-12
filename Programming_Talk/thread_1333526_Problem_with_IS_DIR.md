---
title: "Problem with IS_DIR"
date: 2009-11-21
forum: Programming Talk
---

### Post by miodas007 on 2009-11-21
Hi,
i have a problem. Makro IS_DIR return me alwayes true. Why? I will be grateful if someone help me.
This is my source:
```
oid find(const char *where, const char *which)
{
    DIR *directory; //nasz biezacy katalog
    struct stat status; //informacje o naszych kolejnych plikach
    struct dirent *directory_list; //wszystko o atrybutach konkretnego pliku

    directory = opendir(where);
    while((directory_list = readdir(directory)) != NULL) //je&#347;li otwarcie sie nie powiodlo do readdir() = NULL
    {
        lstat(directory_list->d_name, &status);
        if(compare(which, directory_list->d_name))
            printf("%s\trozmiar = %d\n", directory_list->d_name, status.st_size);
        if(S_ISDIR(status.st_mode)) //ALWAYES RETURN TRUE. WHY??
           find(directory_list->d_name, which);
    }
}
```

ps. sorry for my english:)

---

### Post by Arndt on 2009-11-21
> **miodas007 said:**
> Hi,
i have a problem. Makro IS_DIR return me alwayes true. Why? I will be grateful if someone help me.
This is my source:
```
oid find(const char *where, const char *which)
{
    DIR *directory; //nasz biezacy katalog
    struct stat status; //informacje o naszych kolejnych plikach
    struct dirent *directory_list; //wszystko o atrybutach konkretnego pliku

    directory = opendir(where);
    while((directory_list = readdir(directory)) != NULL) //je&#347;li otwarcie sie nie powiodlo do readdir() = NULL
    {
        lstat(directory_list->d_name, &status);
        if(compare(which, directory_list->d_name))
            printf("%s\trozmiar = %d\n", directory_list->d_name, status.st_size);
        if(S_ISDIR(status.st_mode)) //ALWAYES RETURN TRUE. WHY??
           find(directory_list->d_name, which);
    }
}
```

ps. sorry for my english:)

I can run your code with minor changes, so S_ISDIR does what it should here. But I had to add one thing: you must skip the entries "." and "..". Otherwise the function will call itself until it crashes. Perhaps that is what you interpret as S_ISDIR always returning true?

If not, add lots of printf so you see better what happens.

---

### Post by miodas007 on 2009-11-21
> you must skip the entries "." and "..".]
Sorry, but i don't understand what I have to skip this entries.
> Otherwise the function will call itself until it crashes. Perhaps that is what you interpret as S_ISDIR always returning true?If we comment the recursive ```
find(directory_list->d_name, which);
```situation is the same.

---

### Post by Arndt on 2009-11-22
> **miodas007 said:**
> Sorry, but i don't understand what I have to skip this entries.
If we comment the recursive ```
find(directory_list->d_name, which);
```situation is the same.

OK, then your problem is not due to excessive recursion. But is it the case that S_ISDIR returns true for every entry? Print out the file name and the value of the mode field, to see what is happening.

---

### Post by dwhitney67 on 2009-11-22
I agree with Arndt; you do not want to consider the '.' nor the '..' entries when searching the directories.  These ought to be skipped.  Use strcmp() to detect these, and if found, just continue to the next result returned by readdir().
```

while((directory_list = readdir(directory)) != NULL)
{
   if (strcmp(directory_list->d_name, '.')  == 0 ||
       strcmp(directory_list->d_name, '..') == 0)
   {
      continue;
   }

   ...
}

```

Also, I am a bit confused why you chose to use lstat(); are you hoping to obtain other information that is not available with merely looking at the 'd_type' field of struct dirent?  If the 'd_type' field is equal to DT_DIR, then you have a directory.

Another thing that you are missing is the concatenation of the original directory path to the 'd_name' before you call your function recursively.  When readdir() returns a valid value, it is not the full path of the directory entry, it is merely the name.  So to construct the *next* 'where' string, you would need to take current 'where' plus a '/' character, and then finally append the 'd_name'.

---

### Post by miodas007 on 2009-11-22
>  Use strcmp() to detect these, and if found, just continue to the next result returned by readdir().
I have done it

> Another thing that you are missing is the concatenation of the original directory path to the 'd_name' before you call your function recursively. When readdir() returns a valid value, it is not the full path of the directory entry, it is merely the name. So to construct the *next* 'where' string, you would need to take current 'where' plus a '/' character, and then finally append the 'd_name'. 	  	
Hmmm.....I don't know if I understand your tip.
My code is:

```
void find(char *where, char *which)
{
    DIR *directory; //nasz biezacy katalog
    struct stat status; //informacje o naszych kolejnych plikach
    struct dirent *directory_list; //wszystko o atrybutach konkretnego pliku

    directory = opendir(where);
    while((directory_list = readdir(directory)) != NULL) //je&#347;li otwarcie sie nie powiodlo do readdir() = NULL
    {
        if(!strcmp(directory_list->d_name, ".") || !strcmp(directory_list->d_name, "..")) continue;
        printf("actual file/direct = %s\n", directory_list->d_name);
        lstat(directory_list->d_name, &status);
        if(!strcmp(which, directory_list->d_name))
            printf("%s\trozmiar = %d\n", directory_list->d_name, status.st_size);
        if(S_ISDIR(status.st_mode)){
            printf("MAMY KAT\n");
            where = strcat(where, "/");
            where = strcat(where, directory_list->d_name);
           find(where, which);
        }
    }
}
```

Now, IS_DIR alwayes return me false. Why?

---

### Post by dwhitney67 on 2009-11-22
> **miodas007 said:**
> ...
        if(S_ISDIR(status.st_mode)){
            printf("MAMY KAT\n");
            where = strcat(where, "/");
            where = strcat(where, directory_list->d_name);
           find(where, which);
        }
    }
}[/CODE]

If only it were this easy... but sorry, it is not.

You do not have any idea how big is the memory space pointed to by 'where', thus it is possible that you may overrun your buffer.  You will need to use allocation, or easier yet, declare a buffer on the stack, so that you can build the proper path name.

Anyhow, it appears that you are still using lstat(), yet you did not indicate why.  If all you care is to determine whether you have a directory entry, look at whether directory_list->d_type is equal to DT_DIR.

Here's a simple example demonstrating the information I am trying to convey:
```

#include <dirent.h>
#include <string.h>
#include <stdio.h>

void findDirs(const char* path)
{
   if (path == 0) return;

   DIR* dir = opendir(path);

   if (dir)
   {
      printf("Found directory: %s\n", path);

      struct dirent* de = 0;

      while ((de = readdir(dir)) != 0)
      {
         if (strcmp(de->d_name, ".")  == 0 ||
             strcmp(de->d_name, "..") == 0)
         {
            continue;
         }

         if (de->d_type == DT_DIR)
         {
            // a directory

            char newPath[1024] = {0};

            snprintf(newPath, sizeof(newPath) - 1, "%s/%s", path, de->d_name);

            findDirs(newPath);
         }
         else
         {
            // not a directory
            printf("Found file: %s\n", de->d_name);
         }
      }
   }
}

int main(int argc, char** argv)
{
   findDirs(argv[1]);
   return 0;
}

```

---

