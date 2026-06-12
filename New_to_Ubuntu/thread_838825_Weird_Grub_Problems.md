---
title: "Weird Grub Problems"
date: 2008-06-23
forum: New to Ubuntu
---

### Post by neurostu on 2008-06-23
So when I boot my computer, I get a grub error saying "File Not Found". I can then go back to the grub menu and edit the boot line from (hd1,0) to (hd0,0).  When I do that I can boot into ubuntu. However when I edit my grub conf file and make the change permanent I cannot even get grub to load. I get a grub error before grub boots.

Can anyone explain this to me?

---

### Post by phidia on 2008-06-23
What grub error do you get after making changes permanent? (that's important to know)
The file you need to edit is /boot/grub/menu.lst (that's a lowercase L after menu.) you don't want to edit any grub conf file.

---

