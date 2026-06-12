---
title: "Failure in locating library"
date: 2012-02-10
forum: New to Ubuntu
---

### Post by mmasroorali on 2012-02-10
Dear All,
The error is intriguing. I installed cycas from [here]("http://www.cycas.de/"). The installation went fine. However, when I start cycas like this,
```
/usr/local/bin/cycas39_verbose
```
the following error message is shown,
```
Gtk-WARNING **: Failed to load module "libcanberra-gtk-module.so": libcanberra-gtk-module.so: cannot open shared object file: No such file or directory
```

However, the library is there.
```
masroor@RafidHamiz:~$ locate libcanberra-gtk-module.so
/usr/lib/debug/usr/lib/gtk-2.0/modules/libcanberra-gtk-module.so
/usr/lib/gtk-2.0/modules/libcanberra-gtk-module.so
/usr/lib/gtk-3.0/modules/libcanberra-gtk-module.so

```

Also, no new installation is necessery.
```
sudo apt-get install libcanberra*
```
says that no new installation is necessary.

cycas starts though, but no input works inside.

Any suggestion will be appreciated.

---

### Post by TeoBigusGeekus on 2012-02-10
As I've answered in your other [thread]("http://ubuntuforums.org/showthread.php?t=1923190"), please stop doing this to yourself: it's not worth it...
There'll never be good cad/bim software for linux while we live - period.
I've been where you've been a thousand times before; I've tried almost every crappy linux cad program that exists (cycas, bricscad, medusa, brl-cad, draftsight, archimedes, qcad, etc.) - they're not worth your time if you're trying to do a professional job.

TL;DR: Just dual boot with windows.

---

