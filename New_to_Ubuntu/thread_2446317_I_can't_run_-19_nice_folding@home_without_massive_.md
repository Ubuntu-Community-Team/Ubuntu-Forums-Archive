---
title: "I can't run -19 nice folding@home without massive lag in programs"
date: 2020-06-28
forum: New to Ubuntu
---

### Post by lukensmall on 2020-06-28
I'm running 20.04 LTS and I can't run anything along with wine and itunes renice()ed to -10 without massive lag (pulseaudio is already high priority). This is shouldn't happen. A very low priority nice()ed 19 folding@home, nor firefox, shouldn't interfere with high priority programs.

---

### Post by Holger_Gehrke on 2020-06-28
I do believe the problem is itunes. If you look at it's various entries on [wine's appdb]("https://appdb.winehq.org/"), you'll find lots of reports on problems and bad performance. The only reason to use it at all is to buy music from Apple's store, for everything else there's better, native programs.

Holger

---

