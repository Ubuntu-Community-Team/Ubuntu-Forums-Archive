---
title: "[SOLVED] Where do deleted (Samba) files go? [WinXP]"
date: 2008-05-27
forum: New to Ubuntu
---

### Post by BassKozz on 2008-05-27
I have an extra disk on my machine that is mounted under **/media/extra_storage**, w/in that I have a folder called **/work** that I SAMBA share to a WinXP machine.  I have that **/work** directory mounted on my WinXP machine.

What happens when I delete a file from that shared **/work** directory while on my WinXP machine?  The file didn't end up in my WinXP Recycling Bin :confused:

I checked **/media/extra_storage/.Trash-user** but it's not there, and there isn't a trash folder under **/media/extra_storage/work/**
Does it just immediately get erased? Is there a way to force SAMBA to first dump the files to **/media/extra_storage/.Trash-user** or something like that?

---

### Post by Oldsoldier2003 on 2008-05-27
> **BassKozz said:**
> I have an extra disk on my machine that is mounted under **/media/extra_storage**, w/in that I have a folder called **/work** that I SAMBA share to a WinXP machine.  I have that **/work** directory mounted on my WinXP machine.

What happens when I delete a file from that shared **/work** directory while on my WinXP machine?  The file didn't end up in my WinXP Recycling Bin :confused:

I checked **/media/extra_storage/.Trash-user** but it's not there, and there isn't a trash folder under **/media/extra_storage/work/**
Does it just immediately get erased? Is there a way to force SAMBA to first dump the files to **/media/extra_storage/.Trash-user** or something like that?

Files saved on a samba server don't go to the trash bin when you delete them, they are deleted. (you should have received a confirmation dialog with this information and asking you if you wanted to proceed)  If the files are critical and you don't have a backup you could try running photorec or some other recovery utility to recover the file if the data has not yet been overwritten.

---

### Post by oedha on 2008-05-27
as far as i know.....and based on mine
when you're on XP and delete that network storage files....they will gone ( my problem too :) )
when you're on ubuntu and do the deletion......the deleted files will be hidden on .Trash-username folder ( this can be restored )

---

### Post by Oldsoldier2003 on 2008-05-27
if the files were deleted remotely then yep, they are indeed gone. In my post above I just assumed that it was done remotely since the files would have been in his trash bin if he did it locally on the samba server.

---

### Post by BassKozz on 2008-05-28
> **oedha said:**
> as far as i know.....and based on mine
when you're on XP and delete that network storage files....they will gone ( my problem too :) )
when you're on ubuntu and do the deletion......the deleted files will be hidden on .Trash-username folder ( this can be restored )

> **Oldsoldier2003 said:**
> if the files were deleted remotely then yep, they are indeed gone. In my post above I just assumed that it was done remotely since the files would have been in his trash bin if he did it locally on the samba server.
Thanks for the info guys,
Is there a way to setup/force the SAMBA server to move files deleted remotely into the **/.Trash-username/** directory instead of deleting them permanently?
Thanks again,
-BassKozz

---

### Post by BassKozz on 2008-05-28
> **BassKozz said:**
> Thanks for the info guys,
Is there a way to setup/force the SAMBA server to move files deleted remotely into the **/.Trash-username/** directory instead of deleting them permanently?
Thanks again,
-BassKozz

Guess not :confused:

---

### Post by BDNiner on 2008-05-28
I don't believe so. Windows will always permanently delete files that are contained on a network share. you would have to use an undelete software to recover the files. I use freeundelete but i don't think it will work on linux partitions, i have only used it to recover files from NTFS network shares.

---

### Post by H.Callahan on 2008-05-28
> **BassKozz said:**
> Thanks for the info guys,
Is there a way to setup/force the SAMBA server to move files deleted remotely into the **/.Trash-username/** directory instead of deleting them permanently?
Thanks again,
-BassKozzAs has been noted, this is Windows behavior, not a behavior of the SAMBA server.  Anything Windows deletes on a non-local drive are permanently deleted (at least as much as Windows permanently deletes anything).  Vigilance and recovery software are about the only options.

---

### Post by Cadmus on 2008-05-28
There's a link here about a samba recycle bin a few posts down

[http://ubuntuforums.org/showthread.php?t=155763](http://ubuntuforums.org/showthread.php?t=155763)

Not tried it myself, bt the reasoning seems sound, anything removed from a samba share goes into a recycle bin on the share.

---

