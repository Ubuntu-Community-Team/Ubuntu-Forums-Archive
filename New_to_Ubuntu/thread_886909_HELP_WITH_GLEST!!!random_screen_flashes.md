---
title: "HELP WITH GLEST!!!random screen flashes"
date: 2008-08-11
forum: New to Ubuntu
---

### Post by phatmonk on 2008-08-11
I recently installed glest on my ubuntu machine. I am new to ubuntu and therefore don't know how to check the speed of my integrated graphics card. I installed glest using synaptic manager, it runs fine, but every time i click the whole screen goes black or white. It all turns negative and flashes back even on the lowest graphical settings. HELP:confused::confused::(:(:(:-({|=:-({|=

---

### Post by tjwoosta on 2008-08-12
do you have compiz enabled (desktop effects)?

if you do then your problem is caused by compiz (it happens to me also)

to temporarily disable compiz press **alt-f2** and type this (important that you dont use terminal here)
```
metacity --replace
```

then play your game

when your done playing do this to turn it back on ( use **alt-f2** here also)
```
compiz --replace
```

---

### Post by shlicshlac on 2008-09-09
I had the same problem, and turning off the effects solved it for me. Thanks!

---

