---
title: "libnux update"
date: 2012-05-23
forum: New to Ubuntu
---

### Post by Nadarasan on 2012-05-23
how to update libnux and libnux common2?

---

### Post by Rex Bouwense on 2012-05-23
What version of Ubuntu have you installed and how did you install libnux?

---

### Post by Nadarasan on 2012-05-23
ubuntu12 and installed libnux while installing ubuntu.

---

### Post by MG&amp;TL on 2012-05-23
If you want the latest, grab it from launchpad, and build from source.

If you just want normal updates, just update from update manager. Why the fuss about libnux? It's quite an obscure package.

---

### Post by roelforg on 2012-05-23
Try this in the terminal:
```

sudo apt-get update
sudo apt-get install libnux-2.0-0 libnux-2.0-common

```

---

