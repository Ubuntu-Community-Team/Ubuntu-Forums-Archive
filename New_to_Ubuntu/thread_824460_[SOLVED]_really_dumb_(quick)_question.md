---
title: "[SOLVED] really dumb (quick) question"
date: 2008-06-10
forum: New to Ubuntu
---

### Post by WinterMadness on 2008-06-10
I only ask this because im not sure how to word it into a search engine that would give me oppropriate results

but, lets say im using the terminal (I know I dont have to use this) and im browsing my folders that are meant for windows. How do I get into Program Files? The space screws it up

joe@joe-laptop:/host$ cd Program Files
bash: cd: Program: No such file or directory

---

### Post by hyper_ch on 2008-06-10
it is advice to use a descriptive thread title that reflects the problem inside than a generic one like "noob here" or "help needed".

You want help from people? Then you should also help them to help you.

---

### Post by Barrucadu on 2008-06-10
You need to escape the space, or enclose the whole thing in quotes.
```
cd Program\ Files
```
```
cd "Program Files"
```

---

### Post by wormser on 2008-06-10
> **Barrucadu said:**
> You need to escape the space, or enclose the whole thing in quotes.
```
cd Program\ Files
``````
cd "Program Files"
```

Another method is start typing the path or a command and hit the tab key.  Please use a descriptive title next time.  It makes it easier to find answers by searching.  Mark the thread Solved and click the star to give thanks on the post that helped.

---

