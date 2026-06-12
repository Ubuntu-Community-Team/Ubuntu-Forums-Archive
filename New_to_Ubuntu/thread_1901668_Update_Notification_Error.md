---
title: "Update Notification Error"
date: 2011-12-29
forum: New to Ubuntu
---

### Post by JeremySchubert on 2011-12-29
Before I can complete a set of updates, the notification areas is telling me that I have to run 'sudo apt-get install -f' in terminal.  I did that and received the message 
> 
E: The package fax4100lpr needs to be reinstalled, but I can't find an archive for it.So do I just have to download and reinstall this package to clear the error?

---

### Post by wolfen69 on 2011-12-29
Did you manually install this package? If you *know* you do not need any fax software, you could do:
```
sudo dpkg --remove --force-remove-reinstreq fax4100lpr
```

---

### Post by JeremySchubert on 2011-12-29
Thanks, that did the trick.  To make it work I also had to create a missing file with the instructions found here:
[http://www.linuxquestions.org/questions/linux-newbie-8/package-unremovable-with-exit-status-127-a-470122/](http://www.linuxquestions.org/questions/linux-newbie-8/package-unremovable-with-exit-status-127-a-470122/)

Can someone please tell me how to mark a thread solved?

---

