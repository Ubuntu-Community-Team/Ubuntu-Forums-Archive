---
title: "Whiles, SSH and Bash"
date: 2010-02-18
forum: Programming Talk
---

### Post by crazycaveman on 2010-02-18
I'm trying to set up a script to update the passwd file nightly on a machine for NIS.  In order to do this, I have to get the details from a 2nd machine through SSH.  I have tried running the following command to no avail:
```
cat /tmp/users.lst | ssh user@server "while read username; do getent passwd $username >> /shared/folder/passwd.tmp; done"
```
and
```
ssh user@server "while read username; do getent passwd $username >> /shared/folder/passwd.tmp; done </shared/folder/users.lst"
```
However, it seems that the output of the cat command (nor the redirect) is not being piped over to the SSH session; the passwd.tmp file will be full of the "standard" users (root, ntp, etc.).  I have tried putting the users.lst file on the shared folder for the pipe and it still won't work.  Would anyone have some idea on how to do this?  I know I can run the while loop locally and just use ssh for the getent, but I'd like to reduce the overhead as much as possible; I ran it that way originally and it took too long for my tastes.  Thanks!

---

### Post by diesch on 2010-02-18
In
```
"while read username; do getent passwd $username >> /shared/folder/passwd.tmp; done"
```

the local shell replaces $username *before* the command is run. That is if in your local shell $username is 'foo' you are actually running

```
cat /tmp/users.lst | ssh user@server "while read username; do getent passwd foo >> /shared/folder/passwd.tmp; done"
```

Use '...' instead of "..."

---

### Post by crazycaveman on 2010-02-18
Thanks a lot, diesch; that did it!

---

