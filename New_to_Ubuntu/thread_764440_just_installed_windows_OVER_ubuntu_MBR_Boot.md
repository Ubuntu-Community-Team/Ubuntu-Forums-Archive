---
title: "just installed windows OVER ubuntu MBR Boot"
date: 2008-04-23
forum: New to Ubuntu
---

### Post by asnd16 on 2008-04-23
So can someone point me in the write direction to get the GRUB back . . . I had Hardy installed on one partition and I just installed winows on a sepereate. . .I know all I have to do is bring back the option of selecting which System I want to boot from. . .so how do I do this??

---

### Post by Tatty on 2008-04-23
[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows?action=show&redirect=RestoreGrub](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows?action=show&redirect=RestoreGrub)

That should do it :)

---

### Post by asnd16 on 2008-04-24
OK so I followed the guide and got the Grub list back but there is no option for windows ZleezP soo I added it I think when I used find /boot/grub/stage1   the output was (hd0,0) soo I resumed to place the root there restarted and got my ubuntu list back . . . no xp so I entered again and added xp at (hd0,1) <--would this be typical?

---

### Post by philinux on 2008-04-24
This might help.

[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

---

