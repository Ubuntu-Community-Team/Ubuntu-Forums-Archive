---
title: "Waze for Linux (Qt based)"
date: 2012-03-13
forum: New to Ubuntu
---

### Post by damagedspline on 2012-03-13
I do the Waze Qt port for Nokia N900/N9/N950 and someone asked me to port it and make it run on any Linux. So I did. Well, kinda.

The code is not yet ready for multiuser env so the installer below should be run per user and is i386 specific. In the future I will fix the code and make a proper deb.
Read the release notes before using.

Installer: [http://code.google.com/p/waze-qt/downloads/detail?name=WazeInstaller_i386_0.0.6.sh]("http://code.google.com/p/waze-qt/downloads/detail?name=WazeInstaller_i386_0.0.6.sh")

What is Waze? Waze is a community based GPS and navigation application

---

### Post by damagedspline on 2012-03-14
Known issue that was found is that the application segfault when attempting to input text.

I will fix it tonight and re-release the installer.

---

### Post by damagedspline on 2012-03-14
New installer @ [http://code.google.com/p/waze-qt/downloads/detail?name=WazeInstaller_i386_0.0.6.sh]("http://code.google.com/p/waze-qt/downloads/detail?name=WazeInstaller_i386_0.0.6.sh")

Remove the old before reinstalling with:
```

rm -Rf ~/bin/waze ~/MyDocs/.waze

```

What fixed:
[LIST=1]
[*]turn fullscreen off when clicking F
[*]no more 20% battery warning on desktop
[*]new directory (.waze instead of MyDocs/.waze).
[/LIST]

---

