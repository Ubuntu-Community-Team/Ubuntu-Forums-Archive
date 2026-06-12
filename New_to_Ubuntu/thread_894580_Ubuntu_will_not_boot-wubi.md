---
title: "Ubuntu will not boot-wubi"
date: 2008-08-19
forum: New to Ubuntu
---

### Post by MeTylerDurden on 2008-08-19
[SIZE="3"]Hi, I have Ubuntu installed in Windows XP and am getting a <windows>\system32\hal.dll.   please reinstall copy of missing file.    
 I have done all of the fixes and repairs in Recovery mode from the xp cd.  Also have done system restore.   
 I see the hal.dll file loacated in system32 so I don't think that is the problem.
 The only thing I can think that I blundered on was going into windows-temp-and throwing away a bunch of dat files. 
 what do I do to get booting again?[/SIZE]

---

### Post by chrisod on 2008-08-19
Does XP boot normally? I've had the dreaded "missing file" error several times over the years with XP and it's always ended with me doing a complete reinstall of XP.

---

### Post by MeTylerDurden on 2008-08-19
Xp boots fine, only whne I choose Ubuntu.  I think that the communication between xp and Ubuntu is down.  Surely I tossed some valuable file.. at least I keep blaming myself. 
  I thought maybe doing a new wubi install might work ,but dont know if I lose all my work in Ubuntu or if it would install another Ubuntu and leave the old one, or if it would repair it.. i dont know anything - I forgot how to breathe

---

### Post by mlentink on 2008-08-19
> **MeTylerDurden said:**
> Xp boots fine, only whne I choose Ubuntu.  I think that the communication between xp and Ubuntu is down.
Basically, there *is* no communication between XP and Ubuntu, only between the Windows boot-loader and Ubuntu under Wubi.

> **MeTylerDurden said:**
>   Surely I tossed some valuable file.. at least I keep blaming myself. I'm afraid you did. 
I don't know all that much about Wubi, but I seem to remember Wubi stores its virtual partitions in something like .dat files. I sure hope you didn't throw those away, but it does look like it...
Sorry.

---

### Post by MeTylerDurden on 2008-08-19
Where can I get more virtual partitions?

---

### Post by mlentink on 2008-08-19
I don't think I understand your question. Wubi creates virtual partititions when you install Ubuntu through it. Basically, as is my understanding, those virtual partitions are stored in files in the Windows file-system, most likely NTFS. At boot time, the bootloader loads the code necessary to access those partitions-in-files and thus loads Ubuntu.
But if you delete those files, obviously Ubuntu will not be able to boot. It's as if you delete real partitions, or harddrives if you prefer. The bootloader simply won't be able to find your OS anymore.

Now, I not saying that this is what actually happened, although, from your description, it seems likely.

There may be those more knowledgeable about Wubi that are able to assist you better.

---

