---
title: "Recently switched over from Windows and I'm encountering an odd issue with Firefox"
date: 2023-09-26
forum: New to Ubuntu
---

### Post by afflicted on 2023-09-26
Hi, I get this intermittent and odd glitch when I use Firefox and I don't know what's causing it or how to fix it. I can tell when Firefox has gone into it's glitched state because you see black triangles in the corners of its window. This hasn't happened with any other application. I have the default Ubuntu Snap version of Firefox installed. In the linked video I try to resize the window but as you can see it's all glitched out. I then pull a tab to create a new window and everything works as it should but the original window remains glitched. The only way for me to fix it is to close Firefox and re-open.

[https://youtu.be/Gj-qUiFHoQs](https://youtu.be/Gj-qUiFHoQs)

My specs:
[IMG]https://i.imgur.com/p8Bi8H3.png[/IMG]

---

### Post by ActionParsnip on 2023-09-26
What is the output of
```

apt-cache policy firefox

```

---

### Post by afflicted on 2023-09-26
```

firefox:
  Installed: 1:1snap1-0ubuntu2
  Candidate: 1:1snap1-0ubuntu2
  Version table:
 *** 1:1snap1-0ubuntu2 500
        500 http://us.archive.ubuntu.com/ubuntu jammy/main amd64 Packages
        100 /var/lib/dpkg/status

```

---

