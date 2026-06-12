---
title: "Force mounting a NTFS volume"
date: 2008-08-25
forum: New to Ubuntu
---

### Post by Layzie Bone on 2008-08-25
Here's the deal I have a hard disk that has windows on, however, windows fails to boot. My objective is to be able to get the data off the drive. When I plug the drive into USB i get the following message.

"$LogFile indicates unclean shutdown...Operation not supported Mount is denied because NTFS is marked to be in use...if you dont have windows then you can use the force option   your responsibility"

---

### Post by mlentink on 2008-08-25
I'm not exactly sure what your question is....
The message indicates that the USB-drive was probably disconnected while some operation was performed. Do you still have a windwos pc around? If so, connect the USB-drive to the windows machine and then choose to 'safely remove' it. This should correct the problem. 
If you do not have a windows pc around, you can use the 'force' option, but do not be surprised to find errors afterwards.

---

### Post by drs305 on 2008-08-25
The best option is to remount in Windows and then shut down cleanly. You can force mount it in linux. The other option is to install and run the following to clear the error messages:
```
sudo aptitude install ntfsprogs
ntfsfix /dev/*partition.name*

```

It resets the journal but will not actually repair any 'damage' to the disk. It should clear the error and allow a normal mount. You may need to use 'sudo' with the ntfsfix command...

---

