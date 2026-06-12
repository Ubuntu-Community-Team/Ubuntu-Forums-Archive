---
title: "tar command"
date: 2009-03-17
forum: Programming Talk
---

### Post by munishvit on 2009-03-17
After doing some experiments with 'tar' command, I came to following conclusions. But I am quiet doubtful, as noting such is mentioned anywhere. So, if you find me wrong, please let me know.

**Problem-1:**
In case we are creating new archive, 
[COLOR="Red"]tar cvf filename.tar <sources>[/COLOR]
The same hierarchy of folders will be created inside the archive as we mention in <sources>.
For example:
```
$ cd /home/username
$ tar cvf /home/username/new.tar /home/username/dir1 /home/username/dir2
```
This command will not just make archive of files inside 'dir1' and 'dir2', but inside archive there will be created a hierarchy of /home, /home/username/...these directories as well. 
Thus, result of the above will be different from the following commands:
```
$ cd /home/username
$ tar new.tar dir1 dir2
```

**Problem-2:**
In case we are extracting files from archive,
[COLOR="Red"]tar cvf filename.tar[/COLOR]
While extracting, we can not specify where to extract. Files will always be extracted to pwd (present working directory).

**Problem-3:**
In case we want to extract more than one file to pwd.
Let there are two archive files ~/Test/file1.tar and ~/Test/file2.tar
```
$ cd ~
$ tar Test/file?.tar
```
Instead of extracting both the files to /home/username, it gives error. So, I guess wildcards with archive name can not be used as long as they can match more than a single file.

Thanks

---

### Post by lloyd_b on 2009-03-17
1.  Correct.  If you specify the path for the files to archive, tar will create the exact same directory structure in the archive file (meaning that if you specify "/home/username/dir1", when unpacking it will create a "home" in the current directory, a "username" beneath that, a "dir1" beneath that, etc.

If you want to duplicate the behavior of "cd /home/username; tar cvf new.tar dir1 dir2" you'll need to use the "-C" option:```
tar -cvf new.tar -C /home/username dir1 dir2
```

2.  The "-C" option will handle this situation as well:```
tar -xvf new.tar -C /home/username/otherdir
``` will extract the contents of "new.tar" into the directory "/home/username/otherdir".

3.  You need to explicitly tell it which files to untar via the "-f" option (as well as specifying "x" to extract files from that archive).  You *can* untar multiple files using the "-M" option and multiple "-f" declarations, but not using wildcards```
tar -xvM -f file1.tar -f file2.tar
```.

Alternately, you can use "find" as a front end:```
find test -name "file?.tar" -exec tar -xvf {} \;
```

Lloyd B.

---

### Post by munishvit on 2009-03-17
Thanks a lot...You cleared all my doubts:guitar:

---

