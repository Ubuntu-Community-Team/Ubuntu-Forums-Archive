---
title: "bash question: howto run a command after chrooting?"
date: 2010-08-29
forum: Programming Talk
---

### Post by mr clark25 on 2010-08-29
i was trying to make a script that i believe will help many people- it is a bash script that will automate (ok, only kind of...) the process of chrooting and then reinstalling grub.

i have the script on my website here:
[http://mrclark.ath.cx/linux/scripts/grubfix](http://mrclark.ath.cx/linux/scripts/grubfix)

as you can see, i canceled (#)the part that was supposed to happen after chrooting. i tested the script myself, and noticed that it just dropped me at a chrooted terminal.

if you find any other problems with my script, please let me know.

could someone tell me how to do this?

---

### Post by Bachstelze on 2010-08-29
There's no need to chroot to reinstall GRUB, just use --root-directory.

---

### Post by mr clark25 on 2010-10-24
sorry to bring an old thread back, but i have one more question.


does grub generate a new grub.cfg (or menu.lst) when it is installed?

i have (finally) updated the script, and it seems to work. i just don't know if i need to run "update-grub". i tried putting it in the script, but it looks like you must run it after chrooting. i couldn't get it to work.

any suggestions?

---

