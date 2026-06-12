---
title: "Badger vs Gibbob?"
date: 2008-05-09
forum: New to Ubuntu
---

### Post by lesterness on 2008-05-09
So how come I could look into my external hard drive, half full of Windows files, with Breezy Badger, but not Gutsy Gibbon? 

Lester

---

### Post by adult swim on 2008-05-09
unmount your external drive
from terminal put in ```
sudo apt-get install ntfs-3g ntfs-config
```
mount external drive and see ntfs files
edit: if this doesnt work it sounds like the drive wasnt unmounted properly in windows so youll need to boot windows, plug in your external drive, click safely remove hardware and wait until it is ready to remove.  then unplug your external drive, boot ubuntu, plug in your drive and it should work.

---

### Post by LeoSolaris on 2008-05-09
That is rather odd, since Gutsy is supposed to have the better NTFS support. Might want to make sure NTFS-3G is installed, as well as libntfs. It may require configuring with ntfs-config.

Hope something in there helps!

---

### Post by muteXe on 2008-05-09
This worked for me:
[http://ubuntuforums.org/showthread.php?t=785263](http://ubuntuforums.org/showthread.php?t=785263)

Although I agree, when I was using Feisty it just picked up and automounted my windows partition automatically.  I assumed Hardy would do this as well.  Weird.
mute

---

