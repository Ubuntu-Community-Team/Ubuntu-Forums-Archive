---
title: "document lost in file process"
date: 2008-09-23
forum: New to Ubuntu
---

### Post by radiantarchon on 2008-09-23
i cut an pasted a documant to a usb drive but i guess i just pulled it out too fast. now it seems to be neither on the drive or the computer. is there any way to get it back. or am i just screwed.

---

### Post by az on 2008-09-23
From what filesystem did you take it from?

(Linux - ext3, NTFS or msdos)

---

### Post by radiantarchon on 2008-09-23
ext3

---

### Post by Bölvaður on 2008-09-23
remember, allways unmount extermal storage, no matter which os you are running.

---

### Post by drs305 on 2008-09-23
Plug the usb drive back in. Run this command. It will look throughout your system and mounted devices for the filename you enter. Replace **filename** with the name of the file you were transferring.

```

sudo find / -type f -iname **filename**

```

---

### Post by radiantarchon on 2008-09-23
well that didn't work but thanks anyway. ihave an hour to rewrite the paper. so i'm gonna get on it

---

