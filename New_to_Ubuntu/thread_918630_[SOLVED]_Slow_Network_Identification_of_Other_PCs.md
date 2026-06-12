---
title: "[SOLVED] Slow Network Identification of Other PCs"
date: 2008-09-13
forum: New to Ubuntu
---

### Post by bobsmith2 on 2008-09-13
I use TightVNC to connect my Ubuntu PC to an XP PC (I use the XP PC as a DVR - it has no monitor or KB connected). I have a wired network. 

My problem is this: TightVNC on my Ubuntu PC connects to my XP PC instantly. But when I try to connect via Nautilius (to drag/drop a video to the XP PC), it takes a solid ten minutes before my Ubuntu PC "sees" the XP PC. Once connected everything is very fast. How can I get Nautilus to "see" my XP PC quickly? Thanks.

---

### Post by lovinglinux on 2008-09-13
That is weird, because both VNC and Nautilus connect instantly here. Ten minutes to find the other computer is way to much. 

Try typing the the complete path to the shared directory in Nautilus, like smb://192.168.1.2/media

---

### Post by bobsmith2 on 2008-09-13
Thanks lovinglinux. You set me on the right path. When I did what you suggested I connected instantly. So I just made "bookmarks" to the shared folders on my XP PC, and that works great. I didn't understand that "bookmarks" are like mapping drives in Windows (only easier).

---

### Post by lovinglinux on 2008-09-14
> **bobsmith2 said:**
> Thanks lovinglinux. You set me on the right path. When I did what you suggested I connected instantly. So I just made "bookmarks" to the shared folders on my XP PC, and that works great. I didn't understand that "bookmarks" are like mapping drives in Windows (only easier).

You are welcome. You can also create a button on your panels with the following command:

```
nautilus --browser smb://192.168.x.x/whatever/
```

I think "bookmarks" are just bookmarks.

---

