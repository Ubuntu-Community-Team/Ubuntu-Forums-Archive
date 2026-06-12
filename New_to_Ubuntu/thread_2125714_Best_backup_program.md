---
title: "Best backup program?"
date: 2013-03-14
forum: New to Ubuntu
---

### Post by stevebond001 on 2013-03-14
Hi
Can anyone please suggest a decent backup program to use?  I need to take the following into account:
1. I have a NAS which hosts some files.  I want to back these files up to a folder on my local drive.
2. I can connect (through Nautilus) to the SMB share where these files are located, but all of the backup programs I have tried seem to have problems with accessing a SMB share.
3. I want the program to be able to copy just the changed files (i.e. incremental)
4. I don't want the backup to be tarred, zipped, etc - I just want a copy of the file on the NAS in a folder on my PC.
5. As I will run the backup manually, I will mount the share manually before backing up - therefore the program doesn't have to.


I have tried quite a few programs now and all of them have failed (as I can't seem to put the SMB path in as the source - I have to point to the mount point, which is where the problems start)  the programs include:
Lucky backup
deja dup
freefilesync
even good old cp command (which used to work fine in earlier versions of Ubuntu, but don't want to work in this version 12.10)

Either I'm missing something really basic, or there is a gap in the market for a good backup program.

Any assistance would be gratefully received, as this is driving me mad 

Thanks

---

### Post by r-senior on 2013-03-14
Have you considered rsync?

[https://help.ubuntu.com/community/rsync](https://help.ubuntu.com/community/rsync)

---

### Post by stevebond001 on 2013-03-14
Hi
Thanks for the response
I have installed rsync (grsync), but when I try to set the source folder (i.e. the SMB share on my NAS) I have to find the mount point.  After some searching I've found it at /run/user/"User Name"/gvfs/"smb-share,server-nas,share=files,.......etc".
When I try and set this as the path (by browsing) the window just freezes when I try to drill down the SMB share folder structure.  This happens on my PC and Laptop, so I know it's not a problem unique to my PC or Laptop.  I'm suspecting that there is a bug in Ubuntu preventing me from doing this, as this symptom is present in other backup programs as well. btw I can open Nautilus and browse to the SMB share and see all the folders / files, so I know the share is OK.

Any additional help would be gratefully received.

Thanks

---

### Post by Zill on 2013-03-15
stevebond001:  I use luckyBackup here on my systems and it works very well but as I only use Linux systems I do *not* use SMB but NFS.  However, a quick web search reveals that you *should* be able to get luckyBackup working with your NAS via SMB - you just need to mount it properly. ;-)

I suggest the following thread might be of assistance and, in particular, the response from Loukas Avgeriou dated 2011-02-24 seems to be relevant to your problem.  Note that Loukas is the developer of luckyBackup and so his advice should be very valuable!

[How do I backup to my NAS]("http://sourceforge.net/p/luckybackup/discussion/873564/thread/3d7891a1")

ps.  I realise that this thread is regarding backup *to* the NAS.  However, luckyBackup works *both* ways and so your requirement should work equally well once you get the NAS correctly mounted.

---

### Post by stevebond001 on 2013-03-15
Thanks very much for the information.  I have tried both of these and they both sort of work.  Long story, but I appear to be having a problem with copying from my NAS to linux PCs - don't know if it's due to the SAMBA client installed on the NAS, or something else.  But as soon as I have it sorted I will be back to finish this off.

Thanks once again

---

