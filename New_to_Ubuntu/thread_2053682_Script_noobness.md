---
title: "Script noobness"
date: 2012-09-05
forum: New to Ubuntu
---

### Post by MarshyTheKid on 2012-09-05
I'm trying to write a script so when I right click on a rar file it will automatically extract it to a folder. 

```
#! /bin/bash/
unrar x -y $f /home/MarshyTheKid/Videos/Share/
#Notify
notify-send -t 3600 $PWD "Finished!"
```

$ sh ExtractToVideos /home/MarshyTheKid/Desktop/random.rar 


Cannot open /home/MarshyTheKid/Videos/Share.rar
No such file or directory
No files to extract



What am I missing here?

---

### Post by Hadaka on 2012-09-06
Hi, I'm not familure with rar or unrar files...i did however take a look at the
man page for unrar...there wasnt a $f option for file extraction, and a simple
right click probably wont activate your script even it if did work. I would suggest
you ask a mod to move this to the programming thread and perhaps someone there
can help you.

---

### Post by MarshyTheKid on 2012-09-06
I posted it there shortly after here once I realized it was better suited there.

Thread here for future reference. [http://ubuntuforums.org/showthread.php?t=2053696](http://ubuntuforums.org/showthread.php?t=2053696)

---

### Post by lordievader on 2012-09-06
Correct me if I am wrong but should the $f variable represent the archive that needs to be extracted? If so, it is empty, that is why unrar complains what he sees is this:
```
unrar x -y /home/MarshyTheKid/Videos/Share/
```
So it complains of not finding any archive.

A correction would be:
```

#!/bin/bash/ 
f="$1"
unrar x -y $f /home/MarshyTheKid/Videos/Share/ 

#Notify 
notify-send -t 3600 $PWD "Finished!"

```

If you have a script and want to pass arguments to it, $1 is the first argument, $2 the second and so on.

Hope this clarifies things for you,
-Lordievader.

---

### Post by sisco311 on 2012-09-06
Duplicate: [http://ubuntuforums.org/showthread.php?t=2053696](http://ubuntuforums.org/showthread.php?t=2053696)

Thread closed.

---

