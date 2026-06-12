---
title: "Running apktool.jar"
date: 2013-05-19
forum: New to Ubuntu
---

### Post by eduardoB on 2013-05-19
I have fixed inability to run jar but now cannot figure out how to create permission for it to write files to subfolder. I'm getting permission denied error even though the apktool folder is in my home/eduardo folder. I set root (gksu nautilus) but that didn't seem to help.

---

### Post by eduardoB on 2013-05-25
Found a video on YouTube that did what no other web site search could -- solved issue. Using instructions for chown and chmod and placing files in usr/local/bin, I resolved issue of running apktool.jar and even signapk.jar.

---

