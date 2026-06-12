---
title: "bash script help needed"
date: 2009-10-18
forum: Programming Talk
---

### Post by ongbak on 2009-10-18
hi everyone im new to this forum i am currently studying network management course located in australia 
 
i have been given a task and a bunch of papers to write a simple script as its my first time i have no idea how to get it started as far as i got was
 
!#/bin/bash 
 
it has to be a bash script and according to my teacher it is quiet easy but not so easy for me
 
 
so what i need to do is copy thew files to a backup folder /home/backup
at the same time
 
files are etc/host /etc/group and so on
 
anyone can suggest any tips for me how to get this done would be highly appreciated

---

### Post by Dougie187 on 2009-10-18
I'm not quite sure what you are asking for your script to do. All I understand is you want to learn how to move/copy files from one place to another, and in that case, you might want to open a terminal and type ```
man cp
```

Either way though, this appears to be homework. And it is stated in the code of conduct that we can't help with homework problems. So basically you are on your own as far as code goes, unless someone doesn't care what they post, but either way, I think the best you can get here is just some general guidance. You're best bet is to talk to the teacher.

---

### Post by agnes on 2009-10-18
Well this is so simple and it's his first script so I'll give a short example.

for copying all files in directory /bla to another directory (omitting the directories within /etc : )

```
#!/bin/bash

targetdir=/home/yourname/yourdirectory

prevdir=/bla/

cp $prevdir* $targetdir
 
```

For further guidance just read a bash script tutorial.
Like [http://bash.cyberciti.biz/guide/Main_Page](http://bash.cyberciti.biz/guide/Main_Page)

---

### Post by ApEkV2 on 2009-10-18
Here. A really good book (if you are able to get it)
[http://www.borders.com/online/store/TitleDetail?sku=047025128X](http://www.borders.com/online/store/TitleDetail?sku=047025128X)

Some reference stuff.
[http://ss64.com/bash/](http://ss64.com/bash/)

Although the home page sounds offensive,
[http://www.die.net/](http://www.die.net/)

Happy reading.
[http://ubuntuforums.org/search.php?searchid=65468170](http://ubuntuforums.org/search.php?searchid=65468170)

---

### Post by ibuclaw on 2009-10-18
Hi, ongbak.

See here on the [rules on posting Homework assignments]("http://ubuntuforums.org/showthread.php?t=1006666") in this forum.

Regards
Iain

---

