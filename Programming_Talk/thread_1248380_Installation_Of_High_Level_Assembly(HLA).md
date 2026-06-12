---
title: "Installation Of High Level Assembly(HLA)"
date: 2009-08-24
forum: Programming Talk
---

### Post by Tech2077 on 2009-08-24
I'm looking at the instructions of the installation, but i'm fairly new to ubuntu and don't know how to set the assembler up, specificly setting the path, since i can't find it in the .bashrc file.

any help would be appreciated

---

### Post by pepperphd on 2009-08-24
Your .bashrc is in your home folder.  Nautilus (or Konqueror, if that's your thing) won't display it because of the "." in front of it, but it's there. At the command line, type "locate .bashrc" and hit enter.  You should see one at "/home/YOURNAME/.bashrc".  You can edit it by entering "gedit /home/YOURNAME/.bashrc".  You may want to back it up first, which can be done with a "cp /home/YOURNAME/.bashrc /home/YOURNAME/.bashrc_backup".

---

