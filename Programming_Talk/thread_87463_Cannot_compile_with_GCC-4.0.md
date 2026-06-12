---
title: "Cannot compile with GCC-4.0"
date: 2005-11-08
forum: Programming Talk
---

### Post by Zingam on 2005-11-08
The compiler cannot find the <iostream> header, and when I type <iostream.h> it reports that it is depricated but cannot link the compiled objects.

C can be compiled normally but not C++. I have installed everything via Synaptic, that is necessary.

How should I install GCC properly?

---

### Post by thumper on 2005-11-08
sudo apt-get install build-essential

---

### Post by Zingam on 2005-11-08
I have installed build-essentials already. It doesn't work yet.

---

### Post by toojays on 2005-11-09
Try reinstalling libstdc++6-4.0-dev.

---

