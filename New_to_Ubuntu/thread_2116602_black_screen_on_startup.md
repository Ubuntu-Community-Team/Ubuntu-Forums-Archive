---
title: "black screen on startup"
date: 2013-02-16
forum: New to Ubuntu
---

### Post by Jkake on 2013-02-16
hi; My son installed Ubuntu 12;10 for me on an Hp desktop. Have been happily using it for 2 months . Today it won't boot up but seems to go straight to suspend(black screen) I tried intercepting it pressing the escape key and got a boot window with some options that I could  scroll through. Not sure if there some way I can start it in safe mode and find out what is wrong. Starring at a black screen  is no fun. Cheers Jkake

---

### Post by grahammechanical on 2013-02-16
Pressing Esc at that point is bringing up the Grub bootloader menu. We do not normally see the Grub menu if Ubuntu is the only OS installed. So, we need to press ESC to call it up.

At those menu options select Recovery Mode. As you're using 12.10 you will find Recovery Mode under the Advanced Options for Ubuntu submenu.

At the next screen you will get some more options. Try Resume. That sometimes gets us to a desktop.

Another thing to try is - at the Grub menu with Ubuntu highlighted press E. That will put Grub into Edit mode and you will see the boot parameters. Look for a line that has quiet splash near the end of the line. Edit out quiet splash and press F10 to boot.

You will see messages as the OS loads. The last messages before the loading stops will give clues as to what is wrong.

Regards.

---

