---
title: "Install Eclipse C/C++ on 10.10"
date: 2011-04-10
forum: Programming Talk
---

### Post by nikRbokR on 2011-04-10
I've been trying to get this to work for a while. I installed Eclipse from the software center with the intentions of adding the C/C++ plugin/module. Unfortunately, I couldn't figure out how to do that. Then I downloaded the tar.gz but couldn't figure out how to get that to install.

Any help would be appreciated.

---

### Post by nikRbokR on 2011-04-10
Nevermind.

I just did:
```
sudo apt-get install eclipse-cdt
```

---

### Post by randallecook on 2011-04-12
Maybe things have changed in the past couple of years, but I tried installing Eclipse from Synaptic and entered a world of hurt. Installing it manually made everything work better.

Still, I had a hard time getting the CDT to work. It was not as flexible and forgiving, for example, as Visual Studio when it came to adding files in arbitrary locations to a project. Cooperation with Perforce was also shaky.

Good luck.

---

