---
title: "[SOLVED] ubuntu-tweak - anyone know what this error means?"
date: 2008-06-07
forum: New to Ubuntu
---

### Post by crjackson on 2008-06-07
```
charles@MSI-K8N-NEO4-PLAT-SLI:~$ ubuntu-tweak
/usr/lib/python2.5/site-packages/apt/__init__.py:18: FutureWarning: apt API not stable yet
  warnings.warn("apt API not stable yet", FutureWarning)
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Failed to open file '/usr/share/pixmaps/splash/ubuntu-splash.png': No such file or directory
```

---

### Post by crjackson on 2008-06-07
Looks like I pulled the trigger too fast.  I cleaned/purged the package and after a reinstall it works fine.

Have no idea what the error means though.

---

### Post by crjackson on 2008-06-07
Seems I was too quick to call it solved.  After a reboot it's doing the same thing again.

---

### Post by crjackson on 2008-06-10
And here's the fix...

[quote]Thanks crjackson and the bug reporter Mark Krapivner and Soulou at launchpad:bug#238158

I saw your outputs, and there was nothing  serious  error message that cause the Ubuntu Tweak can&#8217;t start.

So I assume that the splash screen cause the problem, now I tell you how to disable the splash, I hope it&#8217;ll solve it.

First, open your terminal(gnome-terminal), and type the following command.

sudo gedit /usr/share/ubuntu-tweak/ubuntu-tweak.py

At the line 33, you&#8217;ll see &#8220;thread.start_new_thread(self.show_splash, ()) &#8220;, now you can put an &#8220;#&#8221; in font of line or delete this line.

So ubuntu-tweak.py will look like this:

```
class TweakLauncher:
def __init__(self):
gtk.gdk.threads_init()
#            thread.start_new_thread(self.show_splash, ())

try:
from PackageWorker import update_apt_cache
except ImportError:
pass
```


Now save the file and try to start Ubuntu Tweak.

Please tell me the whether it is useful, thanks!

---

