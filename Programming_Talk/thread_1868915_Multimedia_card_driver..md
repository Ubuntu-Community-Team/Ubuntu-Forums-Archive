---
title: "Multimedia card driver."
date: 2011-10-25
forum: Programming Talk
---

### Post by sepoto on 2011-10-25
It is my understanding that in the 3x kernel of Linux there is an MMC driver that allows for the reading and writing of flash memory cards. Is this the case? If so how can I obtain the source code for the driver?

Thank You!

---

### Post by sepoto on 2011-10-25
It wasn't that hard. I just did this:

apt-get source linux-image-'uname -r'

I found what I was looking for.

---

