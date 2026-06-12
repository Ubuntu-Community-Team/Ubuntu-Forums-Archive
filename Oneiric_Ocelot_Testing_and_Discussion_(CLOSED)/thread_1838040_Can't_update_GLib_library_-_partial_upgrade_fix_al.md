---
title: "Can't update GLib library - partial upgrade fix also fails"
date: 2011-09-02
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by pimentel28 on 2011-09-02
Hello, I'm unable to update the Glib library, and the partial update fails as update manager crashes. 

Here is the screenshot:

[IMG]http://img828.imageshack.us/img828/707/screenshot20at202011090.png[/IMG]

and the output from terminal:

```

Traceback (most recent call last):
  File "/usr/bin/update-manager", line 106, in <module>
    controler.doPartialUpgrade()
  File "/usr/lib/python2.7/dist-packages/DistUpgrade/DistUpgradeController.py", line 1672, in doPartialUpgrade
    if not self.askDistUpgrade():
  File "/usr/lib/python2.7/dist-packages/DistUpgrade/DistUpgradeController.py", line 903, in askDistUpgrade
    self.cache.requiredDownload)
  File "/usr/lib/python2.7/dist-packages/DistUpgrade/DistUpgradeViewGtk3.py", line 648, in confirmChanges
    len(pkg.summary)))])
TypeError: glib.markup_escape_text() takes at most 1 argument (2 given)
Error in sys.excepthook:
Traceback (most recent call last):
  File "/usr/lib/python2.7/dist-packages/DistUpgrade/DistUpgradeViewGtk3.py", line 467, in _handleException
    apport_crash(type, value, tb)
  File "/usr/lib/python2.7/dist-packages/DistUpgrade/DistUpgradeApport.py", line 30, in apport_crash
    report[f.replace(".","").replace("-","")] = (open(f), )
  File "/usr/lib/python2.7/dist-packages/problem_report.py", line 504, in __setitem__
    assert k.replace('.', '').replace('-', '').replace('_', '').isalnum()
AssertionError

Original exception was:
Traceback (most recent call last):
  File "/usr/bin/update-manager", line 106, in <module>
    controler.doPartialUpgrade()
  File "/usr/lib/python2.7/dist-packages/DistUpgrade/DistUpgradeController.py", line 1672, in doPartialUpgrade
    if not self.askDistUpgrade():
  File "/usr/lib/python2.7/dist-packages/DistUpgrade/DistUpgradeController.py", line 903, in askDistUpgrade
    self.cache.requiredDownload)
  File "/usr/lib/python2.7/dist-packages/DistUpgrade/DistUpgradeViewGtk3.py", line 648, in confirmChanges
    len(pkg.summary)))])
TypeError: glib.markup_escape_text() takes at most 1 argument (2 given)

```

---

### Post by MadCow108 on 2011-09-02
you should not try to partial update that yet.
Wait a while until it upgrades normally.

the crash of the update manager should not happen, may be worth reporting

---

### Post by pimentel28 on 2011-09-02
> **MadCow108 said:**
> you should not try to partial update that yet.
Wait a while until it upgrades normally.

the crash of the update manager should not happen, may be worth reporting

Yeah, that does seem to be a huge pain - I've had upgrade manager crash during regular upgrades after upgrading to 11.10 Beta 1.

Also, nautilus keeps crashing and it seems that GLib is a dependency of it. Guess both issues are worth a report.

---

