---
title: "Hack xpdf or evince?"
date: 2011-08-16
forum: Programming Talk
---

### Post by TheHimself on 2011-08-16
I would like to hack a pdf viewer to add "library" features to it. Xpdf is very fast to start but is slow for going from a page to another. Evince is slow to start but fast in moving from page to page. I was wondering if any of you knew what difference causes this and also which one is more suitable for hacking.

---

### Post by sanderd17 on 2011-08-16
xpdf only loads the page you see while evince loads all pages (or a big amount of them) in RAM at once. In Okular you can choose how big the caching is. You probably can set such an option for Evince somewhere too.

I have no idea which one is the easiest to hack.

---

### Post by cgroza on 2011-08-16
The best approach would be to look at the source code of both of them and see  which one's internal structure is more suitable for your project.

---

