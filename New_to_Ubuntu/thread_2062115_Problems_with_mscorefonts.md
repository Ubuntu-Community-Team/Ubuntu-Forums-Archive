---
title: "Problems with mscorefonts"
date: 2012-09-24
forum: New to Ubuntu
---

### Post by stuartlarsen on 2012-09-24
Hello, I'm new to Ubuntu and have recently installed 12.04 in a dual boot arrangement with Windows 7.
I am getting a red circle warning in the upper tool bar that says the following when clicked...

*An error occurred, please run Package Manager from the right click menu or apt-get in a terminal to see what is wrong. The error message was : 'Unknown Error: '<type 'exceptions SystemError'>' (E:The package ttf mscorefonts-installer needs to be reinstalled but can't find an archive for it.)'. This usually means that your installed packages have dependencies"*

I'm not sure whether it's related but I also can't open the software center.

Any help with this would be very much appreciated

Thanks

Stu

---

### Post by NikTh on 2012-09-24
Hi , 

please open a terminal (Ctrl+Alt+T) and copy-paste from here bellow commands with order. One at time. One line=One command. 

```
sudo apt-get update 
sudo apt-get install -f
sudo dpkg --configure -a
sudo apt-get dist-upgrade
```post the results back here and _put the results between the brackets_ **[noparse]```
Here
```[/noparse]**

Thanks

---

### Post by stuartlarsen on 2012-09-25
Thanks NikTh, really appreciate your reply.
I spent a lot of time on this last night and actually found a fix... by that stage, I could barely keep my eyes open and didn't think to record what I did, sorry. It did involve 3 lines in Terminal including a sudo apt-get clean all (or something like that) and then install and upgrade ... I think. Will try not to do this when I'm so tired again.
Everything seems to working again though now 
Thanks again
Stu

---

