---
title: "save pics in Gimp"
date: 2008-05-18
forum: New to Ubuntu
---

### Post by NHAUN on 2008-05-18
I've recently installed 8.04 and need help with saving downloaded pics from Windows files in GIMP after I've cropped,etc.   I keep getting this message "jpg' failed   Permission Denied

Do I need to activate GIMP, or download something to read my pics?

---

### Post by jimmy the saint on 2008-05-18
If you are talking about editing files that are stored in your windows partition and then saving them back to the windows partition, it is likely that you do not have write permission on that particular partition.  
If this is the case, rather than granting write permission to that system partition, it might be good to move your pictures to a new partition set aside for storage.  This will ensure that you can do whatever you want to your files, from either OS, and not risk doing something that would damage your windows installation by mistake.

---

### Post by NHAUN on 2008-05-19
Thank you for your response.  

I do not have windows partition.  I deleted it completely when loading ubuntu.  So, perhaps I need to attempt to download, from my camera some pics and try to work with gimp and see how it goes for me. 

At this point I cannot seem to get my canon printer working either - it's a steep learning curve - but good for my brain.  :)  

If you have any other suggestions - feel free to reply.  I'm open to anything.

---

### Post by spupy on 2008-05-19
What is the format of these Windows pictures you have? And where are they located?

---

### Post by The Cog on 2008-05-19
Are you trying to save over the original files, and are these files read-only? They might be read-only if you read them from an NTFS partition, windows share or a CD-ROM. See if they're read-only by right-clicking and choosing Properties->Permissions. Try saving as a different filename (or in a different folder).

---

### Post by Crossroads on 2008-05-19
,,, or just open GIMP,start an empty picture and draw anything on it.

Then try to save it.
What folder are you trying to save to?
As The Cog said, try a different folder too - say, Documents

---

