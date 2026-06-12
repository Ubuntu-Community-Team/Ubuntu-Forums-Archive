---
title: "Importing Eclipse From Windows"
date: 2008-01-21
forum: Programming Talk
---

### Post by infamousjre on 2008-01-21
My professor uses a very specific build of eclipse for my Java class. With all of his plugins and settings saved. But its a windows build, so i was wondering if anyone knew what files to move and where to move them to get it close to his build.

My main concern is getting the Visual Class editing environment plugin imported.

---

### Post by bschleusner on 2008-01-26
I think you can just copy the entire directory that eclipse is installed in, and it should work without any modifications under Ubuntu. (it's all java based, right?)

---

### Post by infamousjre on 2008-01-29
except for the actual executables being .exe files... I think.  Where do I put the folder? :-/

---

### Post by tenmillionmilesaway on 2008-01-31
Eclipse uses swt which uses platform specific libraries so its doubtfull that a windows version of eclipse will work on linux.

The plugins are all in the plugin directory in the directory where eclipse is installed.   You should be able to copy them into a linux eclipse install if you can decide which jars and folders to copy.

Are these plugins widely available plugins or are they ones he wrote himself?

---

### Post by infamousjre on 2008-02-01
I think the Visual Class Editor is widely available (and thats the one I really need), except I can't find it, at least not with a proper installation. I think the developer gave up on it and its a dead project.

---

