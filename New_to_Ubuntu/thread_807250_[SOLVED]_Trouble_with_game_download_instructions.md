---
title: "[SOLVED] Trouble with game download instructions"
date: 2008-05-25
forum: New to Ubuntu
---

### Post by SteveNorman on 2008-05-25
I am trying to download the Linux version of the game Fighter ace..
The link to the download instructions are here:
[http://linux.ketsujin.com/index.php?option=com_content&task=view&id=19&Itemid=35](http://linux.ketsujin.com/index.php?option=com_content&task=view&id=19&Itemid=35)

I cant get tarball to unpack, I get this: 

$ tar -jxvf PATH_TO/FighterAce-3.x-112.i386.tbz2
tar: PATH_TO/FighterAce-3.x-112.i386.tbz2: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
tar: Child returned status 2
tar: Error exit delayed from previous errors

I dont know enough to deviate from the instructions,,can this game be downloaded in Ubuntu?

---

### Post by tim_wright on 2008-05-25
Why not jus double click the file which will take you to the archive manager and hit extract? Its a much simpler way for those who are new to linux.

---

### Post by Maestro23 on 2008-05-25
Download to you Desktop?

> cd Desktop

ls (should see the file)

tar -xvf FighterAce-3.x-112.i386.tbz2


Then just continue with the step-by-step instructions on the site.

---

### Post by SteveNorman on 2008-05-25
got it to extract, but all of the other instructions are met with no such file or directory replies

after extraction, I get a file called opt,,
I cd into it to do the other instructions right?

---

### Post by SteveNorman on 2008-05-28
Got it solved here: [http://ubuntuforums.org/showthread.php?t=807244](http://ubuntuforums.org/showthread.php?t=807244)
 in case anyone cares

---

