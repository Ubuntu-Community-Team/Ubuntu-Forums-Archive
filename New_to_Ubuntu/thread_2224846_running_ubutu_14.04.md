---
title: "running ubutu 14.04"
date: 2014-05-18
forum: New to Ubuntu
---

### Post by newblank25 on 2014-05-18
i downloaded Jin chess program. I put the download into a folder name JIn in my home directory & extracted files in that folder. i thought that if I typed jin.jar in the terminal that it would work. Instead I got this message.
The file '/home/michael/.cache/.fr-Es9Ps5/jin-2.14.1/jin.jar' is not marked as executable.  If this was downloaded or copied from an untrusted source, it may be dangerous to run.  For more details, read about the executable bit. can some one tell me how to get program to work. Thx

---

### Post by stalkingwolf on 2014-05-18
right click on the file. select properties . tick the bo that says something about allow opening as executable.

---

### Post by LastDino on 2014-05-18
Not the solution but if its a chess program you're looking for, try pychess, it is available in software centre and it is lot better option than running a Java based game.

---

### Post by SuperFreak on 2014-05-18
pychess

---

### Post by newblank25 on 2014-05-18
yes pychess allows me access to fics. jin is a chess interface

---

### Post by Kingsrookie on 2014-05-18
you can use the chmod command and mark it executable that way.

chmod +x (Path)/jin.rar

---

### Post by Joe_Malin on 2014-05-18
Another hijack: I use chmod +x (or a+x) so often that long ago I created the alias "mx" for it: 
alias mx="chmod a+x"

mostly because a shell script needs execution permission.

---

