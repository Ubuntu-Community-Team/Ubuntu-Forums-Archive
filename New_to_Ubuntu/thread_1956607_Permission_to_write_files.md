---
title: "Permission to write files"
date: 2012-04-11
forum: New to Ubuntu
---

### Post by mashavecher on 2012-04-11
I need to gain permission to write to a particular folder created by the script which installed a program. Only one folder. It is owned by root at the moment and located at: /usr/arb I need to be able to write to folder "arb" to be able to past there file containing database of sequences, so the program can open it and create a server.
How do I do that? Don't want to mess up other folders permissions
Thanks in advance

---

### Post by cortman on 2012-04-11
Use sudo? chmod the folder?

---

### Post by audiomick on 2012-04-11
I would be looking to see if you can get the program in question to use a different folder to store the database in. If that is possible, that seems to be the easiest to me.

As cortman suggested, you could try using sudo or chmod. For instance, you could try running the program in question using sudo to start it. This would probably allow the program to write to the file, but would mean that the program is running with root permissions, which is not recommended.

You could use chmod to change the permissions of the folder to be owned by the user, or to open up the permissions to allow others to read and write to the folder. In fact, this may be your solution. If you don't know how to use chmod (I have to look it up all the time...), you could start an instance of Nautilus with root permissions and change the permissions from there.

To do this, in a terminal
```
gksudo nautilus
```
give your password when requested. The terminall will show a couple of lines of stuff, then the file manager Nautilus will open.

REMEMBER: This instance of Nautilus has root privileges. It WILL NOT ASK for confirmation if you, for instance, tell it to erase system files or such like. Be careful in there, and close it as soon as you have done what you want to do.

Navigate to the folder in question and right click on it. Choose "properties" and go to the "permissions" tab. Set the permissions for "other users" to be able to read and write to the folder. I think there is also a box to tick to apply the change to all files in the folder.


A further thought occurs to me: if you only have to add an existing file once to this folder, and the program can then use this file without having to write anything new to it, you should be able to move the file into the folder in question with the aforementioned instance of Nautilus with root privileges without changing any permissions.

---

### Post by mashavecher on 2012-04-11
Thank you audiomic. I need those privileges in order to run program properly. As I'm new to linux I needed a full guide how to change privileges in one folder only.  I don't need the program to run under root, just ability to write to folder. As the folder is created by the installation script, I guess the only problem I can run into is damaging the program, not the system.
Manual of the program expects that you know basics of operating linux. I have to manage by my self step by step.
Thank you so much

---

