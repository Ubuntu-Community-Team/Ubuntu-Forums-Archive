---
title: "Problem in writing executable script"
date: 2008-10-14
forum: Programming Talk
---

### Post by augustineprasad on 2008-10-14
[B]#to start gedit(a text editor)& firefox

gedit
firefox[/B]

[I]when i execute this exuctable scipt,first the editor opens up but not the firefox..... so once when i close the editor the firefox pops up....Is there any solution to pop up both in the same time within a single executable script

[/I]
---Aj

---

### Post by dwhitney67 on 2008-10-14
Run gedit in the background.

```
#!/bin/sh

gedit &
firefox
```

---

### Post by aska786 on 2008-10-14
Earn money for clicking The Ads [sign up]("http://bux.to/?r=aska786") Here

---

