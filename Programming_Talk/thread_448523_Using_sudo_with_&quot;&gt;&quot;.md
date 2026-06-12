---
title: "Using sudo with &quot;&gt;&quot;"
date: 2007-05-19
forum: Programming Talk
---

### Post by mikeym on 2007-05-19
Hi,

Could someone please tell me what's wrong with the following BASH command?

```

gksudo echo "$1" > /media/.cdimage

```

It won't give me permissions. I imagine it's because it's giving them to the echo but not the direct to file operator. Also I'm not happay about having a list of gksudo's in a row like I do in my script. Is there a way of doing one or checking the result of the first one?

Thanks,

Mikey

---

### Post by YoG%*@ on 2007-05-19
hi,

try running it in a sub-shell: 
```

sudo sh -c "echo \"$1\" > /media/.cdimage"

```

hth
mux

---

### Post by WW on 2007-05-19
Check out [this thread]("http://ubuntuforums.org/showthread.php?t=364904"); in particular, see "Edit 3" of my first post.

---

### Post by heimo on 2007-05-19
If it's a script with lots of things done as superuser, you could run the script itself with sudo and put everything inside without sudo. 

If script script.sh contains:
```
#!/bin/sh
echo "hello" >> file
echo "hello2" >> file
```

And it's then called with
```
sudo ./script.sh
```

Those echos will be run with superuser privileges.

---

### Post by Jucato on 2007-05-20
Another possible solution: [http://ubuntu.wordpress.com/2007/05/17/using-tee-to-write-to-files-and-the-terminal/](http://ubuntu.wordpress.com/2007/05/17/using-tee-to-write-to-files-and-the-terminal/)

---

### Post by RedSquirrel on 2007-05-20
This document in the wiki is worth a look (see "Downsides of using sudo"):

[RootSudo]("https://help.ubuntu.com/community/RootSudo#head-a1a6136e349bca8bd739ef01ebe7a02c65007bd6")

---

### Post by Ramses de Norre on 2007-05-20
You need to understand that ```
sudo echo test >> file
``` runs **echo test** as root, which is totally redundant, and then the shell interprets the **>>** and the shell is running as your current user, thus you wont have write privileges...
Running a whole new shell seems like a little overkill to me, you have the concept of sudo and you just need to use it properly, running the whole shell as sudo because you don't know better is possible but certainly not the best solution.
So the best solution in my eyes is using a program to write to the text file instead of the shell inbuilt, the unix program to do this is tee, read its man page;)
The command from above would become this: ```
echo test|sudo tee -a file
```

---

