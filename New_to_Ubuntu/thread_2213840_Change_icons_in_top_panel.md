---
title: "Change icons in top panel"
date: 2014-03-28
forum: New to Ubuntu
---

### Post by htorres on 2014-03-28
How can I remove some icons from the top right corner of the panel? Mainly I would like to just get rid of this envelope icon that's up there. I uninstalled Empathy because I don't use IM anymore so I no longer need that icon up there.

---

### Post by sotiris2 on 2014-03-29
Remove *indicator-messages* either via Ubuntu software center, Synaptic or command

```
sudo apt-get remove indicator-messages
```

---

### Post by htorres on 2014-03-29
That did the trick. Thank you.

---

