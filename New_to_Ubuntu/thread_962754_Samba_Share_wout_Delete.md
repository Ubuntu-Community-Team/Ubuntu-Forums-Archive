---
title: "Samba Share w/out Delete?"
date: 2008-10-29
forum: New to Ubuntu
---

### Post by BassKozz on 2008-10-29
Is it possible to setup a Samba share with read/write privileges but without a DELETE privilege?

I am setting up a share for my work where multiple users can save/edit/read/write to it, but I would like to remove the ability to DELETE.  Is this possible.

Server = Ubuntu Desktop 8.04
Clients = Multiple - WinXP Sp3 machines

---

### Post by ethoxyethaan on 2008-10-29
If you allow them to "write" content it automatically allows them to remove content. 

example:

a file called TEST.txt is in your shared drive, users are allowed to alter the document (chmod 6) they can just "edit" that file and make it blank.


I don't think its possible and even if it is users can still vandalize it.

---

### Post by BassKozz on 2008-10-29
> **ethoxyethaan said:**
> If you allow them to "write" content it automatically allows them to remove content. 

example:

a file called TEST.txt is in your shared drive, users are allowed to alter the document (chmod 6) they can just "edit" that file and make it blank.


I don't think its possible and even if it is users can still vandalize it.

Good point... ok let me rephrase then;
Write/Read privileges without Edit/Delete ?
Write = ONLY CREATE NEW FILES not modify current/existing ones

---

### Post by Nepherte on 2008-10-29
I don't think that's possible. Both edit and create are linked to the write permission.

---

### Post by BassKozz on 2008-10-29
> **Nepherte said:**
> I don't think that's possible. Both edit and create are linked to the write permission.

Makes Sense... Bummer :(

---

### Post by Coreigh on 2008-10-29
In Windows you CAN set permissions to be able to add and edit files without deleting files. Is this a Windows share you are accessing from a Linux computer? Or a Samba share on a Linux computer you are accessing from a Windows computer?

---

### Post by BassKozz on 2008-10-29
> **Coreigh said:**
> In Windows you CAN set permissions to be able to add and edit files without deleting files. Is this a Windows share you are accessing from a Linux computer? Or a Samba share on a Linux computer you are accessing from a Windows computer?
Linux Share accessing on a WinXP computer

...


**_Update_**
I found this thread: [http://www.linuxquestions.org/questions/linux-software-2/samba-share-with-write-but-not-delete-223222/](http://www.linuxquestions.org/questions/linux-software-2/samba-share-with-write-but-not-delete-223222/)

They made mention of ```
create mode = 555
```

Would this work?

---

### Post by Coreigh on 2008-10-29
I may be mistaken here but I think to make a folder accept adds/edits but no deletes you have to modify the NTFS permissions on the Windows share. This probably won't work at all on XP Home and on Pro or Server you will need admin permissions at least to that folder to make changes.

I could not quickly find a how-to link for you but essentially you want to allow read/write permissions and specifically deny the delete. This is usually in an advanced tab. And this can be applied based on specific users or groups of users *in the windows environment* So you will need to have a Windows user or group that Samba is connecting as.

I know it sounds complicated but that is only because I am glazing over several steps. Admittedly this is probably not a beginner topic.

---

