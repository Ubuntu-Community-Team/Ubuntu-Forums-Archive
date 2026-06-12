---
title: "[SOLVED] Viewing data tracks of audio CD's"
date: 2008-06-12
forum: New to Ubuntu
---

### Post by oronte on 2008-06-12
I'm using version 8.04 64 bit and I can't seem to see the data tracks of audio CD's anywhere. Only Grip reports that there is a data track on the CD. Sound Juicer does not recognise the data track at all. When I open it up in Nautilus it shows me the wav files but noting else. If I look in /cdrom or /media/cdrom directories I can't see anything at all. Please help.

---

### Post by helicase on 2008-06-12
You have to mount the cd to see the data track. Open a terminal and execute the following command:

```
sudo mount /dev/cdrom
```

The track should now be visible in /media/cdrom

---

### Post by oronte on 2008-06-13
Thanks for that. I would have thought such an option would be available in Nautilus, but no. And for others like me, I've figured out to unmount the cd you use:
sudo eject /dev/cdrom

---

