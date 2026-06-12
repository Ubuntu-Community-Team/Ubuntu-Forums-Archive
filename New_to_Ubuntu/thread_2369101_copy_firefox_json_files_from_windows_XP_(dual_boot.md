---
title: "copy firefox json files from windows XP (dual boot system) to ubuntu 16.04 firefox"
date: 2017-08-18
forum: New to Ubuntu
---

### Post by druchkin on 2017-08-18
I am new to ubuntu 16.04.  I have installed a duel boot system.  Ubuntu 16.04 in one partition and windows XP in the original partition.  I would like to copy the json file (which contains tabs and bookmarks) from windows firefox to the appropriate location for ubuntu firefox.  How do I find that location in ubuntu?  For that matter, do you think that the window firefox json will work in ubuntu firefox?

---

### Post by handydandyhim on 2017-08-18
Edit: I misread your question at first, if you want to locate the file on your Windows partition you should be able to see the Windows drive in your file explorer. You should be able to see the NTFS partition and navigate to the location where Windows FF exported the bookmarks.

In Ubuntu you should be able to go to the 'Bookmarks' button in Firefox, click 'Show all bookmarks' (also clicking Ctl+Shift+B). Then click 'Import and Backup' to select the file.
You can also use Firefox Sync to sync all your bookmarks across your devices where Firefox is installed.

---

### Post by leunam12 on 2017-08-18
in ubuntu the Firefox files are located at /home/<username>/.mozilla/firefox

---

