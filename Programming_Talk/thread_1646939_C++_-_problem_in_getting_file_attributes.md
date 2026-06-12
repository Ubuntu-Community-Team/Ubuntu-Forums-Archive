---
title: "C++ - problem in getting file attributes"
date: 2010-12-16
forum: Programming Talk
---

### Post by mecrazycoder on 2010-12-16
Hi, 
   I wrote small piece of code to check whether others have read permission on given directory. But I am getting following error "4 cannot be used as function" while using this S_IROTH where as S_ISDIR is working fine. Here is the code
```
bool FileSearch::isDir ( string dir )
{

    struct stat fileInfo;
    stat(dir.c_str(), &fileInfo);

    if ( S_ISDIR ( fileInfo.st_mode ) && !S_IROTH ( fileInfo.st_mode ) )
    {
        return true;
    }
    else
    {
        return false;
    }

}
```Please help me

---

### Post by Arndt on 2010-12-16
> **mecrazycoder said:**
> Hi, 
   I wrote small piece of code to check whether others have read permission on given directory. But I am getting following error "4 cannot be used as function" while using this S_IROTH where as S_ISDIR is working fine. Here is the code
```
bool FileSearch::isDir ( string dir )
{

    struct stat fileInfo;
    stat(dir.c_str(), &fileInfo);

    if ( S_ISDIR ( fileInfo.st_mode ) && !S_IROTH ( fileInfo.st_mode ) )
    {
        return true;
    }
    else
    {
        return false;
    }

}
```Please help me

You are correct. The man page stat(2) says this about those two:

```
The following POSIX macros are defined to check the file type using the
       st_mode field:
           S_ISDIR(m)  directory?
...

The following flags are defined for the st_mode field:
S_IROTH    00004     others have read permission
...

```

As the compiler tells you (more or less), S_IROTH expands to 4. I suppose they didn't bother to define macros for all the situations, just the most common ones.

If you want to see how macros are expanded, use the -E option with gcc/g++.

---

### Post by mecrazycoder on 2010-12-16
So how to check whether particular file/dir is hidden(using stat) or others have read permission over the file?

---

### Post by MadCow108 on 2010-12-16
you have to use this macro differently, it does not take an argument (see man 2 stat)

do:
```

if ((f.st_mode & S_IROTH) == S_IROTH) ...

```
too to check if that flag is set.

S_ISDIR is a shortcut for a similar thing ((x & S_IFMT) == S_IFDIR)

---

### Post by mecrazycoder on 2010-12-16
Tanx. Let me try

---

### Post by mecrazycoder on 2010-12-16
How to check dir is hidden or not using stat ?

---

### Post by MadCow108 on 2010-12-16
there is no hidden attribute in unix systems as there is in windows.
files are hidden by adding a dot in front of their name, e.g. .myhiddenfile

and what do you mean with not using stat?
in unix (almost) everything is a file and thus should be "stat'able"

---

### Post by mecrazycoder on 2010-12-16
Its not "not using stat". Its "hidden or not".... Ok is there work around to find dir is hidden or any regex to find dir names start with .

---

### Post by MadCow108 on 2010-12-16
you can use basename to get the last level of the full path and check if it has a dot as first character and is not . or ..
man 3 basename

---

