---
title: "[SOLVED] Installing Flock"
date: 2008-06-07
forum: New to Ubuntu
---

### Post by anderskitson on 2008-06-07
I recently installed flock from these instructions [https://help.ubuntu.com/community/InstallingFlock](https://help.ubuntu.com/community/InstallingFlock) , everything seem to go fine, but whenever i try to launch flock it just says starting and then it closes. I tried a restart but still nothing any help?

---

### Post by MattBD on 2008-06-07
I wouldn't install Flock from the website - there's a deb package available at [http://www.getdeb.net/app/Flock](http://www.getdeb.net/app/Flock) which will make it a lot easier.

---

### Post by anderskitson on 2008-06-07
Allright will try, any idea why it wouldnt work?

---

### Post by MattBD on 2008-06-07
> **anderskitson said:**
> Allright will try, any idea why it wouldnt work?

None, I've only ever used the deb package from GetDeb. It's always a bit of a pain if you install something using the Linux binaries - better to go with a deb package if you can get it.

---

### Post by anderskitson on 2008-06-07
Thanks worked great

---

### Post by ikarus2k on 2008-06-07
You need libstdc++5 to run Flock (install it via Synaptic). Mine works 1A OK :D.

You can find further instructions in the [Flock FAQ]("http://flock.com/faq/show/30#q_9069").

---

