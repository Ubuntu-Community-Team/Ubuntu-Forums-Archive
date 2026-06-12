---
title: "Wine - authentication"
date: 2008-05-21
forum: New to Ubuntu
---

### Post by AstralliS on 2008-05-21
When I type:

```
sudo apt-get install wine
```

I get: 

```
WARNING: The following packages cannot be authenticated!
```

Is it safe to continue without authentication?

---

### Post by justin whitaker on 2008-05-21
> **AstralliS said:**
> When I type:

```
sudo apt-get install wine
```

I get: 

```
WARNING: The following packages cannot be authenticated!
```

Is it safe to continue without authentication?

Should be. If you are connecting to an official server or mirror, then you should be fine. 

Any question, and you can always go to WineHQ and download the .deb and install it via dpkg or gdebi.

---

### Post by AstralliS on 2008-05-21
Thanks. I'll get you through WineHQ. :)

---

### Post by Joeb454 on 2008-05-21
Winehq.org will guide you through adding their repository for Ubuntu :) Which does give the added benefit of getting Wine updates pretty damn quick :)

---

### Post by AstralliS on 2008-05-21
I found following repository on WineHQ site:

```
For Ubuntu Hardy (8.04):
sudo wget http://wine.budgetdedicated.com/apt/sources.list.d/hardy.list -O /etc/apt/sources.list.d/winehq.list
```

And I'm using Ubuntu 7.10. Where to find APT keys for Gutsy?

---

### Post by Joeb454 on 2008-05-21
Run the following

```
sudo wget http://wine.budgetdedicated.com/apt/sources.list.d/gutsy.list -O /etc/apt/sources.list.d/winehq.list
``` instead :)

---

### Post by AstralliS on 2008-05-21
I already did that, and after that I did

```
sudo apt-get update
```

to update APT's package. I used alternative way to install it (Applications >> Add/Remove), as it said on WinHQ site, but I didn't find it there.

---

