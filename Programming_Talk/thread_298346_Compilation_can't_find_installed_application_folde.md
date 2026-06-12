---
title: "Compilation can't find installed application folders"
date: 2006-11-12
forum: Programming Talk
---

### Post by Roque on 2006-11-12
I compiled and installed an application from source:
```

cd applicationFolder
./configure && make && sudo make install

```

Then I made small changes to the source, recompiled and tried to run it locally:
```

cd applicationFolder
<modify sources>
make && ./executableName

```

It complains that the data folders aren't present. It's trying to find them locally (in /home/userName/aplicationFolder) but they were installed under the installation prefix folder. In Breezy, however, it had no problem to find them.

Does anyone know how to solve this? Thanks in advance.

---

### Post by Roque on 2006-11-12
I solved it. KDEDIRS was empty. Apparently the Kubuntu installer didn't set the environment variables...

---

