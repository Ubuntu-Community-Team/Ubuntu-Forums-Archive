---
title: "Uninstall programs"
date: 2014-01-28
forum: New to Ubuntu
---

### Post by rogeliofb on 2014-01-28
I installed the latest version of the HPLIP from the hp website but now I would like to uninstalls it. Normally, when you install softwares trough Software Center, you have the posibility to uninstall them, but when you installs the software from 3rd party, usually you can not use the Ubuntu Software Center for this purpose. Can anyone tell me how to do this using the terminal w/ command line?. I'm really newbie in Linux. Thanks......

---

### Post by ian-weisser on 2014-01-28
(Withdrawn)
oldfred's response is superior. Use his advice.

---

### Post by oldfred on 2014-01-28
I have HPLIP installed from HP.

In the folder with HPlip that you downloaded should be this file. I have never used it but it looks like the uninstaller.

uninstall.py

> __version__ = '1.0'
__title__ = 'HPLIP Uninstaller'
__mod__ = 'hp-uninstall'
__doc__ = "Uninstaller for HPLIP ."


---

### Post by rburkartjo on 2014-01-30
you could also open the spm and look for hplip and hplip-data and uninstall

---

