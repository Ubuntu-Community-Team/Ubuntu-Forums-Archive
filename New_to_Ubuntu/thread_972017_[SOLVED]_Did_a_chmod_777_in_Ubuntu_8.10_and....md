---
title: "[SOLVED] Did a chmod 777 in Ubuntu 8.10 and..."
date: 2008-11-05
forum: New to Ubuntu
---

### Post by XanII on 2008-11-05
Just upgraded from 8.04 to 8.10 and i was playing around with themes. Happened to read about some themes that they required you to make a chmod on certain files in the /usr/share/themes folder and since i had problems with some theemes i did a

sudo chmod 777 -r /usr/share/themes

and voila, some icons became unusable on the desktop, menus at the top were lost and replaced with menus seen by the guest user. tried logging on as other users and they too had guest menus.

problems
1) what did i do wrong? i wonder did i maybe change whole / to 777 with chmod? dont understand what harm there is chmoding themes folder to 777.
2) how to get access again. cant even reach the terminal.
3) how to restore default ubuntu upper menu, deleted it as i tried to troubleshoot so now i dont have that either. im burning 8.10 on a disc now, can i use it to 'repair' the system. seems to me that i made a foul that messed the system so maybe restoring all packages and leaving user folders alone can fix most of the problems?

---

### Post by bscbrit on 2008-11-05
You can always get access by rebooting and selecting Recovery Mode.  You will be the only user and logged on as root.  Alternatively, I suppose that you could always use a LiveCD to get access to the machine causing problems.

Mind you, I don't know what you want to do when you get there.....

You could boot from the LiveCD and see what permissions the themes have in its directory - not yours but the directory that is holding its themes.  On my machine they are all owned by root and directories have 755 as their permissions, and files have 744.

---

### Post by eolson on 2008-11-05
Here's what I THINK happened ...
you were trying a recursive chmod and used -r instead of -R

first you did chmod 777  which gave read/write/execute to everybody then the -r was executed removing the read and leaving write/execute.  You can probably fix the whole thing by doing a chmod 777 +r .......

just a guess

remember linux/unix are case sensitive

---

### Post by maybeway36 on 2008-11-05
If you can get to a prompt somehow, try this:
```
ls -l /usr/share/themes
```

---

### Post by XanII on 2008-11-05
I had rwx-r-r on files in usr/share/themes. now i made a proper -R chmod /usr/share/themes and all are now 777. No change though. All problems still persist regardless of which user i logon. Only guest items are visible plus of course i still dont know how to get the default upper menubar back with the 'applications system administration' options. On the second user on this computer theese options above are visible but they are mostly empty, all is locked as it is in the guest mode. 

About chmod: couldnt find chmod -r in the chmod man pages. not +r either. 

i was able to read .bash_history, maybe i can get a clue what command i did.

---

### Post by XanII on 2008-11-05
Hopeless. All programs that i am able to launch does not have their top-part. for example firefox that i have as a icon on desktop is accessible, but what i get is a browser where 'file edit view history...' etc. menu is the top-most. nothing above it. 

This means i cannot move/resize windows. some programs do open, but they open outside the desktop and i cannot reach them. 

Im doing the backups now. :( seems like clean 8.10 install is what is needed.

---

### Post by bscbrit on 2008-11-05
You can always drag a window my pressing the Alt key before pointing to ANY part of the window and dragging.  You should be able to get to all parts of your Firefox window this way.

---

### Post by cariboo on 2008-11-05
the command you are looking for is:

```
chmod -R 755 /usr/share/themes
```

To recreate your top panel right click on the bottom panel and select New Panel. You can then add the applets you need by right clicking on the panel and selecting Add to Panel.

Jim

---

### Post by XanII on 2008-11-06
Alt key does not work. tried that first thing. also the 'move' command is accessible, that should allow me to move with cursor keys? not working. 

Did a chmod -R 755 /usr/share/themes but no effect. 

Studied .bash_history and concluded that chmod 777 /usr/share/themes was the only valid command i had there. -r or +r are not valid as far as i know and im unable to recreate those 'commands'. 

Nevertheless the effect of this (if this is the reason anyway) is quite bad enough to make a re-install. I have backed up my files and grub files and now i'll just solve this with a clean install. Thanks to all who took their time to reply to me though. :)

---

### Post by bscbrit on 2008-11-06
Good Luck.  See you on the forum once you have recovered your computer!

---

