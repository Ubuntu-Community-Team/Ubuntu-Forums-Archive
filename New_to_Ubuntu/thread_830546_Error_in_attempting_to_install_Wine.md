---
title: "Error in attempting to install Wine"
date: 2008-06-15
forum: New to Ubuntu
---

### Post by Threevenge on 2008-06-15
Okay, I've been trying to install Wine on my computer. I enter "sudo apt-get install wine" and this is what it spits out:

"The following packages have unmet dependencies:
  wine: Depends: libldap-2.4-2 (>= 2.4.7) but it is not installable
        PreDepends: dpkg (>= 1.14.12ubuntu3) but 1.14.5ubuntu16 is to be installed
E: Broken packages"


So what exactly should I do to fix this?

---

### Post by iaculallad on 2008-06-15
Try following the Wine Installation Guide.

[http://www.winehq.org/site/download-deb](http://www.winehq.org/site/download-deb)

---

### Post by RomeReactor on 2008-06-15
Hi. Try this: open Synaptic (System->Administration->Synaptic), go to 'Edit->Fix broken packages' and see if you can install Wine afterwards.

---

### Post by Threevenge on 2008-06-16
Alright, iaculallad , you succeeded in pointing me to an obvious process which I apparently didn't follow through all the way the first time. Thanks :P

---

