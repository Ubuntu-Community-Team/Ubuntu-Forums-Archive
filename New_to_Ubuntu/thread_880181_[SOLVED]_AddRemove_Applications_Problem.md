---
title: "[SOLVED] Add/Remove Applications Problem"
date: 2008-08-04
forum: New to Ubuntu
---

### Post by lunanueva on 2008-08-04
I just did a fresh install of 7.10 and am having problems with the add/remove application.  When i attempt to mark something for installation, i get a  'List of Applications is Not Available' message and i can't apply changes.  How do i resolve this problem???

---

### Post by tinny on 2008-08-04
Need some more info.

Whats the output of:

Open a terminal
```

sudo apt-get clean
sudo apt-get update

```

What application are you trying to install / remove?

---

### Post by lunanueva on 2008-08-04
All is fine now.  I had to download a bunch of updates.  Thanks for trying to help Tinny, I like your Bender image.

---

### Post by SunnyRabbiera on 2008-08-04
Yehh Add/remove is kind of primitive anyway, sure its a neat tool to start off with but there are better tools for managing packages.
There is an application called synaptic in the menu's under System > Administration > Synaptic package manager.
In terms of looks it might not look as fancy as add/remove but it is far more advanced.

---

### Post by lunanueva on 2008-08-04
Yeah, I know about synaptic.  The problem was that the Add/Remove application wasn't working properly because it needed some updates.  It's all good now.  Thanks for responding.

---

### Post by tinny on 2008-08-04
> **lunanueva said:**
> All is fine now.  I had to download a bunch of updates.  Thanks for trying to help Tinny, I like your Bender image.

Likewise :guitar:

---

