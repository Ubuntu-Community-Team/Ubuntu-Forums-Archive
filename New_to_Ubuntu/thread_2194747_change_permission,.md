---
title: "change permission,"
date: 2013-12-20
forum: New to Ubuntu
---

### Post by psyclone on 2013-12-20
I created a drive using;

mkdir -v /usr/local/somefolder

but the root owns it. I cant' add anything to it.

I used; 

e1-desktop@e1desktop-MS-7788:~$ sudo chmod a+rwx /usr/local/somefolder


but this doesn't do anything. Also the command line doesn't return anything when I type the above text in.

---

### Post by Iowan on 2013-12-20
What are the results of **ls -l /usr/local**?
[s](Did you try **sudo mkdir -v /usr/local/somefolder **?)[/s] You said you got it created...

---

### Post by psyclone on 2013-12-20
e1-desktop@e1desktop-MS-7788:~$ ls -l /usr/local
total 36
drwxr-xr-x  2 root root 4096 Nov 24 22:40 bin
drwxr-xr-x  2 root root 4096 Aug 21 03:56 etc
drwxr-xr-x  2 root root 4096 Aug 21 03:56 games
drwxr-xr-x  2 root root 4096 Nov 24 22:40 include
drwxr-xr-x  3 root root 4096 Nov 24 22:40 lib
lrwxrwxrwx  1 root root    9 Nov 13 10:45 man -> share/man
drwxrwxrwx  2 root root 4096 Dec 21 01:34 somefolder
drwxr-xr-x  2 root root 4096 Aug 21 03:56 sbin
drwxr-xr-x 12 root root 4096 Nov 24 22:38 share
drwxr-xr-x  2 root root 4096 Aug 21 03:56 src

I tried that same command  'ls -l' ,but it didn't work, I think I used it inside the somefolder dir.

---

### Post by psyclone on 2013-12-20
Also, yes I used  ' sudo [COLOR=#000000]mkdir -v /usr/local/somefolder ' to create the folder.[/COLOR]

---

### Post by psyclone on 2013-12-20
I also get this when I use chmod

e1-desktop@e1desktop-MS-7788:/usr/local$ chmod a+rwx somefolder
chmod: changing permissions of `somefolder': Operation not permitted

---

### Post by Bashing-om on 2013-12-20
psyclone; Hi !

Try this:
```

sudo chmod -R a+rwX somefolder

```
where your Present Working Directory is "/usr/local;
and note the "X" in "+rw[color=red]X[/color] as uppercase. All subdirectories will be marked rwx for user, group, and others. The big "X" will also not make files executable unless they were executable to begin with. There is no way to reproduce this using octal notation

See if this has the desired result and advise, please.

[INDENT][INDENT]ain't nothing but a thing[/INDENT][/INDENT]

---

### Post by psyclone on 2013-12-20
Yes. It worked! The folder is still belongs to root, but I can transfer files into that folder now. (I don't quite understand how that works, but anyway). 
Thanks.

---

### Post by Bashing-om on 2013-12-21
psyclone; Good deal .

As the directory location is within the "system" file hierarchy, might be best left as owned by root, if possible.
Else move it to your /home directory (??)

[INDENT][INDENT]what works, works
[/INDENT][/INDENT]

---

