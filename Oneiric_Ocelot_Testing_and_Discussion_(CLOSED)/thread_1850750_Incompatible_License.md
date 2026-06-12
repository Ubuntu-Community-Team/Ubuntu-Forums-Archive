---
title: "Incompatible License"
date: 2011-09-27
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by maryeliezka on 2011-09-27
Hi, everyone...I'm now trying Ubuntu Oneiric Ocelot Beta 1. After i do some update. I restart my Ubuntu, then find an error message like this: incompatible license. Then, I ended up in recovery mode and can't login like usual. Please, help me...all my task was put in the home folder

---

### Post by effenberg0x0 on 2011-09-27
Is it a Mac? 
I've seen this error message when updating a EFI system with a non-alternative ISO.
If that is the case, more info is here:
[https://help.ubuntu.com/community/UEFIBooting](https://help.ubuntu.com/community/UEFIBooting)

Regards,
Effenberg

---

### Post by maryeliezka on 2011-09-27
Nope, it's not MAC...I wonder how could it happen. I thinked maybe coz i updated the initframs...

---

### Post by effenberg0x0 on 2011-09-27
Do you have any other information you can provide? It would help if you could tell us what is the line you see right before the incompatible license error. It's not a common error message as far as I know.

Ok, before going any further: As you mention that all your important stuff is in your home folder and that you can get to recovery mode, I advise you to backup the important stuff. You can use a USB drive, etc. I wouldn't go further messing with the system before doing that.

If you can get to recovery, you probably can drop to a shell with networking. If that is the case, you could try applying latest updates (sudo apt-get update && sudo apt-get upgrade). Sometimes its all it takes.

Regards,
EFfenberg

---

### Post by maryeliezka on 2011-09-28
It happened after i upgraded several libraries....While i was updating it. I even got several warning from gtk. That's all i know...

---

