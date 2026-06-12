---
title: "How to get the default sources.list?"
date: 2017-11-16
forum: New to Ubuntu
---

### Post by wanggaoteng on 2017-11-16
Hi, today I had take a mistake, I changed the sources.list and have not saved the default sources.list, so the default sources.list lost.
How can I get the default sources.list again, or download from the official website?
Thanks a lot.
P.S. ubuntu16.04.3LTS-64bit

---

### Post by oldfred on 2017-11-16
Do you know what you changed?

There is this, but do not know if it works or not. Before using you may want to compare to your list.
[https://repogen.simplylinux.ch/](https://repogen.simplylinux.ch/)

List all sources
       cat /etc/apt/sources.list; for X in /etc/apt/sources.list.d/*; do echo; echo; echo "** $X:"; echo; cat $X; done 
    
       But do not just import all sources as that can lead to issues of versions:
[http://askubuntu.com/questions/2038/backup-software-sources](http://askubuntu.com/questions/2038/backup-software-sources)
sudo cp /etc/apt/sources.list ~/sources.list.backup
Otherwise if you have added any PPAs or other sources, the tip will only reinstall Ubuntu files, 

Always best to backup before make changes, to any system file to flash drive or other external drive.

 cp /etc/apt/sources.list ~/sources.list.backup
sudo cp -r /etc/apt/sources.list.d /Like-a-FlashDrive

---

### Post by wanggaoteng on 2017-11-17
> **oldfred said:**
> Do you know what you changed?

There is this, but do not know if it works or not. Before using you may want to compare to your list.
[https://repogen.simplylinux.ch/](https://repogen.simplylinux.ch/)

List all sources
       cat /etc/apt/sources.list; for X in /etc/apt/sources.list.d/*; do echo; echo; echo "** $X:"; echo; cat $X; done 
    
       But do not just import all sources as that can lead to issues of versions:
[http://askubuntu.com/questions/2038/backup-software-sources](http://askubuntu.com/questions/2038/backup-software-sources)
sudo cp /etc/apt/sources.list ~/sources.list.backup
Otherwise if you have added any PPAs or other sources, the tip will only reinstall Ubuntu files, 

Always best to backup before make changes, to any system file to flash drive or other external drive.

 cp /etc/apt/sources.list ~/sources.list.backup
sudo cp -r /etc/apt/sources.list.d /Like-a-FlashDrive

Hi, oldfred, I copy some sources from the website and paste them to the default sources.list, then I saved them, and updated, but some warnings appeared,"w:target translations(xxx) at /etc/apt/sources.list and translations(xxx) has been configure many times."
Now I comment out the lines which cause the warnings, then the warnings disappeared.
Thank you very much, I will be careful next time to avoid change the default files in ubuntu.
Best regards.

---

### Post by vasa1 on 2017-11-17
[How to mark threads [SOLVED] or [UNSOLVED]](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

---

