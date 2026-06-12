---
title: "cannot record any audio using sound recorder"
date: 2008-07-29
forum: New to Ubuntu
---

### Post by 1two34 on 2008-07-29
when i open sound preferences and test sound capture I get following message Failed to construct test pipeline for 'gconfaudiosrc ! audioconvert ! audioresample ! gconfaudiosink profile=chat'
Please help

---

### Post by LinuxRocks713 on 2008-07-31
```

sudo apt-get install sound-recorder
sound-recorder -f wav *filename*
#now record what you want to record
#press Ctrl-C to stop

```

---

