---
title: "Easy way of editing files requiring root permission"
date: 2006-02-07
forum: Outdated Tutorials &amp; Tips
---

### Post by peterthewolf on 2006-02-07
Go to Administration/Disks you will be asked for your root password then in any disk browse while under this option you can double click any editable file and amend in gedit. This saves having to sudo in terminal.

---

### Post by dcstar on 2006-02-08
[QUOTE=peterthewolf]Go to Administration/Disks you will be asked for your root password then in any disk browse while under this option you can double click any editable file and amend in gedit. This saves having to sudo in terminal.[/QUOTE]
Or make a Root File Browser icon that launches with the following:

gksudo "nautilus --browser %U"   << This goes in the "**Command**" part of the Launcher **you** will create!

Then you can browse, edit, whatever as root.

---

### Post by peterthewolf on 2006-02-10
Tried that although as an ordinary user I do not how I would have found it.
Further as you can see from below it does not work.

peter@ubuntu:~$ gksudo "nautilus --browser %U"
(nautilus:8144): GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.

--- Hash table keys for warning below:
--> file:///

--- Hash table keys for warning below:
--> file:///

(nautilus:8144): Eel-WARNING **: "nautilus-metafile.c: metafiles" hash table still has 1 element at quit time (keys above)

(nautilus:8144): Eel-WARNING **: "nautilus-directory.c: directories" hash table still has 1 element at quit time (keys above)
peter@ubuntu:~$

---

### Post by peterthewolf on 2006-02-10
Sorry but my mad wife used a bit of female logic and saw what you meant straight away and YIPEE it works fine. Still do not understand why.

---

### Post by caven80 on 2006-02-10
Hey, Peter,

Can u please tell me what exactly that logic was which ur wife used..??
as i'm facing a similar scenario.

---

### Post by dcstar on 2006-02-10
[QUOTE=caven80]Hey, Peter,

Can u please tell me what exactly that logic was which ur wife used..??
as i'm facing a similar scenario.[/QUOTE]
Re-read my (now) edited post.

---

### Post by peterthewolf on 2006-02-11
caven80

Right click on desktop, choose create launcher, against the basic tab put some description in the name (I used "root editor") and choose a suitable icon at bottom of basic tab. Now go to launcher tab and put gksudo "nautilus --browser %U" as mentioned above into command:
Now close and you will have new icon on desktop.

---

### Post by caven80 on 2006-02-12
[QUOTE=peterthewolf]caven80

Right click on desktop, choose create launcher, against the basic tab put some description in the name (I used "root editor") and choose a suitable icon at bottom of basic tab. Now go to launcher tab and put gksudo "nautilus --browser %U" as mentioned above into command:
Now close and you will have new icon on desktop.[/QUOTE]

---------------------------------------------------------------------

Hey peter,

thanks for ur  help. i managed to create the launcher on the desktop and also after initiating the launcher, n putting in my password, i cannot open few folders..it says ' folder cannot be opened' or something like that with some code..

am i not supposed to be able to open anything n everything..??

let me know please..

---

### Post by peterthewolf on 2006-03-02
Sorry for the delay but it just works. Are you sure you hace gksudo in front of the command.

---

### Post by stanz on 2006-03-10
Hi All,
Geez~ Thats kewl! Thanks...
I wish i was here a few days ago, when- by some solar event or something-
I changed permissions- in a really BAD way. 
I use an 'Admin File Manager' in Xandros...and now- thanks to you~ i have that 'saftey net' here too!!

---

