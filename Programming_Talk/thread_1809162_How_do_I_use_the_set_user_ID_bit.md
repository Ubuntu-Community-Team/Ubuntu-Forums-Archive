---
title: "How do I use the set user ID bit?"
date: 2011-07-21
forum: Programming Talk
---

### Post by wwwookie on 2011-07-21
Hi all,  I'm writing a python program that occasionally needs root privileges so I decided to have a look at the SUID bit with a small bash script. I'm not getting the results I want. Here's the script:-
```
#! /bin/bash

echo 'UID = '$UID
echo 'EUID = '$EUID

if touch /foo; then
    echo 'touched /foo'
    rm /foo
    echo 'removed /foo'
else
    echo 'failed to touch /foo'
fi
```When I run it as a normal user I get stopped from writing in the root partition as expected:-
```
$ ls -l
total 4
-rwxr-xr-x 1 wookie wookie 173 2011-07-21 12:10 ids.sh
$ ./ids.sh 
UID = 1000
EUID = 1000
touch: cannot touch `/foo': Permission denied
failed to touch /foo
```When I run it with sudo it works, again as expected:-
```
$ sudo ./ids.sh
UID = 0
EUID = 0
touched /foo
removed /foo
```Now if I make root own it and set the SUID bit, I was expecting to get privileges when I ran it as a normal user but to no avail:-
```
$ sudo chown root ids.sh 
$ sudo chmod u+s ids.sh 
$ ls -l
total 4
-rwsr-xr-x 1 root wookie 173 2011-07-21 12:10 ids.sh
$ ./ids.sh 
UID = 1000
EUID = 1000
touch: cannot touch `/foo': Permission denied
failed to touch /foo
```I tried the same with owner and group set to root, but still no joy

What am I doing wrong?:confused:

---

### Post by Bachstelze on 2011-07-21
The setuid bit does not work on scripts, as a security measure. There's no way around that, no need to ask.

---

### Post by wwwookie on 2011-07-21
Now That has saved me a bit of time! I originally ran into the problem with python though - do I take it what you said applies to python scripts too?

---

### Post by Bachstelze on 2011-07-21
Yes it applies to everything you run with a "shebang" line. Though of course the easy way around is to make a C program with a single system() call that runs your script (basically wha tsudo does), but there is no way to run the script directly.

---

### Post by wwwookie on 2011-07-21
Thanks a lot Bachstelze, that's probably the quickest response I've ever had - have a nice afternoon.

---

