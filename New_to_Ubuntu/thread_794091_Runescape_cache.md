---
title: "Runescape cache"
date: 2008-05-14
forum: New to Ubuntu
---

### Post by shleyman on 2008-05-14
everytime i open the runescape game i get this error message:
```
Error_loader_nocache - Unable to create cache directory.
Runescape was unable to find a suitable place to store its temporary files. To solve this please either:

# Login to your computer as an 'administator' user, and then try loading RuneScape again. This should give it sufficient access to create its temporary cache.

# Or, create a new directory called c:/rscache or /rscache. If possible, set that directory to have full read+write permissions so that all users can write to it. Runescape should then detect that directory and use it for its files.

# If you are unable to do either of the above, then as a last resort you can tell RuneScape not to store any files on the harddisk. When entering the site and choosing between high-detail/low-detail also select 'Unsigned Applet Using Default Java' from the dropdown scroll at the bottom of the detail select page. You will need to do this everytime you load the game. The disadvantage of this is the game will load slower, so if possible use one of the top two solutions instead.

If problems persist then please refer to our technical FAQ which can be found in the FAQ section of our website. 
```

what can i do to solve this?

thanks!!

---

### Post by Joeb454 on 2008-05-14
What happens if you manually create the directory in your home folder called rscache?

Or from a terminal do ```
mkdir rscache
``` that will do it in the correct place (hopefully).

And are you running it from the web? Or from a standalone application?

---

### Post by shleyman on 2008-05-14
from the web
i was goign to create a directory but in new to linux so i wouldnt know where to put it...
thanks

---

### Post by aaaantoine on 2008-05-14
According to the instructions, they want it to be in the root directory ("/rscache").

When I tried to play this game I had the same issue.  I thought it was preposterous to put a directory for a single program at such a high level of the folder tree.  Even in Windows this program behavior has always bugged me, but in a Linux OS it's worse.

Then again, I bet those instructions are for Mac OS X users.

---

### Post by psylem on 2008-07-10
Try this thread...

[http://ubuntuforums.org/showthread.php?t=600822&page=3](http://ubuntuforums.org/showthread.php?t=600822&page=3)

it could be the icedtea java plugin causing this problem.

---

