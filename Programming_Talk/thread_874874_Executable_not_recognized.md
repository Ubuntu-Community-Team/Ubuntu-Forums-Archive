---
title: "Executable not recognized"
date: 2008-07-30
forum: Programming Talk
---

### Post by vessels42 on 2008-07-30
Hi all,

I recently updated a machine to Hardy and I am now having a problem running executables. When I view the contents of the folder in nautilus, it recognizes the .out files as executables, but in the terminal they don't show up in green, and when I type ./<filename> I get "permission denied." If I use sudo (which I never have had to on other machines), I get "command not found."

Any ideas?

Thanks in advance,
Vic

---

### Post by vessels42 on 2008-07-30
Ok, sorry to waste your time. I got it to work, but I am still puzzled.

I was copying the the .out files over the network and they were not recognized. When I copied them on a memory stick and transfered them that way they were recognized.

Is this a bug?

---

### Post by LaRoza on 2008-07-30
Mark them as executable.

```

chmod +x $FILENAME

```

---

### Post by dwhitney67 on 2008-07-30
Where these application compiled/linked on a system with a different compiler (and undoubtedly a different glibc) that your current system?

Also, verify that your executables are indeed runnable programs.  You will need to open a terminal to run this command:
```
$ /bin/ls -l a.out
-rwxrwxr-x 1 userid userid 5846 2008-07-30 10:42 a.out
```
Note the 'x' characters in the output above; these denote that the a.out file is executable for the owner, the group to which the owner belongs to, and for any other user on the system.  The 'r' and the 'w' denote read and write, respectively.  Only the user can read from, write to and delete the file.  All others can only read but not write/delete it.

P.S.  I would suggest that you recompile your applications.

---

### Post by vessels42 on 2008-07-30
LaRoza's suggestion seemed to fix the problem. I'm still confused about why it's necessary to mark it as executable if I copy it over the local network, but not if I copy it on a memory stick.

?

Anyway thanks for the help and thanks for this whole forum.

Vic

---

### Post by Mr.Macdonald on 2008-07-30
I am no expert but if you copy them on a memory stick then "you know that these executable are safe" but over a network who knows, it like downloading them from the internet. its probably just a safety issue

---

### Post by The Cog on 2008-07-30
More likely, the memory stick is FAT filesystem, and copying files off of FAT to a *nix filesystem normally sets the executable flag in the process. 

Copying across the network will set the file flags however the particular app feels like setting them. NFS, SCP, SFTP will probably carry the *nix flags across properly. I don't know about FTP and others.

---

