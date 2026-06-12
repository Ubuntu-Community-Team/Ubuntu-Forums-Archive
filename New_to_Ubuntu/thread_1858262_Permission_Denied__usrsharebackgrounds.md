---
title: "Permission Denied : /usr/share/backgrounds"
date: 2011-10-12
forum: New to Ubuntu
---

### Post by Krishna Murthy on 2011-10-12
Hi,

Whenever I try to copy pictures to /usr/share/backgrounds it says 'permission denied'.

How do I solve this ?

Thank you.

---

### Post by Pynalysis on 2011-10-12
> **Krishna Murthy said:**
> Hi,

Whenever I try to copy pictures to /usr/share/backgrounds it says 'permission denied'.

How do I solve this ?

Thank you.


Try this:
open a terminal window
type gksu nautilus
press enter

Navigate to and copy the files you want 
and paste them in /usr/share/backgrounds

The copy and paste are all done using the new instance of nautilus.

~Pynalysis

---

### Post by Perfect Storm on 2011-10-12
Like this:
```
sudo cp -r picturename /usr/share/backgrounds
```

---

### Post by unfinishedsweet on 2012-01-21
what should original permissions be? I have changed them and would like to get back to original state

---

### Post by grahammechanical on 2012-01-21
@unfinishedsweet

Please post your question as a new post. And please give more information. What files are you talking about? And what did you change the permissions to?

This question is about getting root or administrator access to folders and files (for editing). And we do that by using the gksudo command to open a special session of the file manager (nautilus) or gedit (a text editor).

Regards.

---

