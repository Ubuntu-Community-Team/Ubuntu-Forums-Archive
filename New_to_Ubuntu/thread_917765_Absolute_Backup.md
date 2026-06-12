---
title: "Absolute Backup"
date: 2008-09-12
forum: New to Ubuntu
---

### Post by Sugz on 2008-09-12
Ok i have had some crazy ideas recently, but before i do carry any of them out, i need to backup Ubuntu.
But as far as im concerned, backing up just my files is not enough, i need to backup everything, 
Configs, Desktop Theme, AVant look and feel, compiz configs, Files. Literally everything, so if my laptop does just blow up, i want to be able to just do something that will restore it back to its full Ubuntu glory like nothing at all bad happened.
Is this possible?

Many thanks

-Sugz

---

### Post by halitech on 2008-09-12
try Remastersys, it's worked for me and you can choose between a full backup or a live cd version

[http://www.remastersys.klikit-linux.com/](http://www.remastersys.klikit-linux.com/)

---

### Post by Sugz on 2008-09-12
In the live CD version, would i be able to somehow copy that image onto the Hard drive so it essentially is like a normal install?

---

### Post by halitech on 2008-09-12
basically the live cd (or dvd depending on the size of your backup) is used to reinstall and put you back exactly the way you were when you made the backup.

---

### Post by handydan918 on 2008-09-12
assuming you want to copy hda1 to hda5, this can be done (from a live cd)

```
rsync -av /mnt/hda1/ /mnt/hda5/ 
```

Best not to try this with the file systems in use (mounted) as system writes during a lengthy transfer could bork things.

---

### Post by phidia on 2008-09-12
[Time Vault]("https://wiki.ubuntu.com/TimeVault") appears to be beta now, or beta candidate so that could be a useful tool also. Downloads [here]("https://launchpad.net/timevault/+download").

---

### Post by prshah on 2008-09-12
> **Sugz said:**
>  i need to backup Ubuntu.
But as far as im concerned, backing up just my files is not enough, i need to backup everything

Take a look at [Exact duplicate of entire HDD]("http://ubuntuforums.org/showthread.php?t=874643") for many tips.

---

### Post by smausert on 2008-09-26
I just used the new version of remastersys to do a backup and it worked flawlessly.  The gui was great for me as I am a noobie to linux.  This application is more like it.  AND IT WORKED!  My iso file was 2.2G as I did not purge the packages.  To whoever did that work, thank you very much. It is great.

---

