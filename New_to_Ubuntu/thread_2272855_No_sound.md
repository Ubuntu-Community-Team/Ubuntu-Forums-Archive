---
title: "No sound"
date: 2015-04-09
forum: New to Ubuntu
---

### Post by sandipan_biswas on 2015-04-09
After last update my ubuntu 14.04 lts sound not come from my computer. help

---

### Post by newb85 on 2015-04-09
Just making sure, you mean you had sound on Ubuntu 14.04 before, but last time you updated the software it stopped working?

For starters, have you checked the volume levels in alsamixer?  (In a terminal, type alsamixer and hit enter.  Make sure the Master and Speaker controls are turned up.)

If that doesn't work, give us more details on your sound card.  You can get the specifics by

```
sudo lshw -C sound
```

The lshw command doesn't change your machine, it just gathers info on the hardware (in this case, on the sound card.)  Post the results exactly.  

*It will prompt you for a password.  It's the password for your Ubuntu user account.  You won't get any visual feedback as you type.  That's normal, and for security reasons.*

---

