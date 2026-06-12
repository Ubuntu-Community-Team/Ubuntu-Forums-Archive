---
title: "difference between root user and administrator???"
date: 2013-03-08
forum: New to Ubuntu
---

### Post by Susss on 2013-03-08
Guys m new to ubuntu so m having a little problem in understanding the difference between the root user and the administrator.....and m not able to extract my files in opt directory...how is that possible?I really need your help guys....:confused::confused:

---

### Post by arpanaut on 2013-03-08
This: [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

Should give you the basics of how that works with Ubuntu.

---

### Post by grahammechanical on 2013-03-08
You should read this [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

Basically there is no difference except
 
a) Administrator is a more easily understood term than Root for new users to Linux.

b) in Ubuntu even the administrator runs the OS as a standard user. When we try to do anything requiring administrator (root) privileges we get asked to authenticate with our password. Once we do that the task is run as authorised by root. Once the task is completed or a certain amount of time has passed we revert to working as a standard user.

The files in the home folder are owned by that user. The system files are owned by Root/administrator. We (the administrator running as standard user) can access those files as read only but we cannot write (edit) them. Nor can we over-copy them. What we can do is run the File Manager (nautilus) as administrator or root and we can do the same with the default text edit Gedit. Open a terminal

```
gksudo nautilus
```

```
gksudo gedit
```

You will need to authorise by entering your password. The characters will not be echoed to the screen. Type the password in and press Enter when you are asked to put in the password. You can append a path to a file and Gedit will open that file. You will then be using these utilities with administrator privileges until you close the utility. So, be careful.

Regards.

---

### Post by coldcritter64 on 2013-03-08
root user is an actual user account on the system. This is one account you should not operate in or access its privilege level with sudo unless making system changes, you can do serious system damage by mistake while operating as root.

Any normal user account can become an Administrator account if added to the sudo group, the first account installed on an Ubuntu installation is added to the Admin/sudo group automatically so the machine can be administered with a locked out root account. Locking the root account and using sudo to raise privileges as needed is used in Ubuntu by default, it is a part of Canonical's securtiy model.

PS. The rootsudo link in the post above is a good start to understanding the use of sudo. Cheers. :)

---

### Post by Warren Hill on 2013-03-08
Basically **root** is special account which exists on all Unix like systems including Linux.  You can think of **root  **as being equivelent to God in the sense that **root  **can do anything thats possible on the system and is assumed to be infallable. In Ubuntu this account is locked by default to prevent anyone logging on as **root**.  An **administrator **is a user who can make changes like **root **but has to go through one extra step to run commands.  This is intended to remind users that the command they are running may have serious consequences and require them to enter a password before they make changes.

To make a user an administrator all that is neccesary is to add them to the **sudo** group.  In earlier versions it was the **admin** group.  By default the first user you create is an adminstrator; all others are not unless you manually add them to the correct group. 
The extra step is to prefix command line commands with **sudo**; for GUI programs press ALT+F2 and type **gksu** followed the name of the program to run.

For example **gksu nautilus** will run the file manager as **root**.

[The link]("https://help.ubuntu.com/community/RootSudo") given in posts two and three is an exellent description.

---

### Post by Susss on 2013-03-09
thank u guys...ur reply helped a lot

---

