---
title: "Gnome panel and/or AWN problem..."
date: 2008-06-03
forum: New to Ubuntu
---

### Post by idontknowme on 2008-06-03
Recently i decided to uninstall one of my gnome panels in favour for the much more attractive Avant Window Navigator. Well i went to delete my bottom gnome panel ( closing all  applets first ) and confirming the delete process. So i proceeded to install the new AWN manager only for it to give me one minor but fustrating problem. Every time i went to restart my computer i would have to start my AWN manager manually. Needless to say that got very tiresome after a few times. I tried to install AWN the three ways i know how : Add/Remove,Terminal,and Synaptic, and still i get the same problems. 

  Heres where it starts to get beyond my primitive knowledge on linux:

  I uninstalled my AWN manager and replaced it with a traditonal Gnome panel. when i went to open a program i found out that i didn't show up on the new panel that i just created! i also found out that when i went to minimize a window that it didn't show up on the panel either! This is very fustrating to me and would like to know if any one else had that problem or if they know how to fix this. Also if anyone knows how to fix the AWN problem i was having please give a VERY dumbed down awnser. 

P.S I went in the awn manager and clicked the autostart feature and still had the same problem.

  I hope this will help out any one else that had any similar problems to!


idontknowme :confused:

---

### Post by starcannon on 2008-06-03
If you'd like to keep awn but just want it to auto start, that is easy to do, 

**System-->Preferences-->Sessions**

Then:

**Add-->Name=AWN-->Command=avant-window-navigator-->OK**

Reboot and Avant should auto start itself (assuming its still intalled)
**-------------------------------------------------------------------------**
If you still want to restore the gnome panels we can do that if you wish.

**Applications-->Accessories-->Terminal**
```
 rm -R ./.gconf
```
**Reboot**
Your panels should be factory fresh :)

---

### Post by idontknowme on 2008-06-04
Just one more noob thing and i will give you an offoical thanks and close this forum. I notice that you gave me a terminal comand that had [rm] in the command. I thought that any command with the letters [rm] in it would erase all data at the root and user level, leaving me with a bricked system.

  Thanks for the other advise though! It worked like a charm. The only thing i am questioning is, why didn't think of that?


idontknowme

---

### Post by Golem XIV on 2008-06-05
> **idontknowme said:**
> Just one more noob thing and i will give you an offoical thanks and close this forum. I notice that you gave me a terminal comand that had [rm] in the command. I thought that any command with the letters [rm] in it would erase all data at the root and user level, leaving me with a bricked system.

  Thanks for the other advise though! It worked like a charm. The only thing i am questioning is, why didn't think of that?


idontknowme

**rm** stands for "remove".  It's the equivalent of the MS-DOS command **del**

The -R option means "recursive", i.e. it will go down the directory tree.

So the command that starcannon posted would delete the .gconf directory and all its files and subdirectories.  An equivalent command in Windows/DOS would be **deltree .gconf**.  Deleting this directory will force Gnome to recreate it with default settings at the next login.  

This being said, I wouldn't use  **rm -R ./.gconf** but rather
```
rm -R ~/.gconf
```
where the ¨~¨ sign denotes your home directory.

---

### Post by alexandremrj on 2008-06-05
Hello,

there are two different issues:

AWN: When you click inside awn-manager to start at boot it sometimes doesn't work so it's safer to simply add awn to the sessions manager - like starcannon said.

Gnome-panel: I know this may sound stupid but did you add the window list applet to the bottom panel? This is the only way to see the windows you minimize and have open.

---

