---
title: "Failed to execute default terminal emulator Input/Output error"
date: 2020-06-22
forum: New to Ubuntu
---

### Post by skylixia on 2020-06-22
After trying to change the default python from 2.7 to 3.7 by changing priority with
```
sudo update-alternatives --install /usr/bin/python python /usr/bin/python3 
```
I have not been able to open a new terminal window anymore and get "Failed to execute default terminal emulator Input/Output error".
This affects the terminal emulator, byobu terminal and htop.
The preferred application for the terminal emulator is set to Debian X but setting to Gnome does not change anything.
With the terminal window I had left open I ran the following line as suggest in [this post:]("https://ubuntuforums.org/showthread.php?t=1894293") 
```
exo-open --launch TerminalEmulator
```
but got back:
```
Traceback (most recent call last):
  File "/usr/bin/gnome-terminal", line 9, in <module>
    from gi.repository import GLib, Gio
  File "/usr/lib/python3/dist-packages/gi/__init__.py", line 42, in <module>
    from . import _gi
ImportError: cannot import name '_gi' from 'gi' (/usr/lib/python3/dist-packages/gi/__init__.py)
Gtk-Message: 12:07:56.708: GtkDialog mapped without a transient parent. This is discouraged.

```
What can I do ?

---

### Post by erind on 2020-06-22
"Input/Output" error is usually caused by a problematic (damaged) hard drive, run a disk check on that drive. Also make sure that you're not running out of disk space, run** df -h** from a terminal.

---

### Post by Impavidus on 2020-06-23
Changing the default python version to 3.7 may be a bad idea. Before Ubuntu 20.04 there are still vital tools that depend on Python 2.7 being de default version of Python. As update-alternatives only sets up some symlinks, it should be easy to undo, even if you have to use a live disk. However, an I/O error suggests that more is going on.

---

### Post by ActionParsnip on 2020-06-23
If you switch it back, is it OK?

---

