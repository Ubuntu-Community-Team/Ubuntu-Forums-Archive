---
title: "[SOLVED] How do I get &amp;quot;Admin&amp;quot; rights to move files?"
date: 2008-08-13
forum: New to Ubuntu
---

### Post by Ice Poll on 2008-08-13
Ice POll:

I clicked on applications in the bottom left corner of my screen and then clicked on Add/Remove programs and I had it Download and Install a game called Tremulous.

I made a mod (.cfg files) for this game in /home/<My name>/Desktop/<My name>/CFG_Files
And I want to move this mod (.cfg files) to /usr/share/games/tremulous/base
But it wont let me because I don't have Admin rights... But I only set one user and one password when I installed Ubuntu!  How do I get the Admin right I need to do this?

---

### Post by iaculallad on 2008-08-13
> **Ice Poll said:**
> Ice POll:

I clicked on applications in the bottom left corner of my screen and then clicked on Add/Remove programs and I had it Download and Install a game called Tremulous.

I made a mod (.cfg files) for this game in /home/<My name>/Desktop/<My name>/CFG_Files
And I want to move this mod (.cfg files) to /usr/share/games/tremulous/base
But it wont let me because I don't have Admin rights... But I only set one user and one password when I installed Ubuntu!  How do I get the Admin right I need to do this?

Open your terminal and input the command below:

```
gksudo nautilus
```

From there, you could move the file you wanted. Just be careful of what you move/delete when using this mode.

---

### Post by perlluver on 2008-08-13
> **Ice Poll said:**
> Ice POll:

I clicked on applications in the bottom left corner of my screen and then clicked on Add/Remove programs and I had it Download and Install a game called Tremulous.

I made a mod (.cfg files) for this game in /home/<My name>/Desktop/<My name>/CFG_Files
And I want to move this mod (.cfg files) to /usr/share/games/tremulous/base
But it wont let me because I don't have Admin rights... But I only set one user and one password when I installed Ubuntu!  How do I get the Admin right I need to do this?

Press alt+f2, then type gksu nautilus.  Be careful, you will have admin rights over everything.

---

### Post by ad_267 on 2008-08-13
[https://wiki.ubuntu.com/RootSudo](https://wiki.ubuntu.com/RootSudo)

---

### Post by Ice Poll on 2008-08-13
THANK YOU SO MUCH PERLLUVER!!!!!!!!!!!!!  That worked!!!!!!  YES!!!!!!  THANK YOU!!!!!!!:):):):):):):):)

---

### Post by Martje_001 on 2008-08-13
Please mark this thread as [SOLVED].

---

