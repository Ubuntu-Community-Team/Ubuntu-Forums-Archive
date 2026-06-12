---
title: "background screwy after wake"
date: 2020-07-21
forum: New to Ubuntu
---

### Post by jrbwhippets on 2020-07-21
I'm newish to Ubuntu. I am probably using the wrong search terms to look for help. I'm running 20.04 on a Lenovo W510, but this problem occurred with my previous install of Ubuntu (18? the last LTS): my computer goes to sleep, and when I wake and log in, the background is screwed up.

[IMG]https://live.staticflickr.com/65535/50138336532_afcd719862_b.jpg[/IMG]

I'm using the recommended NVIDIA driver:
[IMG]https://live.staticflickr.com/65535/50138115586_fab58863b4_b.jpg[/IMG]
Should I try the X.org driver? Any other hints?

Thanks in advance!

---

### Post by #&amp;thj^% on 2020-07-21
Known and on-going problem for Debian based OS's
Try from a console or Terminal:
```
gnome-shell --replace
```

---

### Post by jrbwhippets on 2020-07-21
Ran it, system crashed, forced logout. Logging in, of course, fixed the issue... until the next time it hibernates.

Thanks for letting me know it's a known issue!

---

### Post by jrbwhippets on 2020-07-28
I have been trying a couple extra ways of making wake on suspend work, and I saw a post about editing GRUB to include a line forcing the windows driver to nouveau. I tried it, and it does seem to have fixed the problem! However, my screen res is now 640 x 480. *groan*

I have a hunch that this knowledge might help, though, to pin down how to fix the problem? Anyone?

---

