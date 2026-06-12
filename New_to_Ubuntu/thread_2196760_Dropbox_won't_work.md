---
title: "Dropbox won't work"
date: 2013-12-31
forum: New to Ubuntu
---

### Post by hugodaniel2 on 2013-12-31
I've installed the latest version of Drop Box, _***dropbox_1.6.1_amd64.deb***_, and _***nautilus-dropbox_1.6.1_all.deb***_, but when I retart my pc I get the following error:

***OSError: [Errno 13] Permission denied: '/home/me/Dropbox'***

I'm not able to open the Dropbox folder inside my home folder.

I've already tried to reinstall both this apps, but without luck. I'm quite new to Linux and, currently I'm working with Ubuntu 13.10.

Does anybody know what I can do?

Thanks a lot, and a Happy New Year!

---

### Post by ajgreeny on 2013-12-31
Let's see the output of ```
**ls -l | grep Dropbox
```** in terminal to see what the permissions are on Dropbox.

---

### Post by hugodaniel2 on 2013-12-31
Using that command I get the following output: drwx------ 9 root root   4096 Dez 31 11:08 Dropbox

---

### Post by Coltman151 on 2013-12-31
you installed dropbox as root, and only root has permission to run dropbox.

---

### Post by ajgreeny on 2013-12-31
Try command ```
sudo chown user:user /home/user/Dropbox
```  If you have any files in the folder you may need to use the -R option to make the files in the folder yours as well, ie **sudo chown -R user:- - - etc etc**. Type your username where I have shown **user**

How did you install the dropbox .deb file you had?

---

### Post by hugodaniel2 on 2014-01-02
Ok [**[COLOR=#000000]ajgreeny[/COLOR]**]("http://ubuntuforums.org/member.php?u=27747"), the command you've indicated has worked.

[B]sudo chown -R user:- - - etc etc

[/B]Answering your question, well, I've installed Dropbox downloading the .deb file, and executing and installing it, using the Ubuntu Software Center, and also using the terminal.[B]

sudo apt-get install dropbox

[/B]Thanks for your help.

---

