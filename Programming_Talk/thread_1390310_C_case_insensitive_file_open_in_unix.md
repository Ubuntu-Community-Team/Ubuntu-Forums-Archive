---
title: "C case insensitive file open in unix"
date: 2010-01-25
forum: Programming Talk
---

### Post by jero3n on 2010-01-25
I need an open function in C (unix) that the filename parameter is case insensitive.

I wrote this ugly function:

```

int open_ci(const char *path, const char *filename)
{
    DIR *dir; struct dirent *entry; int i;
    char tmp[PATH_MAX+1], entryname[PATH_MAX+1];

    if((dir = opendir(path)) == NULL) {return -1;}
    while((entry = readdir(dir))) {
        i=0;  while( (entryname[i] = toupper(entry->d_name[i])) ) i++;
        i=0;  while( (tmp[i] = toupper(filename[i])) ) i++;
        if(strncmp(tmp, entryname, PATH_MAX) == 0) {
            i = open(entry->d_name, O_RDONLY);
            closedir(dir);
            return i;
        }
    }
    return -1;
}
```

Is there any easier way?

---

### Post by LKjell on 2010-01-25
Then you have a problem if there exist files name "hey" and "heY" . How do your program knows which file to open?

---

### Post by lisati on 2010-01-25
Short of actually reading the disk directory or using some kind of "best guess" routine where you take a potshot and hope it works I can't think of any way at the moment...

Edit: nicely said, LKjell

---

### Post by jero3n on 2010-01-25
> **LKjell said:**
> Then you have a problem if there exist files name "hey" and "heY" . How do your program knows which file to open?

my program is aware of this.. in this specific application i need some files that are always unique in each path. but they are not written in the same way as they come from windows.

> **lisati said:**
> Short of actually reading the disk directory or using some kind of "best guess" routine where you take a potshot and hope it works I can't think of any way at the moment...

yes.. but it is very slow when there are lots of files in the directory.. 
i hoped that there were some built-in function in unix..

---

### Post by lisati on 2010-01-25
> **jero3n said:**
> my program is aware of this.. in this specific application i need some files that are always unique in each path. but they are not written in the same way as they come from windows.



yes.. but it is very slow when there are lots of files in the directory.. 
i hoped that there were some built-in function in unix..

I haven't heard of one. And by the way, this is a [Linux]("http://lmgtfy.com?q=linux") support forum, not a Unix support forum.....

---

### Post by jero3n on 2010-01-25
> **lisati said:**
> I haven't heard of one. And by the way, this is a [Linux]("http://lmgtfy.com?q=linux") support forum, not a Unix support forum.....

:)

Well in fact I need this for Linux. Does it make any difference?

---

### Post by jflaker on 2010-01-25
---Move the input and filename/foldername to temporary variable
---convert the input and the filename/foldername temporary variables to UPPER or lower case (your choice)...if they match, that is the one that you want....
---use the original filename/foldername variable for file operations as that contains the real file/folder name.

---Caveat: Linux can have FileName and Filename and be different entities altogether, so you MAY get the wrong target filename/foldername.



> **jero3n said:**
> I need an open function in C (unix) that the filename parameter is case insensitive.

I wrote this ugly function:

```

int open_ci(const char *path, const char *filename)
{
    DIR *dir; struct dirent *entry; int i;
    char tmp[PATH_MAX+1], entryname[PATH_MAX+1];

    if((dir = opendir(path)) == NULL) {return -1;}
    while((entry = readdir(dir))) {
        i=0;  while( (entryname[i] = toupper(entry->d_name[i])) ) i++;
        i=0;  while( (tmp[i] = toupper(filename[i])) ) i++;
        if(strncmp(tmp, entryname, PATH_MAX) == 0) {
            i = open(entry->d_name, O_RDONLY);
            closedir(dir);
            return i;
        }
    }
    return -1;
}
```

Is there any easier way?

---

### Post by MadCow108 on 2010-01-25
use strncasecmp, its (unlike its name suggests) case insensitive

---

### Post by jero3n on 2010-01-25
thanks for the replies.

---

### Post by PanP5 on 2010-04-13
> **MadCow108 said:**
> use strncasecmp, its (unlike its name suggests) case insensitive

This isn't working for me. The compiler is complaining:

error: ‘strncasecmp’ was not declared in this scope

What's the deal? Here's my code:

```

#include <iostream>
#include <string>
using namespace std;


int main()
{
   string s1;
   string s2;

   cout << "First word: ";
   cin >> s1;
   cout << "Second word: ";
   cin >> s2;

   if(strncasecmp(s1,s2)>0)
   cout << s1 << " is greater. " <<endl;

   else if(strncasecmp(s1,s2)<0)
   cout << s2 << " is greater. " <<endl;

   else if(strncasecmp(s1,s2)==0)
   cout << "They are equal" << endl;

   else
   cout << "What happened?" << endl;

   return 0;
}

```

---

### Post by kknd on 2010-04-13
You must include string.h . Since you're using C++, use:

[PHP]
#include <cstring>
[/PHP]

---

### Post by PanP5 on 2010-04-14
> **kknd said:**
> You must include string.h . Since you're using C++, use:

[PHP]
#include <cstring>
[/PHP]

Thanks!

I assumed <string> was a superset of everything in <string.h>. Guess not.

---

