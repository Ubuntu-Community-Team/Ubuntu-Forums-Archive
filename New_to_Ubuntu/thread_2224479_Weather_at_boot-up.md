---
title: "Weather at boot-up"
date: 2014-05-16
forum: New to Ubuntu
---

### Post by ray9 on 2014-05-16
How can I get "My Weather Indictor" to launch at boot?


Thanks

---

### Post by bapoumba on 2014-05-16
It would help if you would state the ubuntu release and flavor you are using, thanks.

---

### Post by ray9 on 2014-05-16
Oh, sorry.  It's 14.04 LTS.

---

### Post by Frogs Hair on 2014-05-16
As I remember, the application has the a setting for startup in preferences.

---

### Post by monkeybrain20122 on 2014-05-16
It is in My Weather Indicators' Preferences > General Options. Check the box "autostart"

---

### Post by ray9 on 2014-05-17
Thank you.  That was easy!

---

### Post by Kurt_Alan on 2014-05-17
What is this program?  I would like it.  Can you give me a ```
 sudo apt-get 
``` ?

---

### Post by monkeybrain20122 on 2014-05-17
> **Kurt_Alan said:**
> What is this program?  I would like it.  Can you give me a ```
 sudo apt-get 
``` ?

Not sure if it is in the repository, I always install it from ppa

```
sudo add-apt-repository ppa:atareao/atareao 
sudo apt-get update
sudo apt-get install my-weather-indicator
```

Or you can just open synaptic, go to Settings > Repositories > Other Software and click Add and enter the line "ppa:atareao/atareao" (without quotes) and reload synaptic and then search for it and install. I am not fond of sudo apt-get install blah because package names may change and you may mistype. synaptic is much better for searching as well.

---

