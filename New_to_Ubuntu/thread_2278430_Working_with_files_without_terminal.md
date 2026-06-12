---
title: "Working with files without terminal"
date: 2015-05-16
forum: New to Ubuntu
---

### Post by konrad9 on 2015-05-16
As a past windows user I am accustomed to running everything through GUI.. I'm a programmer and most of the time I'm willing to edit some files. I'm not really familiar with running each file through terminal with sudo gedit... to make simple change. I would like to right click on file, open with gedit/sublime text and be allowed to save the file without any problems. Is it possible to do ?

I solved the problem:

I found Superlime plugin that lets me to save as root in SublimeText directly.

---

### Post by TheFu on 2015-05-18
Using **sudo gedit** is dangerous for a few reasons.  Set your EDITOR environment variable to any editor you like and use **sudoedit file-to-edit**. To understand why this is more secure AND better, you can check out the manpage for sudoedit.

[http://ubuntuforums.org/showthread.php?t=2269093](http://ubuntuforums.org/showthread.php?t=2269093) has some more background and a few other options.

It is possible to modify certain file managers to extend functionality. Alas, I don't use file managers often enough to say how to accomplish that. Sorry.

---

### Post by mastablasta on 2015-05-19
i remember that you could open file manager as root in old Xubuntu and then you opened the files as root.

I am not sure actually what you are trying to do. sudo Is needed only when you are doing changes to system files / files that affect the system. or in other words when setting up the system. once it is setup  you don't need it that much. some file manager also have plugins or by default an option when you right click you can open as root. I think windows works much in the same way now.

---

