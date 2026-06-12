---
title: "Need KDE Headers under Gnome?"
date: 2007-07-26
forum: Packaging and Compiling Programs
---

### Post by thejavo on 2007-07-26
I'm installing kfb, is a Firebird administrator, when I do ./configure, I obtain this message:
"checking for KDE... configure: error:
in the prefix, you've chosen, are no KDE headers installed. This will fail.
So, check this please and use another prefix!"
Since I'm working under Gnome, I don't have de KDE Headers, when I try
"sudo apt-get kdebase-dev"
apt informs me that It will install 108 Mb of KDE software... is there someway of not 
doing this?. I didn't find any parameter for ./configure that help me with this, or at least,
I didn't understand if there's any. ](*,) 

Please excuse my english.

---

### Post by mastapat11 on 2007-07-28
I ran into this too, for k3b.
Try "sudo apt-get install kdelibs-dev"
It downloads only 12mb of files which expands to 45mb.
should remove the compile error. :KS

---

