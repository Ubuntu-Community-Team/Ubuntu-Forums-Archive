---
title: "What does cp -u ?"
date: 2012-12-01
forum: New to Ubuntu
---

### Post by honeybear on 2012-12-01
Hi,

To me it is not clear the man page of cp. 

```
       -u, --update
              copy only when the SOURCE file is newer than the destination file or when the desti-
              nation file is missing

```

Does cp check the date/time or does cp does check using sort of md5sum... still a mystery? 

what about directories? 

```
cp -u -r Dir  /target
```

will if check all files in there into Dir and look at /target? 

any ideas?

---

### Post by zombifier25 on 2012-12-01
The -u flag checks that if
1. The destination file already exists, and
2. The destination file's modification date is newer than the source file
then the source file will not be copied. If used on directories, then cp will check for all files in the directory.

If you want to view the modification date of a file, use
```
ls -l
```
The command for manualy changing the modification date is 'touch', in case you want to test the functionality yourself.

---

### Post by honeybear on 2012-12-01
> **zombifier25 said:**
> The -u flag checks that if
1. The destination file already exists, and
2. The destination file's modification date is newer than the source file
then the source file will not be copied. If used on directories, then cp will check for all files in the directory.

If you want to view the modification date of a file, use
```
ls -l
```
The command for manualy changing the modification date is 'touch', in case you want to test the functionality yourself.

I was wondering if date of modif is same but size in bytes differs... whether cp would over-write

---

### Post by audiomick on 2012-12-01
You can find out about the options of a command using the man page. Type

```
man <command name>
```

in the terminal.

In this case,

```
man cp
```

---

### Post by Wim Sturkenboom on 2012-12-01
> **honeybear said:**
> I was wondering if date of modif is same but size in bytes differs... whether cp would over-write

You can easily test it yourself.

In below example I have two files (somefile and anotherfile) with different sizes.

Step 1: give them the same timestamps using the _touch_ command
```

wim@i3-2120:~/testje$ touch somefile anotherfile

```

Step 2: check that the timestaps are the same using the _stat_ command
```

wim@i3-2120:~/testje$ stat somefile
  File: `somefile'
  Size: 9               Blocks: 8          IO Block: 4096   regular file
Device: 806h/2054d      Inode: 9306726     Links: 1
Access: (0664/-rw-rw-r--)  Uid: ( 1000/     wim)   Gid: ( 1000/     wim)
Access: 2012-12-01 17:45:59.332076817 +0200
Modify: 2012-12-01 17:45:59.332076817 +0200
Change: 2012-12-01 17:45:59.332076817 +0200
 Birth: -
wim@i3-2120:~/testje$ stat anotherfile
  File: `anotherfile'
  Size: 12              Blocks: 8          IO Block: 4096   regular file
Device: 806h/2054d      Inode: 9306727     Links: 1
Access: (0664/-rw-rw-r--)  Uid: ( 1000/     wim)   Gid: ( 1000/     wim)
Access: 2012-12-01 17:45:59.332076817 +0200
Modify: 2012-12-01 17:45:59.332076817 +0200
Change: 2012-12-01 17:45:59.332076817 +0200
 Birth: -

```
Step 3: do the copy
```

wim@i3-2120:~/testje$ cp -u somefile anotherfile

```
Check the result of the copy operation; I'm using the _stat_ command again, you can also check with an appropriate utility (e.g. text editor for text files).
```

wim@i3-2120:~/testje$ stat somefile
  File: `somefile'
  Size: 9               Blocks: 8          IO Block: 4096   regular file
Device: 806h/2054d      Inode: 9306726     Links: 1
Access: (0664/-rw-rw-r--)  Uid: ( 1000/     wim)   Gid: ( 1000/     wim)
Access: 2012-12-01 17:45:59.332076817 +0200
Modify: 2012-12-01 17:45:59.332076817 +0200
Change: 2012-12-01 17:45:59.332076817 +0200
 Birth: -
wim@i3-2120:~/testje$ stat anotherfile
  File: `anotherfile'
  Size: 12              Blocks: 8          IO Block: 4096   regular file
Device: 806h/2054d      Inode: 9306727     Links: 1
Access: (0664/-rw-rw-r--)  Uid: ( 1000/     wim)   Gid: ( 1000/     wim)
Access: 2012-12-01 17:45:59.332076817 +0200
Modify: 2012-12-01 17:45:59.332076817 +0200
Change: 2012-12-01 17:45:59.332076817 +0200
 Birth: -

```

---

### Post by Wim Sturkenboom on 2012-12-01
> **audiomick said:**
> You can find out about the options of a command using the man page.
honeybear did that; see below exrtact from opening post

> **honeybear said:**
> 
To me it is not clear the man page of cp. 


---

### Post by audiomick on 2012-12-01
Oops. Not paying attention...

---

