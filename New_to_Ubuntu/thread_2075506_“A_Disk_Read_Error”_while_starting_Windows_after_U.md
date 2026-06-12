---
title: "“A Disk Read Error” while starting Windows after Ubuntu upgrade + Boot Repair"
date: 2012-10-24
forum: New to Ubuntu
---

### Post by johnvit on 2012-10-24
I just upgraded to 12.10. After installing the files and rebooting I had come across following problem:
  [INDENT]   **error file not found**
      **grub rescue> _**
 [/INDENT]  This problem was easily solved by repairing the boot using Boot Repair tool. 


  But after this, Windows won't start. It's giving following error:
  [INDENT]   **A disk read error has occurred **
      **Press Ctrl+Alt+Del to restart**



How do I fix this?


[IMG]http://i.stack.imgur.com/W4daB.jpg[/IMG] [/INDENT]

---

### Post by YannBuntu on 2012-10-24
hello

1) use a Windows disk this way: [https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader](https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader) , until you get direct access to Windows
2) then run Boot-Repair to recover the GRUB menu

---

