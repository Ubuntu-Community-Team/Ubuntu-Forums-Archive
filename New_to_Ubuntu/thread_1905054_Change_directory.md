---
title: "Change directory"
date: 2012-01-05
forum: New to Ubuntu
---

### Post by F.R Mostert on 2012-01-05
Hi I am not able to change directory more that one level see below - I know it is my fault but I just do not know how to do it.  Please help and explain the process.
reimerd@reimerd-Dell-System-XPS-L502X:~$ cd/home/reimerd/cinepaint/ 
bash: cd/home/reimerd/cinepaint/: No such file or directory
reimerd@reimerd-Dell-System-XPS-L502X:~$ cd home
bash: cd: home: No such file or directory
reimerd@reimerd-Dell-System-XPS-L502X:~$ cd/ home
bash: cd/: No such file or directory
reimerd@reimerd-Dell-System-XPS-L502X:~$ cd reimerd
bash: cd: reimerd: No such file or directory
reimerd@reimerd-Dell-System-XPS-L502X:~$ cd home
bash: cd: home: No such file or directory
reimerd@reimerd-Dell-System-XPS-L502X:~$ cd /home
reimerd@reimerd-Dell-System-XPS-L502X:/home$ cd /reimerd
bash: cd: /reimerd: No such file or directory
reimerd@reimerd-Dell-System-XPS-L502X:/home$ cd reimerd
reimerd@reimerd-Dell-System-XPS-L502X:~$ cd /home
reimerd@reimerd-Dell-System-XPS-L502X:/home$ cd /reimerd
bash: cd: /reimerd: No such file or directory
reimerd@reimerd-Dell-System-XPS-L502X:/home$ cd reimerd
reimerd@reimerd-Dell-System-XPS-L502X:~$ cd /home
reimerd@reimerd-Dell-System-XPS-L502X:/home$ cd /reimerd
bash: cd: /reimerd: No such file or directory
reimerd@reimerd-Dell-System-XPS-L502X:/home$ ls
reimerd
reimerd@reimerd-Dell-System-XPS-L502X:/home$ cd/reimerd
bash: cd/reimerd: No such file or directory
reimerd@reimerd-Dell-System-XPS-L502X:/home$ cd / reimerd
reimerd@reimerd-Dell-System-XPS-L502X:/$ cd /home
reimerd@reimerd-Dell-System-XPS-L502X:/home$ ls
reimerd
reimerd@reimerd-Dell-System-XPS-L502X:/home$ cd/reimerd
bash: cd/reimerd: No such file or directory
reimerd@reimerd-Dell-System-XPS-L502X:/home$ cd /home/reimerd
reimerd@reimerd-Dell-System-XPS-L502X:~$ cd /reimerd
bash: cd: /reimerd: No such file or directory
reimerd@reimerd-Dell-System-XPS-L502X:~$ cd /home
reimerd@reimerd-Dell-System-XPS-L502X:/home$ /reimerd
bash: /reimerd: No such file or directory
reimerd@reimerd-Dell-System-XPS-L502X:/home$ / reimerd
bash: /: Is a directory
reimerd@reimerd-Dell-System-XPS-L502X:/home$ cd/ reimerd
bash: cd/: No such file or directory
reimerd@reimerd-Dell-System-XPS-L502X:/home$ cd\reimerd
cdreimerd: command not found
reimerd@reimerd-Dell-System-XPS-L502X:/home$ cd home/reimerd
bash: cd: home/reimerd: No such file or directory
reimerd@reimerd-Dell-System-XPS-L502X:/home$ cd /reimerd
bash: cd: /reimerd: No such file or directory
reimerd@reimerd-Dell-System-XPS-L502X:/home$ ls

Regards

Reimerd:oops::redface:

---

### Post by jtarin on 2012-01-05
When your terminal starts it is already in the /home/reimerd directory, as noted by the shell prompt.......thus the command as you have it```
cd/home/reimerd/cinepaint/ 
```should be entered as ```
cd cinepaint/ 
```

---

### Post by papibe on 2012-01-05
Hi F.R Mostert

Take a look at these tutorials:
- [Moving around in the Linux file system]("http://www.tuxfiles.org/linuxhelp/linuxfiles.html").
- [How to Use The Command Line]("http://www.linfo.org/command_line_lesson_1.html").

Basically, you need a space between the command 'cd' and its parameter (the directory you want to go). For example:

Instead of this:
```
cd/home/reimerd/cinepaint/
```
Try this:
```
cd /home/reimerd/cinepaint/
```
Hope it helps,
Regards.

---

### Post by wildmanne39 on 2012-01-05
Hi, the first command should look like this, it needs a space between the cd and /.
```
cd /home/reimerd/cinepaint/ 
```
Thanks

---

### Post by F.R Mostert on 2012-01-06
Thanks to all for the help.

Reimerd

---

### Post by jtarin on 2012-01-06
> **F.R Mostert said:**
> Thanks to all for the help.

ReimerdAnd your solution was?

---

### Post by wildmanne39 on 2012-01-06
Hi, your welcome!

---

