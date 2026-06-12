---
title: "Dismounted boot drive"
date: 2012-02-07
forum: New to Ubuntu
---

### Post by NM020110 on 2012-02-07
I'm fairly sure that I misled someone with that title, but hopefully it worked.  My apologies if this was asked before.

I have successfully installed ubuntu to my external hard drive.  It boots fine, and runs a mite better than the windows installation on the same computer.  There is only one problem, at the moment.

Recently, the cord was damaged, and as a result the cord will very easily slide out of the port on the external hard drive, disconnecting it.  Now, I was wondering what happens if the hard drive that your operating system is installed on gets dismounted.  I know now that it appears to drop to a debug interface of some kind.

The mouse remains functioning, as does the clock and battery indicator.  I get a gnome interface, and can open nautilus, though I can find no files through nautilus.  Thus far I have been unsuccessful at bringing up a terminal.

Is it possible to re-mount the drive from this state, thereby avoiding the need for a hard reset of the computer?

If more information is requested, and I can obtain it, then it shall be provided.

---

### Post by cariboo on 2012-02-11
You should just be able to mount the drive using something like the following command:

```
sudo mount /dev/sdb1 /
```

substitute your device label for the one in the example above.

---

