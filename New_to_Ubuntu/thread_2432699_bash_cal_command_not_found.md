---
title: "bash: cal: command not found"
date: 2019-12-06
forum: New to Ubuntu
---

### Post by jackprogrammer on 2019-12-06
My ubuntu is installed in docker,and i use mac.Many commands are not found.The most i have installed,
but the cal command i can't install,and anybody help me?As below is the command used to install cal,sitll can't work.

123456:/# apt-get install cal
Reading package lists... Done
Building dependency tree
Reading state information... Done
E: Unable to locate package cal

---

### Post by deadflowr on 2019-12-06
cal isn't it's own package thus why it doesn't have an install option of it's own,
it should be part of the bsdmainutils package.

---

### Post by jackprogrammer on 2019-12-06
Thank you very much:guitar:
I have installed the command cal.
One more question i want to ask you,how can i check the command from which package just by myself?

---

### Post by deadflowr on 2019-12-07
Pre-install use apt-file search (apt-file may need to be installed)
See [https://unix.stackexchange.com/questions/191977/how-can-i-find-the-package-that-contains-a-program-in-debian]("https://unix.stackexchange.com/questions/191977/how-can-i-find-the-package-that-contains-a-program-in-debian")

Post-install when the file exists on the system use dpkg-query
(It also helps to use th which command to get the full file name like
```
which <command-name>
dpkg-query -S <output-from-which>
```


Example
```
which ls
```
will output
```
/bin/ls
```
```
dpkg-query -S /bin/ls
``` will output
```
coreutils: /bin/ls
```
coreutils is the package it belongs to.

---

### Post by kevdog on 2019-12-07
@deadflowr

Nice explanation

---

### Post by jackprogrammer on 2019-12-07
Thanks for your help! 

I have had a try,i can find the package now.

It's a great answer!

Have a nice day.:KS:popcorn:

---

### Post by The Cog on 2019-12-07
You can compress that into one line like this:
```
dpkg-query -S $(which cal)
```
although oddly, my answer for **which ls** is different to  deadflowr's:
```
$ dpkg-query -S $(which ls)
dpkg-query: no path found matching pattern /usr/bin/ls
```

---

