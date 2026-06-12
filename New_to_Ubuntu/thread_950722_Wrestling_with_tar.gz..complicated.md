---
title: "Wrestling with tar.gz..complicated"
date: 2008-10-17
forum: New to Ubuntu
---

### Post by joey-elijah on 2008-10-17
Total n0ob question, but i really do have troubles trying to get to grips with anything that comes as a tar.bz.whatever

Most of the time when i run xvzf tar whatever.tar.gz etc i'm told that the file doesn't exist/isn't there. Even if i copy/paste the file name.

Given my default download location is the desktop, and terminal is already "on" the desktop... i don't get it.

If i manage to get past that, i usually find i'm unable to "cd" to the extracted directory.

If i get that far (i usually end up typing cd and the dragging the extracted folder into the terminal and removing the quottation marks) i'll try a ./configure and nothing will happen.

What am i doing wrong?! 

Secondly, i am a dock-a-holic. I have docks on my windows, ubuntu and mac 'puters, but whenever a tar.gz is installed it doesn't end up in the menu's for easy dragging onto my dock. 

Whenever i create a custom launcher linking to the 'file you click to get it to run inside the filename folder' it doesn't work. Hmmph.

help much?

---

### Post by nothingspecial on 2008-10-17
Terminal does not default to the desktop, it defaults to your home folder. Try ```
cd Desktop
``` before trying to manipulate files on/in it.

---

### Post by greg@localhost on 2008-10-17
Reading over your post, your issues concerning tar seem to be to do with paths - you say that you can't cd to the extracted directory, file doesn't exist etc. Remember to use pwd to check where you are, and that su may change your path.
 
./configure will only work if the file is actually there - you should check this first.

If you post some actual examples or error messages, then I can help you further.

---

### Post by Sarmacid on 2008-10-17
I was about to suggest the cd Desktop, but anyways, not all the .tar.gz's have a ./configure, so sometimes you should take a look at the readme. Also, to untar this kinds of files, you can just do it through the GUI.

---

### Post by Orange_and_Green on 2008-10-17
Hello joey-elijah :)

> **joey-elijah said:**
> Most of the time when i run xvzf tar whatever.tar.gz etc i'm told that the file doesn't exist/isn't there. Even if i copy/paste the file name.

I don't know if this is the core of your problem or just a typo, I'll point it out anyway. The correct command is
```
tar -xvzf filename.tar.gz
```
Not the other way round. Good luck:KS

---

