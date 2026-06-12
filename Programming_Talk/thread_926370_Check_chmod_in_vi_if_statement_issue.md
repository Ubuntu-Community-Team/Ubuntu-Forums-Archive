---
title: "Check chmod in vi if statement issue"
date: 2008-09-21
forum: Programming Talk
---

### Post by radamsiii on 2008-09-21
Need to test directory, checking mode is 775 otherwise making it so. 
```

If [ -R testdir 775 ] ; then echo “statement’
Else
Chmod –R 775 testdir

```
Is there a way to do this?
What man pages could help?

Thank you for looking

---

### Post by ghostdog74 on 2008-09-21
```

find -type d -perm 755 -name "test"

```
if there is output, then the directory "test" has 755.

---

### Post by radamsiii on 2008-09-21
Thank you so much for the reply. I am writing a script that will create a large directory, adding users and groups and assigning them to the appropriate directories. These directories must be set to mode 775. I have the program complete and working, I want to check the directory path to insure it is set to 775 and if not then set it that way otherwise move to the next if statement. 

Short version, directory is test/test2/test3
Check test and its children, if set to 775 then next ; otherwise
Change mode to 775

Thank you 
R,

---

### Post by dwhitney67 on 2008-09-22
After you finish creating your directory structure (tree), change the permission on each directory to the permission-level you wish.

For example:
```
find ./topdir -type d -exec chmod 755 {} \;
```

This command finds all directories within 'topdir', including the directory 'topdir', and changes their permission-level to 755.

I really do not see the need to determine if each directory is set to 755 or not, when the command shown above will ultimately just set the directories to the permission level you want.

---

