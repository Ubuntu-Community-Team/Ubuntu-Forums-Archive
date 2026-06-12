---
title: "still havign issues after the move"
date: 2008-08-18
forum: New to Ubuntu
---

### Post by gatordoc on 2008-08-18
I have done as suggested by folks (reseat ram ..etc) it doesnt seem to be a hardware issue. 

I can log into the failsafe terminal where i changed what I coudl think of from my previously hard-lined configuration (I had a dedicated IP, from a closed network)

I figured out that the gnome interface may not be working and I found a thread where it said 
--------------------------------------------------------------------------------

Try deleting all the .gnome .gnome2 .gconf .gconfd folders in your home directory.

--------------------------------------------------------------------------------

I have no idea where this stuff is located so I couldnt try it. I found a gnome folder in /etc and a gconf folder there as well but I did not delete anything.

Thanks for the help ubuntu community

---

### Post by finer recliner on 2008-08-18
please continue on your original thread, so other users know what you are talking about:

[http://ubuntuforums.org/showthread.php?t=890960](http://ubuntuforums.org/showthread.php?t=890960)

---

### Post by aloshbennett on 2008-08-18
Your .gnome .gnome2 etc would be present under /home/<your username>

To delete them, try this on a terminal
> 
figo@zion$ cd
figo@zion$ rm -rf .gnome .gnome2 .gconf .gnofd


Leave the /etc folders alone :)

PS: Please be careful what you are deleting when you use 'rm -rf'

---

### Post by ajgreeny on 2008-08-18
If I were you I would use nautilus to rename these folders rather than remove them, just in case they may be useful again.  Open nautilus, hit Ctrl+H to show hidden files and folders and then navigate to the hidden folders (all folders and files with names starting with a **.** eg **.gconf** are hidden by default)  Just rename them as .gconfbak or .gconf~ etc etc. and then logout and back in again.

---

### Post by finer recliner on 2008-08-18
mods please remove this thread, or merge it with 
[http://ubuntuforums.org/showthread.php?t=890960](http://ubuntuforums.org/showthread.php?t=890960) 

@ajgreeny: please read the original thread to catch up with the discussion. thanks for the input though.

---

