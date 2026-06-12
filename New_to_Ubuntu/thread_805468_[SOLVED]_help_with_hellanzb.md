---
title: "[SOLVED] help with hellanzb"
date: 2008-05-24
forum: New to Ubuntu
---

### Post by lazydesi on 2008-05-24
Hi Linux gurus,

In order to d/l some info from news server ,I installed Hellanzb and it creates a folder in file system with name Media.

now i d/l the nzb (1234.nzb) on desktop, I tried to copy that file to daemon.queue and due to root problem, i am unable to copy that file.

I tried to copy that file using nautilus , but no sucess.

is their a way to copy the file from desktop to daemon.queue root folder???

i tried chown command to change the user access of hellanzb folder but no sucess

---

### Post by NT4usB on 2008-05-24
When I first installed hellanzb and configured it to run on startup it ran as root. Wouldn't let me do anything with it until I chmod -R and chown -R .../hellanzb/prfx/nzb/hellanzbState.xml
When I removed all the startup stuff and launch it manually, it works fine.

---

### Post by lazydesi on 2008-05-24
thanks for the reply, but still it was not allowing me to copy the file from desktop to folder

---

### Post by NT4usB on 2008-05-24
open a terminal and cd into the nzb folder
```
cd ... /hellanzb/prfx/nzb/
```
post the output of: ```
ls -al
```

---

### Post by lazydesi on 2008-05-24
drwxr-xr-x  2 user user    4096 2008-05-24 13:02 .hellanzb

---

### Post by NT4usB on 2008-05-25
That doesn't look like enough info. I was expecting to see:```
drwxrwxrw-  8 ct ct  4096 2008-05-24 23:36 .
drwxrwxrw-  4 ct ct  4096 2008-03-21 22:07 ..
drwxrwxr-x  2 ct ct  4096 2008-05-24 23:34 daemon.current
drwxr-xr-x  2 ct ct  4096 2008-05-22 07:51 daemon.postponed
drwxrwxr-x  2 ct ct  4096 2008-05-24 20:22 daemon.processing
drwxrwxr-x  2 ct ct 12288 2008-05-24 23:53 daemon.queue
drwxrwxr-x 13 ct ct  4096 2008-05-24 00:41 daemon.temp
drwxr-xr-x  2 ct ct  8192 2008-05-24 23:58 daemon.working
-rw-r--r--  1 ct ct   247 2008-05-24 23:36 hellanzbState.xml
-rw-r--r--  1 ct ct   190 2008-05-24 23:34 hellanzbState.xml.bak

```specifically, the xml file. It was that file, when root owned it, kept me from doing anything...

---

### Post by lazydesi on 2008-05-26
drwxr-xr-x 8 root root 4096 2008-05-24 14:42 .
drwxr-xr-x 4 root root 4096 2008-05-24 13:39 ..
drwxr-xr-x 2 root root 4096 2008-05-24 13:39 daemon.current
drwxr-xr-x 2 root root 4096 2008-05-24 13:39 daemon.postponed
drwxr-xr-x 2 root root 4096 2008-05-24 13:39 daemon.processing
drwxr-xr-x 2 root root 4096 2008-05-24 13:39 daemon.queue
drwxr-xr-x 4 root root 4096 2008-05-24 14:42 daemon.temp
drwxr-xr-x 2 root root 4096 2008-05-24 13:39 daemon.working
-rw-r--r-- 1 root root   55 2008-05-24 14:42 hellanzbState.xml
-rw-r--r-- 1 root root   55 2008-05-24 13:39 hellanzbState.xml.bak

i think the xml file is owned by root, can you clearly explain how to make changes in steps

thanks

---

### Post by NT4usB on 2008-05-26
There's the problem.
You can change it by (assuming your username is 'user'.)
cd into the directory.
```
cd .../hellanzb/prfx/nzb/
sudo chown -R user:user *
sudo chmod -R 777 *
```
Is hellanzb starting automatically at startup? If it is it will revert to root every time you restart your pc.

---

### Post by lazydesi on 2008-05-27
> **NT4usB said:**
> There's the problem.
You can change it by (assuming your username is 'user'.)
cd into the directory.
```
cd .../hellanzb/prfx/nzb/
sudo chown -R user:user *
sudo chmod -R 777 *
```
Is hellanzb starting automatically at startup? If it is it will revert to root every time you restart your pc.

thanks mate, now it works perfect,

Is hellanzb starting automatically at startup? 

I dont think so

---

### Post by NT4usB on 2008-05-27
Glad you got it going.
Another feature of hellanzb you might not be aware of, it will process a folder full of split files, zips, or RARs you have downloaded via other means. (with hellnzb running):```
 hellanzb.py process .../path/to/folder/
```will combine, extract, and clean up for all files it finds a par2 for in the folder.
Way easier than running par2verify, then unrar, then deleting manually.

---

### Post by NT4usB on 2008-05-27
Glad you got it going. Be sure to mark the thread solved using the thread tools above.
Another feature of hellanzb you might not be aware of. It will process a folder full of split files, zips, or RARs you have downloaded via other means. 
(with hellnzb running):```
 hellanzb.py process .../path/to/folder/
```will combine, extract, and clean up for all files it finds a par2 for in the folder.
Way easier than running par2verify, then unrar, then deleting manually.

---

