---
title: "[SOLVED] awk and bash not getting along"
date: 2007-10-23
forum: Programming Talk
---

### Post by Westerberg on 2007-10-23
Trying to remove blank lines by piping standard output through awk
```
james@james-desktop:~$ echo "hello
> 
> 
> world" | awk '!/^$/'
bash: !/^$/: event not found
> 

```
results in the above error message.

Interestingly, applying the same command to a file succeeds:
```
james@james-desktop:~$ cat myfile 
hello


world
james@james-desktop:~$ awk '!/^$/' myfile 
hello
world

```
Why the error in first example?

---

### Post by Westerberg on 2007-10-23
Nevermind.  I found out at the command line '!' is bash's history character.  I have to set 
```
histchars=
```
in .bashrc to get it to work.

---

### Post by vijayanand_sodadasi on 2008-02-08
> **Westerberg said:**
> Nevermind.  I found out at the command line '!' is bash's history character.  I have to set 
```
histchars=
```
in .bashrc to get it to work.

Or you can escape the ! on the command line by \
example:
```
awk '\!/^$/' foo.txt
```

---

