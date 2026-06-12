---
title: "Why does a folder need execute permission?"
date: 2009-10-11
forum: Programming Talk
---

### Post by froggyswamp on 2009-10-11
Folks I noticed that despite having read/write access to a folder (inside home dir, which contains simple non-executable files) I can't read its content (files) until I also set the execute flag.
I'm surprised, anyone knows what's the reason?

---

### Post by peetbull on 2009-10-11
This is indeed a confusing part of directory privileges.

As I get it:

[LIST]
[*]write: create or delete files
[*]execute: access files
[/LIST]
Maybe a real-life-ish example could give you the idea. Warning: it might sound odd, but it sustains the analogy.

Consider a real carton box (directory) in which we can add/remove any piece of paper (file) we want.

[LIST]
[*]read: browsing the papers
[*]write: adding/removing papers
[*]execute: touching the box (to open it, or move it)
[/LIST]
A more detailed guide about file permissions can be found here:
[http://www.albany.edu/faculty/gms/homepage101/unix_permissions.html](http://www.albany.edu/faculty/gms/homepage101/unix_permissions.html)

Be well!

---

### Post by sgosnell on 2009-10-11
You shouln't need to set the execute bit on a folder.  I don't know what's wrong, but something is if you have to set that.  If you're the owner, you can access the files unless something is wonky.

---

### Post by GuyCorngood on 2009-10-12
From [Wikipedia]("http://en.wikipedia.org/wiki/File_system_permissions"):

[INDENT]The execute permission, which grants the ability to execute a file. This permission must be set for executable binaries (for example, a compiled c++ program) or shell scripts (for example, a Perl program) in order to allow the operating system to run them. **When set for a directory, this permission grants the ability to traverse its tree in order to access files or subdirectories, but not see files inside the directory (unless read is set).**[/INDENT]

So:

```
% pwd
/home/mark/tmp
% ls -l
total 8
dr--r--r-- 2 mark users 4096 2009-10-12 01:03 r
dr-xr-xr-x 2 mark users 4096 2009-10-12 01:03 rx
% cd r
cd: permission denied: r
% cd rx
% pwd
/home/mark/tmp/rx
% cd ..
% ls r
ls: cannot access r/file: Permission denied
ls: cannot access r/dir: Permission denied
dir  file
% ls rx
otherdir  otherfile
% cd r/dir
cd: permission denied: r/dir
% cd rx/otherdir 
% pwd
/home/mark/tmp/rx/otherdir
```

---

### Post by Mister.Vash on 2009-10-12
> **sgosnell said:**
> You shouln't need to set the execute bit on a folder.  I don't know what's wrong, but something is if you have to set that.  If you're the owner, you can access the files unless something is wonky.

If you have drives are setup normally, then you do to have that set.  Permissions are different when mounting windows file systems, but that wasn't what was being asked about.

If everything is setup normally, in your home folder for example, and you create a test folder with a file in it then chmod 600 to the new folder to get rid of the execution bit, you would no longer be able to see the file that you put in it.  Go ahead and try if you like, you should be able to access that folder under normal conditions.

Here are some additional details on it
[http://content.hccfl.edu/pollock/AUnix1/FilePermissions.htm](http://content.hccfl.edu/pollock/AUnix1/FilePermissions.htm)

It's best to think of them as two different bits - the execution bit on a file means you can execute that program - the execution bit on a directory basically allows the contents of the directory to bee seen.  So with that bit, you can't see the contents of the folder.

---

### Post by wmcbrine on 2009-10-12
On a directory, setting the executable bit allows you to *change to* or *use* that directory (*not* to read it). A directory without the executable bit set isn't useful, but a directory with the executable bit set, but the read bit *not* set can be. You can change to such a directory, but not list it. You can still read and write files in this directory if you know their names, even though you can't list them.

Edit: Or, in other words, what #4 said.

---

### Post by froggyswamp on 2009-10-12
Thanks everybody!! if I wasn't that greedy I'd buy you a beer :)

---

