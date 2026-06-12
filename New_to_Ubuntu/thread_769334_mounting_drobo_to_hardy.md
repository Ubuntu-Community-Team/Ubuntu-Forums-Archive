---
title: "mounting drobo to hardy"
date: 2008-04-26
forum: New to Ubuntu
---

### Post by to young on 2008-04-26
I use external Drobo hard drive.  Which is not working under hardy.  worked perfectly under gutsy.  

solution is posted in this this thread

[http://ubuntuforums.org/showthread.php?p=4663892#post4663892](http://ubuntuforums.org/showthread.php?p=4663892#post4663892)

the thread is closed.  

however,  I am total newbie and do not know how to edit that file.  can some one please tell me step by step.  how to do it.

and also what am I doing with these commands.  

Thank you so much in advance.  

to young

---

### Post by mick8985 on 2008-04-26
Hardy doesn't seem to automount drives as soon as they are plugged in anymore, so they don't show up on the desktop. However the unmounted drive should be visible in the places menu and will be mounted as soon as selected. Check that it isn't actually available in the places menu.

---

### Post by to young on 2008-04-26
I already tried that.

I had another ext3 drive which did mount and showed up on desktop.
USB flash drives also work fine.


however it is not recognizing the Drobo Drive.

Solution seems to be single line addition to /etc/fstab 
/dev/sdc1 /media/Jrobo ext3 defaults 0 0

however it does not give me permission to edit this file,  I cannot save changes to this file.  

somebody please helpme.

---

### Post by mick8985 on 2008-04-26
You should be able to edit that file using sudo, but if you still cannot edit the file, then do ```
sudo chmod +w /etc/fstab
```

---

