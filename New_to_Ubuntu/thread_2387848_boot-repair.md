---
title: "boot-repair"
date: 2018-03-24
forum: New to Ubuntu
---

### Post by sanjay544 on 2018-03-24
I'm getting problem [http://paste.ubuntu.com/p/JKkz9Dgp5r/](http://paste.ubuntu.com/p/JKkz9Dgp5r/) please help me to solve it.

even grub is not detecting windows image .

---

### Post by oldfred on 2018-03-24
You may need to turn off UEFI Secure Boot.

Can you not directly boot Windows from UEFI boot menu.
Grub is showing it in the menu, but only boots working Windows. And that means Windows cannot be hibernated, nor need chkdsk.

You are showing Ubuntu 15.04, long time obsolete. You need to reinstall. Be sure to backup all your data first.
If you do not want to regularly update or re-install, best to use LTS versions that are good for 5 years.
 [https://wiki.ubuntu.com/Releases](https://wiki.ubuntu.com/Releases)

---

