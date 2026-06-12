---
title: "usb 4.1 gig mem stick"
date: 2008-05-23
forum: New to Ubuntu
---

### Post by philipluna66 on 2008-05-23
I have been using my memory stick to transfer data from one computer to my windows xp computer but my ubuntu doesnt recognise it any more. I have tried mounting in in the window option but nothing. before when I pluged it in it picked it up straight away. It still works in my windows xp

---

### Post by PmDematagoda on 2008-05-23
Install ntfsfix with:-
```
sudo apt-get install ntfsprogs
```

Once that is done, do:-
```
sudo ntfsfix /dev/path-to-drive
```
Once ntfsfix is finished try mounting the drive again.

---

