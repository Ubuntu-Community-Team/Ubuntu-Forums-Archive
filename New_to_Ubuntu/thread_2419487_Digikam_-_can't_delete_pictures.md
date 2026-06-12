---
title: "Digikam - can't delete pictures"
date: 2019-05-22
forum: New to Ubuntu
---

### Post by fernandoribeiro on 2019-05-22
Hello,

I am running digikam 5.6.0 in ubuntu. I can't delete any pic (displays message couldn't move image blabla to collection trash". 

Console displays:

digikam.database: Deleting files: (QUrl("file:///home/fernando/Pictures/por organizar/novas/P4262376.JPG"))
digikam.general: Got image deletion notification from ImageViewUtilities for  1  images.
digikam.general: Using  4  CPU core to run threads
digikam.general: Action Thread run  1  new jobs
digikam.iojob: DELETING:  "/home/fernando/Pictures/por organizar/novas/P4262376.JPG" 
 FILE EXISTS?  true 
 IS TO TRASH?  true
digikam.iojob: DTrash: Image album root path: "/home/fernando/Pictures"
digikam.iojob: Trash folder for collection:  "/home/fernando/Pictures/.dtrash"
digikam.general: Event is dispatched through a passive pop-up
QLayout: Attempting to add QLayout "" to QWidget "", which already has a layout
digikam.iojob: Thread Finished
digikam.general: One job is done
digikam.metaengine: Exiv2 ( 2 ) :  Directory OlympusCs, entry 0x0101: Strip 0 is outside of the data area; ignored.

Now  i must confess two things. First i am new to linux, and second, this  came after i messed around. First I had a problem, my disk was almost  full so i understood that images were not being properly deleted. Then i  ended up surfing around all corners of google to find out a solution  "digikam sudo rm ~/.local/share/Trash/metadata" that solved the problem.  But now i can't remove pictures anymore. Supposedly a new metadata file should be created after the old one was deleted and as soon as i delete a new file after this process, but it didn't happen. Perhaps i can just create a new metadata file? If so, what should be in it? Sorry if this has been  answered, but i tried several things already and this is my last resort.  Thanks in advance!

PS: I followed this post [https://forum.kde.org/viewtopic.php?f=66&t=88418](https://forum.kde.org/viewtopic.php?f=66&t=88418) but no new metadata file was created. I must also say that I can delete files outside digikam.

---

### Post by LwIh%*7 on 2019-06-03
See: [https://ubuntuforums.org/showthread.php?t=970285](https://ubuntuforums.org/showthread.php?t=970285)

Someone posted a similar problem and it seemed to have been solved on that thread.

---

