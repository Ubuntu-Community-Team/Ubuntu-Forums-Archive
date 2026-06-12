---
title: "Confused about file permissions"
date: 2010-01-15
forum: Programming Talk
---

### Post by kahumba on 2010-01-15
Hi,
I noticed that no matter how I "chmod" a text file as root, it has no effect on me (thus on root). I can always read/write to it even if I issue "chmod 000 rootfile.txt".

If so, why have the option to set restrictions on root if they have no effect anyway?

---

### Post by doas777 on 2010-01-15
[U]root can read anything always

sorry boutthe underline. it won;t stop...
[/U][]("http://www.unix.com/unix-dummies-questions-answers/46013-file-permission-000-a.html")

---

### Post by d3v1150m471c on 2010-01-15
chmod 755 path/to/filename (if it's in your home folder, which makes like tremendously easier, then just type the filename by itself.)

this will give all the permissions in the world to the file. Or you can be lazy like me and right click the file, go into properties, permissions tab, and the check off or adjust whatever you want it to do.

---

### Post by d3v1150m471c on 2010-01-15
Just a side question but what are you trying to do with the file? If you're doing a bash script then add this line under your first comments. example:

#!/bin/bash
# your comments and whatnot
gksudo bashscriptname

That will pop open a graphical superuser prompt for your password and then run the program. If you do this make sure you have a command at the end of the program because, depending on what the script does, it will just continue to run incessantly...over and over and over, and eat up every bit of your cpu... I've had this happen to me before when i was first learning bash scripts.

---

### Post by kahumba on 2010-01-15
So, basically one should never bother about the first number in the  "chmod" command, right?
Except when un/setting the "execute" bit, right?

@[d3v1150m471c]("http://ubuntuforums.org/member.php?u=979822") I'm just learning and got curious about this.

---

### Post by arubislander on 2010-01-15
> **kahumba said:**
> Hi,
I noticed that no matter how I "chmod" a text file as root, it has no effect on me (thus on root). I can always read/write to it even if I issue "chmod 000 rootfile.txt".

If so, why have the option to set restrictions on root if they have no effect anyway?

there are no options to set restrictions on root. Any restritctions you set apply to everyone else except root.

---

### Post by doas777 on 2010-01-15
> **kahumba said:**
> So, basically one should never bother about the first number in the  "chmod" command, right?
Except when un/setting the "execute" bit, right?

@[d3v1150m471c]("http://ubuntuforums.org/member.php?u=979822") I'm just learning and got curious about this.

 by first number do you mean when using a 3-digit set or a 4digit? if you are using 4byte, then the first number controls suid(sticky), sgid, and another one that escapes me at the sec.

no you cannot lock out root. it's designed like that on purpose.

---

### Post by kahumba on 2010-01-15
I see, 
thanks everyone

---

