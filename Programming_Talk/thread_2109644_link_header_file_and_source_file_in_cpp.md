---
title: "link header file and source file in cpp"
date: 2013-01-28
forum: Programming Talk
---

### Post by sanda199 on 2013-01-28
Hi everyone, I wrote one cpp source program in ubuntu and I saved it in one directory. I saved my header file in different directory. How can i link them back? For my program, I must put my header file and source file in different directory. so how can i solve it? Thanks millions.

---

### Post by dwhitney67 on 2013-01-28
Header files and source files are compiled, not linked.  Linking occurs at a different stage, which for simple projects, it often not apparent.

Anyhow, say you have a project with source code and header files in separate directories... a layout such as:
```

+ MyProject
    + include
        Header.h
    + src
        Main.cpp
    + bin

```
To build the executable into the 'bin' directory, a statement such as the following could be used from the 'MyProject' level:
```

g++ -Wall -pedantic -I./include src/Main.cpp -o bin/myproject 

```
Later, and presumably after you understand and get comfortable with the statement above, you can decide if you want to delve into Makefile development.  A Makefile will obviate the need to type the long g++ statement, and can make building larger projects a breeze.

---

### Post by r-senior on 2013-01-28
You can specify a directory to search for include files using the 'I' option. From the g++ manual page:

> -I dir
           Add the directory dir to the list of directories to be searched for
           header files.  Directories named by -I are searched before the
           standard system include directories.  If the directory dir is a
           standard system include directory, the option is ignored to ensure
           that the default search order for system directories and the
           special treatment of system headers are not defeated .  If dir
           begins with "=", then the "=" will be replaced by the sysroot
           prefix; see --sysroot and -isysroot.


---

### Post by sanda199 on 2013-01-29
> **dwhitney67 said:**
> Header files and source files are compiled, not linked.  Linking occurs at a different stage, which for simple projects, it often not apparent.

Anyhow, say you have a project with source code and header files in separate directories... a layout such as:
```

+ MyProject
    + include
        Header.h
    + src
        Main.cpp
    + bin

```To build the executable into the 'bin' directory, a statement such as the following could be used from the 'MyProject' level:
```

g++ -Wall -pedantic -I./include src/Main.cpp -o bin/myproject 

```Later, and presumably after you understand and get comfortable with the statement above, you can decide if you want to delve into Makefile development.  A Makefile will obviate the need to type the long g++ statement, and can make building larger projects a breeze.


Thanks a lot. I have solved :)

---

### Post by dwhitney67 on 2013-01-29
> **sanda199 said:**
> Thanks a lot. I have solved :)

You're welcome.  Please mark the thread as solved.

---

