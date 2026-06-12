---
title: "Ubuntu won't load"
date: 2008-09-02
forum: New to Ubuntu
---

### Post by mercenary10 on 2008-09-02
I was logged in just fine yesterday, but today, after the ubuntu screen with the loading bar disappears, the screen simply goes black and nothing happens. I sat there for 10 minutes, just waiting. I googled it, and saw some similar issues that were fixed by logging in using CTRL+ALT+F2, but that did nothing. I can login to windows just fine, but ubuntu just sits there.

Any help would be appreciated, thanks in advance.

---

### Post by dracayr on 2008-09-02
try booting via recovery mode and choose "fix X server"


dracayr

---

### Post by mercenary10 on 2008-09-02
> **dracayr said:**
> try booting via recovery mode and choose "fix X server"


dracayr

That worked, but now when I login, after the beige screen I get a black screen then a white screen. It just sits at the white screen, I tried the fix X server option again, still nothing. 

Thanks

---

### Post by lapubell on 2008-09-02
pressing Ctrl+Alt+F1 will bring you to a different command line prompt.  You can log in there.  Does this work?

If no, let me know.  If yes...

try dpkg-reconfigure xserver-xorg.

---

### Post by mercenary10 on 2008-09-02
> **lapubell said:**
> pressing Ctrl+Alt+F1 will bring you to a different command line prompt.  You can log in there.  Does this work?

If no, let me know.  If yes...

try dpkg-reconfigure xserver-xorg.

I can't login there. Before this happened, I enabled some restricted video drivers and was downloading updates, but when I woke up my PC was off.

When I try to login there, I can enter my userID but it won't let me type my password.

---

