---
title: "clean up disk space"
date: 2008-09-04
forum: New to Ubuntu
---

### Post by yragrelluf on 2008-09-04
i am big into clean harddrives, so i am posting my cleanup procedures. any addl. input would be greatly appreciated.

Step 1, open you web browser(s) and clear the private data.
Step 2, open a terminal and type
                     sudo apt-get clean
                     sudo apt-get autoclean
                     sudo apt-get remove
                     sudo apt-get autoremove
                     sudo localepurge
Step 3, open program gtkorphan (in the repos) and use it to get rid of orphaned packages and libs. Do not use gtkorphan if you are using earOS media center, because it will wipe out the media centers dependencies.

Step 4, go into your home folder, and select show hidden files. delete .thumbnails, any empty directories. if you are not using custom themes, you can delete .themes and .icons. any saved game data is stored in their respective hidden folder, but you will have to start fresh in the game if you delete them. Also check for folder and files that are for removed programs and delete them.

Step 4. caution, dont do this unless you know what your doing.
             you can remove unwanted themes and screensavers from the    filesystem using sudo or nautilus, but i dont think i should be telling people to mess with the f.s. right now. I will post how to later if anybody wants me to.

---

### Post by orpheus07 on 2008-09-05
If I'm low on disk space, I use **Disk Usage Analyzer** to figure out what's eating it and where the files are located. It's bundled with Ubuntu. 

You can find it under Applications->Accessories->Disk Usage Analyzer. :)

---

### Post by Crafty Kisses on 2008-09-05
I think it's a tutorial, thanks for the information, can be very useful to some.

---

### Post by iaculallad on 2008-09-05
You could also try deleting the .bak files on your /boot filesystem folder.

```
sudo rm /boot/*.bak
```

---

### Post by yragrelluf on 2008-09-05
Removing .bak files? What are they? I dont like to mess with what I don't know.

---

### Post by iaculallad on 2008-09-05
> **yragrelluf said:**
> Removing .bak files? What are they? I dont like to mess with what I don't know.

They're the backup files for the system kernel images.

---

### Post by Crafty Kisses on 2008-09-05
That can technically remove some space, also log files I guess I know log files in some cases can take up a lot of space.

---

