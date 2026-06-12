---
title: "Unable to copy files from Root Directory"
date: 2012-10-23
forum: New to Ubuntu
---

### Post by apascual89 on 2012-10-23
Hi, first post. I'm on Ubuntu 12.10, currently unable to copy or move files from my root directory to my Home directory. I'm trying get it a file off of my computer. It gives me the error : "Error while copying while copying the file into /home/Andres/Desktop" .

When I click on Show more details, it says Error opening file: Permission denied.

I used the gksu nautilus command and that was working yesterday, but for some reason it isn't today. 

Any help would be greatly appreciated.

---

### Post by dolphin194 on 2012-10-23
Are you booted from a Live CD?

---

### Post by apascual89 on 2012-10-23
> **dolphin194 said:**
> Are you booted from a Live CD?

No, I  did a full install. Thanks for the reply.

---

### Post by dolphin194 on 2012-10-23
Your account will need to be in the sudoers file. Make sure you have permission to run commands as root. You can also use the **cp** command with **sudo** to copy files through the terminal as a last resort. You can also boot from a Live CD and nautilus as root with **gksu** commands as root that way.

Another thing you can do is drop to a root shell by typing **sudo -s** and running nautilus through it.

---

### Post by apascual89 on 2012-10-23
OK I will try. Is there any reason why gksu nautilus worked yesterday, but not today? I'm the only one that uses the computer and I did the setup.

---

### Post by dolphin194 on 2012-10-23
Well, the permissions could have changed. I have Ubuntu on a server computer, and when a new file is added to a directory, for some reason the permissions get set to something other than how I want them to be.

---

