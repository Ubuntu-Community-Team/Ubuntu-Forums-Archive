---
title: "[SOLVED] Deleted File"
date: 2008-06-04
forum: New to Ubuntu
---

### Post by F.R Mostert on 2008-06-04
Hi,

I am very new to linux and Ubuntu. I originally installed Ubuntu 7.10 and upgraded to 8.04.  While running updates I got a a broken package message and tried to fix with synaptic.  I eventually deleted the file and now I do not have any menu after startup can any one help me. I know how to get to dpkg can i fix this from there?
:):redface:
Regards

---

### Post by Oldsoldier2003 on 2008-06-04
> **F.R Mostert said:**
> Hi,

I am very new to linux and Ubuntu. I originally installed Ubuntu 7.10 and upgraded to 8.04.  While running updates I got a a broken package message and tried to fix with synaptic.  I eventually deleted the file and now I do not have any menu after startup can any one help me. I know how to get to dpkg can i fix this from there?
:):redface:
Regards

try this from a terminal
```

mv ~/.gnome2 ~/.gnome2_old
```

and then log out and back in. This should force gnome to recreate default settings

---

### Post by F.R Mostert on 2008-06-05
Thank you please tell me how to get to the terminal, must I do a safe start-up and go to dpkg?

---

### Post by F.R Mostert on 2008-06-16
Hi Me again I have tried the mv command but it tell me "no such file or directory"

---

### Post by alienexplorers on 2008-06-16
Go to you home directory and do a ls-la and look to see if .gnome2 is there.

---

