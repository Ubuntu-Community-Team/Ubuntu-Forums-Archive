---
title: "[SOLVED] No sound on youtube/websites after upgrade."
date: 2008-07-16
forum: New to Ubuntu
---

### Post by ninja senses on 2008-07-16
I just upgraded to hardy heron(was on gutsy) and Everything went good with the switch except for the sound on websites and movie players such as youtube.  Can anyone help?

---

### Post by Blahblah54 on 2008-07-16
Do you have libflashsupport installed? If not I would give that a try, seems to work for a lot of people.

---

### Post by RomeReactor on 2008-07-16
Hi. Does Flash work aside from this problem? If so, close Firefox and try installing **libflashsupport**--look for it in Synaptic (System->Administration->Synaptic); or to install it from the terminal:
```
sudo aptitude install libflashsupport
```

Now open Firefox again.

EDIT: Hurmm... too slow...

---

