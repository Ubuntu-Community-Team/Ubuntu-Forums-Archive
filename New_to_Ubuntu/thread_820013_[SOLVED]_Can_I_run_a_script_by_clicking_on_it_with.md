---
title: "[SOLVED] Can I run a script by clicking on it without being asked if I want to displa"
date: 2008-06-05
forum: New to Ubuntu
---

### Post by MiniMe on 2008-06-05
Hello,

I've written a very small script.

I gave it execute permissions under the file properties -> permissions tab. Whenever I click on the file I'm prompted "Do you want to run "filename", or display its contents?" I'd like to always run the file. Is there a way I can avoid clicking "run" when prompted and have the file always run when I click it?

I doubt the specifics of the script matters just in case: I created the script to kill wineserver because sometimes it consumes 100% of my cpu. 
[https://bugs.launchpad.net/ubuntu/+source/wine/+bug/205895](https://bugs.launchpad.net/ubuntu/+source/wine/+bug/205895)

The file contains:

#!/bin/bash
kill -9 `pidof wineserver`
kill -9 `pidof IEXPLORE.EXE`

Any help would be appreciated. Thank you in advance.

---

### Post by utsuprainfra on 2008-06-05
you could create a launcher by right clicking on the desktop and specifying

/bin/bash /path/to/script 

as the command.

---

### Post by iaculallad on 2008-06-05
In nautilus window go to edit->preferences, under the "behavior"  tab, there are options for "Executable text files".

---

### Post by jpeddicord on 2008-06-05
> **iaculallad said:**
> In nautilus window go to edit->preferences, under the "behavior"  tab, there are options for "Executable text files".

More specifically, you want **Run executable text files when they are opened**.

---

### Post by MiniMe on 2008-06-05
Thanks all! Much appreciated.

---

