---
title: "Any platform to develop GUI applications on ARM"
date: 2011-10-03
forum: Programming Talk
---

### Post by vkbidve on 2011-10-03
Hi,

Does anybody of you know any good platform to develop GUI applications in ubuntu (or any generic linux distro) for ARM?

---

### Post by ve4cib on 2011-10-03
Any open-source tool for writing GUIs should do the trick.  QtCreator and Anjuta are the first two that come to mind.  MonoDevelop may also be usable, but I honestly don't know if Mono is usable on non-Intel family CPUs.

---

### Post by vkbidve on 2011-10-03
OK. But my basic question is, if i develop a GUI application, then can i cross-compile it for ARM architecture? Will everything including the GUI designs be ported to ARM using QtCreator/Anjuta?

---

### Post by fct on 2011-10-03
In mobile you have Android, Qt for Nokia (to be deprecated for Windows Phone 7), Samsung's Bada, Maemo/Meego (also to be deprecated), etc.

Each platform usually provides SDKs that may or not work under Linux. Gcc compiles to ARM, no problem. But the toolkits are what actually shape the platform and the tools you must use. They are also usually accompanied with simulators to test your code on, before testing in hardware.

I suggest these two:

Android SDK (for tablets too): [http://developer.android.com/sdk/index.html](http://developer.android.com/sdk/index.html)

Nokia Qt SDK (for Symbian models and the N9): [http://www.developer.nokia.com/Develop/Qt/Tools/](http://www.developer.nokia.com/Develop/Qt/Tools/)

---

### Post by ve4cib on 2011-10-03
> **vkbidve said:**
> OK. But my basic question is, if i develop a GUI application, then can i cross-compile it for ARM architecture? Will everything including the GUI designs be ported to ARM using QtCreator/Anjuta?

Assuming you are writing programs for a tablet or netbook (or similar device) equipped with an ARM processor and has Linux installed on it, then yes, everything will work provided you...

1- install the appropriate libraries (e.g. Qt) on the ARM device
2- properly cross-compile your application for ARM architectures
3- avoid using any libraries that are incompatible with ARM (e.g. Wine)

What kind of ARM device are you wanting to program for?  If it's a mobile phone or something running Android/iOS/WP7 then your options suddenly become much more restricted, and you'll need to use the appropriate SDKs and dev tools.  But if it's running any kind of normal Linux distro (e.g. Angstrom on a Beagleboard, or Always Innovating's Touchbook) then the standard battery of Linux dev tools will suit your needs.

---

