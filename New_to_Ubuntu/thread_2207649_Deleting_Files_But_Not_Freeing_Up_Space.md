---
title: "Deleting Files But Not Freeing Up Space?"
date: 2014-02-24
forum: New to Ubuntu
---

### Post by Chris_Corbett on 2014-02-24
Hi,
I'm having an issue with the media server I'm running at home.
I am running Ubuntu Server edition on it and I have a 250GB HDD and a 2TB HDD in the server. The 2TB server is where the majority of the media is stored and as such it has become full, because of this I decided it was time to clear some space and delete some media that wasn't being watched/used. However after deleting some TV series and movies than space was not being freed up and I have no idea why.

As you can see in the image below, there should be roughly 80GB free however it registers as 100% full. 
Am I missing something obvious?

Thanks,
Chris.

[ATTACH=CONFIG]250645[/ATTACH]

---

### Post by tgalati4 on 2014-02-24
There is probably a Trash Can that needs to be emptied.  

Open a terminal and post the following:

```
df -h /dev/sdb
```

It could take a while to release the inodes and show the space as freed up.  How much did you delete?

It's not a good idea to let linux file systems get to 100% full.  Bad things happen.

---

### Post by Bucky Ball on 2014-02-24
> **tgalati4 said:**
> There is probably a Trash Can that needs to be emptied.  



+1. I had exactly the same problem and once the trash was emptied, fine. You probably aren't running a desktop environment on a server, but if you are, simple as opening the trash and emptying.

---

### Post by monkeybrain20122 on 2014-02-25
The trash can is an idiotic design. If I want to delete something I want it gone, not to be moved to another folder. If you are running a desktop environment the file manager usually provides a way to add an option like "delete for real" in the right click menu. e.g in Nautilus it is in File > Preferences > behaviour, there is a similar option in dolphin, in Pcmanfm you can configure delete to bypass trash can etc.

---

