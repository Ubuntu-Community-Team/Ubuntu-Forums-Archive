---
title: "Measurement velocity which I copy data to inside pen drive"
date: 2019-03-16
forum: New to Ubuntu
---

### Post by sed_faster on 2019-03-16
Hello,

Exist some software to measurement the velocity I can copy file to the pen drive? The process copy it is faster (to 2GB almost 30 seconds). But If I try unmount the pen drive, through arrow in file manager (Nautilus) this message appear on top screen ([https://snag.gy/zxGBLE.jpg](https://snag.gy/zxGBLE.jpg)). The pen drive unmount after this almost 2 minutes. Why this happen? My system this is it: [https://snag.gy/zB0sFi.jpg](https://snag.gy/zB0sFi.jpg)

Thanks

---

### Post by Impavidus on 2019-03-17
That suggests a data transfer rate of about 10MB/s, which is slow, but not implausible for an old usb drive.

The file manager reports the copy is complete when it has written all contents to the file on the usb drive and has closed it. From that moment, when another application opens the file on the usb drive, it will find the new contents. However, the file hasn't actually been written to the usb drive, as it is cached by the OS. If you modify or delete the file before it was completely written to the usb drive, some parts of the old version never get there. Only after a sync it is guaranteed that the data is on the drive. This sync happens automatically when you unmount the usb drive.

I found [here]("https://unix.stackexchange.com/questions/48235/can-i-watch-the-progress-of-a-sync-operation") how you can monitor the sync operation.

---

