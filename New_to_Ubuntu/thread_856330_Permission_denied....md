---
title: "Permission denied...?"
date: 2008-07-11
forum: New to Ubuntu
---

### Post by slammed87d21 on 2008-07-11
I sooo feel like a newbie now. I was gonna put a song I downloaded for FoF into the song folder, but when I did, I had a popup that said: Error moving file: Permission denied. What am I doing wrong? Anyone else have this problem before?

---

### Post by MasterXandrex on 2008-07-11
It's probably a file system permission error. Try right-clicking > properties > permissions and make sure your username owns it and has read and write.


Xan

---

### Post by DariusS on 2008-07-11
try again, but this time open up terminal (applications>accessories>terminal) and type:```
gksudo nautilus
```
then type in your password. this will open a file manager in super user mode. 
WARNING! BE CAREFUL! this will give you permission to delete and/or edit important system files, so ONLY access folders you are familiar with.

---

### Post by MasterXandrex on 2008-07-11
OK, I don't mean to give you a hard time... but I keep seeing this EVERYWHERE. Why is it that people seem to think that to solution to all permission errors is to use do it as root. 

Don't you think that perhaps there is a reason that he cannot move the file or that there is an underlying problem with the application that he is using to save the file. 

Damnit, "Do it as root" is not a propper answer. That's like someone coming to you and saying their front door is stuck and you telling the to drive their car through it.

Good lord!

Xan

---

