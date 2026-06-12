---
title: "Editing Files"
date: 2021-12-21
forum: New to Ubuntu
---

### Post by kenbright on 2021-12-21
How do I open /edit the file “/lib/udev/rules.d/60-gpsd.rules” on ubuntu 20.04 - It's to get  an old samsung notebook to work with a gps dongle. I believe I need root to do it. If I try to use g edit it can't even see the file but have found it using su in a terminal. After several years I remain a Linux novice!

---

### Post by Holger_Gehrke on 2021-12-21
The best way to edit files that need root permissions to write to is to use 'sudoedit'. This copies the file (using root if necessary), opens the copy in an editor, and copies it back (again using root permissions if necessary) after you've made your changes. But if you just call 'sudoedit /lib/udev/rules.d/60-gpsd.rules' you'll probably find yourself in vi, a very powerful but not really beginner-friendly editor. To tell sudoedit to use another editor you have to set the variable EDITOR:
```

EDITOR=/usr/bin/gedit sudoedit /lib/udev/rules.d/60-gpsd.rules

```

Holger

PS: You might want to set EDITOR permanently. To do so, edit ~/.bashrc and add a line 'export EDITOR=/usr/bin/gedit'

---

### Post by Impavidus on 2021-12-21
I think the default editor here is nano. I use vim. You can use the EDITOR environment variable to set it to any text editor you like. The editor itself doesn't run as root, so there are none of the risks you had with sudo <editor>.

There is however one issue to take care of. sudoedit does the following:
1: copy the file to a temporary location;
2: start an editor with the argument to edit that temporary file;
3: wait for the the editor to terminate;
4: if the temporary file has been changed, copy it back and delete the temporary file.

Some editors (mousepad on my Xubuntu system, but maybe gedit does it too) check to see if another instance of the editor is already running. If so, the new instance tells the old instance to open a new tab or window with the file to edit, then the new instance terminates, allowing you to edit the file in the old instance. But when the new instance terminates, sudoedit proceeds past step 3, sees that the file hasn't been modified, doesn't save any changes and deletes the temporary file. Then you edit the file, save it to the temporary location and close the editor, but sudoedit has already terminated, so doesn't copy the file back. So the changes only get saved in the temporary location in /var/tmp/.

In mousepad you can prevent this behaviour by using```
EDITOR="mousepad --disable-server"
```

---

### Post by TheFu on 2021-12-21
+1 for using **sudoedit** and setting the EDITOR environment variable to whatever editor you prefer. Depending on your shell (the default is bash), you can add 1 line to your ~/.bashrc file, logout, login, and have sudoedit use whatever editor you like. The line is:

```
export EDITOR=gedit
```
Probably want to put that at the very bottom of the ~/.bashrc file.

If you only use a GUI, this should be fine.  If you sometimes remote into the system using ssh, using a GUI editor is a poor choice, but it is up to you.

---

