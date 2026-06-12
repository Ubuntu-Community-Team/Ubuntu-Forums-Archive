---
title: "Makefile for  different machines"
date: 2009-08-19
forum: Programming Talk
---

### Post by flylehe on 2009-08-19
Hi, I have a C++ program that will run on several machines that use a Network File System. For each of the C++ libraries that my program uses, I installed a version for each machine, under ~/program_files/machinename/libraryname.

"machinename" is obtained via bash command "hostname". On the machines I am using, "hostname" outputs something like "io21.aaa.bbb.edu" and I take only "io21" as "machinename" for the path to the libraries. In bash, I learned that
```

    $ HOST=hostname # now the value of HOST is "io21.aaa.bbb.edu"
    $ HOST=${HOST%%.*} # extract "io21" from "io21.aaa.bbb.edu"
    $ echo ${HOST}
    io21

```

In the Makefile of my program, I want to call these bash commands to specify the path to the library according to the current machine:
```

    HOST := $(shell hostname)
    HOST := $(shell ${HOST%%.*})
    LDFLAGS=-L${HOME}/program_files/${HOST}/libraryname/lib
    CXXFLAGS=-Wall -I${HOME}/program_files/${HOST}/libraryname/include

```

The first line is working i.e. HOST is "io21.aaa.bbb.edu", but the second line which extracts "io21" doesn't work and HOST is still "io21.aaa.bbb.edu".

I am wondering how I should solve this problem?

Thanks and regards!

---

### Post by dwhitney67 on 2009-08-19
I know Makefile lingo somewhat well, but not the shell scripting.

I know the following statement will help you; just replace your second HOST statement with this:
```

HOST := `echo $(HOST) | cut -d '.' -f1`

```

---

### Post by jpkotta on 2009-08-20
According to the hostname manpage,
```
hostname --short
```

---

