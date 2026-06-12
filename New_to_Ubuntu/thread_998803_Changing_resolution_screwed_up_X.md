---
title: "Changing resolution screwed up X"
date: 2008-12-01
forum: New to Ubuntu
---

### Post by faraz_k86 on 2008-12-01
I installed kubuntu 8.10 and by default it was on a very high resolution. So I changed it to 1024 X 786, which was normal for my 17" monitor.

When i pressed apply, the screen got screwed up like every thing was 5 times bigger and then it just hung there.

I restarted X by ctrl alt and backspace but that was not reponding.

I had to reset my system. when i restarted kubuntu it was the same problem, everything was 5 times bigger and the system froze..

help..

---

### Post by taurus on 2008-12-01
Boot into recovery mode from GRUB menu and at the prompt, reconfigure your X server again with

```
dpkg-reconfigure -phigh xserver-xorg
shutdown -r now
```

---

### Post by arochester on 2008-12-01
If you boot into recovery mode from GRUB menu there is an option: Try to recover XServer. I would try that first.

---

### Post by alienexplorers on 2008-12-01
Restart in recovery mode and when the selection box comes up select xfix.  When complete click on resume normal boot.

---

