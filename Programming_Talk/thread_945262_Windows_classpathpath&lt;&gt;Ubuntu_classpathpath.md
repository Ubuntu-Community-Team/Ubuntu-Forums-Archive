---
title: "Windows classpath/path&lt;&gt;Ubuntu classpath/path"
date: 2008-10-12
forum: Programming Talk
---

### Post by hoboy on 2008-10-12
In windows you have the path notion where you put can put your xxx.exe to be excute, and you have classpath where you put xxx.jar for window to find, what/where is the corespondent to these files in ubuntu ?
in case I want to manually set a classpath, or a path to a file ?

---

### Post by dwhitney67 on 2008-10-12
The PATH environment variable provides information to the shell as to where to locate executable programs.  If you want to augment this variable, do so in your ~/.bashrc file.  For example:
```
export PATH=$PATH:/some/dir/path
```

For Java, the CLASSPATH environment variable is used.  It works similarly to the PATH variable; in other words, it is defined and set in the same manner.

P.S.  PATH and CLASSPATH do not necessarily have to be set in ~/.bashrc.  They can be temporarily set within a script.

---

### Post by hoboy on 2008-10-12
> **dwhitney67 said:**
> The PATH environment variable provides information to the shell as to where to locate executable programs.  If you want to augment this variable, do so in your ~/.bashrc file.  For example:
```
export PATH=$PATH:/some/dir/path
```

For Java, the CLASSPATH environment variable is used.  It works similarly to the PATH variable; in other words, it is defined and set in the same manner.

P.S.  PATH and CLASSPATH do not necessarily have to be set in ~/.bashrc.  They can be temporarily set within a script.

Where is located ~/.bashrc ? in ubuntu ?

---

### Post by dwhitney67 on 2008-10-12
> **hoboy said:**
> Where is located ~/.bashrc ? in ubuntu ?

The ~ character is short-hand notation (understood by the bash shell) for /home/userid, where userid is your particular userid.

Thus whenever you need to reference your home directory, while typing in a terminal, use the ~.

---

### Post by geirha on 2008-10-12
And putting a . infront of a filename or directoryname, will make it hidden in linux. To see hidden files in Nautilus, use Ctrl+H to toggle showing them, in the terminal you can pass the -a option to ls to show them. ```
ls -a ~
```

---

