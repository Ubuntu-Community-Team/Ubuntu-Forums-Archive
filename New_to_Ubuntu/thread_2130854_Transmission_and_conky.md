---
title: "Transmission and conky"
date: 2013-03-30
forum: New to Ubuntu
---

### Post by MikeJParry on 2013-03-30
Transmission reports different speed than conky.
Is there a way to monitor what bandwidth each app uses ?

---

### Post by DuckHook on 2013-03-30
Conky just uses system-level info, but samples at differing rates depending on how you programmed Conky. Transmission uses its own internal sampling code, not the system-level info, so I would not be surprised if there were discrepencies. I would rely on Transmission for all of your torrent traffic, but Conky for all else. You are not going to get an exact rate from any app. More like just a moving average or a snapshot at a given time.

---

