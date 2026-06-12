---
title: "[SOLVED] No hardware info, no device manager"
date: 2008-08-22
forum: New to Ubuntu
---

### Post by Lorelei- on 2008-08-22
This is possibly be going to illustrate my newbie-ness, but when I was trying to find my hardware information to access the device manager to check something last night it didn't appear to exist on my system (I'm running 8.04). I went to where it should be under 'System - Preferences', but it doesn't show there at all.

Do I need to install something additional for this or should it already be there?

If I need to install something, please can someone point me in the right direction.

Ta!

---

### Post by Bradtek on 2008-08-22
I have it in  
Applications / System Tools / Device Manager


Check if you have it installed type in terminal
```
gnome-device-manager
```

---

### Post by Lorelei- on 2008-08-22
hmmm not sure I saw it there either, but as this was after working a 16hour day yesterday, its fairly probable that the world was all blurring into one!

---

### Post by Bradtek on 2008-08-22
> hmmm not sure I saw it there either

It's quite possible  I put it there myself.

It might be a case of it is installed but has no menu entry.
Right click on your Menu and select Edit Menus
Click which section you want it in 
eg System/Preferences  or Applications/System Tools.
Click New Item
Give it a name 
command = gnome-device-manager
ok etc etc

---

### Post by Lorelei- on 2008-08-22
thank you Bradtek, I appreciate the help.

Shall have a play around with it tonight and see if I can make it appear somewhere so I can access it.

---

### Post by silverglade00 on 2008-08-22
```
me@mycomputer:~$ gnome-device-manager
The program 'gnome-device-manager' is currently not installed.  You can install it by typing:
sudo apt-get install gnome-device-manager
bash: gnome-device-manager: command not found
```

Looks like you need to install it first. The package from the repos creates the menu entry for you in the place that Bradtek mentioned.

---

