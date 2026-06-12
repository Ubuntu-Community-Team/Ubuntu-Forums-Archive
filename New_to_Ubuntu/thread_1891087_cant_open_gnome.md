---
title: "cant open gnome"
date: 2011-12-04
forum: New to Ubuntu
---

### Post by matx028083 on 2011-12-04
i am brand new to linux, i have ubuntu server 11.10 and i downloaded gnome desktop, had it up and running once. now i cant get it back all i can get is the lui i can type in startx and it just goes black then i have to reboot the computer(virtual box).i assume i am doing something wrong. i am mainly learning linux just to get used to it because i plan to build a new computer in a few months and want to run only linux. i would rather not even have the gui but my internet is wifi only with a wireless adapter. gui would make it alot easier to install.

---

### Post by 3rdalbum on 2011-12-05
You might find it easier to start with regular Ubuntu and add server packages on top of that. Ubuntu Server is Ubuntu Desktop, minus the GUI. Literally.

Your instructions seem a bit old. These days, you start the GUI by using the command:

```
sudo service lightdm start
```

That is, assuming you've got the lightdm display manager installed - that's the Ubuntu default for Ubuntu Desktop. You might have GDM instead - same command, just put 'gdm' instead of 'lightdm'.

Once you've typed the command you should be able to log in and access the GUI desktop as normal.

Other distributions still might use "startx", but Ubuntu is a bit different.

---

### Post by diablo75 on 2011-12-05
I would also suggest starting with Ubuntu Desktop edition and then installing the services on top of it after.  It's easier.  Ubuntu Server isn't really intended to be run with a GUI.

---

