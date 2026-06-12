---
title: "If I get virus on linux can it transfer to the windows parition?"
date: 2013-05-17
forum: Recurring Discussions
---

### Post by iseeu1001 on 2013-05-17
Okay so I have a 1tb on my laptop and I am interested in making dual boot with windows 8 and ubuntu but first I would like to know if I get a windows virus on wine can it be transferred over to my windows partition since they are on the same hard drive?

---

### Post by matt_symes on 2013-05-17
Thread moved to **security discussions**.

---

### Post by miegiel on 2013-05-17
> **iseeu1001 said:**
> Okay so I have a 1tb on my laptop and I am interested in making dual boot with windows 8 and ubuntu but first I would like to know if I get a windows virus on wine can it be transferred over to my windows partition since they are on the same hard drive?

Yes and no, it depends on how smart the virus is. That said, a virus would probably have to be that smart by accident. I can't imagine a virus "developer" would put time and effort into infecting a windows installation from a linux installation using wine. Still running .exe's you don't trust in wine isn't a good idea ;)

---

### Post by HermanAB on 2013-05-18
Short answer: No.

Long answer:
There are no viruses that actually work in Wine, although there possibly could be, but the virus writers are too lazy support Wine properly.

So unfortunately, if you want a virus to transfer from Linux to Windows, then you will have to do so manually using FTP or similar...

---

### Post by cariboo on 2013-05-18
With the last comment, this threads needs to be moved to [Recurring]("http://ubuntuforums.org/forumdisplay.php?f=302"), as this subject has been discussed numerous times.

---

### Post by 3rdalbum on 2013-05-19
Short answer: No.

Long answer: Noooooooooooooo.

Descriptive answer: Computer viruses aren't biological, if the code is not running (and modern viruses won't run on Wine) then it cannot spread of its own accord. It's not like you can use Wine for everything; Wine only runs a small percentage of Windows programs so the chance of even accidentally running a virus in Wine is pretty low, and of course even if you double-click on it it won't run long enough to do anything.

---

### Post by Bufeu on 2013-05-20
There's not malwares that actually works very well in Wine. I guess that they're too lazy to make the malware support Wine. But yes, some malware *can* run in Wine. And software executed via Wine have access to your home directory. So yes, a malware can log, delete and move files, but only within the home directory. Wine doesn't support Autorun, so if the malware adds itself to the Autorun, nothing really can happen.
Malwares for Windows simply won't work in Linux. But Linux malwares, malwares written for Linux systems, will work under Linux. The danger with Linux malwares is if they get root access. If a Linux malware gets root access, you are toasted.

---

