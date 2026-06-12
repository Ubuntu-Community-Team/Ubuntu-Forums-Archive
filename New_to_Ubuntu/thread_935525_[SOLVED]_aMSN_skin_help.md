---
title: "[SOLVED] aMSN skin help"
date: 2008-10-01
forum: New to Ubuntu
---

### Post by EvanRogers on 2008-10-01
Hey i need help with aMSN. I am trying to change the skin and when i try to drag and drop the skin file to the skins folder of aMSN it sais "Error moving file: Permission Denied" even tho i am owner of the computer. 

I should also say that i am EXTREMELY new to ubuntu OS. Please help a newbie :D

---

### Post by EvanRogers on 2008-10-01
ahh please help me guys lol i hate the amsn default skin.

---

### Post by binbash on 2008-10-01
you have to move it via sudo.i guess you are trying to copy the theme to /usr/share/amsn/skins/

try to move files via sudo mv

---

### Post by EvanRogers on 2008-10-01
how do i do that? via sudo im new

---

### Post by binbash on 2008-10-01
Just open nautilus as root

$gksudo nautilus

and move the theme folder to /usr/share/amsn/skins

you will just do c/p

---

### Post by EvanRogers on 2008-10-01
ok so i cant open root because it sais its a broken link.

---

### Post by SuperSonic4 on 2008-10-01
You do not need to copy to /usr. You can copy to ~/.amsn/skins where ~ is /home/<username>

If you really want to use root then press alt+f2 and type gksudo nautilus and navigate to /usr/share/amsn/skins

---

### Post by EvanRogers on 2008-10-01
Thanks supersonic that helped me and i got it working now.

---

