---
title: "where is the root trash in 8.10?"
date: 2008-11-16
forum: New to Ubuntu
---

### Post by bronner on 2008-11-16
hi, 

i deleted some files from the recycle bin and i need them back
im using intrepid 8.10, i can't seem to find the root trash folder 
with gksudo nautilus...there's a .local/root/trash but there's only 
two empty folders in it...what can i do?

---

### Post by empthollow on 2008-11-16
sorry to say, but if i am understanding the files are gone.  If you deleted them from the trash bin, they are no longer on your hard drive.  The trash folders you are looking in are for trash bin contents.

---

### Post by bronner on 2008-11-16
huh thats weird because i've done it before in hardy...after emptying the files from the trash, i was able to get them back from some other folder...

---

### Post by boblemur on 2008-11-16
how did you delete them?

because im prity sure if it was from console they are gone...

you could still try locate <filename> in terminal
and if there around somewhere then that might find them...

---

### Post by empthollow on 2008-11-16
the only situation i've had that is similar is that some of the files that i moved to trash didn't appear in the system trash folder.  This happened to me in hardy.  I had to delete them manually to remove them.  I noticed that in hardy they had changed the locations of the user trash folders but i assumed it was a bug because you are not suppose to have to go and delete files manually.   Perhaps, what i had assumed as a bug worked to your favor in hardy.

---

### Post by bronner on 2008-11-16
nah i just clicked 'empty trash' in the recycle bin...

---

### Post by ad_267 on 2008-11-16
No, if you delete a file it is gone, it doesn't go to root's trash or any other folder. 

It goes to your own trash if you just press delete, but if you actually delete the file by pressing shift+delete, right clicking and selecting delete, or removing it from your trash it is gone for good. The roots trash is if you delete something in Nautilus when running it as root, but I'm not sure if this still applies in 8.10.

There are recovery tools available that may be able to recover the file.

---

### Post by ciscosurfer on 2008-11-16
@bronner,

Like [ad_267]("http://ubuntuforums.org/member.php?u=472577") alluded to, your data is not necessarily gone (yet).  You can give this page a shot: [https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery)

---

### Post by bronner on 2008-11-16
no wait, i found it...nevermind i just used photorec

---

### Post by SunnyRabbiera on 2008-11-16
> **ciscosurfer said:**
> @bronner,

Like [ad_267]("http://ubuntuforums.org/member.php?u=472577") alluded to, your data is not necessarily gone (yet).  You can give this page a shot: [https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery)

right a file is never quite deleted till its space is used.
its sort of why hard drives fragment over time though

---

### Post by Gone fishing on 2008-11-16
In Linux Format I was reading a review of Stellar Phoenix a Windows undelete program that will let you reover deleted files from ext3 partitions.

So if you have a Windows partition you could give it ago.

---

