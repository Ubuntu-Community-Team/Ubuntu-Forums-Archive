---
title: "Uninstalled Plymouth now no splash"
date: 2014-07-26
forum: New to Ubuntu
---

### Post by Vombocorn on 2014-07-26
Hey, I intslled plymouth to change my splash. I uninstalled it cause I couldn't work out how to open it. I was told in the launcher but nothing was there. Now when ever I boot Ubuntu and shutdown Ubuntu it just comes up with a bunch of code.

Please tell me how to fix this.
Thank you!

---

### Post by grumblebum2 on 2014-07-26
What exactly did you install/uninstall and what instructions are you following?

---

### Post by Vombocorn on 2014-07-26
I installed then uninstalled Plymouth. Myself.

---

### Post by Vombocorn on 2014-07-26
Would re-installing Ubutnu help fix my problem. If so, how do I re-install Ubutnu without loosing all my data.

---

### Post by grumblebum2 on 2014-07-26
Plymouth is a default application so I don't understand where your getting this info to change your splash screen.
You really need to give better explanations or it's hard to help.
What release are you using?
Did you use the software center to install/uninstall plymouth?

What does this terminal command show...
```
update-alternatives --display default.plymouth
```

---

### Post by deadflowr on 2014-07-26
> **Vombocorn said:**
> Would re-installing Ubutnu help fix my problem. If so, how do I re-install Ubutnu without loosing all my data.

reinstall plymouth then run
```
sudo update-alternatives --config default.plymouth

```
from a terminal.
then select the plymouth theme if any is listed.
changes should take affect after a reboot.

---

