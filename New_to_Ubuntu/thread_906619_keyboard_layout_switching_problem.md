---
title: "keyboard layout switching problem"
date: 2008-08-31
forum: New to Ubuntu
---

### Post by almsamim on 2008-08-31
i have a problem with keyboard layout switching with all who installed ubuntu of mine:confused:
the problem is that after restarting 
the layout switching shortcut doesn't work [COLOR=Red]although it's checked  [/COLOR]
and i remove check and check again so it works
after every restart
:confused:

i hope i find  a solution for that , as i think it's from updates

---

### Post by unutbu on 2008-08-31
Is changing the keyboard layout on a system-wide level be acceptable?

---

### Post by almsamim on 2008-08-31
> **unutbu said:**
> Is changing the keyboard layout on a system-wide level be acceptable?

how on a system-wide level ?? :(
can u expalin ?

---

### Post by unutbu on 2008-08-31
Your keyboard layout can be set by editing /etc/X11/xorg.conf. Changing xorg.conf will affect all users of the system. This is what I mean by "system-wide". If you are the only user of your machine, then this is okay. If there are other users then maybe this would not be okay.

---

### Post by almsamim on 2008-08-31
> **unutbu said:**
> Your keyboard layout can be set by editing /etc/X11/xorg.conf. Changing xorg.conf will affect all users of the system. This is what I mean by "system-wide". If you are the only user of your machine, then this is okay. If there are other users then maybe this would not be okay.

yes i wanna that way wide-system
but what should i do with xorg.conf?????????????????

---

### Post by unutbu on 2008-08-31
Take a look at [http://ubuntuforums.org/showthread.php?t=898912](http://ubuntuforums.org/showthread.php?t=898912).
Then, if it isn't clear what to do, follow the instructions in post #2: [http://ubuntuforums.org/showpost.php?p=5651956&postcount=2](http://ubuntuforums.org/showpost.php?p=5651956&postcount=2)

---

