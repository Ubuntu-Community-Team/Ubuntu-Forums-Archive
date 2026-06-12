---
title: "problem after mounting a new device"
date: 2019-11-19
forum: New to Ubuntu
---

### Post by shinelink on 2019-11-19
Dear all,
I am new to Ubuntu. I have a standalone machine with ubuntu 16.04 LTS. Recently, I wanna expand the storage of my computer so I bought a 1T Kingston SSD. I migrated home/ from the old SSD to the new one and mounted the new home/ folder by following the steps at the following link:
[https://www.maketecheasier.com/move-home-folder-ubuntu/](https://www.maketecheasier.com/move-home-folder-ubuntu/)

However, after mounting the new SSD (with home/ pointed to the new SSD), I failed to launch Jupyter notebook from Terminal. I resolved to reinstall the Jupyter notebook. Still, when I launched the newly installed Jupyter notebook, I was not able to execute some old scriptings. It seems to me that the system couldn't access the previously installed programs/ packages. Grateful if anyone would offer help to me. Many thanks in advance.

---

### Post by jeremy31 on 2019-11-19
Moved to New to Ubuntu

---

### Post by TheFu on 2019-11-20
Exactly how did you move the files over?  
Did you get all the hidden files or did you use some GUI to drag-n-drop and miss all those other files?

I skimmed those instructions.  Probably should stay with websites that have "ubuntu" in the domainname for complex instructions going forward.  [https://help.ubuntu.com/community/Partitioning/Home/Moving](https://help.ubuntu.com/community/Partitioning/Home/Moving) is an example where they don't leave you guessing how to move the files and handle some things which some people might run into with --exclude options.  They provide a fairly exact command which will get everything and cover encrypted directories and some cleanup.  Though I'm not a fan of how-to guides using sudo gedit, which is terrible advice.  It should be sudo -H gedit, if that editor is used - or better suggest using **sudoedit** instead to edit all system files.

Doing little things consistently, like using sudoedit, can avoid hassles later.

---

