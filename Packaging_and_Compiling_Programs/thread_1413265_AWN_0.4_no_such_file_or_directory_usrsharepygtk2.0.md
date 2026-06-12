---
title: "AWN 0.4: no such file or directory /usr/share/pygtk/2.0/defs/desktopagnostic.defs"
date: 2010-02-22
forum: Packaging and Compiling Programs
---

### Post by fraser_m on 2010-02-22
When I run make on AWN 0.4 (lp:awn) I get:

```
Traceback (most recent call last):
  File "/usr/share/pygobject/2.0/codegen/codegen.py", line 1717, in <module>
    sys.exit(main(sys.argv))
  File "/usr/share/pygobject/2.0/codegen/codegen.py", line 1675, in main
    p.startParsing()
  File "/usr/share/pygobject/2.0/codegen/scmexpr.py", line 113, in startParsing
    for statement in statements:
  File "/usr/share/pygobject/2.0/codegen/scmexpr.py", line 27, in parse
    fp = open(filename, 'r')
IOError: [Errno 2] No such file or directory: '/usr/share/pygtk/2.0/defs/desktopagnostic.defs'
make[2]: *** [awn.c] Error 1
make[1]: *** [all-recursive] Error 1
make: *** [all] Error 2

```

Any ideas? autogen.sh runs fine, says I have all the deps.

---

### Post by JDrive on 2010-04-24
Getting the same problem when I try to make as well. Satisfied all the dependencies.

---

### Post by SevenMachines on 2010-04-24
it looks like its missing a dependency on the python-desktop-agnostic package, you might need to install libdesktop-agnostic-bin too

---

### Post by JDrive on 2010-04-24
> **SevenMachines said:**
> it looks like its missing a dependency on the python-desktop-agnostic package, you might need to install libdesktop-agnostic-bin too

Installed the package, but still getting the same error.

Thanks!

---

### Post by SevenMachines on 2010-04-24
might depend on the package version i guess. do you get,
$ dpkg -L python-desktop-agnostic |grep desktopagnostic.defs
/usr/share/pygtk/2.0/defs/desktopagnostic.defs

[EDIT] It appears that this file appears in lucid and not in karmic

---

