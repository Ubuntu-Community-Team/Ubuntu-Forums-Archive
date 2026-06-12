---
title: "Unable to mount volume D ????"
date: 2008-05-07
forum: New to Ubuntu
---

### Post by Delawaredave on 2008-05-07
Have Ubuntu and Windows installed as dual boot.   Windows OS is corrupted and I can't fix - Windows chkdsk runs and then hangs

So I am using Ubuntu and love it.  Trying to access drive D and get the following error:

"Unable to mount...mount is denied because NTFS is marked to be in use.... you can use the 'force' option for your own responsibility.  Type on command line:

mount -t ntfs- 3g /dev/sda5 /media/d -o force

What does above mean ?  Should I try this command ?  My My Documents is on this D drive -- so I'm trying to salvage.

Thanks !!!

---

### Post by prshah on 2008-05-07
> **Delawaredave said:**
> Have Ubuntu and Windows installed as dual boot.   Windows OS is corrupted and I can't fix - Windows chkdsk runs and then hangs

"Unable to mount...mount is denied because NTFS is marked to be in use.... you can use the 'force' option for your own responsibility.  Type on command line:

mount -t ntfs- 3g /dev/sda5 /media/d -o force


As suggested, you can use the "-o force" option, on your own responsibility. This is NOT the first action I would recommend. There is a very real chance of losing your files.

You can get a live windows CD (such are availible, but I don't think they are legally allowed), or run a recovery console using the XP CD, and then run chkdsk/f on your drive. Let it complete.

If it doesn't complete and you have no choice, you can try the force option for ubuntu's mount command.

Note that if chkdsk hangs, I suspect bad blocks (bad sectors), in which case it's (usually) time to change the drive.

---

### Post by OldTimeTech on 2008-05-07
Also in Ubuntu...go to synaptic package manager and search for the ntfs-3g in the repositories and load that....

With that application/driver, you should then be able to read the data on the windows side.

---

### Post by AndrewTheArt on 2008-05-07
Yes, just run that from a terminal. You might or might not need to type "sudo" before it for super permissions. If the regular command doesn't work try 

```
sudo mount -t ntfs- 3g /dev/sda5 /media/d -o force
```

Just a small note, this wouldn't normally happen, it's just because you're NTFS drive is corrupt. Normally, you would not need the command line for this :)

---

### Post by Delawaredave on 2008-05-08
Thanks a bunch !  I do think it is a "failing" hard drive.

Running Ubuntu, I can now "see" the Windows folders I want to keep.

Question:  using Ubuntu to copy a Windows My Documents folder to an external drive, **can I be assured that all the files will copy correctly and remain intact ?**

So non-Linux files (like Excel and Word) will copy OK to external drive using Ubuntu ?

As I "rescue" these Windows folders with Ubuntu, I just want to make sure that all will copy.

Thanks !

---

### Post by bumanie on 2008-05-08
Everything will copy fine as long as the files/folders you are copying are not on suspect/corrupted parts of the drive. That is something neither you nor anyone else can tell!! You could look up dd rescue and try that, it's very good at retrieving as much as is possible to recover, but difficult to understand if you are new to linux.

---

### Post by glennric on 2008-05-08
Everything should copy fine as long as they are not corrupted on the drive to begin with.  Linux can deal with any windows file, they are still just files.  You can even open the files you referenced in linux with OpenOffice.

---

