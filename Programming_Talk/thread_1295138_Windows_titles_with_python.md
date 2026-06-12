---
title: "Windows titles with python"
date: 2009-10-19
forum: Programming Talk
---

### Post by oscrp on 2009-10-19
Hi!, I'm doing a small app on python, and I need to get the name of the song from the title of the spotify window, but I don't know how to get the active windows title from gnome. Is there a way to get them through dbus, or something like that?

Thanks in advance!

---

### Post by docomo on 2009-10-27
One way would be to install wmctrl and call that from python:

```
pipe = subprocess.Popen("wmctrl -l", shell=True, stdout=subprocess.PIPE).stdout

```

And then read the lines from pipe, detect the one that has "Spotify" in it, and strip away what you don't need from the string.

---

