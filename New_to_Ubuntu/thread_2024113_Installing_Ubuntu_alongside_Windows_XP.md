---
title: "Installing Ubuntu alongside Windows XP"
date: 2012-07-13
forum: New to Ubuntu
---

### Post by Islandgryl on 2012-07-13
There are several Tutorials to be found in these Forums or elsewhere that give clear and helpful advice together with step by step instructions aimed at beginners.

**bogan**.


I did the side by side install without taking care enough with regard to the partioning and have confused the XP install and it won't boot, I am hoping to be able to "fix" it.

I'm sorry to jump in this thread [[http://ubuntuforums.org/showthread.php?p=12098436#post12098436]](http://ubuntuforums.org/showthread.php?p=12098436#post12098436]) but this is a close as I have been able to find to this topic.  and hoped someone would direct me..is there a way to fix the XP partition records once they have been changed by a Ubuntu install?? and is there a How to Tutorial on this topic?

Very beginner and not careful enough...oops.

---

### Post by mastablasta on 2012-07-13
first of all you should post in a new post.
 
secondly you din't provide enough info. but if you chose formating the windows XP partition during dual boot setup then you overwrote the data and it will probably be nearly impossible to retreive the data. what i suggets is to post in new thread and add some data (such as how the disk is devided (maybe a pic from gparted) etc.

---

### Post by oldos2er on 2012-07-13
Posts moved to their own thread.

---

### Post by NikTh on 2012-07-13
**Hello [Islandgryl]("http://ubuntuforums.org/member.php?u=1499141") and Welcome to Ubuntu Forums ! **

Can you boot to Ubuntu ? If you cannot , then boot from a LiveCd/Usb . 
Open a terminal (Ctrl+alt+t) and copy-paste these commands from here to your terminal , one at time .
```
sudo fdisk -l 
sudo parted -l
```Post back here the results . 
**Put the results inside [CODE] tags by highlighting the text and click # symbol at the top of message pane. **
Thanks

---

