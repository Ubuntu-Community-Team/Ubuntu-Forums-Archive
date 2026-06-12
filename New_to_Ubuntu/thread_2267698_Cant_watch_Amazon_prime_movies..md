---
title: "Cant watch Amazon prime movies."
date: 2015-03-03
forum: New to Ubuntu
---

### Post by francisco17 on 2015-03-03
Hi all,

Trying to watch amazon prime, keep getting message to update adobe player. Gave me a link and i downloaded a tar.gz file but dont know what to do next.

---

### Post by Vladlenin5000 on 2015-03-03
You need to do the usual system-wide updates. The *flasplugin-installer *takes care of everything. This will update within the last version for Linux only, just adding the latest security fixes, but enough for not having the error message.
For better results use Google Chrome that already includes the most up-to-date flash for Linux thanks to a special agreement between Adobe and Google.

---

### Post by francisco17 on 2015-03-03
How do you start the system wide updates?

---

### Post by Vladlenin5000 on 2015-03-03
GUI method (assuming you have a standard Ubuntu with its characteristic Unity desktop): Search software update in the dash, click and run the updater.

In terminal: Do the following commands one at a tim
```
sudo apt-get update
sudo apt-get upgrade
sudo apt-get dist-upgrade (optional)
```

---

### Post by francisco17 on 2015-03-03
ok, i figured it out and ran the updates but i still cant get it to play.

---

### Post by Vladlenin5000 on 2015-03-03
Did you notice any line about the package I mentioned before during the updates? Any error message? 
Have you already tried with Google Chrome? If so, what were the results?

---

### Post by francisco17 on 2015-03-03
There were no error messages during updates. When i try to play on chrome, it just doesnt play. It stays as a black screen. I an play youtube videos, just right now cant watch anything on amazon prime.

---

### Post by kerry_s on 2015-03-03
i don't think amazon works on linux yet, they have some drm thing going on. i've heard you could use the pipelight(aka: silverlight) plugin but very unstable.
i tried for a bit, but never got it to work. not a big deal for me, i have the fire tv hdmi dongle, but i canceled prime & kept netflix. netflix works on everything, linux through chrome browser, on fire tv, it can even be cast to my chromecast from any device i have, just a much better deal than amazon.

---

### Post by MrSteve on 2015-03-03
to get amazon prime to work in firefox with flashplayer you need to install HAL ...
[https://launchpad.net/~mjblenner/+archive/ubuntu/ppa-hal](https://launchpad.net/~mjblenner/+archive/ubuntu/ppa-hal)

---

