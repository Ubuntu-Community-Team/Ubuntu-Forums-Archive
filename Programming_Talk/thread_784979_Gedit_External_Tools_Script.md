---
title: "Gedit External Tools Script"
date: 2008-05-07
forum: Programming Talk
---

### Post by pmaconi on 2008-05-07
I am trying to configure the gedit external tools plugin to use g++ to compile a program and then execute it. Right now, I have it so that it builds correctly, but whenever it tries to execute it gets a segmentation error. I'm not sure why this problem occurs or what I can do to fix it. Any ideas?

Build Script:
> g++ "$GEDIT_CURRENT_DOCUMENT_PATH" -o "${GEDIT_CURRENT_DOCUMENT_PATH%.*}"

Run Script:
> "${GEDIT_CURRENT_DOCUMENT_PATH%.*}"

---

### Post by pmaconi on 2008-05-07
I got this to work somewhat by changing my run script to: 
> xterm -hold -e "${GEDIT_CURRENT_DOCUMENT_PATH%.*}"

However, I would rather use gnome-terminal. As far as I can tell, the following script should work:
> gnome-terminal -x "${GEDIT_CURRENT_DOCUMENT_PATH%.*}"
But about half the time, the terminal starts running whatever my program is and then locks up.

---

