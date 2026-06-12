---
title: "detect if it's a dir, using opendir(const char*)"
date: 2009-05-08
forum: Programming Talk
---

### Post by cl333r on 2009-05-08
Folks, how do I detect when the path passed to opendir points to a file (not to a dir)? - I need to handle this.
My code only handles the case when the file can't be opened at all:

```

DIR *dir=0;
    try {
	dir=opendir(sFullDirPath.c_str());
    } catch(int errType) {//never triggered
        cout << "Probably not a dir: " << errType << endl;
        return;
    }
    if(dir == NULL) {
	return "Can't open dir: " + sFullDirPath;
    }

```
Any working example please?

---

### Post by johnl on 2009-05-08
Hi,

You can use stat() prior to calling opendir() to make sure that it is a directory.  

```

/* untested */
#include <sys/types.h>
#include <sys/stat.h>
#include <unistd.h>


/* ..... */
struct stat statbuf;

if (stat(some_file.c_str(), &statbuf) < 0)) {
    /* doesn't exist or other failure */
    perror("stat");
} else {
    /* sucessfully stat'd file */
    if (S_ISDIR(statbuf.st_mode)) {
       /* it's a directory  
        * call opendir(...) */
    }
}

```

---

### Post by ibuclaw on 2009-05-08
[http://www.opengroup.org/onlinepubs/009695399/basedefs/sys/stat.h.html](http://www.opengroup.org/onlinepubs/009695399/basedefs/sys/stat.h.html)
```

#include <sys/stat.h>
char *path = "/tmp";
/*
...
*/
struct stat st;
if(! lstat(path, &st))
{
    if(S_ISDIR(st.st_mode))
        printf("%s is a directory\n", path);
}
else
printf("Cannot stat %s\n", path);

```

Regards
Iain

[EDIT]
Heh, someone beat me ;)

---

### Post by cl333r on 2009-05-08
Thanks a lot! It's (finally) working!!

---

### Post by Arndt on 2009-05-08
> **tinivole said:**
> [http://www.opengroup.org/onlinepubs/009695399/basedefs/sys/stat.h.html](http://www.opengroup.org/onlinepubs/009695399/basedefs/sys/stat.h.html)
```

#include <sys/stat.h>
char *path = "/tmp";
/*
...
*/
struct stat st;
if(! lstat(path, &st))
{
    if(S_ISDIR(st.st_mode))
        printf("%s is a directory\n", path);
}
else
printf("Cannot stat %s\n", path);

```


But why 'lstat' and not 'stat'?

---

### Post by ibuclaw on 2009-05-08
> **Arndt said:**
> But why 'lstat' and not 'stat'?

To quote the open standard:
[QUOTE='[The Open Group Base Specifications Issue 6]("http://www.opengroup.org/onlinepubs/009695399/functions/lstat.html")']
The lstat() function shall be equivalent to stat(), except when path refers to a symbolic link. In that case lstat() shall return information about the link, while stat() shall return information about the file the link references.
[/QUOTE]

Regards
Iain

---

### Post by Arndt on 2009-05-09
> **tinivole said:**
> To quote the open standard:


Regards
Iain

Precisely. So why choose 'lstat' when you're not interested in links as such?

---

