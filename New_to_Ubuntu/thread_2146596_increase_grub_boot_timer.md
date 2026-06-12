---
title: "increase grub boot timer"
date: 2013-05-19
forum: New to Ubuntu
---

### Post by john rosswrock on 2013-05-19
How to increase the default grub boot timer...
thanx in advance

---

### Post by pqwoerituytrueiwoq on 2013-05-19
edit these lines as needed in [FONT=courier new]/etc/default/grub
GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10[/FONT]
then run [FONT=Courier New]sudo update-grub[/FONT]

---

### Post by fantab on 2013-05-19
[QUOTE=/etc/default/grub][FONT=courier new]
[SIZE=2]GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
**GRUB_TIMEOUT=10**[/SIZE][/FONT][/QUOTE]

If you are dual-booting then you have edit the 'bold line'. The value '10' means ten seconds. After edit SAVE the file and from Terminal run: *sudo update-grub*

---

