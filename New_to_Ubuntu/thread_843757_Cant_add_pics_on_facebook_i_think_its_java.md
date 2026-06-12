---
title: "Cant add pics on facebook i think its java"
date: 2008-06-28
forum: New to Ubuntu
---

### Post by Kedster on 2008-06-28
i this isent directly about ubuntu but i think it why i have the problem.
i use face book for pictures, and i wanted to post some pics (like 300 lol)
but the uploader on facebook is java i think and it doesn't load. so installed (from add and remove) the java 6 console, that didnt work so i went to firefox add ons and used the java add on it didnt work what else could i do to try to fix it.

---

### Post by ConMan318 on 2008-06-28
Open Synaptic and search "sun-java".  Check the boxes for:
```

sun-java6-bin
sun-java6-fonts
sun-java6-jdk
sun-java6-jre
sun-java6-plugin
```

Then click 'apply'.  That should install everything you need for Java plugins if not more.

You could also use 'sudo apt-get install', either way.  Just get those packages somehow.

---

### Post by Kedster on 2008-06-28
i did all that and i still can upload photos like it just sits there 
like maybe its not java but like what else could it be

---

### Post by halitech on 2008-06-28
I followed the steps here

[http://ubuntuforums.org/showthread.php?t=595398&highlight=facebook](http://ubuntuforums.org/showthread.php?t=595398&highlight=facebook)

and then went to facebook and the java upload works like a charm now :)

ps. just did it about 10 minutes ago cause I was having the same problem as you but was using the simple uploader till today:

---

