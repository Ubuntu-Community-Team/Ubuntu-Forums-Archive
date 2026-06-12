---
title: "directories syntax?"
date: 2008-07-17
forum: New to Ubuntu
---

### Post by ra2008 on 2008-07-17
Hi.

some directories have "~/"
whats is "~"????

---

### Post by hyper_ch on 2008-07-17
~ represents the home directory of the current user

---

### Post by iaculallad on 2008-07-17
> **ra2008 said:**
> Hi.

some directories have "~/"
whats is "~"????

It means HOME directory.

EDIT: Got beaten on speed..

---

### Post by ra2008 on 2008-07-17
lol

---

### Post by Nameless_one on 2008-07-17
On the filesystem, ~ stands for /home/<username>, where <username> is your username, obviously.

---

### Post by hyper_ch on 2008-07-17
> **Nameless_one said:**
> On the filesystem, ~ stands for /home/<username>, where <username> is your username, obviously.

not necessarily... if you are logged in as root then ~ stand for /root ;) and also you can use a user's home to some other place ;)

---

### Post by ra2008 on 2008-07-17
then y when i type :

```
root@ra2008:~# ls 
``` the output is :
Desktop

and when i type 
```
ra2008@ra2008:~$ ls
```
i see all my home directory contents; Documents, music, etc......

---

### Post by hyper_ch on 2008-07-17
seems you have different bash.rc files.

---

### Post by ra2008 on 2008-07-17
what is bach.rc files?
how can i make "ls" command in both situations show the same?
thanks

---

### Post by Bachstelze on 2008-07-17
> **ra2008 said:**
> then y when i type :

```
root@ra2008:~# ls 
``` the output is :
Desktop

Because you are in root's home directory, which contains but the Desktop folder.

> **ra2008 said:**
> and when i type 
```
ra2008@ra2008:~$ ls
```
i see all my home directory contents; Documents, music, etc......

Because this is *your* home folder, which contains other stuff besides Desktop.

---

### Post by t0p on 2008-07-17
> **ra2008 said:**
> 
how can i make "ls" command in both situations show the same?
thanks

You can't.  When you are root, in root's home directory, the "ls" command shows you the contents of root's home directory (which ain't much!)  When you are your usual user name, "ls" shows you your own home directory.

If you want to see your own home directory while logged into root, you'll have to navigate there:

```
cd /home/username
ls

```

---

### Post by Vivaldi Gloria on 2008-07-17
The command pwd shows the name of the current directory.

```
root@narval:~# pwd
/root

vivaldi@narval:~$ pwd
/home/vivaldi
```

So for root, ~ is /root, but for vivaldi, ~ is /home/vivaldi.

---

