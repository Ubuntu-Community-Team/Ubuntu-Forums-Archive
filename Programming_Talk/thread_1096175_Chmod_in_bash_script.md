---
title: "Chmod in bash script"
date: 2009-03-14
forum: Programming Talk
---

### Post by Rany Albeg on 2009-03-14
Hi all , 

I've just started to learn shell programing and i wrote a simple script to set permissions to a specific folder.

it goes:
---

#!/bin/bash

read -p "Folder's full path : " PATH

read -p "Enter permission number : " PERMISSION

chmod -R "$PERMISSION" "$PATH"

exit 0

---
When i try to run this i get an error message :

Folder's full path : /home/rany/Desktop/folder1
Enter permission number : 700
**./SecureAFolder: line 9: chmod: command not found**

also i changed line 9 to begin with **'sudo'** but i get :

**./SecureAFolder: line 9: sudo: command not found**


Thanks.

---

### Post by gjoellee on 2009-03-14
if you are changing the permissions form some certain groups and users, just use ie:
```
chmod -R 775 /opt/lampp/
```you don't need any variables or anything

---

### Post by snova on 2009-03-14
You appear to be overwriting the $PATH variable. This is used by the shell as a list of directories to search in for commands.

Since chmod probably isn't in the folder you're overwriting it with, it doesn't work. :)

Simply rename the variable:

```

#!/bin/bash
read -p "Folder's full path : " DIRECTORY
read -p "Enter permission number : " PERMISSION
chmod -R "$PERMISSION" "$DIRECTORY"
exit 0

```

By the way, that'll also operate on files, which usually don't need +x permissions. Perhaps instead replace the second to last line with:

```
find "$DIRECTORY" -type d -exec chmod $PERMISSION {} \;
```

Which will run it on all subdirectories, but not files.

---

### Post by ghostdog74 on 2009-03-14
be careful when chmodding especially if you find you have done something wrong. To get back your permissions, do a backup
```

find `pwd` -printf "%u:%p\n" > /tmp/backup.txt

```
to undo
```

while IFS=":" read a b; do chown $a $b done < /tmp/backup.txt

```

---

### Post by Rany Albeg on 2009-03-15
Thank you guys ;)
Have a nice day.

---

