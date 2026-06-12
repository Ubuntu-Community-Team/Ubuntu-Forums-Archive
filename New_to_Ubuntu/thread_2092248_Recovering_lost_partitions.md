---
title: "Recovering lost partitions"
date: 2012-12-07
forum: New to Ubuntu
---

### Post by Amjad88 on 2012-12-07
This is my first time using Ubuntu. I had 5 partitions with Windows XP installed on one of them, at the Ubuntu install options I chose to replace the Windows installation with the Ubuntu installation at which point I immediately noticed that Ubuntu is deleting my partitions so I pressed the restart button before it began to format the drive. When I boot from CD now I only get one inaccessible 500 GB partition. No format has taken place on the drive but I can't access my data because Ubuntu deleted all the partitions. Is there anyway to restore my data?

Thank you.

---

### Post by audiomick on 2012-12-07
I think your chances are fairly good of getting your partitions back. I haven't had to do this, but from what I have read, it should be possible. Most important is to not try and write to the drive in any way at all until you can do the recovery stuff.

Here are a couple of pages with some info.
[https://help.ubuntu.com/community/DataRecovery]("https://help.ubuntu.com/community/DataRecovery")
[http://askubuntu.com/questions/186193/deleted-partition-recovery]("http://askubuntu.com/questions/186193/deleted-partition-recovery")

Regarding the installation process: If you are wanting to install to a specific partition and to retain some other partitions on the drive that are on OS installs, you need to go into the manual partitioning option during the install process. Where you can choose "replace windows" or "beside windows", you need to choose "something else". That will get you into the partitioning tool, where you can work on your partitions individually, create new ones and whatever. There, you can tell it to install to one partition and leave the rest alone, or you can create mount points where you can mount your existing partition to your new install without formatting them.

---

### Post by Amjad88 on 2012-12-07
Thank you very much. Problem was solved and precious data restored.

---

