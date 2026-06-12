---
title: "[SOLVED] I messed up /dev/ttyUSB0 what can I do?"
date: 2008-10-02
forum: New to Ubuntu
---

### Post by neurostu on 2008-10-02
I was trying to create a symbolic link:
bstamp-> ttyUSB0

so I typed:
```

sudo ln -s bstamp ttyUSB0

```
then I realized I had the syntax backwards... now my ttyUSB0 is pointing to nothing... how can I fix this?

---

### Post by neurostu on 2008-10-02
All I had to do was:
```

sudo rm ttyUSB0

```
then unplug my USB device for a while, when I plugged it back in ttyUSB0 showed up again under /dev/

---

