---
title: "getting permissions for edit the contents in the folders in usr/share/games"
date: 2008-11-09
forum: New to Ubuntu
---

### Post by hatten on 2008-11-09
I want to edit the contents in the folder usr/share/games/OpenLieroX but i do only have the permissions to read. The properties tells me that as i am not the owner i may not change the permissions of the folder. I am admin of the computer and it was me that installed the game. How can i change the permissions?

Image of the properties of the folder
[http://img291.imageshack.us/img291/6216/screenshotopenlieroxprodq6.png](http://img291.imageshack.us/img291/6216/screenshotopenlieroxprodq6.png)

---

### Post by freak42 on 2008-11-09
On the console to get admin rights you prepend your commands with sudo. It temporarily elevates your rights to root rights. When asked for your password you use your own standard password.

If you want to remove a file for instance instead of writing

rm file.txt

you write

sudo rm file.txt

If you want a graphical window to enter your password (like from a script that doesn't run in a console) use gksudo.

So if you want to manipulate your files with nautilus (the file browser) with root rights you can press alt-f2  to bring up the "run application" window and then enter "gksudo nautilus" this will bring up a nautilus instance with root rights.

Be aware that with root rights you can delete any file even if it is important for the workings of your system! So use with care and think twice before doing anything. Also backup your system.

hth

---

### Post by hatten on 2008-11-09
I want to both remove, add and edit files. Is the gksudo nautilius temporary or is there any way to make it possible for me to always be able to edit the files, i want for instance also be able to download files to the folder with firefox and is that possible with gksudo nautilius?

oh, and i want to do everything in the normal file browser and not in terminal, im not used to the terminal yet and know like no commands =P

---

### Post by freak42 on 2008-11-09
the ability is temporary (until you close that instance of nautilus). you can download files with firefox to another location and copy them over with your root-instance of nautilus.

---

### Post by PmDematagoda on 2008-11-09
> **hatten said:**
> I want to both remove, add and edit files. Is the gksudo nautilius temporary or is there any way to make it possible for me to always be able to edit the files, i want for instance also be able to download files to the folder with firefox and is that possible with gksudo nautilius?

It seems to me that you do not fully understand the permissions system of Linux. Yes, it is true that you do have admin powers, but having these powers all the time isn't that good a thing to do. So it is advised that you stick to the normal security practices of Ubuntu(Linux) and take up those admin powers only when it is necessary. 

If you want to run games and want to have normal read/write permissions, then you should use your home directory or another special directory instead. What game are you trying to run? Perhaps I can help you set it up in your home directory.

---

### Post by hatten on 2008-11-09
EDIT:didn't see your post.

yes it is possible to install it in the home folder. I'm thinking if it is worth it to move it there

---

### Post by PmDematagoda on 2008-11-09
> **hatten said:**
> EDIT:didn't see your post.

yes it is possible to install it in the home folder. I'm thinking if it is worth it to move it there

If you want full access to the game folder and don't want to create problems by changing permissions, then in my opinion, the best thing to do is to install it to home.

---

### Post by hatten on 2008-11-09
okay, done :D

thanks for the help, excellent forum. a problem solved in 30 minutes :)

---

