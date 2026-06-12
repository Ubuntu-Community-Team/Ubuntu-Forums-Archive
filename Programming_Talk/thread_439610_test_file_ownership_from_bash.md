---
title: "test file ownership from bash?"
date: 2007-05-10
forum: Programming Talk
---

### Post by jmc1024 on 2007-05-10
I need to test file ownership and the group from bash.  I haven't figured out a 
straight forward way to do this.  Can anyone suggest something before I start 
working on something using ls and sed?
Thanks,
Mark

---

### Post by finer recliner on 2007-05-10
use the comand:
```

ls -l

```

this will display file permissions, owner and group information for all files in a directory.

(or i did misinterpret your question?)

---

### Post by psusi on 2007-05-10
The test command, which can be abbreviated as [, can test the mode bits of a file.  It has options to see if it is a normal file, or a symlink, or if you can write to it, and so on.  Do you just want to see if you have access to it, or who actually owns it?

---

### Post by s1ightcrazed on 2007-05-10
> **jmc1024 said:**
> I need to test file ownership and the group from bash.  I haven't figured out a 
straight forward way to do this.  Can anyone suggest something before I start 
working on something using ls and sed?
Thanks,
Mark

if you're looking for a way to pull the group info on a file (or list of files) then I would suggest using awk instead of sed. 

ls -l filename | awk '{ print $3 }'               <-- will give you the owner
ls -l filename | awk '{ print $4 }'               <-- will give you the group

there are other ways to do this, but this should get you started.

---

### Post by jmc1024 on 2007-05-11
Yea, ls -l will display them, but then I've got to use sed to pull out the group and
owner columns before I can test against a string.  I was hoping someone knew 
of a command and/or flag that would save me using sed to slice and dice ls -l's
output.
Many Thanks,
Mark

---

### Post by amo-ej1 on 2007-05-11
See man 1 stat:

```

edb@lapedb:~$ stat -c %U test.c
edb

```

You can use the format string to get these informations from the file:

```

The valid format sequences for files (without --file-system):

  %a   Access rights in octal
  %A   Access rights in human readable form
  %b   Number of blocks allocated (see %B)
  %B   The size in bytes of each block reported by %b
  %d   Device number in decimal
  %D   Device number in hex
  %f   Raw mode in hex
  %F   File type
  %g   Group ID of owner
  %G   Group name of owner
  %h   Number of hard links
  %i   Inode number
  %n   File name
  %N   Quoted file name with dereference if symbolic link
  %o   I/O block size
  %s   Total size, in bytes
  %t   Major device type in hex
  %T   Minor device type in hex
  %u   User ID of owner
  %U   User name of owner
  %x   Time of last access
  %X   Time of last access as seconds since Epoch
  %y   Time of last modification
  %Y   Time of last modification as seconds since Epoch
  %z   Time of last change
  %Z   Time of last change as seconds since Epoch

Valid format sequences for file systems:

  %a   Free blocks available to non-superuser
  %b   Total data blocks in file system
  %c   Total file nodes in file system
  %d   Free file nodes in file system
  %f   Free blocks in file system
  %C - Security context in SELinux
  %i   File System ID in hex
  %l   Maximum length of filenames
  %n   File name
  %s   Block size (for faster transfers)
  %S   Fundamental block size (for block counts)
  %t   Type in hex
  %T   Type in human readable form


```

---

### Post by jmc1024 on 2007-05-11
Perfect!  stat -c %U is exactly what I was looking for.
Many Thanks,
Mark

---

