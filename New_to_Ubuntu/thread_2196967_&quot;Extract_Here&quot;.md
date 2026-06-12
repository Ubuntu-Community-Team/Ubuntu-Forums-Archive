---
title: "&quot;Extract Here&quot;"
date: 2014-01-01
forum: New to Ubuntu
---

### Post by blueskychipita on 2014-01-01
In LXDE, e.g., lubuntu, lxle, etc., when I extract a zipped file, selecting "extract here", the individual parts of the file are shown rather than the "folder" in while the extracted files are located.  In ubuntru, mate and xfce, "extract here" keeps the extracted files in a folder next to the zipped folder.

Any suggestions as to what I might add to lubuntu to achhieve the same results as in ubuntu, etc.?  Thanks

---

### Post by Frogs Hair on 2014-01-01
Hello and Welcome

If there is an open with option  set it to the file manager rather than Archive Manager. I haven't had LXDE installed for a long time and don't remember the options in the file manager.

---

### Post by VMC on 2014-01-01
Did you try the "Extract To.." option then point it to a folder of choice?

---

### Post by blueskychipita on 2014-01-02
I could not find this option - thanks though.

---

### Post by blueskychipita on 2014-01-02
> **VMC said:**
> Did you try the "Extract To.." option then point it to a folder of choice?

I did, and the results were the same:  the unzipped file was was presented as individual parts.  Again, with Unity, xfce, cinnamon and mate DEs, the extracted file is present in it's own folder.

---

### Post by Frogs Hair on 2014-01-02
I see the same behavior after installing PCman on Ubuntu . All sub folders are displayed instead of a parent folder with sub folders inside. Huge waste of space and difficult to work with.

---

### Post by monkeybrain20122 on 2014-01-02
It is weird, but only happens with .zip files. tar.gz files do extract to their own directories. pcmanfm still uses FileRoller but FR doesn't behave this way in Nautilus (I just logged into a second lxde desktop to check this so Fileroller is the same one in Unity)

Perhaps someone has already filed a bug report against pcmanfm?  The closest thing I have found on launchpad is [https://answers.launchpad.net/ubuntu/+source/pcmanfm/+question/214574](https://answers.launchpad.net/ubuntu/+source/pcmanfm/+question/214574), it is not really a bug report.

---

