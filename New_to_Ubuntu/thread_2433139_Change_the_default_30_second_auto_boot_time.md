---
title: "Change the default 30 second auto boot time ?"
date: 2019-12-14
forum: New to Ubuntu
---

### Post by Drakkor on 2019-12-14
Trying for a quicker auto boot and wanted to lower the default time from 30 to perhaps 1 second 
Is this possible ? Thanks

---

### Post by Impavidus on 2019-12-14
I guess you are referring to the time the grub menu shows. Edit /etc/default/grub with```
sudoedit /etc/default/grub
```and change the line with```
GRUB_TIMEOUT=30
```to some number you like more. I set it to 3. You can set it to 0, which will disable the menu completely, but that will make it hard to access the menu when you need it. After you edited the file, run```
sudo update-grub
```to make the changes effective.

---

