---
title: "[SOLVED] Can't copy many files to cd"
date: 2008-08-14
forum: New to Ubuntu
---

### Post by japhyr on 2008-08-14
Hello,

I have enjoyed ubuntu for several months now without bothering to back anything up.  This morning I started backing up some data.  I burned a couple dvd's and a cd.  I load a blank disc, and an icon appears on the desktop.  I open nautilus, and drag the folders I want to the disc icon.  I then double click the disc icon, and click "Write to Disc".  I get a dialog in which I can rename the disc, and start writing.  Each time, it shows a status bar and writes the disc in 2-10 minutes, depending on the amount of data.  I successfully burned a disc containing a number of folders which held 600+ pictures.

I am trying to back up a programming folder.  It has a large number of files in it, about 3000, but the total size is just over 50mb.  When I drag this folder to the blank disc icon, I get a message that files are being copied to the blank disc (I assume references, not actual files).  When I double click the blank disc icon, I see the files and the "Write to Disc" button.  I click the "Write to Disc" button, and I can name the disc.  When I click the final "Write" button, a dialog flashes on the screen, but disappears faster than I can read it, and nothing seems to happen.

Any idea why the files are not being written?  Any way to see any errors that are being generated in the process?

---

### Post by japhyr on 2008-08-14
Bump.  I tried using a dvd, and got a message "Unhandled Error: Aborting" when I clicked "Write".  Any ideas?

---

### Post by mevets on 2008-08-15
Try running
```

nautilus-cd-burner

```
from the terminal. It might give you some useful output that you dont get from the gui.

---

### Post by japhyr on 2008-08-15
I can't find any instructions for using nautilus cd burner from the command line.  I type "nautilus-cd-burner" at the terminal prompt, and it says "unable to write cd/dvd - no files selected".  How do I specify which folder/ files I want to burn from the command line?

---

### Post by mevets on 2008-08-15
You should open nautilus and drag files onto the disc first as you did before. Then you can run nautilus-cd-burner.

---

### Post by japhyr on 2008-08-15
Thanks for the help.  I get a whole bunch of this line:
```
(nautilus-cd-burner:24411): GLib-CRITICAL **: g_error_free: assertion `error != NULL' failed

```

and the final output is:
```
** (nautilus-cd-burner:24411): WARNING **: Unable to prepare tracks for burning

```

Does that point to anything in particular?

---

### Post by japhyr on 2008-08-15
I updated my system, restarted, and tried again with the same results.  My write speed choices are maximum possible, 28.2x, 18.8x, and 9.4x.  I tried at maximum possible and at 9.4x, with the same results.  Any new ideas?

---

### Post by LowSky on 2008-08-15
try using a different program like Gnomebaker or k3b

---

### Post by japhyr on 2008-08-15
Thanks for the suggestion.  I tried gnomebaker, and got an error that the directories were too deep (max 6 levels!).  I tried k3b, and as installed it did not balk at the directory depth.  Success!  Thank you everyone.

---

