---
title: "Kaffeine opens but wont run"
date: 2008-05-23
forum: New to Ubuntu
---

### Post by saskatchewan on 2008-05-23
I have tried opening Kaffeine in a terminal window and some text pops up in the window then the window closes before I can read it.

When I try to open Kaffeine by clicking the icon then nothing happens.
Any suggestions?

---

### Post by Xiong Chiamiov on 2008-05-26
Do a purge reinstall.  From adept, you can right-click on kaffeine, then click first reinstall, then purge.  Or, if you prefer, you can
```

sudo aptitude purge kaffeine; sudo aptitude install kaffeine

```

---

