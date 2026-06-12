---
title: "[SOLVED] CLI - removing directory"
date: 2008-09-23
forum: New to Ubuntu
---

### Post by adamogardner on 2008-09-23
well only for the sake of experimenting and learning did I make a directory called 'workspace' and now I'm trying to rid myself of it (for the same reasons I made it, I have tried several approaches by the book as revealed in my history below.  Can someone offer some further insight into what is going on.  incidently when I open the worspace folder in Nautilus it is empty as it is supposed to be but being shown differently on the terminal.

adamogardner@CRONUS:~$ rm workspace
rm: cannot remove `workspace': Is a directory
adamogardner@CRONUS:~$ sudo rm -d workspace
sudo: unable to resolve host CRONUS
[sudo] password for adamogardner: 
rm: cannot remove `workspace': Is a directory
adamogardner@CRONUS:~$ ls

installed_software.txt                        Videos
[INSTALLERCACHE]                              workspace
isotostick.sh                                 xorg.bak
madwifi-ng-r2756+ar5007

adamogardner@CRONUS:~$ rmdir workspace
rmdir: failed to remove `workspace': Directory not empty.
adamogardner@CRONUS:~$ rmdir --ignore-fail-on-non-empty workspace 
adamogardner@CRONUS:~$ ls

installed_software.txt                        Videos
[INSTALLERCACHE]                              workspace
isotostick.sh                                 xorg.bak
madwifi-ng-r2756+ar5007

---

### Post by terry_gardener on 2008-09-23
you can always use the command "sudo rm -r workspace"

please be carefull with rm -r commands

run the above command in the directory where the workspace directory lies.

---

### Post by Mornedhel on 2008-09-23
rm -r directory.

For future reference, see 'man directory'.

---

### Post by DrOlaf on 2008-09-23
Can you remove it within Nautlius?

The directory may have some hidden files within it. You could try

```

cd directory
ls -a
rm .*

```

---

### Post by adamogardner on 2008-09-23
> **terry_gardener said:**
> you can always use the command "sudo rm -r workspace"

please be carefull with rm -r commands

run the above command in the directory where the workspace directory lies.

oh I see that option '--recursive' , but why didn't the others work?
-d means remove an empty directory.  it's empty i can't ls it, I don't see anything inside.  I want options from the dangerous letter -r.  What makes it dangerous- that it takes down whole families like the --parents (-P)option?  Why no use -P instead of -r and rmdir instead of rm, respectively?

---

### Post by adamogardner on 2008-09-23
> **DrOlaf said:**
> Can you remove it within Nautlius?

I'm sure that wouldn't pose a problem.  I'm just getting aquinted with CLI drills

---

### Post by hyper_ch on 2008-09-23
rmdir works only if the dir is empty.

use

```

ls -al

```
to list all the content of a dir... it might as well have hidden files.

---

### Post by adamogardner on 2008-09-23
> **hyper_ch said:**
> rmdir works only if the dir is empty.

use

```

ls -al

```
to list all the content of a dir... it might as well have hidden files.

NICE! look what I found:
adamogardner@CRONUS:~$ ls -al workspace
total 12
drwxr-xr-x  3 adamogardner adamogardner 4096 2008-08-17 19:48 .
drwxr-xr-x 88 adamogardner adamogardner 4096 2008-09-23 13:10 ..
drwxr-xr-x  3 adamogardner adamogardner 4096 2008-08-17 19:48 .metadata
adamogardner@CRONUS:~$ 

are these my missing photos?  why is it hidden here?  how can I find out or display this; cat drwr-xr-x....? or what?  I'm not in a hurry to delete, i'm mostly interested in screwing around, and would like to know how I got these hidden (what?).

---

### Post by hyper_ch on 2008-09-23
it's hidden because it starts witha period ".". The "d" says it's a directory... so go in it an look what's in there.

---

### Post by terry_gardener on 2008-09-23
for more information about file premissions check out the following link.

[https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions)

---

### Post by adamogardner on 2008-09-23
i see that the hidden materia starts with a 'd', but I see no '.' at all.  What is there a total of 12 of? I'm 9 short.

so drwxr-xr-x means directory followed by read/write/execute permissions?

---

### Post by hyper_ch on 2008-09-23
et voilà

> **adamogardner said:**
> drwxr-xr-x  3 adamogardner adamogardner 4096 2008-08-17 19:48 [size=6]**.**[/size]metadata


---

### Post by DrOlaf on 2008-09-23
> **adamogardner said:**
> i see that the hidden materia starts with a 'd', but I see no '.' at all.  What is there a total of 12 of? I'm 9 short.

so drwxr-xr-x means directory followed by read/write/execute permissions?

You have a directory in there called .metadata and so you just go into it by typing 

```
cd .metadata
```

and then you can see what's in there.

---

### Post by terry_gardener on 2008-09-23
the file premissions for the folder you have are follows. 
drwxr-xr-x

d = directory 
rwx = owner has read, write and execute permissions 
r-x = group has read and execute permissions 
r-x = other has read and execute permissions 

all the information on this is included in the link provide earlier 

also if a file or folder name starts with a full stop "." it is classed as a hidden file or folder. 

hope this helps

---

