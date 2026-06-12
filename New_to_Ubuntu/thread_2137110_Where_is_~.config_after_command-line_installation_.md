---
title: "Where is ~/.config after command-line installation? Also how to run openbox?"
date: 2013-04-19
forum: New to Ubuntu
---

### Post by FrontLoadedAnvils on 2013-04-19
I am using a command-line installation of 64 bit ubuntu.

Whenever I freshly do a command-line installation of 64 bit ubuntu, I find that I don't have a ~/.config **directory**. I am also having trouble running stand-alone openbox on this installation. Does anyone have any advice?

---

### Post by ibjsb4 on 2013-04-19
An easy way to do that would be with xorg and a no frills display manager.

```
sudo apt-get install xorg slim openbox
```

When Slim DM comes up, use the F1 key to pick openbox.

---

### Post by mikewhatever on 2013-04-19
The .config directory is used for storing various desktop/application related configs. Since you only have a command line installation, there is, apparently, not reason to have the .config dir. Needless to say, you can just create it.

---

