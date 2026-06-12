---
title: "File Permissions Issue"
date: 2013-04-21
forum: New to Ubuntu
---

### Post by Brandon93 on 2013-04-21
Hi everyone! This is my first post on the forums so be nice. :)

I installed Ubuntu two days ago and have never used any linux software before so i'm in a bit of a pickle. 
Being an exWindows user, i'm used to being able to move/edit/delete whatever I needed, but here i'm having problems. 

My problem is that I have found a theme that I want to install, but when I do a "drag and drop" into usr/share/themes,  it it says I do not have permissions. 
**I already have sudo permissions**

I found a command online which I tried. "sudo mv /home/Downloads/Core /SYSTEM/usr/share/themes"
Core folder is what I wish to move to the themes folder. 

After hitting enter, I receive this message "mv: cannot stat `/home/Downloads/Core': No such file or directory"

Question: What am I doing wrong/Is there another method to this?

---

### Post by claracc on 2013-04-21
here, [http://askubuntu.com/questions/213697/how-can-i-install-themes](http://askubuntu.com/questions/213697/how-can-i-install-themes), there is a detailed guide about how to install themes in ubuntu 12.10.

---

### Post by 3rdalbum on 2013-04-21
> **Brandon93 said:**
> Hi everyone! This is my first post on the forums so be nice. :)

I installed Ubuntu two days ago and have never used any linux software before so i'm in a bit of a pickle. 
Being an exWindows user, i'm used to being able to move/edit/delete whatever I needed, but here i'm having problems. 

My problem is that I have found a theme that I want to install, but when I do a "drag and drop" into usr/share/themes,  it it says I do not have permissions. 
**I already have sudo permissions**

I found a command online which I tried. "sudo mv /home/Downloads/Core /SYSTEM/usr/share/themes"
Core folder is what I wish to move to the themes folder. 

After hitting enter, I receive this message "mv: cannot stat `/home/Downloads/Core': No such file or directory"

Question: What am I doing wrong/Is there another method to this?

In Ubuntu, your ordinary user account can't modify the filesystem as a security measure. You can temporarily obtain the permissions of root (the administrator) by using the Sudo or Gksudo commands. Sudo is used for terminal commands, but Gksudo is used for running GUI programs as root.

If you type:

```
gksudo nautilus
```

into the terminal, it will ask for your password and then open Nautilus (the file browser) as root. Within that window, you'll be able to navigate to /usr/share/themes and drag your theme directory to it. Make sure you close the root Nautilus window afterwards; you should only use root when you absolutely need it otherwise you can screw up the permissions and security of your system.

The two reasons why your command didn't work are because there is no such directory as /home/Downloads/Core, and the destination directory is /usr/share/themes not /SYSTEM/usr/share/themes. Remember, you can drag and drop files and directories into the terminal window and their full path will be put into the terminal.

---

