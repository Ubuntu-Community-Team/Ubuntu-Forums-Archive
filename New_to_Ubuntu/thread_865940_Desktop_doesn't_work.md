---
title: "Desktop doesn't work"
date: 2008-07-21
forum: New to Ubuntu
---

### Post by alican timur on 2008-07-21
All the icons on my desktop has disappeared, and i can't open up my desktop folder with nautilus. When I try to change the directory to Desktop in terminal, it shows fine and everything's there. Help please?

---

### Post by alican timur on 2008-07-21
and when i reboot and log in, it tries to open my home folder but it closes right back for like 10 times then it stops and my desktop is still not shown. i can't right click on my desktop too.

---

### Post by sharks on 2008-07-21
restore nautilus:
[www.psychocats.net/ubuntu/nonautilusplease](www.psychocats.net/ubuntu/nonautilusplease)

---

### Post by alican timur on 2008-07-21
nothing happened, it's the same.

---

### Post by sharks on 2008-07-21
have u changed ur filemanager to thunar and restore back to nautilus?

---

### Post by icarusfall on 2008-07-21
Yeah, I had this problem a while ago, eventually it went away, but I had to delete a few dot files in my home directory to force nautilus to restore itself. It's probably not the ideal solution, but it might be worth following the above tutorial to switch to Thunar, see if you can open up the desktop in Thunar, and then switch back to Nautilus.

---

### Post by alican timur on 2008-07-21
okay, i switched to thunar, and i can open up the desktop folder, but still can't see the desktop (the one when you get if you minimize everything).

in terminal, when i try to run nautilus, i get:
```

alican@Alican-HQ:~/Desktop$ nautilus
Initializing nautilus-share extension
seahorse nautilus module initialized

** (nautilus:8932): WARNING **: Unable to add monitor: Not supported
Segmentation fault

```

---

### Post by sharks on 2008-07-21
now restore nautilus using that link.

---

### Post by alican timur on 2008-07-21
i had already restored nautilus. i deleted a "scanner utility" shortcut from my desktop and it's back to normal now.

---

### Post by sharks on 2008-07-21
if ur question is solved please mark it solved from thread tools and thank the person who helped u by their posts by clicking on the STAR medal button under their post(not a must)

---

