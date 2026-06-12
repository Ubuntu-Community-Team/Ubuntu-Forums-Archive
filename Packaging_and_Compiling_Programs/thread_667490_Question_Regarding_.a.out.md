---
title: "Question Regarding ./a.out"
date: 2008-01-14
forum: Packaging and Compiling Programs
---

### Post by NuNn DaDdY on 2008-01-14
This is just a minor issue which I have experienced since I have been programming.  Whenever I create an executable file from a program say "cc -o hello hello.c" I receive the hello executable.  From here to run the program I have to type "./hello" to execute the file.  However, some people are able to run the executable by simple typing "hello".  What steps do I have to take so I too can just do this.

---

### Post by geraldm on 2008-01-14
linux gains some speed by working out of a cache.  Whenever a package creates or updates library files or even executables, the old cache remains until an updated cache is created. The update is accomplished:
```

sudo ldconfig

```
As for omitting the leading "./" for the executable, the directory in which the executable is located must be on the search path, otherwise it is necessary for the OS to find the executable.

Gerald

---

### Post by amingv on 2008-01-14
To run programs like that, the directory where the program is must be included in your PATH variable.
You can create a bin directory in your home folder, and I think the .bashrc script will automatically set it in PATH; if not, you can modify .bashrc to do so.
Still, I would not recommend using such a directory as your programming playground. Use it only if you need to have some useful program handy, because the more stuff is in your PATH, the more the system will have to search for an important file it needs to open. Also, if you create a bin directory in your home, it will only be available to you by default.

---

### Post by dwhitney67 on 2008-01-14
In plain english, add this to your ~/.bashrc file:

```
export PATH=./:$PATH
```

This will augment your PATH environment variable to search the current working directory, thus obviating the need to preface any filenames (that you want to execute) with the './'.

---

### Post by Joeb454 on 2008-01-14
**dwhitney67** described exactly what I did, I know how you feel, it's not much, but it's a real time saver when used with tab complete :D

---

### Post by vek on 2008-01-15
Just be aware that the reason the current folder is not in the search path is from the old days of multi-user-machines, where users would leave fake binaries in their home folders (like a fake "ps" or fake "ls" binary) in the hopes that an admin would execute those commands while snooping in their folders.  (The commands would have admin priveleges).

Of course, those security risks may not be a problem on your machine if its single user, and that you aint going to be executing commands in a root shell in a folder that 'the internet' or others on the network have access to...

---

