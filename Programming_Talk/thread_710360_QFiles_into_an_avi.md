---
title: "QFiles into an avi"
date: 2008-02-28
forum: Programming Talk
---

### Post by harold4 on 2008-02-28
I'm playing around with the kopete src, working on adding the ability to save yahoo webcam sessions.

If I have QFiles sitting in /tmp/<randomname>.tmp, which is a bmp, How would one go about adding bmp files in real time to an avi?

---

### Post by PaulFr on 2008-02-29
Does this help? **[http://www.mplayerhq.hu/DOCS/HTML/en/menc-feat-enc-images.html](http://www.mplayerhq.hu/DOCS/HTML/en/menc-feat-enc-images.html)**

---

### Post by harold4 on 2008-02-29
The right idea, but mplayer wants to use all the imgaes in the dir at once.

Ideally, I'd be able to have a process stay open and keep appending images to the avi file.

---

