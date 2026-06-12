---
title: "[SOLVED] windows pop up at login"
date: 2008-06-18
forum: New to Ubuntu
---

### Post by Zopiac on 2008-06-18
when i login to my main account, opera, nautilus, and pidgin all pop up. I had 'remember windows at login' checked, but its been a while since ive unchecked it! nautilus isnt even my file browser anymore, thunar is. i have it set that pidgin opens at login, so i can understand that. is there a way to have it open minimized, though? Anyways, ive had this problem for a long time. can ANYONE help???

---

### Post by sdennie on 2008-06-18
If you are still using gnome, you should be able to fix that by shutting down all applications and going to System->Preferences->Sessions->Session Options and clicking the big button that says "Remember Currently Running Applications" (which will be basically none).

---

### Post by Zopiac on 2008-06-18
> **vor said:**
> If you are still using gnome, you should be able to fix that by shutting down all applications and going to System->Preferences->Sessions->Session Options and clicking the big button that says "Remember Currently Running Applications" (which will be basically none).

shutting down all applications....like kill processes? or just close them

---

### Post by sdennie on 2008-06-18
Just closing all the windows should be sufficient.  The idea is that you are going to take a "snapshot" of the running applications and start those every time you login.  If you have no running applications when you take that "snapshot", nothing should be started at login time.

---

### Post by Zopiac on 2008-06-18
well, now awn does not open, even though it is listed under the startup programs. perhaps i have the command wrong?

---

### Post by sdennie on 2008-06-18
I'm not sure why AWN wouldn't run but, if you go through the original process with AWN open, it should save AWN as one of the applications to run at startup.

---

### Post by Zopiac on 2008-06-18
> **vor said:**
> I'm not sure why AWN wouldn't run but, if you go through the original process with AWN open, it should save AWN as one of the applications to run at startup.

it was open :/

---

### Post by tjwoosta on 2008-06-18
this is the proper awn command

```
avant-window-navigator
```

---

### Post by Zopiac on 2008-06-18
> **tjwoosta said:**
> this is the proper awn command

```
avant-window-navigator
```

alright, it was correct...but still nothing

---

