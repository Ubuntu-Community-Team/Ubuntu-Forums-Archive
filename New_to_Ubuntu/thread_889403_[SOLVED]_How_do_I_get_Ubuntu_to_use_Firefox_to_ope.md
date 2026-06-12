---
title: "[SOLVED] How do I get Ubuntu to use Firefox to open .html files by default?"
date: 2008-08-14
forum: New to Ubuntu
---

### Post by zzzonked on 2008-08-14
Title says it all. Ubuntu is currently giving me a prompt with choices like "display", "open in terminal", "run" every single time I open .html files. Very annoying.

---

### Post by Locutus_of_Borg on 2008-08-14
right click > properties > open with > make sure set as default box is checked

---

### Post by ad_267 on 2008-08-14
Sounds like they might be marked as executable. This sometimes happens if you've copied the files over from Windows. You will need to right click on them and go to properties - permissions and make sure they are not executable.

You can do this for all html files in a directory from the terminal:
```
cd ~/path/to/files
chmod a-x *.html
```

---

