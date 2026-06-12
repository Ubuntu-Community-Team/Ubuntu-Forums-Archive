---
title: "[SOLVED] How to edit a file in treminal"
date: 2008-06-21
forum: New to Ubuntu
---

### Post by harsh_ on 2008-06-21
I have this file vsftpd.conf; for vsftpd...But when i edit the file using gedit it gives me an error "This file can be only written by root.U don have enuf permisions"


Something to do with sudo/chmod.... Please help and even if i execute sudo gedit vsftpd.conf
then wrie something for the file in the terminal itself??? Please elaborate... I'm new to linux

---

### Post by Vivaldi Gloria on 2008-06-21
Press Alt+F2 and 

```
gksudo gedit /path_to_the_file/filename
```

Or in the terminal try

```
sudo nano /path_to_the_file/filename
```

In order to use a program as root use gksudo in graphical environments and sudo in the terminal.

You press Alt+F2 and 

```
gksudo nautilus
```

to browse your filesystem as root.

---

### Post by drs305 on 2008-06-21
> **harsh_ said:**
> I have this file vsftpd.conf; for vsftpd...But when i edit the file using gedit it gives me an error "This file can be only written by root.U don have enuf permisions"


Something to do with sudo/chmod.... Please help and even if i execute sudo gedit vsftpd.conf
then wrie something for the file in the terminal itself??? Please elaborate... I'm new to linux

When you receive a message like that it means that you are trying to edit a system file or a file owned by another user. You don't normally have permission to change those files. However, you can temporarily gain permission to edit these files by assuming administrative powers.

You do this with the sudo command. Open your text editor with the following command. I use gedit, but you may use nano, vi, etc. For graphical applications, 'gksudo' is preferred over 'sudo'.
```
gksudo gedit /path/filename
```

It will ask for a password. Enter your password. You will not see anything but it will be registered. Hit enter and you should now be able to edit the file.

---

### Post by ajgreeny on 2008-06-21
To read more about sudo and its advantages and disadvantages go [here]("https://help.ubuntu.com/community/RootSudo").

---

