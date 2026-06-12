---
title: "How to set file permission"
date: 2012-04-09
forum: New to Ubuntu
---

### Post by mgrameshbabu on 2012-04-09
Hi Ubuntu users,
I have questions.

1) I am using administrative account. Still I could not able to set file permission. I could not able to make any changes.

2) I have one more question. I want to extract a folder (1.8GB) into /opt. The total space allotted for this (/opt) is about 702MB space only (I think by default). How to increase space in /opt file system?

Thanks in advance
Ramesh

---

### Post by codemaniac on 2012-04-09
Hello mgrameshbabu , Here is a brief tutorial for you to understand the file permissions in Unix based Operating systems .
[http://www.dartmouth.edu/~rc/help/faq/permissions.html](http://www.dartmouth.edu/~rc/help/faq/permissions.html)

---

### Post by adit on 2012-04-09
There is no such thing as administrative account in ubuntu.  If you want to set permission for a file, you should be the owner of that file.  In the terminal type
```
ls -l name_of_the_file
```
This will tell who is the owner of the file.  You are trying to set permission of file to which you are not the owner.  That is why it does not work.

---

### Post by codemaniac on 2012-04-09
chmod command is used to set file permissions , for administrative permission changes you might need to add add sudo prefix to it .

---

### Post by adit on 2012-04-09
Type the code in the terminal and post the output.
```
mount |grep opt
```
This will tell you in which partition opt is mounted.  If no output is produced it is mounted under the same filesystem as root filesystem.

---

### Post by dwhite on 2012-04-09
> **mgrameshbabu said:**
> Hi Ubuntu users,
I have questions.

1) I am using administrative account. Still I could not able to set file permission. I could not able to make any changes.


Ramesh

you can also set permissions this way,

[LIST]
[*] right click on the file,
[*]select "properties"
[*]select the "permissions" tab and set the permissions with the menus
[/LIST]

---

### Post by zombifier25 on 2012-04-09
> **dwhite said:**
> you can also set permissions this way,

[LIST]
[*] right click on the file,
[*]select "properties"
[*]select the "permissions" tab and set the permissions with the menus
[/LIST]

You must be root to change permission of files you don't own however.
```
gksudo nautilus
```
Then do the above.
The command line method is quicker (only need to append sudo to the beginning of the command)

---

