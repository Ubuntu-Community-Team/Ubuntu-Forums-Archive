---
title: "C++ Directory Delete Help"
date: 2007-05-07
forum: Programming Talk
---

### Post by bobbocanfly on 2007-05-07
I just started teaching myself C++. I already know PHP and C# so i know a bit of the basics.
Taking the advice of someone on here i am writing a file/directory deletion module to replace the rm command.

I have the file deletion working perfectly but cant get the directory deletion working properly. I can only delete empty folders and have no idea how to go about deleting all the files in a folder.....

The code i am using at the moment is...

```
int delDir(char* dirName)
{
if (rmdir(dirName))
{
cout << "Directory successfully deleted";
return 1;
}
else
{
perror("");
return 0;
}
}
```

Any suggestions?

---

### Post by LaRoza on 2007-05-07
This will delete a directory and its contents.

```

rm -rf 

```

---

### Post by bobbocanfly on 2007-05-07
> **LaRoza said:**
> This will delete a directory and its contents.

```

rm -rf 

```

I think you misunderstood me a bit. I am trying to write my own version of 'rm'  in C++, not find out how to delete a directory in the terminal.

---

### Post by amo-ej1 on 2007-05-08
Well lesson one is read the manpages ;-)

man 2 rmdir tells you:


```

NAME
       rmdir - delete a directory

SYNOPSIS
       #include <unistd.h>

       int rmdir(const char *pathname);

DESCRIPTION
       rmdir() deletes a directory, which must be empty.

```


Now suppose you are in a situation and you don't know how to handle it, how do you proceed ? Well you figure out how someone else does it. In this case you know that rm -rf already performs the behavior you want so you should examine rm -rf, first create a little test environment, next use strace to see which systemcalls rm -rf is using:

```

e@lape:~$ cd /tmp/
e@lape:/tmp$ mkdir k
e@lape:/tmp$ cd k
e@lape:/tmp/k$ touch a b c d e f g h i j k l m n o p q r s t 
e@lape:/tmp/k$ cd ..
e@lape:/tmp$ strace rm -rf k
execve("/bin/rm", ["rm", "-rf", "k"], [/* 31 vars */]) = 0

<SNIP>

unlink("k")                             = -1 EISDIR (Is a directory)
open(".", O_RDONLY|O_LARGEFILE)         = 3
lstat64("k", {st_mode=S_IFDIR|0755, st_size=528, ...}) = 0
chdir("k")                              = 0
lstat64(".", {st_mode=S_IFDIR|0755, st_size=528, ...}) = 0
open(".", O_RDONLY|O_NONBLOCK|O_LARGEFILE|O_DIRECTORY) = 4
fstat64(4, {st_mode=S_IFDIR|0755, st_size=528, ...}) = 0
fcntl64(4, F_SETFD, FD_CLOEXEC)         = 0
getdents64(4, /* 22 entries */, 4096)   = 528
unlink("a")                             = 0
unlink("b")                             = 0
unlink("c")                             = 0
unlink("d")                             = 0
unlink("e")                             = 0
unlink("f")                             = 0
unlink("g")                             = 0
unlink("h")                             = 0
unlink("i")                             = 0
unlink("j")                             = 0
unlink("k")                             = 0
unlink("l")                             = 0
unlink("m")                             = 0
unlink("n")                             = 0
unlink("o")                             = 0
unlink("p")                             = 0
unlink("q")                             = 0
unlink("r")                             = 0
unlink("s")                             = 0
unlink("t")                             = 0
getdents64(4, /* 0 entries */, 4096)    = 0
close(4)                                = 0
fchdir(3)                               = 0
rmdir("k")                              = 0
close(3)                                = 0
close(1)                                = 0
exit_group(0)                           = ?

```

So you can clearly see, first rm tries to sissue unlink() on the directory, but unlink returns isdir, next the directory is changed and all files within that directory are unlink()'ed. When that is done rmdir() is called to remove the directory (for unlink see man 2 unlink which basicy removes a file if it isn't a directory).

Now the only thing missing from this puzzle is how to read the files in the directory, for this man 3 readdir (which isn't a systemcall and therefore not shown in the strace) might be of interest ;)

---

### Post by jamescox84 on 2007-05-08
```

#include <cstdlib>
#include <string>

void rm(const std::string &path)
{
    std::string command = "rm -R \"";
    command += path + "\"";
    std::system(command.c_str());
}

int main()
{
    rm("directory");
    
    return 0;
}

```

Not a very elegant solution but a start, and it works!

---

### Post by amo-ej1 on 2007-05-10
I'd call it a quick 'n dirty fix ;-)

using system you won't be able to read the status of the delete, what if certain files have wrong permissions set and cannot be deleted ?

---

### Post by jamescox84 on 2007-05-10
Yeah, and also if the file name contains double quotes they maybe problems, seams they wont be escaped properly.

But you could use the return value from std::system, to check for success.

Hey, what am I trying to do here, your absolutely right! It was just plain dirty of me to suggest such a thing. I'm going now to wash my mouth out. :lolflag:

---

### Post by slavik on 2007-05-10
> **jamescox84 said:**
> ```

#include <cstdlib>
#include <string>

void rm(const std::string &path)
{
    std::string command = "rm -R \"";
    command += path + "\"";
    std::system(command.c_str());
}

int main()
{
    rm("directory");
    
    return 0;
}

```

Not a very elegant solution but a start, and it works!

using 'system' is HORRIBLE!!! When you are trying to replace something that has to operate without a shell, you cannot assume that there is a shell ... please refrain from using system at all ...

---

### Post by rbprogrammer on 2007-05-10
maybe i'm just a noob, but how would you execute a command like "rm" if you can't use system()??

---

### Post by jamescox84 on 2007-05-11
You can use.

```

#include <cstdio>

int main() 
{
    // The problem is remove, does not work recusivly
    std::remove("filename");
    return 0;
}

```

But like every one here said, I'm a very naughty, dirty boy for ever suggesting std::system().

---

