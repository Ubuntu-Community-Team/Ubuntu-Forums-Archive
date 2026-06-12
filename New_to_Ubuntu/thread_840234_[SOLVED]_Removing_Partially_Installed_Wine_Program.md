---
title: "[SOLVED] Removing Partially Installed Wine Program"
date: 2008-06-25
forum: New to Ubuntu
---

### Post by lhb1142 on 2008-06-25
I attempted to install a program under Wine. It would not install completely. I tried to uninstall it but it would not uninstall completely and still remains showing under Wine programs.

Would someone please tell me the command line dialog to completely remove this undesired program completely?

Thank you very much. By the way, I appreciate all the help I have thus far received on this forum. The experts here really make the process of learning to manipulate Ubuntu Linux very pleasant and easy for this (now, hopefully, forever former) Windows user.

---

### Post by Circus-Killer on 2008-06-25
well, if you talking about the wine menu entries, you can use the menu editor located under "System -> Preferences" to remove those unnecessary entries.

1) if you have not installed anything else on wine, then you could actually probably get away with just deleting the wine directory (/home/user/.wine).

2) if you have other windows programs already installed, then you can just delete the program files and directories also located in the wine directory mentioned above.

both 1 and 2 will probably require you to remove the menu entries manually.

---

