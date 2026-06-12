---
title: "'alias' command is not working in shell script"
date: 2009-09-02
forum: Programming Talk
---

### Post by bilol on 2009-09-02
Hi all,
When I use alias command in command prompt,it is working,as shown below: 
```
dhiman@dhiman-desktop:~$ alias list='ls -l'
dhiman@dhiman-desktop:~$ list
total 116432
-rw-r--r-- 1 dhiman dhiman         0 2009-09-01 14:23 03161430
-rw-r--r-- 1 dhiman dhiman         0 2009-09-01 14:35 04111230
-rw-r--r-- 1 dhiman dhiman         0 2009-09-01 14:31 04121230
-rw-r--r-- 1 dhiman dhiman        14 2009-08-31 14:28 alphabet
-rwxr-xr-x 1 dhiman dhiman      6362 2009-09-01 15:26 a.out
-rw-r--r-- 1 dhiman dhiman 113422336 2009-08-31 16:53 aptoncd-20090831-CD1.iso
drwxr-xr-x 4 dhiman dhiman      4096 2009-08-26 14:06 code
```

But, when I am using it **within a shell script** it is not working, as shown below: 

```
dhiman@dhiman-desktop:~$ cat test
alias list='ls -l'
list
dhiman@dhiman-desktop:~$ bash test
test: line 2: list: command not found
```
Can Anybody explain the phenomenon...
Thanks in advance.

---

### Post by geirha on 2009-09-02
Aliases only work in interactive shells. You should use functions instead; they work both in interactive and non-interactive shells, and can also take arguments.

```

list() { ls -l; }
list

```

---

### Post by Arndt on 2009-09-02
> **bilol said:**
> Hi all,
When I use alias command in command prompt,it is working,as shown below: 
```
dhiman@dhiman-desktop:~$ alias list='ls -l'
dhiman@dhiman-desktop:~$ list
total 116432
-rw-r--r-- 1 dhiman dhiman         0 2009-09-01 14:23 03161430
-rw-r--r-- 1 dhiman dhiman         0 2009-09-01 14:35 04111230
-rw-r--r-- 1 dhiman dhiman         0 2009-09-01 14:31 04121230
-rw-r--r-- 1 dhiman dhiman        14 2009-08-31 14:28 alphabet
-rwxr-xr-x 1 dhiman dhiman      6362 2009-09-01 15:26 a.out
-rw-r--r-- 1 dhiman dhiman 113422336 2009-08-31 16:53 aptoncd-20090831-CD1.iso
drwxr-xr-x 4 dhiman dhiman      4096 2009-08-26 14:06 code
```

But, when I am using it **within a shell script** it is not working, as shown below: 

```
dhiman@dhiman-desktop:~$ cat test
alias list='ls -l'
list
dhiman@dhiman-desktop:~$ bash test
test: line 2: list: command not found
```
Can Anybody explain the phenomenon...
Thanks in advance.

Yes, the manual page can:

 >       Aliases are not expanded when the shell is not interactive, unless  the
       expand_aliases  shell option is set using shopt (see the description of
       shopt under SHELL BUILTIN COMMANDS below).

---

### Post by bilol on 2009-09-02
Thanks a lot.

---

