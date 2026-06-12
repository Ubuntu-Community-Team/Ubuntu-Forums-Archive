---
title: "[SOLVED] Upgrade File locations"
date: 2008-11-02
forum: New to Ubuntu
---

### Post by jacobroecker on 2008-11-02
I'm out of HDD space on my EEEpc 4g and can't upgrade to 8.10 until I clean some of it off.  Where does Ubuntu hold the upgrade files it has already used (I think I can free up some space by deleting those)

OR

Is there a way to tell it to cache those files on the SD card I have plugged into the machine?

-Jacob
[Reprise]("http://reprise.trailbrain.com")

---

### Post by Sand Lee on 2008-11-02
Well if you're talking about the .debs of previously dowloaded/upgraded packages, they are in /var/cache/apt/archives. If you want to remove these files, you have to run ```
sudo apt-get clean
```

---

### Post by jacobroecker on 2008-11-02
Looks like that did the trick! 

Thanks!

---

### Post by Sand Lee on 2008-11-02
No problem. Don't forget to read my sig =] :guitar:

---

