---
title: "How to hide format option from that menu"
date: 2019-01-15
forum: New to Ubuntu
---

### Post by lethalneo on 2019-01-15
How to hide or put a password on formatting partitions to prevent other users from formatting my data accidentally

[![desktop screen][1]][1]


  [1]: [https://i.stack.imgur.com/22eEW.png](https://i.stack.imgur.com/22eEW.png)

---

### Post by Impavidus on 2019-01-15
You need root permissions to format anything, so it should already be protected with a password. Unless you're using a live disk. I don't think they made an exception for this, like they did when allowing ordinary users to mount partitions (like removable drives) not mentioned in fstab. It would be a bad idea.

---

### Post by oldrocker99 on 2019-01-15
Never run this, but it's a very destructive command:```
 
cd /
sudo rm -R *
``` This almost always requires a sudo command. The utility gnome-disk-utility, which can format disks, does not, IIRC, require root access, so, for general users, I would uninstall that utility if it is installed.

BTW, never, ever run this command, which will delete **EVERYTHING** on your drives, including /home. It is only as a warning, and is a prime example of not using cut/paste in a terminal without looking it up. You are very safe copying and pasting posted code here on the Ubuntu Forums; be careful on other websites. It probably isn't malicious code, but if you don't recognize the command, look it up to see what it does.

---

