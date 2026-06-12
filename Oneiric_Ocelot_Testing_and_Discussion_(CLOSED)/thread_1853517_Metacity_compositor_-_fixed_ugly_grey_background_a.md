---
title: "Metacity compositor - fixed ugly grey background at session startup"
date: 2011-10-02
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by lucazade on 2011-10-02
Who is using unity-2d session with metacity-compositor enabled, in order to have a transparent UI, 
should have seen the *horrible* plain grey screen after plymouth (or after lightdm if autologin is not enabled) and 
before the wallpaper is actually loaded.

Well... i've uploaded a fixed metacity package in my ppa that solves this... going to open a bug report on launchpad and propose a patch.

Not a vital issue but now at least bootup is flickerless.

[https://launchpad.net/~lucazade/+archive/metacity-backport](https://launchpad.net/~lucazade/+archive/metacity-backport)

---

### Post by lucazade on 2011-10-02
[https://bugs.launchpad.net/metacity/+bug/864779](https://bugs.launchpad.net/metacity/+bug/864779)

---

### Post by mc4man on 2011-10-02
Will have to give your ppa a try later today. 
(is it just my browser or are the 'affects' on your bug report slightly messed up?

---

### Post by lucazade on 2011-10-02
yep.. you're right.
I should have filed the bug against metacity and affecting also unity-2d projectg.. but I did the opposite :/

---

### Post by mc4man on 2011-10-02
by messed I mean screen

---

### Post by lucazade on 2011-10-02
ah no... I don't have that issue.
the affect box is well displayed here.

---

### Post by mc4man on 2011-10-02
something to do with maxed vs. non-maxed window..
If you want to set back to unity-2d page you should be able to, I don't want to mess w/ your bug report or would give it a try

---

### Post by MacUntu on 2011-10-02
Is this metacity for sure? Can I dupe that one then: [https://bugs.launchpad.net/unity-2d/+bug/860638](https://bugs.launchpad.net/unity-2d/+bug/860638) ?

---

### Post by lucazade on 2011-10-02
> **MacUntu said:**
> Is this metacity for sure? Can I dupe that one then: [https://bugs.launchpad.net/unity-2d/+bug/860638](https://bugs.launchpad.net/unity-2d/+bug/860638) ?

yes..it is the same issue.. can mark as dupe!

---

### Post by Harry33 on 2011-10-02
Thank Lucazade for this fix.

I do not have Unity installed at all, but occasionally when gnome-shell cannot be started and the fallback session (gnome-panel) gets loaded instead, I see this ugly light gray flickering before DE is ready.
I use nvidia-current. I do not use Plymouth at all.

Now after your update, this flickering is gone. It works well.

---

### Post by lucazade on 2011-10-03
> **Harry33 said:**
> Thank Lucazade for this fix.

I do not have Unity installed at all, but occasionally when gnome-shell cannot be started and the fallback session (gnome-panel) gets loaded instead, I see this ugly light gray flickering before DE is ready.
I use nvidia-current. I do not use Plymouth at all.

Now after your update, this flickering is gone. It works well.

You're welcome, glad it is useful

---

