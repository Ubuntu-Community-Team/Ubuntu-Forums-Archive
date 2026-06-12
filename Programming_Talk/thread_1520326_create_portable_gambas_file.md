---
title: "create portable gambas file"
date: 2010-06-29
forum: Programming Talk
---

### Post by chaemil on 2010-06-29
hi

how can i run the .gambas file on the machine where is'nt installed the gambas2 package?
i want to run the file from usb stick or something else. and that require to make it portable and pack wit it some binary files but i dont know which and how tell the system to run them..

thx for yout response

---

### Post by C.S.Cameron on 2010-06-29
Can you make a persistent Live USB flash drive using the Startup Disk Creator from the Live CD and then install Gambas to it?

---

### Post by chaemil on 2010-06-29
i dont want to create a live system... this will be used as a launcher to my game project in blender.. it will be like portable gimp or something else in windows...

---

### Post by kalaharix on 2010-06-30
Normally you need an installation of Gambas runtime to run a 'compiled' Gambas application. Looking at the Gambas forum, you can define a GB_DIR environment variable that points at the Gambas installation directory.

With that, you should be able to run Gambas from your USB key, provided that the destination O.S. has all the needed shared libraries installed.

You can put all the needed shared libraries on the USB key too, and run Gambas completely, by using the LD_LIBRARY_PATH environment variable. 

It sounds complicated and I haven't tried it myself.

---

### Post by chaemil on 2010-06-30
oh thannks i will try it... i'm guessing that i can do the same with the blenderplayer binary....

---

### Post by chaemil on 2010-06-30
but... is there somewhere somebody who knows how to do it?  i will need it with gambas and blenderplayer binary

---

