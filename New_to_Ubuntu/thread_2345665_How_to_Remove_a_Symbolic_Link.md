---
title: "How to Remove a Symbolic Link"
date: 2016-12-06
forum: New to Ubuntu
---

### Post by oobvi on 2016-12-06
I made what I believe is a symbolic link with the following code:

```
sudo ln -s /usr/share/ca-certificates/mozilla/* /opt/Citrix/ICAClient/keystore/cacerts
```

My understanding of this is that the first directory will point to the second directory. 

How do I remove it? I believe I should use:

```
 unlink /opt/Citrix/ICAClient/keystore/cacerts 
```

and not "rm", which would delete the second directory and not just remove the link, is this correct? And unlink should be used with the secondary directory, not the first, right?

---

### Post by Dennis N on 2016-12-06
The target of the link is first, and the link is second. You can delete the link from the file manager (select it and use delete key), or terminal using **rm**. You need administrative privileges since you made it with sudo.

Edit:
Also, target must be a single specific file or directory, (can't use *) so actually no link would have been created here.

---

### Post by oobvi on 2016-12-06
I found that code from this post:

[https://ubuntuforums.org/showthread.php?t=1975705](https://ubuntuforums.org/showthread.php?t=1975705)

But if the link was not created then will not do anything to undo it. I thought it had caused a problem because the application I was trying to use stopped working after that, but it works fine now so may have not been related.

---

### Post by SeijiSensei on 2016-12-06
Soft links are no different from other files and can be deleted with rm.  Hard links require unlink, but they are much less common. I can't think of a time when I've created a hard link, but I use symlinks all the time.

To create a symbolic link to a directory use
```

ln -s /path/to/target/directory /path/to/somelinkname

```

---

### Post by Dennis N on 2016-12-06
> I found that code from this post:

Well, that post is interesting. Check this out as to the effect of the asterisk:
Initial setup:
```
dmn@Roxanne:~/work/test2$ tree
.
&#9500;&#9472;&#9472; dir1
&#9474;** &#9500;&#9472;&#9472; file1
&#9474;** &#9492;&#9472;&#9472; file2
&#9492;&#9472;&#9472; dir2

2 directories, 2 files

```
Command:
```
dmn@Roxanne:~/work/test2$ ln -s dir1/* dir2
```
Result:
```
dmn@Roxanne:~/work/test2$ tree
.
&#9500;&#9472;&#9472; dir1
&#9474;** &#9500;&#9472;&#9472; file1
&#9474;** &#9492;&#9472;&#9472; file2
&#9492;&#9472;&#9472; dir2
    &#9500;&#9472;&#9472; file1 -> dir1/file1
    &#9492;&#9472;&#9472; file2 -> dir1/file2

2 directories, 4 files

```
Creates two symlinks in dir2 to the two files in dir1. In the command, dir2 must be a directory, which does not have to be empty. The links are named as the target files are, and if the same file name already exists in dir2, that link fails to be created.

_Implications for your command in post #1_ - if **/usr/share/ca-certificates/mozilla/** contains files, then the experiment above suggests links will be created to each of them in **/opt/Citrix/ICAClient/keystore/cacerts** IF cacerts is a directory. So, you need to check that!

---

### Post by kpatz on 2016-12-06
> Hard links require unlink, but they are much less common.Hard links can be removed with rm or unlink.  In fact, rm unlinks as well--there's no "delete file" call in Unix/Linux, only an unlink call.  The file (inode and data) is deleted/space freed once the last hard link is unlinked.

Perhaps I'm old school from the old SysV days before symlinks became popular, but I use hard links all the time.

---

