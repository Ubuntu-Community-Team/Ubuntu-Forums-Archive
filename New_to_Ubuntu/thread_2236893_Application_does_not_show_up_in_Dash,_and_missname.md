---
title: "Application does not show up in Dash, and missnamed in Launcher"
date: 2014-07-29
forum: New to Ubuntu
---

### Post by Tom_Carr on 2014-07-29
I just installed something called kfind from the software center.  It shows up on the launcher as "Find Files/Folders" even though it is really named kfind.  When I to Dash and type either find or kfind, it does not show up.

---

### Post by mc4man on 2014-07-29
What shows up in the unity launcher, (or any launcher) is what's on the Name= line in the app's .desktop file. In this case it's - 
Name=Find Files/Folders
As far as not showing in the Dash well it's a kde app & has this line in it's .desktop so it will not show in other sessions - 
OnlyShowIn=KDE;

To get it to show in an ubuntu (unity) session that line would need to be, (in /usr/share/applications/kde4/kfind.desktop) - 
OnlyShowIn=KDE;Unity;

---

### Post by Tom_Carr on 2014-07-29
Thanks for your help mc4man

in 
/usr/share/applications/kde4/
I have a file named Find Files/Folders which is a desktop configuration file, but I don't understand how I could change that.
Also, I looked at the properties and it said I was not the owner so I could not change the permissions.

---

### Post by deadflowr on 2014-07-30
Open a text editor, and the open the file from there.
Usually you would click on file system and then go to usr > share > applications > kde4 > file.
Then edit it as suggested.
Then save it with "save as".
when saving it this way, instead of trying to save it to the system folder /usr/blah, save it to the hidden user folder, .local.
 (In the window listing places to save it, right click  and select show hidden.)
Then go to .local > share > applications > save it here.
Files saved here will/should show in the dash, as well as the changes you make will always stick for you.

---

