---
title: "[C++] Mkdir command"
date: 2011-12-06
forum: Programming Talk
---

### Post by erotavlas on 2011-12-06
Hi,

I need to create a directory under C++ on Linux. I know the mkdir function and I would like to replicate the command line "mkdir -p dir_path". I have tried with
```

#include <sys/types.h>
#include <sys/stat.h>

int status = mkdir("dir_path", S_IRWXU);


```
as specified here [http://linux.die.net/man/3/mkdir](http://linux.die.net/man/3/mkdir). I would like to create a directory also in the case of which the parent's directory doesn't exist. How can I pass the argument -p?

Thank you

---

### Post by ofnuts on 2011-12-06
> **erotavlas said:**
> Hi,

I need to create a directory under C++ on Linux. I know the mkdir function and I would like to replicate the command line "mkdir -p dir_path". I have tried with
```

#include <sys/types.h>
#include <sys/stat.h>

int status = mkdir("dir_path", S_IRWXU);


```as specified here [http://linux.die.net/man/3/mkdir](http://linux.die.net/man/3/mkdir). I would like to create a directory also in the case of which the parent's directory doesn't exist. How can I pass the argument -p?

Thank youYou can't... in the shell command, they are likely splitting the path and creating the intermediate directories one by one. Note that you can use the dirname() call to extract the successive parent names.

---

### Post by ehmicky on 2011-12-06
Hey,
Look at create_directories(), from boost::filesystem (and it'll be portable too)

---

### Post by erotavlas on 2011-12-06
Thank you for fast reply. I know that a simpler way is to use the boost library but I would like to avoid it and I also would like to avoid the use of system.
So the only way is to use mkdir combined with dirname. Is it true?
Do you an example of how I can do?

Thank

---

### Post by dwhitney67 on 2011-12-06
Why do you want to avoid the boost library?  It is meant to be an extension for C++.  Are you working on a school assignment in which your professor wants you to learn the basics?

Anyhow, to complete this "assignment" the hard-way, you need to decompose a given directory path into individual directories.  This is the purpose of using dirname().  So if you need to create a series of directories, say "a/b/c", then you should have a list like:  "a/b/c", "a/b", "a"

By reverse-iterating through this list, you should call mkdir() for each string in the list.  Using the aforementioned example, mkdir() is called for "a", then "a/b", and finally "a/b/c".

Don't forget to perform error checking!  You may also need to read about dirname(), wrt its behavior with paths containing "/" or ".".

---

