---
title: "using svn checkout on plugdev-owned partition?"
date: 2008-04-18
forum: Programming Talk
---

### Post by Haf on 2008-04-18
Hello, I am having problems with SVN.
The situation is as follows: I have a dualboot PC and waat to have a FAT32 partition that I can use for programming projects both under Ubuntu and Windows. I want to use SVN for several projects, but svn has problems with accessing the partition, I believe maybe because of the way that it is mounted. Oddly enough, I can create, changeand remove files on it as a user, but the svn client always gets permission denied errors, when trying to checkout a project.
Example:
```
desktop:/media/Projects/cpp/svn/scummvm/trunk$ svn co https://scummvm.svn.sourceforge.net/svnroot/scummvm/scummvm/trunk
svn: Kann Berechtigungen auf »trunk/.svn/entries.2.tmp« nicht setzen: Operation not permitted
```
The part " Kann Berechtigungen auf »trunk/.svn/entries.2.tmp« nicht setzen" is German and means something like " Can't set rights to »trunk/.svn/entries.2.tmp«"

This is how the partition is defined in the fstab:
```
/dev/sda8       /media/Projects     vfat     rw,defaults,uid=0,gid=46,umask=000     0     0
```

Any idea how I can fix this?
As I just realized, the svn client is also able to create files and folders, as it creates a .svn folder before it throws the error.
mmh...

---

### Post by mssever on 2008-04-18
It's likely that svn is trying to set permissions on the files. Of course, that will fail on FAT32, since that filesystem has no concept of UNIX permissions. Better to put it on an ext3 permission and then install the Windows ext3 driver so you can access it from Windows.

---

### Post by Haf on 2008-04-18
Thank you for your help.

Well, that's really strange, as other applications just ignore the fact that they can't set any user rights. Can't this behaviour of svn be changed somehow? I don't really want to convert this partition to ext3 unless absolutely necessary.

---

### Post by mssever on 2008-04-18
> **Haf said:**
> Thank you for your help.

Well, that's really strange, as other applications just ignore the fact that they can't set any user rights. Can't this behaviour of svn be changed somehow? I don't really want to convert this partition to ext3 unless absolutely necessary.

The thing is, permissions are important. For example, how can you run scripts if they aren't executable? Some files require exact permissions to be set. If svn didn't preserve permissions, it would break code sometimes. Many other applications don't care because it isn't their job to make sure that files are EXACTLY a certain way. You can hunt through the svn documentation; perhaps there's a way to make svn ignore permissions. Otherwise, I don't think that you have very many options.

---

### Post by Haf on 2008-04-18
Well, oddly enough, the windows version of svn obviously doesn't care about rights. ;)

Ok, it seems that I've got to go through with this ext3 conversion. :/

Thanks for your help!

---

### Post by mssever on 2008-04-18
> **Haf said:**
> Well, oddly enough, the windows version of svn obviously doesn't care about rights.

It can't. Windows permissions are completely different from UNIX permissions. There's no comparison. If the Windows version tried to preserve UNIX-style permissions, then it would break.

---

