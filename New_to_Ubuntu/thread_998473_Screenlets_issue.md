---
title: "Screenlets issue"
date: 2008-11-30
forum: New to Ubuntu
---

### Post by Truck449 on 2008-11-30
Hello all, upon startup my clear weather screenlet is unable to find weather settings. I have to click on it and reapply the zip code setting then it works. Any ideas why its unable to reapply the code itself?

---

### Post by binbash on 2008-11-30
Please link the the screenlet you are using if you install it from a resource, it is probably that screenlet's bug.

---

### Post by Truck449 on 2008-11-30
Its screenlets, clearweather from weather.com

---

### Post by binbash on 2008-11-30
are you using intrepid ? Because i saw a bug here  : [https://bugs.launchpad.net/ubuntu/+source/screenlets/+bug/228278](https://bugs.launchpad.net/ubuntu/+source/screenlets/+bug/228278) it may be a problem if you cant get the results.Also this may be your problem : [http://ubuntuforums.org/showthread.php?t=957011](http://ubuntuforums.org/showthread.php?t=957011)

---

### Post by Truck449 on 2008-11-30
The second thread you posted looks like the answer. Im just not sure how to have the screenlet wait 20 seconds on startup before booting. Any ideas? Sry im a total noob

---

### Post by Beernut on 2008-12-07
I tried the suggested fix in the thread below but it didn't work for me maybe you'll have better luck.

[http://ubuntuforums.org/showthread.php?t=884861&highlight=screenlets+sleep](http://ubuntuforums.org/showthread.php?t=884861&highlight=screenlets+sleep)

I did get it to work using a script at startup with the following in it like what was mentioned in a previous post.

```
#! /bin/sh
sleep 20;
exec python -u /usr/share/screenlets/ClearWeather/ClearWeatherScreenlet.py > /dev/null &
```

I saved it as screenlets.sh in a scripts folder in my home directory then made it executable.  Then you have to go to System > Preferences > Sessions and add the script to your startup.  It's a bit of a pain but it works.

---

