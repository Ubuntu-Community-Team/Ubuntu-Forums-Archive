---
title: "Repository Window not Appearing"
date: 2008-09-20
forum: New to Ubuntu
---

### Post by wpurcell on 2008-09-20
Hello. I'm running GnewSense, an Ubuntu derivative. When in Synaptic, after clicking on System then Repo's, the Repo window appears for a fraction of a second, disappears, then a window appears saying the repos have changed, reload same. Because of this, repos cannot be changed. Any one have an idea what might be going on? Thanks for your time.

---

### Post by ladr0n on 2008-09-21
What happens if you go to System > Administration > Software Sources?  Does it exhibit the same behavior, or does it open correctly?

---

### Post by sayakb on 2008-09-21
Post the output of:
```
gksudo software-properties-gtk
```

---

### Post by wpurcell on 2008-09-21
> **ladr0n said:**
> What happens if you go to System > Administration > Software Sources?  Does it exhibit the same behavior, or does it open correctly?
Same thing.

---

### Post by wpurcell on 2008-09-21
> **LinuxIsInnovation said:**
> Post the output of:
```
gksudo software-properties-gtk
```
Here's the output:
william@william-desktop:~$ gksudo software-properties-gtk
Traceback (most recent call last):
t/__init__.py:18: FutureWarning: apt API not stable yet
  File "/usr/bin/software-properties-gtk", line 101, in <module>
    app = SoftwarePropertiesGtk(datadir=data_dir, options=options, file=file)
  File "/usr/lib/python2.5/site-packages/softwareproperties/gtk/SoftwarePropertiesGtk.py", line 115, in __init__
    self.show_distro()
  File "/usr/lib/python2.5/site-packages/softwareproperties/gtk/SoftwarePropertiesGtk.py", line 351, in show_distro
    for (name, uri, active) in self.distro.get_server_list():
  File "/usr/lib/python2.5/site-packages/aptsources/distro.py", line 212, in get_server_list
    compare_mirrors(self.used_servers[0], self.main_server)):
  File "/usr/lib/python2.5/site-packages/aptsources/distro.py", line 205, in compare_mirrors
    return re.match(mir1.strip("/ "), mir2.rstrip("/ "))
AttributeError: 'NoneType' object has no attribute 'rstrip'
Thanks for your efforts!

---

### Post by wpurcell on 2008-09-28
Hello again. So, no one has an idea what might be going on? I hope I'm not missing out on important updates because of this problem.

---

