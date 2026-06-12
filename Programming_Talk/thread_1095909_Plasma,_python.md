---
title: "Plasma, python"
date: 2009-03-14
forum: Programming Talk
---

### Post by matmatmat on 2009-03-14
I've been following the Getting Started Tutorial [here]("http://techbase.kde.org/Development/Tutorials/Plasma/Python/GettingStarted").
When I try to install it says it failed, when I try to run the main.py it gives this import error:
[PHP]
matio@ubuntu:~/Desktop/hello-python/contents/code$ python main.py 
Traceback (most recent call last):
  File "main.py", line 6, in <module>
    from PyKDE4 import plasmascript
ImportError: cannot import name plasmascript
[/PHP]
What do I need to do?

---

### Post by txcrackers on 2009-03-14
Do you have the following packages installed?

python-kde4
python-qt4-common
python-plasma

---

### Post by snova on 2009-03-14
Do you have **python-kde4** installed?

If you already do, all I can think of is that this tutorial is for a newer version of KDE than is available in Intrepid, or whatever release you're using.

Actually, that seems likely:

```

$ apt-file search plasmascript
$

```

Meaning I can't find a file with 'plasmascript' in its name anywhere, in any package. And since this is Intrepid with backports and KDE 4.2 PPAs enabled, I think I can safely say it won't be around until Jaunty. :(

---

Oh, here it is:

[http://packages.ubuntu.com/search?suite=jaunty&arch=any&mode=filename&searchon=contents&keywords=plasmascript](http://packages.ubuntu.com/search?suite=jaunty&arch=any&mode=filename&searchon=contents&keywords=plasmascript)

Confirmation, it's in Jaunty. Couldn't find it anywhere else, though. Sorry.

---

