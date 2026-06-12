---
title: "Permissions for 'lost and found'"
date: 2008-08-22
forum: New to Ubuntu
---

### Post by The ragman on 2008-08-22
I have just changed from Windows Vista Pro, to Ubuntu, and for the most part, I am happy with the change. A couple of programs on the windows platform are going to be missed, but I can live with it. 

What I am a little concerned with, is the folder, within the BIN folder called Lost and Found. It informs me that I don't have the authority to enter it. I am not having a system on my computer with secrets, so how do I get into the folder, lost and found?

I loaded Ubuntu from a donated disc, with no documentation.

---

### Post by yabbadabbadont on 2008-08-22
lost+found is the folder used to hold broken files/directories after the disk has been run through a file system check after a crash.  Sort of like the CHK**** files that chkdsk creates under DOS/Windows.  It is normally restriced to root, which means you have to use sudo in order to get permission to work in it.

---

### Post by OutOfReach on 2008-08-22
[This]("http://tldp.org/LDP/Linux-Filesystem-Hierarchy/html/lostfound.html") might be worth a read.
Basically, it is used by the system and is 'locked' so you would need to access it with root privileges.

---

### Post by yabbadabbadont on 2008-08-22
> **OutOfReach said:**
> [This]("http://tldp.org/LDP/Linux-Filesystem-Hierarchy/html/lostfound.html") might be worth a read.
Basically, it is used by the system and is 'locked' so you would need to access it with root privileges.

Thanks.  That was the link I was looking for to add to my post.  You beat me to it.  :D

---

### Post by iaculallad on 2008-08-22
> **The ragman said:**
> I have just changed from Windows Vista Pro, to Ubuntu, and for the most part, I am happy with the change. A couple of programs on the windows platform are going to be missed, but I can live with it. 

What I am a little concerned with, is the folder, within the BIN folder called Lost and Found. It informs me that I don't have the authority to enter it. I am not having a system on my computer with secrets, so how do I get into the folder, lost and found?

I loaded Ubuntu from a donated disc, with no documentation.

On your terminal, input the command below to get you the privilege:

```
gksudo nautilus
```

and from there, try browing the "Lost and Found" folder.

Actually, Ubuntu creates the "Lost and Found" folder on every partition for the purpose of recovering broken files during disk checks.

---

### Post by OutOfReach on 2008-08-22
> **yabbadabbadont said:**
> Thanks.  That was the link I was looking for to add to my post.  You beat me to it.  :D
:D

The ragman: I wouldn't really worry about that lost+found folder, but if you feel curious do what iaculallad said.

---

### Post by The ragman on 2008-08-23
Thank you for the explanation - I will go look, as I have a major problem with secrets on my computer - paranoia is my usual state..  :lolflag:

---

