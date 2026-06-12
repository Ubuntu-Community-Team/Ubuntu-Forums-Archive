---
title: "Uninstalling Eclipse"
date: 2013-02-15
forum: New to Ubuntu
---

### Post by lusbyclark on 2013-02-15
Two weeks ago I installed the Eclipse IDE and a bunch of its plugins.  I have since discovered that I really do not want Eclipse, so I want to uninstall Eclipse.  I tried

sudo apt-get remove eclipse

from the Eclipse directory, but nothing seemed to happen.  At least Eclipse and its plugins are all still in residence.  

What are the proper steps/commands to rid my computer of this software?

---

### Post by r-senior on 2013-02-15
How did you install it?

If you used apt-get or Software Center/Synaptic, etc, apt-get remove will remove the program itself but you'll need to delete the workspace that contains the hidden directories where you would have created your projects and where it likes to put its plugins.

Use Nautilus (file manager), press Ctrl-H to show hidden files and have a look in your workspace directory. You'll probably find a directory called .metadata in there somewhere, which should have all the plugins. If you don't need the workspace, just delete the whole thing.

(I'm looking at my SpringSource Tool Suite installation so it could be slightly different but it's all Eclipse at the end of the day).

---

### Post by Frogs Hair on 2013-02-15
Try removing from the software center or the following command. 
```
sudo apt-get remove --purge eclipse
```

---

