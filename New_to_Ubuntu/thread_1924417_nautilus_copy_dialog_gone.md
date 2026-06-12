---
title: "nautilus copy dialog gone"
date: 2012-02-12
forum: New to Ubuntu
---

### Post by Nihilithik on 2012-02-12
Greetings UbuntuSuperGurus, 
i'M coping a large set of files, and my copy dialog window disappeared. I know it's a noob question, but how can i get it back?

---

### Post by thomsebastin on 2012-02-12
> **Nihilithik said:**
> Greetings UbuntuSuperGurus, 
i'M coping a large set of files, and my copy dialog window disappeared. I know it's a noob question, but how can i get it back?
hi nihilithik,
i think copy dialogue s still there but ua not able to do it since you're not the root.press alt+F2, type gksudo nautilus(u can type this in terminal either)..u'll be prompted for password.Enter it,then i think u'll be able to copy paste.
me too just a beginner,hope experienced users will come up with a better answer!!
-cheers

---

### Post by gdea73 on 2012-02-12
It's relatively simple, in Nautilus you can close a file transfer dialog if it's in your way - it will be minimized to the system tray (top-right if running Gnome 2). It's a little icon with a folder and I think a cursor, if you click on it, there's an option "Show file copy dialog."

This is the way it works in Ubuntu 10.10, I'm not sure if it's different on Unity, but this is what I've noticed on my installs.

---

### Post by LinuXofArabiA on 2012-02-12
Why bother with the GUI, when you can do all the copying you need in one command? Go back to the proper (ol fashioned) way. 

Here is a good read to get you going on the 'cp' command.

[http://linuxcommand.org/lts0050.php#cp](http://linuxcommand.org/lts0050.php#cp)

Regards
[]("http://linuxcommand.org/lts0050.php#cp")

---

### Post by thomsebastin on 2012-02-12
> **LinuXofArabiA said:**
> Why bother with the GUI, when you can do all the copying you need in one command? Go back to the proper (ol fashioned) way. 

Here is a good read to get you going on the 'cp' command.

[http://linuxcommand.org/lts0050.php#cp](http://linuxcommand.org/lts0050.php#cp)

Regards

**+1** on that.....

---

### Post by Nihilithik on 2012-02-13
Well guys, thanks for the tips, but here lye the problems. I am using 11.01, logged in as Ubuntu, which i think is unity not gnome, and the files are already in the process of moving. Its a very long file transfer, i am backing up my win 7 music and videos, and such. I am doing this through a router at a blazing speed of 1.1 MPS (meg per sec). However my copy dialog window disappeared and, while all the files are still copying, i now don't have a progress bar, or any way to check elapsed time, or time until completion.

i searched through the usual forums, and goggled stuff, and there seems to be a bug in the way the GUI is worked out, but all i could find were bug reports w/o any fix.

---

### Post by 3rdalbum on 2012-02-13
There should be an indicator in your top panel that looks like a folder with an arrow in it. Click on this and your file copy dialog should come back.

Otherwise, you can click twice on the Home Folder icon in the Launcher (the left sidebar on the screen) to reveal all open file browser windows, including the copy box.

If this still doesn't work, then you are probably not copying anymore.

---

### Post by Nihilithik on 2012-02-15
> **3rdalbum said:**
> There should be an indicator in your top panel that looks like a folder with an arrow in it. Click on this and your file copy dialog should come back.

Otherwise, you can click twice on the Home Folder icon in the Launcher (the left sidebar on the screen) to reveal all open file browser windows, including the copy box.

If this still doesn't work, then you are probably not copying anymore.


that did it. thanks. i dont know why i could find that through a casual google search, sheeesh.

---

### Post by aliqasemi on 2012-09-02
> **Nihilithik said:**
> Greetings UbuntuSuperGurus, 
i'M coping a large set of files, and my copy dialog window disappeared. I know it's a noob question, but how can i get it back?
mine is disappeared too, non of the above worked for me, what can I say, just praying it get fixed by itself !

Edit:
the command:
wmctrl -R "File Operations"
does the job, incase....

---

### Post by finechap on 2012-10-15
How annoying is it that the Copy Dialogue disappears?

It is possible to get it back but it is not entirely straight forward, unless you're lucky.

You have to get at the Dolphin icon in the action bar, usually on the left. Right click it for "Show Copy Dialogue".

If this doesn't work and it didn't for me; there should be a tiny white triangle (or two) to the left of the icon.
Click on this tiny, tiny white triangle and the dialogue should re-appear!

---

### Post by Charlietje on 2012-11-09
> **aliqasemi said:**
> mine is disappeared too, non of the above worked for me, what can I say, just praying it get fixed by itself !

Edit:
the command:
wmctrl -R "File Operations"
does the job, incase....


+1
```
wmctrl -R "File Operations"
```

---

### Post by The Bright Side on 2012-12-02
None of the suggestions in this thread work for me. I am copying 180 GB from my hard disk to my external drive as I'm typing this, and the copy progress dialog is gone, and it's impossible to bring it back.

The Nautlius icon in the launcher has a progress bar on it, so I have a rough idea how far I am into the process, but it doesn't replace the good old copy dialog.

I remember this problem occurring about 1.5 years ago or so. Sad that it's back.

I'm on Ubuntu 12.04, 64 bit. Does anybody know if there's a bug report for this?

EDIT: found it!
[https://bugs.launchpad.net/ubuntu/+source/unity/+bug/1010132](https://bugs.launchpad.net/ubuntu/+source/unity/+bug/1010132)

---

### Post by Cincinnatux on 2013-03-27
I realize I'm waaaay late for this, but a workaround I've been using is as follows:

If I minimize each open window on my desktop, the last one is the file operations dialog.  I then right-click on it, set it to "always on top" and then I can re-maximize my other applications and get back to work while still having instant access to the file operations dialog.  Until the bug is resolved, this works for me.  YMMV.

- Cincinnatux

> **The Bright Side said:**
> None of the suggestions in this thread work for me. I am copying 180 GB from my hard disk to my external drive as I'm typing this, and the copy progress dialog is gone, and it's impossible to bring it back.

The Nautlius icon in the launcher has a progress bar on it, so I have a rough idea how far I am into the process, but it doesn't replace the good old copy dialog.

I remember this problem occurring about 1.5 years ago or so. Sad that it's back.

I'm on Ubuntu 12.04, 64 bit. Does anybody know if there's a bug report for this?

EDIT: found it!
[https://bugs.launchpad.net/ubuntu/+source/unity/+bug/1010132](https://bugs.launchpad.net/ubuntu/+source/unity/+bug/1010132)

---

### Post by satya-461 on 2013-11-04
> **aliqasemi said:**
> mine is disappeared too, non of the above worked for me, what can I say, just praying it get fixed by itself !

Edit:
the command:
wmctrl -R "File Operations"
does the job, incase....


This worked for me! Thanks!

---

### Post by coffeecat on 2013-11-04
Old thread. Closed.

---

