---
title: "help me with this tar command"
date: 2011-01-19
forum: Programming Talk
---

### Post by tisungho on 2011-01-19
Hi,

I have a lot of BIG tarball files in a directory, say, a.tar.gz, b.tar.gz, c.tar.gz ... in /home/myuser/tarball directory
I want to untar ONLY the files with .c extention to /home/myuser/untar. I use this command:

```
find /home/myuser/tarball -type f -name *.tar.gz -exec tar -zxvf '{}' -C /home/myuser/untar *.c \;
```

The problem is that I get error when a tarball file doesn't contain any .c file.

Could you please help me work this out?

Thanks!

---

### Post by Arndt on 2011-01-19
> **tisungho said:**
> Hi,

I have a lot of BIG tarball files in a directory, say, a.tar.gz, b.tar.gz, c.tar.gz ... in /home/myuser/tarball directory
I want to untar ONLY the files with .c extention to /home/myuser/untar. I use this command:

```
find /home/myuser/tarball -type f -name *.tar.gz -exec tar -zxvf '{}' -C /home/myuser/untar *.c \;
```

The problem is that I get error when a tarball file doesn't contain any .c file.

Could you please help me work this out?

Thanks!

I suggest you list the files first and pick out the names ending in .c, then extract those.

Having "*.c" like you do isn't likely to do the right thing anyway, since it matches what is in your current directory.

---

### Post by psusi on 2011-01-19
The shell expands *.c to all .c files in the current directory, instead of passing '*.c' to tar.  You need to put single quotes around it to stop that.

---

