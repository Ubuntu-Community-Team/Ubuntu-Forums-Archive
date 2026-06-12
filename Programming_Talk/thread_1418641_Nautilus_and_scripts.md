---
title: "Nautilus and scripts"
date: 2010-02-28
forum: Programming Talk
---

### Post by oakgrove on 2010-02-28
I have a little python script: 
```

#!/usr/bin/env python

import sys,os           

args=sys.argv[1:]

for file in args:
        os.system('xterm -e "mp3splt -t 74.00 %s -d $HOME"' % file)

```

Now, the script works great, and does what it looks like it does; I just right click on an mp3 and tell nautilus to open the mp3 with this script and it splits it into 74 minute segments.  The only thing is, if I select multiple files, it starts a new script for each file.  IOW, it doesn't actually use the loop in the script to go through each file one by one.  It starts a complete new instance of the script for each file so, in effect, doing every file I select at the same time.

This isn't really so bad but, I would really like to know how to tell nautilus to just append each file as an argument and run the script once and just let the loop inside of the script handle the rest.  

Any help would be appreciated.

SOLUTION

I was running my script on the files from the "open with" menu as opposed to just having the script in the $HOME/.gnome2/nautilus-scripts directory. When you use the "open with" menu, it actually creates a new instance of your script for each file. When you use the "scripts" menu in the right click dialog, that's when it passes all of the selected files as arguments.

---

### Post by geirha on 2010-03-01
Been a while since I messed around with nautilus scripts, but I seem to remember it passes the files in environment variables, so make a test script that just prints os.environ to a file.

---

### Post by ssam on 2010-03-01
you could look how g-scripts do it
[http://g-scripts.sourceforge.net/](http://g-scripts.sourceforge.net/)

---

### Post by oakgrove on 2010-03-01
Thanks very much for the replies on this. 

I figured out what the issue was.  I was running my script on the files from the "open with" menu as opposed to just having the script in the $HOME/.gnome2/nautilus-scripts directory.  When you use the "open with" menu, it actually creates a new instance of your script for each file.  When you use the "scripts" menu in the right click dialog, that's when it passes all of the selected files as arguments.  

That's interesting.  I always thought the scripts thing was redundant as it seemed to just duplicate the open with.  Now, seems it treats things a little differently than I thought.  That would explain some unexpected behavior I experienced in the past with this.

---

