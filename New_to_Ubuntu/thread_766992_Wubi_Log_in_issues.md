---
title: "Wubi Log in issues"
date: 2008-04-25
forum: New to Ubuntu
---

### Post by hardcastle1 on 2008-04-25
Hey,

I installed the Wubi package earlier and upon providing the username and p'word and going through the installation, I rebooted and let it do it's thing, it all worked apparently.

So I try and log in and it tells me permission denied, that came up something like this - 'Dev/null/bash permission denied' 

After that came up, I couldn't do anything and had to reboot.

I deffinately used the right login and password, so im just wondering what may've caused this and what solutions there may be?

---

### Post by Aearenda on 2008-05-05
I don't know what has caused this. If you follow the instructions in [http://ubuntuforums.org/showthread.php?p=4868110#post4868110](http://ubuntuforums.org/showthread.php?p=4868110#post4868110) for getting into recovery mode, and then do the step to discover your username as given there, the shell is the last entry on that line - so on my pc, that line shows ```
system:x:1000:1000:System Administrator,,,:/home/system:/bin/bash
```
It sounds like your shell entry is wrong. Try this and tell us what you see.

---

