---
title: "Spotify blocking me from anything else in terminal"
date: 2017-10-01
forum: New to Ubuntu
---

### Post by comapathic on 2017-10-01
hi im new to learning the whole coding process and messed up pretty bad while following what i thought were good spotify instructions and my terminal has been stuck on it and erroring out a lot. i keep getting the message, E: Type 'sudo' is not known on line 1 in source list /etc/apt/sources.list.d/spotify.list
E: The list of sources could not be read.
E: Could not open lock file /var/lib/dpkg/lock - open (13: Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?
and am unable to do anything else even install other programs. is there a way to fix this without doing a reinstall? i appreciate any help thank you.

---

### Post by jeremy31 on 2017-10-01
Post results for ```
cat /etc/apt/sources.list.d/spotify.list
```
You might have another update program open and that will cause the E: Could not open lock file /var/lib/dpkg/lock - open (13: Permission denied) or it might be because you didn't use sudo to update

---

