---
title: "How do i clean junk files and temporary internet files?"
date: 2008-06-18
forum: New to Ubuntu
---

### Post by sharks on 2008-06-18
How do i clean junk files and temporary internet files?

---

### Post by kpkeerthi on 2008-06-18
[http://www.ubuntugeek.com/cleaning-up-all-unnecessary-junk-files-in-ubuntu.html](http://www.ubuntugeek.com/cleaning-up-all-unnecessary-junk-files-in-ubuntu.html)

---

### Post by philinux on 2008-06-18
Firefox - tools - clear private data.

When you reboot linux will get rid of it's temporary files.
Linux is not windows as the saying goes.

---

### Post by Absolute-Zero on 2008-06-18
To clean the internet cookies you need to go to your browser options, TOOLS-CLEAR PRIVATE DATA

Fslint - is the progrom to delete junk, duplicates and so on (be careful not to delete your own files such as themes)

---

### Post by MasterSander on 2008-06-18
Ctrl+Shift+Delete in firefox is the shortcut to delete them :P

---

### Post by kpkeerthi on 2008-06-18
Also look in $HOME and $HOME/.config for any residues (hidden folders & files) left behind by programs that you once had but not any longer. 

Another thing you might want to check is the ~/.thumbnails where nautilus caches thumbnails. Take a look at how big this has grown up to now. You may want to clean up unused thumbnails. A good strategy is to keep only recently or mostly used thumbnails and delete others. I usually delete thumnails that are not used in the last 15 days using the following command:
```
find ~/.thumbnails -name "*.png" -atime +15 -exec rm '{}' ';'
```
Perhaps, put this command in your crontab and set it to run once in 15 days.

---

