---
title: "hard disk full"
date: 2008-06-01
forum: New to Ubuntu
---

### Post by n7tzg on 2008-06-01
I just installed Hardy today, having been through Easy Eft, I had to update my way through Fiesty, Gutsy, and Hardy.  Now when I boot, I get the low disk space message, and wondered where the best place to get rid of useless fat is.  I have next to nothing installed on my system and 32Gb of hard disk space.  Any suggestions?  I had thought about the older kernel installations, and their associated files, but I don't know where they are located.

Any suggestions would be greatly appreciated.

Rob

---

### Post by tamoneya on 2008-06-01
well if youhave been using since FF you probably have a lot of packages downloaded.  Try cleaning them out with ```
sudo apt-get clean
sudo apt-get autoclean
```

---

### Post by iaculallad on 2008-06-01
> **n7tzg said:**
> I just installed Hardy today, having been through Easy Eft, I had to update my way through Fiesty, Gutsy, and Hardy.  Now when I boot, I get the low disk space message, and wondered where the best place to get rid of useless fat is.  I have next to nothing installed on my system and 32Gb of hard disk space.  Any suggestions?  I had thought about the older kernel installations, and their associated files, but I don't know where they are located.

Any suggestions would be greatly appreciated.

Rob

To gain more disk space, try to:

-Remove packages in your cache directory
```
sudo apt-get clean
```
-Try to remove old/unused linux-kernels using your Synaptics

---

### Post by n7tzg on 2008-06-01
I already ran apt-get clean, and it didn't seem to free any space.  I then went to /boot and removed all of the old vmlinuz, etc files.  I will try synaptics next, but I am not quite certain what I need to do there.

Rob

---

### Post by iaculallad on 2008-06-01
Just uncheck the old/unused kernel in the Synaptics.

---

### Post by n7tzg on 2008-06-01
Thank you all for your great suggestions.  I have applied them, and I at least have 3Gb (10%) free space now.  Thanks again

---

