---
title: "Help needed on /home folder"
date: 2008-05-11
forum: New to Ubuntu
---

### Post by Davi0 on 2008-05-11
Did something really dumb (newbie from windows) and dragged a copy of /home (/home/enigma - where enigma is my name) folder to desktop. Then without thinking sent to garbage bin.

Don't know how to either move/merge to original folder location and won't allow deleting.

How do i clean this mess up ?

Doesn't seem to have created any  issues (yet).

---

### Post by HunterThomson on 2008-05-11
> **Davi0 said:**
> Did something really dumb (newbie from windows) and dragged a copy of /home (/home/enigma - where enigma is my name) folder to desktop. Then without thinking sent to garbage bin.

Don't know how to either move/merge to original folder location and won't allow deleting.

How do i clean this mess up ?

Doesn't seem to have created any  issues (yet).

If you just "copyed" the /home to the desktop. You can boot into the live cd and then delete the copy in there with no problem.

---

### Post by volkswagner on 2008-05-11
If you can't right click the folder and select cut, then paste back to home, then try

```
sudo nautilus
```

From a terminal and try cut/paste again.

---

### Post by Davi0 on 2008-05-11
Booted off live Cd and folder doesn't show in trash.

Before I did this I "cut and pasted" to original folder. Result of this was I now have 2 "enigma" folders in /home (/home/enigma/enigma).

This extra folder won't allow to be deleted (greyed out) or moved to garbage bin (no permissions).

Any other suggestions ?

---

### Post by DieB on 2008-05-11
try following

chown -R enigma:enigma /home/enigma/enigma

this will change the owner of the folder and its inhibits to you. After that you should be able to delete.

But: did i get you right /home/enigma/enigma is just a copy of /home/enigma?

---

### Post by HunterThomson on 2008-05-11
> **Davi0 said:**
> Booted off live Cd and folder doesn't show in trash.

Before I did this I "cut and pasted" to original folder. Result of this was I now have 2 "enigma" folders in /home (/home/enigma/enigma).

This extra folder won't allow to be deleted (greyed out) or moved to garbage bin (no permissions).

Any other suggestions ?

OK, I have never real done this kind of thing in the ubuntulive CD I just figured it would work. I alwas use the backtrack Linux live cd (or realy I use backtarck3 USB but no matter) In a live cd and for sure backtrack you are like super super root and you can do anything you want to the harddrive and it is linux so you can read it just fine then you can delete  all the that suff that got messed up. I don't meen put it in trash in the live cd from the harddrive I meen hi light it and hit the delete key. 

This is for real and for sure works so try it agin. And, a whole lot faster and EZ'r then messing around for hr's trying to do it in ubuntu.

---

### Post by Davi0 on 2008-05-11
Ok, I am back to a normal folder (enigma) in /home. That is this folder contains another folder called desktop & that's all.

Can't get rid of the copy I originally dumped in garbage bin now because of this error -

"Couldn't remove the folder bottom_panel_screen0.
 Error removing file: Directory not empty".

How do I alter permissions to allow this to be deleted, assuming it is only a permissions issue. 

The contents of the garbage bin doesn't show in the live Cd boot at all.

---

### Post by billgoldberg on 2008-05-11
if you do 

"sudo nautilus" in a terminal

you should be able to do anything you want.

If you can't figure it out, it might be faster to back up the home folder and reinstall ubuntu, then copy the contents of the home folder to the new /home

---

### Post by HunterThomson on 2008-05-11
> **billgoldberg said:**
> if you do 

"sudo nautilus" in a terminal

you should be able to do anything you want.

If you can't figure it out, it might be faster to back up the home folder and reinstall ubuntu, then copy the contents of the home folder to the new /home

Ya that should work too. In the live cd you would need to find and delete the contents of the trash in the file system I don't know where that is located though.

---

### Post by Davi0 on 2008-05-11
Thanks billgoldberg. The craziest thing is when I open the garbage bin from Ubuntu the folder 'enigma' is there. When I opened nautilus from terminal there is nothing in the garbage bin (same when I boot from the live cd).

This is the terminal results when opening nautilus -

enigma@enigma-desktop:~$ sudo nautilus
[sudo] password for enigma: 
Initializing nautilus-share extension
seahorse nautilus module initialized

** (nautilus:6147): WARNING **: Unable to add monitor: Not supported

--- Hash table keys for warning below:
--> trash:///

(nautilus:6228): Eel-WARNING **: "nautilus-metafile.c: metafiles" hash table still has 1 element at quit time (keys above)

Does this indicate an issue ?

---

### Post by the8thstar on 2008-05-11
**Tentative how-to **(terminal + GUI): 

1. Do a ***sudo nautilus ***in the terminal to be granted root privileges for this time only.

2. Navigate to your home dir and folder. Select the folder by right-clicking on it, and check the Permissions tab.

3. Go up a level (/Home), select the folder and move it to the trash.

4. Flush the trash.

---

### Post by Davi0 on 2008-05-11
Trash won't flush, this is the problem (read above).

---

### Post by snooptodd on 2008-05-11
your trash folder is in ~/.local/share/Trash

in a termanal type
```
ls -hl ~/.local/share/Trash/files/
```
if you see the folder u want to delete then in the termanal type 
you can post the output of that command if you are not sure what you are looking at.

```
THIS IS DANGEROUS PLEASE ONLY DO THIS IF YOU KNOW WHAT YOU ARE DOING.
rm -rf ~/.local/share/Trash/files/* ~/.local/share/Trash/info/*

-r recursive
-f force
they are needed to delete directorys that are not empty.
```
that will only delete what is in the Trash folder. BUT if there is any typo it could delete everything. What i like to do before running that command is replace the rm -rf with ls first to make sure i dont screw anything up.

---

