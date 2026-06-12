---
title: "Howto: Nano syntax highlight"
date: 2010-05-19
forum: Outdated Tutorials &amp; Tips
---

### Post by dragos2 on 2010-05-19
Recent versions of Ubuntu like 10.04 has nano syntax highlighting enabled.

But for previous versions just use:

To enable for one user:
```

cp /etc/nanorc ~/.nanorc
nano ~/.nanorc
#scroll to bottom and uncomment the languages that you want
# syntax highlighting for

```


To enable for all users edit /etc/nanorc direcly.

---

