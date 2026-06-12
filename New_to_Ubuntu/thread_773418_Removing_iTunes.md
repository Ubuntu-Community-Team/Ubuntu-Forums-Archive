---
title: "Removing iTunes"
date: 2008-04-28
forum: New to Ubuntu
---

### Post by saskatchewan on 2008-04-28
There are some things installed in Wine that I have had no luck in removing. I tried installing iTunes and it did not work. But now I can't uninstall it. I tried through the wine menu but no luck. I tried uninstalling wine but no luck.

Any suggestions?

---

### Post by bodhi.zazen on 2008-04-28
remove ~/.wine

```
sudo apt-get remove --purge wine
rm -rf ~/.wine
```

Then log out and back in if you need your menu refreshed.

---

### Post by saskatchewan on 2008-04-28
Hi

I tried what you suggested but I still have all those files.  I am not sure what I did wrong.

---

### Post by bodhi.zazen on 2008-04-29
What files exactly ?

---

### Post by Sjovan on 2008-04-29
if you removed ~/.wine, then you have removed the settings. rm -R /path/to/itunes should take care of the files you are talking about.

---

