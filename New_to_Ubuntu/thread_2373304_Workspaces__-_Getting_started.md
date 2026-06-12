---
title: "Workspaces  - Getting started"
date: 2017-10-05
forum: New to Ubuntu
---

### Post by sterator on 2017-10-05
I've tried using the Workspace tutorial (  [https://help.ubuntu.com/stable/ubuntu-help/shell-workspaces.html](https://help.ubuntu.com/stable/ubuntu-help/shell-workspaces.html)  ) but I don't see what the tutorial says to look for; I have no Behavior Tab in the Personal section in either of the items named, "System Settings."

Any suggestions on how to get up to speed on this? It can't be that hard.

Thank you!

---

### Post by again? on 2017-10-05
System settings > Appearances > behaviour tab

Still can't find...
What release and session are you using.
Post the output of these 2 terminal commands.
```
lsb_release -a
echo $DESKTOP_SESSION
```

---

### Post by sterator on 2017-10-05
17.04. I am using the Cinnamon DTE..does that impact what settings I'm allowed to see?

No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 17.04
Release:    17.04
Codename:    zesty





$DESKTOP_SESSION
cinnamon

---

### Post by deadflowr on 2017-10-05
> 17.04. I am using the Cinnamon DTE..does that impact what settings I'm allowed to see?
Yes, very much so.
Cinnamon has it's own settings which are different from the default for Ubuntu.
(which is what the tutorial shows)

See if Left_ctrl +Left_alt + Up arrow key still opens the workspace expo (overview).
If it still does, then at the right, usually, you can press the + sign to add more.

I don't use cinnamon, I have before, but not in a while so not sure if that still works.

---

### Post by sterator on 2017-10-05
OK..so, Ctrl-Alt-(arrow) does make things happen..I can see all the work  spaces, go to specific ones, and I presume create new ones...I suppose  that assigning an application to a space is done best from the  application's icon in the toolbar?

Thank you...this was very simple. You helped greatly!

---

