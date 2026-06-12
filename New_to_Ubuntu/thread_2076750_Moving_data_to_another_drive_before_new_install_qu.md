---
title: "Moving data to another drive before new install question."
date: 2012-10-26
forum: New to Ubuntu
---

### Post by mikodo on 2012-10-26
Hi,

I need to move my stuff, to another drive before installing a new drive and OS (Xubuntu 12.04). Yes, I regularly backup my ~/ with an app called Back in Time. I don't want to back up my whole home, as I don't want my dot files and such anymore, with the new install.

I know how to backup and restore my FF and TB profiles, now. What's left are the files and folders in my ~/ that I want. Copy and Pasting my Documents, works just fine, I find.

I have 48.3 Gb of Music I want to Copy and Paste to the backup, too. I know people use TAR and Rsync for stuff like this, but keeping it simple with Copy and Paste, is probably best for me.

**Question**:

Is there anything wrong with using Copy and Paste, of 48.3 Gb of Music to another drive (attached USB Drive), to achieve good results for backup and restore?

Thanks.

---

### Post by pqwoerituytrueiwoq on 2012-10-26
it will take longer than rsync, unless you skip existing files witch will not backup updated metadata, this will also result in duplicates if you rename something unlike rsync
this is the command i used up update my ipod
```
rsync -av --delete ~/Music/ /media/ipod/Music/
```
(i soft moded my ipod shuffle, i can have my music anywhere and use any file name)

---

### Post by newb85 on 2012-10-26
I wouldn't see a problem with that approach.  In general, when copying files like this, you might want to do it in a way that preserves the time stamp and permissions.

Also, it will save you some headaches if you make sure to use the exact same user name on your new machine.  Capitalization matters!

---

### Post by mikodo on 2012-10-26
> **newb85 said:**
> I wouldn't see a problem with that approach.  In general, when copying files like this, you might want to do it in a way that preserves the time stamp and permissions.

Also, it will save you some headaches if you make sure to use the exact same user name on your new machine.  Capitalization matters!Yes, I will use exactly the same one user name as I have now.

Does coping and pasting, preserve time stamp and permissions, automatically, or will I have to do it by command line with cp and arguments?

Thanks.

---

### Post by newb85 on 2012-10-26
GUI copy and paste?  Don't think so, but I'm not sure.  Why don't you do a quick experiment?

---

### Post by pqwoerituytrueiwoq on 2012-10-26
if you are just backing your files (/home/$USER/*) up to a empty drive for a clean install
using the gui copy/paste is perfectly fine
not so much for cloning a drive though

---

### Post by mikodo on 2012-10-26
> **newb85 said:**
> GUI copy and paste?  Don't think so, but I'm not sure.  Why don't you do a quick experiment?Good idea. I GUI copied and pasted my /documents to the external drive, and then to my /desktop from the backup, and all three have the same time stamps and perms (original, backup on ext. drive and the desktop. So, I guess the Time Stamps and Permissions are preserved this way.

Don't know if I can do this kind of copying with such a big file as my compressed Music file though. I guess I can try that too, but that would be a long experiment backing it up, then copying it somewhere to see if everything worked ...

Thanks.

---

### Post by mikodo on 2012-10-26
> **pqwoerituytrueiwoq said:**
> if you are just backing your files (/home/$USER/*) up to a empty drive for a clean install
using the gui copy/paste is perfectly fine
not so much for cloning a drive thoughThanks for your help.

Basically, what I would do with the GUI copy and paste, is copy it (the large Music file), to a partition on my external drive, then copy it back to my new install, on the new internal drive. 

Sound OK?

---

### Post by mikodo on 2012-10-26
Well, I just GUI copied and pasted one file of Music (40 songs), to a test backup on the external drive partition. Then copied that, to the desktop. Everything worked, the songs played from each. I did notice tho, that the time stamps changed each time, when I checked the properties. 

Below is a screenshot of clicking the properties of the files, from left to right:

1. The original from ~/Music file.
2. From the copied file to my external drive partition.
3. From the file copied from my external drive partition to my desktop.

It seems to work fine, with just the time stamps not the same (I don't know if this is important or not).

Thanks. -> I'm going for supper.

---

### Post by mikodo on 2012-10-27
Well, 48.3 Gb of music copied to my USB partition through GUI copy and paste, just fine. Plays well. It took just 29 minutes for it all.

Thanks.

---

