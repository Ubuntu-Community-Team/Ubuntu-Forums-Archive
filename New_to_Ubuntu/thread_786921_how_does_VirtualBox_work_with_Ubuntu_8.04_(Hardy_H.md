---
title: "how does VirtualBox work with Ubuntu 8.04 (Hardy Heron) ?"
date: 2008-05-08
forum: New to Ubuntu
---

### Post by TMcKSmith on 2008-05-08
New Ubuntu user here (former Kubuntu & Mandriva user)  I was told that VirtualBox does not yet work with Hardy, is that true?  I notice that "virtualbox" is not available in Synaptic, rather "virtualbox-ose".  Is that the same thing?  Is it as simple as just installing this package from Synaptic?  Thanks for the responses in advance.

---

### Post by brazh on 2008-05-08
I've downloaded VirtualBox v1.5.6 from official site [http://www.virtualbox.org](http://www.virtualbox.org) (deb-file). It works excellent on my Kubuntu 8.04. There is version 1.6 available, but I have not tried it yet.

---

### Post by brazh on 2008-05-08
After your post, I've tried new VirtualBox version 1.6 - seems to work excellent too :)

---

### Post by wallabo on 2008-05-09
If you upgraded from Gutsy to Hardy than vbox will not work because of incorrect kernel modules. you can use adept or synaptic to replace (remove) the old virtualbox-ose-(guest)-modules-2.6.xx-xx and install the same ones ending with the appropriate kernel version 2.6.24-17.  If unsure about kernel version try 'uname -r'.
Apply the changes and vbox is running fine again

---

