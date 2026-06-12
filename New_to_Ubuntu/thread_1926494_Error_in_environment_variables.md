---
title: "Error in environment variables"
date: 2012-02-16
forum: New to Ubuntu
---

### Post by Zombir on 2012-02-16
Hi,
I started using Ubuntu few years ago but couldn't carry on with it for some reason. So its safe to consider me as a total noob still. 
Recently I gave my 64bit  laptop with Ubuntu 10.10 32bit version installed to a friend for his project. He returned me my laptop saying nothing and then when I start my terminal I get the error message:

```
bash: /usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games: No such file or directory
bash: /usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games:/home/pram/K426/dat/: No such file or directory
bash: /usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games:/home/pram/K426/sum/: No such file or directory

```Now I understand (please correct me if I'm wrong) that this is some meddling with environment variables but I cannot really see a way of correcting the error. 

Is this a wrong line added to a wrong file? Please help me to correct the error.

---

### Post by lechien73 on 2012-02-16
The first places I would check would be in .bashrc in your home folder, and /etc/bash.bashrc. The altered path could have been added there.

---

### Post by Zombir on 2012-02-16
No, sorry they were not there. I with my very little knowledge of shell commands tried:

```
cat ~/.bashrc | grep K426
cat /etc/bash.bashrc | grep K426

```
and came up with nothing. Anywhere else to look? Please :(

---

### Post by lechien73 on 2012-02-16
Ok, then try in /etc/environment :)

---

### Post by Zombir on 2012-02-17
Yes, it was there! Thank you. :) I erased the unwanted parts. Now what's remaining is:

```
 PATH="/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games"

```

Then I restarted the computer and, the error is still there!!!! 
What could I do? Please help.

---

### Post by lechien73 on 2012-02-17
Hmmmm...is the error exactly the same? If you open a terminal and type:

```
echo $PATH
```

Has the path changed?

The only other file I can think of, where this could have been changed, is .profile in your home directory.

---

### Post by Zombir on 2012-02-17
Error looks exactly the same. But the PATH variable has changed:

```
 bash: /usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games: No such file or directory
bash: /usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games:/home/pram/K426/dat/: No such file or directory
bash: /usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games:/home/pram/K426/sum/: No such file or directory

```and the PATH:

```
~$ echo $PATH
/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games

```And I noted that the path Ubuntu's claiming that is not there actually exists and there are few binaries in those folders. 

```
cat ~/.profile | grep K426

```returns nothing either. 

Please help :(

---

