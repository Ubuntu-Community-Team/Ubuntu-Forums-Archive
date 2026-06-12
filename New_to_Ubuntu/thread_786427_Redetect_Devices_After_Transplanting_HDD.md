---
title: "Redetect Devices After Transplanting HDD"
date: 2008-05-08
forum: New to Ubuntu
---

### Post by punong_bisyonaryo on 2008-05-08
Hello everyone!

If I install Ubuntu onto a computer and transfer the hard drive it's on to another PC, would it be possible to redetect all devices? I've read this [thread]("http://ubuntuforums.org/showthread.php?t=653282") where this guy had to redetect his devices because he switched mainboards using update-pciids but will it also work for this case since practically all devices will have changed? From experience, I know this isn't possible in Windows as it will give you a BSOD.

Thanks!

---

### Post by jazzgossen on 2008-05-08
I don't think this should be a problem, if I understand the question correctly. I have used an Ubuntu installation installed on one computer after moving the HDD to a laptop instead. The only thing I hade to change were the graphics drivers, since the two computers used different graphics cards. Otherwise, no problem.

---

### Post by punong_bisyonaryo on 2008-05-08
Did yours do it automatically? I'm thinking I would be needing to do an update-pciids and a dpkg-reconfigure xserver-xorg. Is there anything else I have to do?

---

### Post by jazzgossen on 2008-05-09
I didn't update pciids. I edited my xorg.conf to use intel instead of via (changed one line), and installed the appropriate intel driver package. That's it. Though I can't guarantee it will be the same for all computers. But I think Ubuntu polls the hardware at boot time, so it should be all plug-n-play.

---

