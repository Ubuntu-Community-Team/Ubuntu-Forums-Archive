---
title: "How do I load files from a windows XP DVD to ubuntu?"
date: 2014-05-05
forum: New to Ubuntu
---

### Post by Timothy_Cota on 2014-05-05
After 8 years of dreaming about it I took the plunge and switched to ubuntu 14.04 from Win. XP.  I burned discs with files that I need.  Now how do I load these files into ubuntu?

---

### Post by oldfred on 2014-05-05
Nautilus is the Ubuntu file manager. If you have a different flavor, you may have a different file manager. But not really much different than Windows Explorer in that select, copy & paste from DVD into /home. Copy music into the Music folder, Documents into Doucuments folder etc.

Been ages since I had to recover from DVD, but I still make them regularly for the most important files on my system. You may have to change from read only to read write.

If you run this it will show that $USER is a variable with your name, so you can just copy these two commands, chown & chmod
echo $USER
You can in mass change all files in /home to defaults.
 sudo chmod -R a+rwX,o-w /home/$USER
All directories will be 775.
All files will be 664 except those that were set as executable to begin with.
      
 sudo chown $USER:$USER /home/$USER

Do not run on any system partition. The -R is recursion and it changes everything  in all lower levels. I accidentally ran  a change at / once with -R and had to reinstall as too much changed.

---

### Post by 3rdalbum on 2014-05-06
> **Timothy_Cota said:**
> After 8 years of dreaming about it I took the plunge and switched to ubuntu 14.04 from Win. XP.  I burned discs with files that I need.  Now how do I load these files into ubuntu?

Insert the DVD, when it appears on the left side click it, drag your files to your home directory.

Or did you mean something else?

---

### Post by Timothy_Cota on 2014-05-06
You hit it on the head.  My family and I are continually amazed by  how smooth and intuitive ubuntu is, and how simple some of the tasks are once someone tells you how to do it.
                                                                                                                                                                                                                                                      Thanks, unktim

---

