---
title: "Read-only filesystem"
date: 2012-11-11
forum: New to Ubuntu
---

### Post by NazirahRahman on 2012-11-11
HI.

I'm using Ubuntu 11.1 and I'm trying to edit the filesystem to fix the sound but I can't save it as it's read-only. It says that I'm not the owner so I don't have the permission to change the settings. I'm guessing because I'm not the one who created those files so I can't change them :confused:. HOW DO I REMOVE THE READ-ONLY FROM THE FILESYSTEM? PLEASE HELP :( THANK YOU IN ADVANCED.

---

### Post by zombifier25 on 2012-11-11
What are you trying to do specifically?

---

### Post by pqwoerituytrueiwoq on 2012-11-11
[s]11.10 is EOL[/s] - misread table [https://wiki.ubuntu.com/Releases](https://wiki.ubuntu.com/Releases)
what file are you trying to edit?
what kind of sound problem are you having

---

### Post by zombifier25 on 2012-11-11
> **pqwoerituytrueiwoq said:**
> 11.10 is EOL

Just for clarification, no it's not. It still has 6 months.

---

### Post by pqwoerituytrueiwoq on 2012-11-11
> **zombifier25 said:**
> Just for clarification, no it's not. It still has 6 months.
opps edited last post accordantly, clearly need to clean my glasses, and maybe some sleep/food

---

### Post by Wim Sturkenboom on 2012-11-11
The files that you're trying to edit are more than likely owned by root, so you need to become root to edit/save them. It's, by the way, not a read-only file system; unless something is wrong. In a terminal, use
```

sudo vi file-to-edit

```
If you don't know vi, replace _vi_ it with one that you know (like _nano_). Or if you prefer a GUI based editor
```

gksudo gedit file-to-edit

```

---

### Post by newb85 on 2012-11-11
[s]Yes, I know this might be quibbling, but when you use sudo or gksudo, you are temporarily acquiring superuser privileges, but you are not becoming root.  If you became root, then the path shorthand "~" would no longer work, as your home directory would no longer be *your* home directory.[/s]

Edit: Conceded to be incorrect.  See Wim's posts below.  More conclusively, this from the sudo manpage:
```
...
       -u user     The -u (user) option causes sudo to run the specified
                   command as a user other than root.  ...
```

---

### Post by Wim Sturkenboom on 2012-11-11
> 
Yes, I know this might be quibbling, but when you use sudo or gksudo, you are temporarily acquiring superuser privileges, but you are not becoming root.


```

wim@i3-2120:~$ ls -l
total 120
drwxrwxr-x 2 wim wim 4096 Nov  4 11:03 1_emailbackup
drwxrwxr-x 2 wim wim 4096 Oct 14 17:50 conky
...
...
wim@i3-2120:~$ sudo vi abc.txt
[sudo] password for wim: 
wim@i3-2120:~$ ls -l
total 124
drwxrwxr-x 2 wim  wim  4096 Nov  4 11:03 1_emailbackup
[COLOR="Red"]-rw-r--r-- 1 root root    4 Nov 11 16:37 abc.txt[/COLOR]
drwxrwxr-x 2 wim  wim  4096 Oct 14 17:50 conky
...
...

```
[Q.E.D.](http://en.wikipedia.org/wiki/Q.E.D.) ;)

> 
If you became root, then the path shorthand "~" would no longer work, as your home directory would no longer be your home directory. 

The difference, to my knowledge is like the difference between _su_ and _su -_. The former keeps the environment of the user that issued su while the latter uses the environment of the new user.

---

### Post by bogan on 2012-11-11
Hi!,** newb85** & [B]Wim Sturkenboom,
[/B] 
Showing my ignorance, when I use 'sudo', I DO GET TO BE ROOT:```
alan@alan-MS-7616:~$ ls -l
total 80
drwxr-xr-x 2 alan alan  4096 Oct 18 22:06 Desktop
drwxr-xr-x 2 alan alan  4096 Nov  1 22:32 Documents
drwxr-xr-x 3 alan alan  4096 Oct 29 16:26 Downloads
-rw-r--r-- 1 alan alan  8445 Oct 18 21:58 examples.desktop
......
7 more lines:
......
alan@alan-MS-7616:~$ sudo -i
[sudo] password for alan: 
root@alan-MS-7616:~# ls -l
total 4
drwxr-xr-x 2 root root 4096 Oct 28 20:44 Desktop
xxx no more lines xxx
root@alan-MS-7616:~# exit
logout
alan@alan-MS-7616:~$ 

```How about that ??

And why are my permissions different from yours ?

Chao!, **bogan**.

---

### Post by Wim Sturkenboom on 2012-11-11
We're going way off topic

_sudo -i_ makes you root (it has nearly the same environment as _sudo su -_ would give you), just like _sudo somecommand_, nothing special about that (and exactly what I indicated for sudo). To make it clear, I was proving newb85's statement to be incorrect.

I'm using 12.04; maybe default umask has changed from 12.04 to 12.10 and hence the difference in permissions.

---

### Post by newb85 on 2012-11-12
The most conclusive argument against my earlier (incorrect) statement would be
```
sudo whoami
```
:)

---

