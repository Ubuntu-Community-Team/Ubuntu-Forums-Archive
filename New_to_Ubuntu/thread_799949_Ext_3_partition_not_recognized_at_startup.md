---
title: "Ext 3 partition not recognized at startup"
date: 2008-05-19
forum: New to Ubuntu
---

### Post by O-pos on 2008-05-19
Hello,

I have a separate ext3 partition only for my personal data like movies, music, documents (no /home). I did clean install of Ubuntu Hardy, and when I boot the computer, the system does not recognize this partition by default. Then, when I go to places>computer>200GB Disk (this is the drive I'm talking about), then it works. I have a wallpaper picture, the file of which is stored on this drive and the wallpaper gets displayed only after I performed above described procedure. Shortcuts also start to work only after that. How can I make it so that it gets mounted/recognized at the startup of the system?

---

### Post by nirkir on 2008-05-19
You'd probably want to manually edit /etc/fstab for that.

This topic has been discussed before, try the following links for more information:

[http://ubuntuforums.org/showthread.php?t=283131]("http://ubuntuforums.org/showthread.php?t=283131")
[https://help.ubuntu.com/community/AutomaticallyMountPartitions]("https://help.ubuntu.com/community/AutomaticallyMountPartitions")

A small advice, use UUID when mounting. I had problems between updates on Hardy when using disk locations (e.g /dev/sd??)

---

