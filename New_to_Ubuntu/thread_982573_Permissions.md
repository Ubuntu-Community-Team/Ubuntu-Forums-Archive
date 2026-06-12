---
title: "Permissions"
date: 2008-11-14
forum: New to Ubuntu
---

### Post by DMTSERVICES on 2008-11-14
I have hooked up a firewire drive and can't change the permissions from root to user to allow my windows machine to see it?

---

### Post by SunnyRabbiera on 2008-11-14
well you may have to enter super user do mode in a terminal to get what you need.
I am not 100% sure on how to do what you need to do but a good starting point is to open up a terminal and put in the command sudo

---

### Post by Mardoct909 on 2008-11-14
Let's open up the file manager as root. Open the terminal and type in:

```
gksudo nautilus
```

Great. Now we have a graphical interface for our task. Press the "go" button at the top, and press on "Computer"

Your device should be listed there as an icon. Right-click, go to permissions and edit as desired.

---

### Post by TheSiscoCoon on 2008-12-02
I have the same problem as the first guy. But with a USB flash drive. I changed the format from fat32 too ext3 and ever since then I can't save anything in it or create folders nothing. Tried changing formats around thinking it was that. But realized later that some how the Owner got changed from "user" to "root". I tried that last guys idea and found that doesn't work. Or at least that there isn't an option to change the "owner". "Properties" is grayed out even with the drive I have access already.

I know it is something probably so simple and stupid that it is right in front of my face. I just can't see it.

Sisco

---

