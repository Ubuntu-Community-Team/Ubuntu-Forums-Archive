---
title: "[SOLVED] Permissions getting annoying."
date: 2008-06-04
forum: New to Ubuntu
---

### Post by jhmiller42 on 2008-06-04
I've had to edit more than a few config files to get this rig running with 8.04, so I've gotten somewhat used to the terminal commands necessary to edit a file. But if I navigate to a file in File Browser and open it using the GUI, I can't save anything in gedit because I "do not have the permissions necessary."

Well, why the hell doesn't it just ask for the password then? Is there any way to do this without resorting to the frigging terminal?

---

### Post by Martje_001 on 2008-06-04
Try this:

ALT+F2 --> gksudo gedit

---

### Post by wolfen69 on 2008-06-04
navigate to it with root permissions.
```
gksudo nautilus
```

---

### Post by jromer on 2008-06-04
In the terminal I launch nautilus (that's the default file browser) with the sudo command

gksudo nautilus

that will launch the file browser and allow for editing of files via gedit.

---

### Post by drs305 on 2008-06-04
Everyone else has told you the commands. I've placed "sudo" shortcuts on my top panel for nautilus (gksudo nautilus) and gedit (gksudo gedit). I use red icons for each one so I know when I open these I will be able to work with system files and others which don't belong to me. I made them red because it's possible for me to do damage in this mode. ;-)

---

### Post by jhmiller42 on 2008-06-04
Thanks, that last bit will be damned helpful. It was getting annoying, when I didn't know precisely where a file was, to find it in nautilus and then have to open a terminal. Anyhow, problem solved. Thanks.

---

### Post by sayakb on 2008-06-04
Please mark the thread as solved.
(Thread tools->Mark thread as solved)

---

