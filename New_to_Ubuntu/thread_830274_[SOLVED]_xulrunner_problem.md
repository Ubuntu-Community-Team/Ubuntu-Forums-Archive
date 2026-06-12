---
title: "[SOLVED] xulrunner problem"
date: 2008-06-15
forum: New to Ubuntu
---

### Post by Bix in Austin on 2008-06-15
Hello again;
Actually this is an addition to my previous post. I have finally gotten a screenshot of the error message moved to win 2k on this computer. Well I thought I would get it in this post but not this time. Anyway the error message is as follows;

E:/var/cache/apt/archives/xulrunner-1/9_1/9~rcl +nobinonly-Oubuntul~8.04.2_i386.deb: short read in buffer_copy (backend dpkh-debduring`./usr/.iob/xulrunner-l.9/libmozjs.so').
I seem to have a permanent note to download this file for update. The file name in the download screen is;
xulrunner l.9
xul+spcom application runner (size 7.0MB)I have tried several times to get this file but the error always comes up. I can get other updates without any problems though.:mad:
I have found this fine in the folder specified in the error message but I can't do anything with it. I was hoping to delete it and reinstall it but so far I can't. With this error I have lost use of firefox and must go back to my old win2k to get out. I sure hope somebody has an answer for this. I am now thinking about reloading the whole shebang over again.
Bix in Austin

---

### Post by sdennie on 2008-06-15
I would try the following:

```

sudo rm /var/cache/apt/archives/xulrunner*
sudo apt-get update
sudo apt-get upgrade

```

Edit:
That will remove any cached xulrunner packages, update the list of available packages and then upgrade anything that can be upgraded.

---

### Post by Bix in Austin on 2008-06-16
Thanks vor for the information, I will try your solution right away.
Bix in Austin

---

### Post by Bix in Austin on 2008-06-16
Thanks vor, your solution worked. I am now using Firefox on Ubuntu again.
Bix in Austin

---

