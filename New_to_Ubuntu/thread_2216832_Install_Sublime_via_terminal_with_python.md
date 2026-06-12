---
title: "Install Sublime via terminal with python"
date: 2014-04-14
forum: New to Ubuntu
---

### Post by meierdesigns on 2014-04-14
hey guys,


I'm trying to install sublime on my ubuntu.

entered the following:

$ python sublime_plugin.py

Traceback (most recent call last):
  File "sublime_plugin.py", line 4, in <module>
    import sublime
ImportError: No module named sublime


what should I do now to install the sublime editor?

Kind regards

---

### Post by slickymaster on 2014-04-14
Why don't you install it using the WebUpd8 PPA? It's really simple, all it takes is to run three lines in a terminal window:```
sudo add-apt-repository ppa:webupd8team/sublime-text-2
sudo apt-get update
sudo apt-get install sublime-text
```

---

### Post by meierdesigns on 2014-04-14
Thank you for the quick answer...

Everything got installed

---

### Post by slickymaster on 2014-04-14
Using webupd8 PPA, Sublime Text 2 will get a proper .desktop file so you can right click files to open in Sublime Text 2 as well as showing up properly in the Unity launcher.
You can also open files from the command line (run "sublime-text-2 /path/to/file" or "subl /path/to/file")

---

