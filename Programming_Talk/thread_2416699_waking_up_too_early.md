---
title: "waking up too early"
date: 2019-04-13
forum: Programming Talk
---

### Post by Skaperen on 2019-04-13
in some past programming i noticed that trying to make my program wake up up after a time interval it would wake up a bit early.  lately i have noticed the dclock program skipping times but taking extra time to do so.  strace showed me it was waking up even when the skips happened, so i suspect it woke up a bit early, obtained the time in seconds, and worked out the same seconds as it was before.  then the next wake-up may or may-not be early.  has anyone had this issue in their programs in Linux or any other OS?  i suspect there might be code in the kernel trying compensate for wake-up delays that can accumulate.

---

