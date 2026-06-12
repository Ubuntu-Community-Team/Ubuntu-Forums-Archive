---
title: "[SOLVED] Scripting Help to change file extensions"
date: 2008-11-06
forum: Programming Talk
---

### Post by WWSmith36 on 2008-11-06
Stupid Camera saves all photos with the extension .JPG

I am looking to create a script that would change all the files in a directory with the extension .JPG to .jpg

I know that this is really simple but I have very little scripting experience :(

---

### Post by Emill on 2008-11-06
Just run in the terminal:
rename 's/\.JPG$/\.jpg/' *.JPG

---

