---
title: "Help !"
date: 2008-07-07
forum: New to Ubuntu
---

### Post by xieu90 on 2008-07-07
hi everyone
in Ubuntu I can see folder with a Lock symbol on it
and I cannot copy files into it, neither delete files from it
how can I do it in GUI ?
because typing sudo rm -r in terminal is so tiring
please !
are there any method to become root in GUI ? (just temporary, and how to turn off Root after I deleted some annoying files?)

---

### Post by nothingspecial on 2008-07-07
```
gksudo nautilus
```

Will give you root access to the file system.

---

### Post by bryncoles on 2008-07-07
whats the folder? 

if you type 'chmod u+rw -R ' (without quotes) into the terminal, then drag and drop the folder into the terminal and press return it should give you permission to read, write and delete that folder and within that folder. 

you can also type 'gksudo nautilus' into the terminal to open the file browser with root privilages BUT THIS WILL ALLOW YOU TO DELETE VITAL SYSTEM FILES IF YOU'RE NOT CAREFUL and so probably isnt the best idea (though i used to do it so who am i to talk)

---

### Post by xieu90 on 2008-07-07
thank you guys
I think I will choose chmod u+rw -R
but both of them are handy ^^ 
:lolflag:
time to go on rampages ^^ 
prepare yourself, my dear computer ^^:lolflag:

---

### Post by bryncoles on 2008-07-07
glad your problem is resolved. dont forget to mark the thread as solved!

---

### Post by hyper_ch on 2008-07-07
it is adviced to use a descriptive topic title, that means a topic title that gives some clue about the content in the thread itself...

a generic topic title like "noob here" or "need help" does not help at all. As you may have notices, just about everyone posting in here has some kind of a problem or issue or question ;)

---

### Post by stalkingwolf on 2008-07-07
you can also try right clicking on the file , then select properties and try changing the permissions.

---

### Post by xieu90 on 2008-07-08
right click method didnt work for me that is why i had to ask 
how do i mark the thread as solved ?
at the first time I wanted to name the thread too
but I didnt know how to name it, can you give it a name instead me ?
and tell me how to rename the thread too

---

