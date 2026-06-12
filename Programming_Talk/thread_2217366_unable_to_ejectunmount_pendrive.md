---
title: "unable to eject/unmount pendrive"
date: 2014-04-17
forum: Programming Talk
---

### Post by IAMTubby on 2014-04-17
Hello,
 How do I eject(unmount) my pendrive from the command line?

I tried doing the following, see output below
```

$ sudo umount /media/Transcend
umount: /media/Transcend: device is busy.
        (In some cases useful info about processes that use

         the device is found by lsof(8) or fuser(1))

```

```

$ sudo udisks --unmount /media/Transcend/
Device file /media/Transcend/ is not a block device: Resource temporarily unavailable
```

Thanks.

---

### Post by ofnuts on 2014-04-17
"umount" is the way to go. But it is complaining that one or more files on it is opened by some process. What often happens it that it is the working directory for some process (could be your script). If it's your script, then make it work with a different working directory. If it's some other process independtn of your script (file explorer, etc...) you have to handle the case manually. You can also try "umount -f"

---

### Post by IAMTubby on 2014-04-17
> **ofnuts said:**
> it is the working directory for some process (could be your script)
ofnuts, I was indeed running it from the same directory as the pendrive.
Ran it from another directory and worked just fine.

Marking the thread as solved.

---

