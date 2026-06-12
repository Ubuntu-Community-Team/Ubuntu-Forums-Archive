---
title: "Flash Player for Chromium?"
date: 2016-11-22
forum: New to Ubuntu
---

### Post by Daveski17 on 2016-11-22
Is there any way that I can play flash videos on Chromium? I used to use the Pepper flash plug in in the Software Centre but that doesn't work now.

Thanks

---

### Post by slickymaster on 2016-11-22
Have you tried to install the adobe-flashplugin package from the Partners repository?

Load up the Software & Updates application and from the Other Software tab check the Canonical Partners option. After that, and in a terminal window run```
sudo apt update && sudo apt install adobe-flashplugin
```Once that done restart Chromium.

---

### Post by Daveski17 on 2016-11-22
OK, I'll check that out thanks.

---

