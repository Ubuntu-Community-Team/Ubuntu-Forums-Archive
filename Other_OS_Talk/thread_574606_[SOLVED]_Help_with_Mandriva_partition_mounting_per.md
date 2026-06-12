---
title: "[SOLVED] Help with Mandriva partition mounting permissions"
date: 2007-10-13
forum: Other OS Talk
---

### Post by 67GTA on 2007-10-13
I recently installed Mandriva 2008. It picked up my Kubuntu partition in fstab. When I open the Kubuntu partition from within Mandriva, most of my /home folders are locked. I have never had this happen before. I'm not sure if Mandriva is the culprit, or some obscure setting in Kubuntu I've changed. When in Kubuntu I get a uuid error when I click on the Mandriva icon. How do I get full read/write access in each direction?

---

### Post by pelle.k on 2007-10-13
It's really simple. Ubuntu creates user/group id:s starting at 1000:1000, and mandriva 500:500.

Change your uid/gid in /etc/passwd (in mandriva) and then chown everything in you home (chown -R, thats is recursively). Then reboot.
You might have to clean out /tmp as well.

[edit]you can actually create your user with 1000/1000 when creating it with userdrake (during installation), by accessing the advanced tab[/edit]

---

### Post by 67GTA on 2007-10-13
Change this:

shawnr:x:500:500:Shawn Rogers:/home/shawnr:/bin/bash

To this:

shawnr:x:1000:1000:Shawn Rogers:/home/shawnr:/bin/bash

in Mandriva?

---

### Post by 67GTA on 2007-10-13
Never mind, I got it. Thanks for the info.

---

