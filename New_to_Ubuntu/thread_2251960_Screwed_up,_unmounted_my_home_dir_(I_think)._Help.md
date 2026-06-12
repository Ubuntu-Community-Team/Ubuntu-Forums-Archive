---
title: "Screwed up, unmounted my home dir (I think). Help?"
date: 2014-11-07
forum: New to Ubuntu
---

### Post by robert136 on 2014-11-07
[COLOR=#000000][FONT=verdana]I'm very new to linux and am running lubuntu on an old P4 (comp1) and raspian on a raspberry pi (comp2). I was messing around today and mounted the home directory of the comp1 on a directory on comp2. While sshed into comp2 from comp1 using:[/FONT][/COLOR]
            [INDENT]
sudo sshfs -o allow_other user@comp1: comp2/dir              [/INDENT]
[COLOR=#000000][FONT=verdana]
It worked fine and I was able to access all the files in the new mounted directory. Done with my playing I unmounted comp1 using:[/FONT][/COLOR]
            [INDENT]
sudo fusermount -u comp2/dir[/INDENT]
[COLOR=#000000][FONT=verdana]
Now when I am on comp1 and I try and access any of the files in my home dir it returns[/FONT][/COLOR]
            [INDENT]
cannot open directory: Permission Denied       [/INDENT]
[COLOR=#000000][FONT=verdana]
Any ideas how I can return it to normal?[/FONT][/COLOR]
[COLOR=#000000][FONT=verdana]I'm sure I haven't provided all the info necessary, but I'm very lost and not sure what to include.[/FONT][/COLOR]
[COLOR=#000000][FONT=verdana]Thanks in advance.[/FONT][/COLOR]

---

### Post by MrSteve on 2014-11-08
open a terminal and write
sudo >file browser name< 
press enter
enter your password
press enter

when nautilus opens go to your home folder and right click 
then click properties > permissions

make sure that you the user is listed and have read and write permission
then tick apply to all file and folders 
click apply

see if you have access now ...

---

