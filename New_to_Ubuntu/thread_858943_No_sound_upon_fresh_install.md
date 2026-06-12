---
title: "No sound upon fresh install"
date: 2008-07-14
forum: New to Ubuntu
---

### Post by FrequencyHopping on 2008-07-14
I performed a fresh install of Ubuntu 8.04, moving up from 7.04. Unlike 7.04 where I had sound immediately without configuration, I have no sound whatsoever from either the headphone jack or speakers with 8.04. I've checked the sound levels on alsamixer, and everything looks fine. Any suggestions?

---

### Post by nowshining on 2008-07-14
go into the Sound menu and select Alsa.

---

### Post by sayakb on 2008-07-14
If selecting ALSA doesn't work, at a terminal, do:
```
sudo apt-get install linux-backports-modules-hardy
```

---

### Post by FrequencyHopping on 2008-07-14
Thanks, I got the problem resolved

---

