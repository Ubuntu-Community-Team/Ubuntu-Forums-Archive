---
title: "C++ Dirent.h - File traversal algorithm"
date: 2011-03-01
forum: Programming Talk
---

### Post by Sub101 on 2011-03-01
Hi all,

Im currently creating an algorithm for directory traversal. The algorithm runs a method if a file is found and moves into the directory if a directory is found.

```
  
if(entry->type == DT_DIR){
[INDENT]//Run method inside this directory
[/INDENT]}
if(entry->type == DT_REG){
[INDENT]// Do stuff on the file
[/INDENT]}


```

The problem, however, is that in some cases the entry->type is thought to be a file when it is a Directory. Has anyone come across this before, and does anyone have any solutions?

Thanks for your time.

---

### Post by Arndt on 2011-03-01
> **Sub101 said:**
> Hi all,

Im currently creating an algorithm for directory traversal. The algorithm runs a method if a file is found and moves into the directory if a directory is found.

```
  
if(entry->type == DT_DIR){
[INDENT]//Run method inside this directory
[/INDENT]}
if(entry->type == DT_REG){
[INDENT]// Do stuff on the file
[/INDENT]}


```

The problem, however, is that in some cases the entry->type is thought to be a file when it is a Directory. Has anyone come across this before, and does anyone have any solutions?

Thanks for your time.

I think more details are needed. Why not the whole program, reduced so that it still shows the error?

---

### Post by gmargo on 2011-03-01
Oops.  More details needed.  Could you be changing the type?

---

### Post by FoxEWolf on 2011-03-01
> **gmargo said:**
> Oops.  More details needed.

Seconded!

---

### Post by t1497f35 on 2011-03-01
I strongly suggest you **stop using dirent.d_type** for checking the type of the file.
I just made this mistake in my app and had to rewrite it to use [stat]("http://www.gnu.org/s/libc/manual/html_node/Reading-Attributes.html#Reading-Attributes") instead.
That's because i.e. on XFS dirent.d_type is not supported because dirent **only** guarantees that the filename (d_name) always be present.

> 
char d_name[]
This is the null-terminated file name component.  This is the only field you can count on in all POSIX systems.            Source:
[http://www.gnu.org/s/libc/manual/html_node/Directory-Entries.html#Directory-Entries](http://www.gnu.org/s/libc/manual/html_node/Directory-Entries.html#Directory-Entries)

Researching this I found bugs on launchpad about apps because they've been relying on dirent.d_type and the solution was to switch over to stat.

PS: since you're using dirent/stat (and if file size etc matters to your algorithm) don't forget about the [LFS]("http://en.wikipedia.org/wiki/Large_file_support") issue, which in glib's gio and other higher level APIs is taken care of automatically.

---

### Post by johnl on 2011-03-01
> **t1497f35 said:**
> I strongly suggest you **stop using dirent.d_type** for checking the type of the file.
I just made this mistake in my app and had to rewrite it to use [stat]("http://www.gnu.org/s/libc/manual/html_node/Reading-Attributes.html#Reading-Attributes") instead.
That's because i.e. on XFS dirent.d_type is not supported because dirent **only** guarantees that the filename (d_name) always be present.

Source:
[http://www.gnu.org/s/libc/manual/html_node/Directory-Entries.html#Directory-Entries](http://www.gnu.org/s/libc/manual/html_node/Directory-Entries.html#Directory-Entries)

Researching this I found bugs on launchpad about apps because they've been relying on dirent.d_type and the solution was to switch over to stat.

I think this is good advice,  use dirent to determine the filename, and then do a **stat** or **lstat** on the file.  Something like this (in C, in C++ you could use a std::stringstream or std::string instead of namebuf/snprintf/etc):

```

#include <stdio.h>
#include <stdlib.h>
#include <sys/types.h>
#include <sys/stat.h>
#include <dirent.h>
#include <unistd.h>
#include <string.h>
#include <limits.h>

static void list_dir(const char* base_dir) 
{
    DIR* dir;
    struct dirent* ent;
    struct stat buf;
    
    char namebuf[PATH_MAX];
    size_t base_len = strlen(base_dir);
    
    if (!(dir = opendir(base_dir))) {
        perror("failed to open directory");
        return;
    }
    
    while((ent = readdir(dir)) != NULL) {
        /* ignore .. and . */
        if (!strcmp(ent->d_name, "..") || !strcmp(ent->d_name, ".")) {
            continue;
        }
        
        snprintf(namebuf, sizeof(namebuf), "%s%s%s",
                 base_dir,
                 (base_dir[base_len - 1] == '/' ? "" : "/"),
                 ent->d_name);

        if (lstat(namebuf, &buf) != 0) {
            perror(namebuf);
            continue;
        }

        if (S_ISREG(buf.st_mode)) {
            printf("FILE: %s\n", namebuf);
        } else if (S_ISLNK(buf.st_mode)) {
            printf("LINK: %s\n", namebuf);
        } else if (S_ISDIR(buf.st_mode)) {
            printf("DIR:  %s\n", namebuf);
            /* recurse, if desired */
            /* list_dir(namebuf);  */
        }
    }

    closedir(dir);
}

```

---

### Post by Sub101 on 2011-03-03
Thanks for your help all. Ill use stat as suggested.

---

