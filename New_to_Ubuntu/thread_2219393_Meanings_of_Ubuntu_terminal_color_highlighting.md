---
title: "Meanings of Ubuntu terminal color highlighting?"
date: 2014-04-23
forum: New to Ubuntu
---

### Post by azure2 on 2014-04-23
Hi!, I'm AZURE2. Im linux noob :D I started learning linux yesterday.
I tried some basic linux shell commands in my terminal window.

Eg:- "ls" command to list all files and directories in current working directory.

I saw those files and directories are highlighted in multiple colors. but I dunno whats that mean.
can somebody explain whats that mean? 

here is a screenshot of my terminal window.
[IMG]http://2.bp.blogspot.com/-Jy8hNTA8xaA/U1hnTD2TDCI/AAAAAAAAAL4/1TGkNszVMUg/s1600/Ubuntu-13.png[/IMG]

---

### Post by sudodus on 2014-04-24
Welcome to the Ubuntu Forums :-)

The color coding is there to help you tell different properties of files and directories apart. If you make a long list with the command

```
ls -l  #ell ess space minus ell
```

it will be easier to see the meaning of the colour codes. Blue is for directories, cyan is for symbolic links, green is for executable files (programs and shell scripts), red is for compressed files, magenta is for picture files ...

For more details, see this link or browse the internet for ***file colour codes in bash***

[http://ubuntuforums.org/showthread.php?t=1651117&p=10269563#post10269563](http://ubuntuforums.org/showthread.php?t=1651117&p=10269563#post10269563)

---

