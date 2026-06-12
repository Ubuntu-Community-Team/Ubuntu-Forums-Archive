---
title: "What am I doing wrong?"
date: 2015-04-26
forum: New to Ubuntu
---

### Post by huff2 on 2015-04-26
Hey guys!

I'm trying to learn how to navigate the file system. Can someone tell me why I cant cd /documents or desktop or any other folder in the following: 

brandon@brandon-NV57H:~$ ls

Desktop    Downloads  Pictures  PycharmProjects  Videos
Documents  Music      Public    Templates

brandon@brandon-NV57H:~$ cd /documents
bash: cd: /desktop: [COLOR=#ff0000]No such file or directory[/COLOR]

brandon@brandon-NV57H:~$ 

It says "no such file or directory" but it appears to exist. What am I doing wrong here?

---

### Post by steeldriver on 2015-04-26
Two things:

1. the leading / tells the system you are referring to a file or directory at the root of the filesystem (an **absolute **path) - if you want to refer to a file or directory in the current directory then just use a relative path, either with no prefix
```

cd Documents

```
or using a prefix that means "current directory"
```

cd ./Documents

```

2. unlike Windows, file and directory names are case sensitive so **Documents **exists but **documents **doesn't

---

### Post by huff2 on 2015-04-26
Thank you so much!

---

### Post by Mark Phelps on 2015-04-26
Also ... you need to pay attention to the Case of letters in Linux.  "Documents" is NOT the same as "documents".  So, if the directory is named "Documents", then "cd documents" is NOT going to work, but "cd Documents" will work.

---

### Post by flaymond on 2015-04-27
[QUOTE=Mark Phelps]Also ... you need to pay attention to the Case of letters in Linux.  "Documents" is NOT the same as "documents".  So, if the directory is named "Documents", then "cd documents" is NOT going to work, but "cd Documents" will work.[/QUOTE]

+1

Also, if you want to access a directory, that contain spaces in the directory name. Just put '\' when use cd command  to format it. Here an example -

```
 cd my\ file     # You cannot access with just 'cd my file', just use 'cd my\ file'

```

If you want to learn about Bash (a scripting/programming language(whatever you might call) that come as default shell for you Terminal. Here a good guide -

[www.linux-training.be/files/books/LinuxTraining.pdf](www.linux-training.be/files/books/LinuxTraining.pdf)

---

### Post by huff2 on 2015-04-27
Thanks for all your help, guys!

---

