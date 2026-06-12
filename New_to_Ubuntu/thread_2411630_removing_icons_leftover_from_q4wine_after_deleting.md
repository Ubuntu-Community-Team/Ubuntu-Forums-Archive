---
title: "removing icons leftover from q4wine after deleting program"
date: 2019-02-01
forum: New to Ubuntu
---

### Post by newblank25 on 2019-02-01
I had installed a window program using Q4wine in ubuntu 18.04. I used Q4wine to remove the program. When i search for programs I type the first letter in activities. Any program which begins with the first letter is shown. The icon is shown but link to it is dead for program was removed. How to I remove this Icon?Thanks for help.

---

### Post by Holger_Gehrke on 2019-02-01
Sounds like a left over .desktop file. Search the files in '~/.local/share/applications/' (a hidden directory in your home directory; desktop files here are your own) and in '/usr/share/applications/' (the place where desktop-files for programs that are installed for all users reside). 

Holger

---

