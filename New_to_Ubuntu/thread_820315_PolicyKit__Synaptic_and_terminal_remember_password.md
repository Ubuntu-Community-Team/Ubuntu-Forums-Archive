---
title: "PolicyKit : Synaptic and terminal remember password between reboots"
date: 2008-06-06
forum: New to Ubuntu
---

### Post by Gourgi on 2008-06-06
is it possible to make synaptic and gnome-terminal to remember and don't ask my password permanently ?
i tried policykit but didn't find anything usefull :(

also where can i find policykit documentation ?
ubuntu help/wiki and google don't give much for this

thanks in advance

---

### Post by billgoldberg on 2008-06-06
Yes, you could enable your root account.

But it's disabled for a good reason.

Read more on it here (including how to enable it)

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by sayakb on 2008-06-06
You can edit the sudoer's file by:
```
sudo visudo
```

But it's much more "secure" to leave them the way they are.

---

### Post by Gourgi on 2008-06-06
i know this is less secure that's why i need it only for terminal & synaptic
how i should edit the sudoers in order to limit my account  to these only rather than ALL

i 've done this limitation in an earlier Hardy release (alpha 5 i think) using GUI Policy kit. Then it had some options like "remember only for this session, remeber for current login, remember forever" or something like this ... This is what i 'm looking for but those options doesn't seem to exist anymore (i had fresh install since).

anyway, thanks both of you 
(if noone else replies, i'll mark it solved)

---

### Post by sque on 2008-11-21
Sorry for bumping this very old thread. But I need to mention here that if someone can run terminal as root, he can do ANYTHING on the OS with root privileges.

---

