---
title: "Problem with G/Rsync ..."
date: 2019-09-21
forum: New to Ubuntu
---

### Post by dagmann on 2019-09-21
I tried GRsync which works great, however whenever the backup job is done the dvd keeps starting up (spinning) and stopping, over and over, and near impossible to get the dvd ejected.
Is anyone familiar with G/Rsync and the use of a dvd as a backup?

I tried using Dolphin to eject the dvd but still no joy.
Dolphin shows the following message:

"An unspecified error has occurred: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken."


This command in Terminal seems to have fixed my issue with the dvd ejection:   eject -i 0
I then tested Dolphin ejection and it worked. For now anyway.

---

### Post by TheFu on 2019-09-21
Try
```
sudo eject
```
from a shell prompt/terminal.

Writing backups to optical media gets expensive quickly.  Whereas a $40 USB3 external HDD will get all the most critical files and easily hold 60+ days of versioned backups, if a real backup tool is used.

I'd be surprised if any backup tool didn't need **mkisofs** to properly write to optical media.

---

### Post by GhX6GZMB on 2019-09-21
I'm not sure you have a problem... writing a DVD can easily take half an hour or more (think video editing) and your description of activity on the DVD drive fits. Rsync has done its job, but the DVD burn process is still running.
Try to be patient.

---

### Post by dagmann on 2019-09-23
Solved

---

### Post by GhX6GZMB on 2019-09-24
Wonderful. Is the solution secret, or...?
This site is about being helpful to everyone.

---

### Post by dagmann on 2019-09-24
I gave up backing up on large files. But using a dvd formatted as a usb drive works great for what I am backing up.

---

