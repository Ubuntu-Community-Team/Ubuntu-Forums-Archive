---
title: "How can I delete many similar files in diferent directories?"
date: 2008-05-28
forum: New to Ubuntu
---

### Post by rs2k on 2008-05-28
I was able to go to my images directory and use "find . -type d -exec chmod 777 '{}' \;" to change all of my images child directories to 777.

How can I delete all images within the same directories that are titled like so: "*.jpg.thumb_*.jpg"

I know it's a fairly simple command, but I am not very good with Linux commands, yet.

---

### Post by Helgiks on 2008-05-28
find ./ -type f -name "*.jpg.thumb_*.jpg" | xargs rm -iv

If you only wan't to execute this in one directory, i.e. only in ./ and not recursive through subdirectories you can use

find ./ -maxdepth 1 -type f -name "*.jpg.thumb_*.jpg " | xargs rm -iv

Or adjust the maxdepth value to your likings.

P.S. The rm -iv is just for security, you can also use

find ./ -type f -name "*.jpg.thumb_*.jpg" | xargas -i echo "rm {}"

to see what will get delete, and if you're satisfied than go ahead with 

find ./ -type f -name "*.jpg.thumb_*.jpg" | xargas rm -v

This is better if you have allot of files, so you won't have to spend long time pressing 'y' to allow it to delete each file.


BTW: You can also use the '-exec' argument to find instead of xargs. Than it would be like

find ./ -type f -name "*.jpg.thumb_*.jpg" -exec rm -v '{}' \;

Does the same as the above.

---

### Post by Victormd on 2008-05-28
```
find . -name '*.jpg.thumb_*.jpg' -delete
```
note the is between apostrophes ('), not quotes (")

I had the same question a few days ago here
[http://ubuntuforums.org/showthread.php?p=5059497#post5059497](http://ubuntuforums.org/showthread.php?p=5059497#post5059497)

---

