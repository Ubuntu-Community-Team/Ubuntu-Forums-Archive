---
title: "can't find the iso image"
date: 2008-10-10
forum: New to Ubuntu
---

### Post by JordanLeach on 2008-10-10
i downloaded ubuntu 8.04 from ubuntu.com and i can't find the iso image to burn onto a cd.
someone please tell me why i'm an idiot!

---

### Post by SunnyRabbiera on 2008-10-10
What is your primary browser?

---

### Post by JordanLeach on 2008-10-10
opera

---

### Post by drs305 on 2008-10-10
The default is often either ~/ (/home/loginname) or to your Desktop ( /home/loginname/Desktop).

You can do a search of your entire system with:
```
sudo find / -name *.iso
```

---

### Post by JordanLeach on 2008-10-10
thats the thing though. i know where it downloaded to, i found the folder but the iso image file just isn't in that folder. sorry i didn't specify that.

---

### Post by SunnyRabbiera on 2008-10-10
Hmm. it should by default save your iso to the desktop or my doccuments.
Are you sure the download was complete?
And did you change any of the settings under opera?

---

### Post by MusicMastaMike on 2008-10-10
Sorry if this sounds like a stupid comment, but are you sure you clicked Save and not Open?  It's an all-too-common mistake.

---

### Post by sleepingdragon on 2008-10-10
I discovered a bug with Opera 9.5. It sometimes fails to move a download to your normal destination folder. Try looking in **/home/yourusername/.opera/cache4/temporary_download/**

EDIT: Forgot that Opera has now upgraded to 9.6, that seems to have resolved the problem for me. It solved a few video quirks with Flash v10 too.

---

### Post by JordanLeach on 2008-10-10
i never thought of trying with a different browser, but i did and it worked so thank you very much

---

### Post by zvacet on 2008-10-10
@ **JordanLeach**

Do you have** Opera downloads** folder in your home directory?

P.S. Upgrade Opera.Version 9.6 in availabe.

---

