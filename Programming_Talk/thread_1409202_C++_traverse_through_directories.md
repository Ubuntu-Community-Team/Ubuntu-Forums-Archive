---
title: "C++ traverse through directories"
date: 2010-02-17
forum: Programming Talk
---

### Post by Woody1987 on 2010-02-17
I need some help with this app im writing in C++. It needs to be able to traverse through some directories. I have some code already done, but write now it just prints out a list of the contents of a directory. I would like it to be able to distinguish between a file and directory, so that for every subdirectory it finds it can move to there.

Code so far:

```
#include <sys/types.h>
#include <dirent.h>
#include <errno.h>
#include <vector>
#include <string>
#include <iostream>

using namespace std;

int getdir(string rootDir, vector<string> &files)
{
    DIR *dir; //the directory
    struct dirent *dp;

    //open the directory
    if((dir  = opendir(rootDir.c_str())) == NULL)
    {
        cout << "Error(" << errno << ") opening " << rootDir << endl;
        return errno;
    }

    while ((dp = readdir(dir)) != NULL)
    {
        files.push_back(string(dp->d_name));

        if(directory do something) //need help here

        if(file do something else)
    }

    closedir(dir);
    return 0;
}

int main()
{
    string rootDir = string(".");
    vector<string> files = vector<string>();

    getdir(rootDir, files);

    for (unsigned int i = 0; i < files.size(); i++)
        cout << files[i] << endl;

    return 0;
}

```

---

### Post by Woody1987 on 2010-02-17
found the answer, i used dp->d_type to find the type.

---

### Post by howlingmadhowie on 2010-02-17
here's a link to a C program google found to do that: [http://www.metalshell.com/source_code/1/Check_Directory.html](http://www.metalshell.com/source_code/1/Check_Directory.html)

---

### Post by Woody1987 on 2010-02-17
Ok, i thought i had solved this, but i havent completely. This program needs to run on both windows and linux. d_type works fine in linux but is not included with mingw on windows for some reason. Is there a way to get the same result on windows?

---

### Post by MadCow108 on 2010-02-17
you could use the boost filesystem library
[http://www.boost.org/doc/libs/1_42_0/libs/filesystem/doc/index.htm](http://www.boost.org/doc/libs/1_42_0/libs/filesystem/doc/index.htm)

---

### Post by Woody1987 on 2010-02-17
> **MadCow108 said:**
> you could use the boost filesystem library
[http://www.boost.org/doc/libs/1_42_0/libs/filesystem/doc/index.htm](http://www.boost.org/doc/libs/1_42_0/libs/filesystem/doc/index.htm)

Perfect! thanks.

---

### Post by ibuclaw on 2010-02-17
I would say use stat.h - it is a more C way of doing things, yes, but it is also lighter on the load. :)
```

#include <sys/stat.h>

struct stat st;
char *path;

stat(path, &st);
if(st.st_mode & S_IFDIR)
{
    // path is a Directory
}

```
and have a look at [the documentation]("http://www.opengroup.org/onlinepubs/009695399/basedefs/sys/stat.h.html") of that header for more indepth review.

Regards
Iain

---

### Post by Woody1987 on 2010-02-17
> **ibuclaw said:**
> I would say use stat.h - it is a more C way of doing things, yes, but it is also lighter on the load. :)
```

#include <sys/stat.h>

struct stat st;
char *path;

stat(path, &st);
if(st.st_mode & S_IFDIR)
{
    // path is a Directory
}

```
and have a look at [the documentation]("http://www.opengroup.org/onlinepubs/009695399/basedefs/sys/stat.h.html") of that header for more indepth review.

Regards
Iain

Even better! cheers.

---

### Post by Cracauer on 2010-02-17
There also is the fts(3) C library which originated from BSD but can probably be found in Linuxens.

Myself, I usually want to traverse over a subset of files based on some random criteria. The commandline find(1) is so much more powerful and fast in coming with the right filters, not to mention easier to debug (just copy'n'paste into shell) that I usually do the equivalent of
```

popen("find . [... lots complicated options ...] | grep -or -whatever", "r");

```

---

