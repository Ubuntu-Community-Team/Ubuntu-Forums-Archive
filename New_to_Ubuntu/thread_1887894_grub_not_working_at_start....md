---
title: "grub not working at start..."
date: 2011-11-28
forum: New to Ubuntu
---

### Post by tahir.salfi on 2011-11-28
hi
i am using ubuntu 10.04 with windows xp,,, 2 day ago i had installed windows xp but now ubuntu is not on OS chose menu,, alas GRUB is not working on startup..............


Help!!!!!:(

---

### Post by crazy bird on 2011-11-28
That's still a big issue with dualboots, never install Linux before Windows. First install Windows than install Linux since Grub does recognize all operating systems installed and shows it in the menu. Windows MBR will overwrite Grub so that you won't be able to see and boot into Linux.
 
Best is to update the Grub using a live-cd. This might help you: [https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2). And this post: [http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351). And this wiki: [https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows).

---

