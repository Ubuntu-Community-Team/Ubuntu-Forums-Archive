---
title: "Ubuntu 12.10 crashing way to much"
date: 2013-02-09
forum: New to Ubuntu
---

### Post by Olipton on 2013-02-09
It crashes like every 5 minutes

info:
kernel bug AT build/buildd/linux-3.5.0/net/core/skbuff.c:127!

i'm using rt3573sta if i remember correctly

belking n750 db wireless adapter



help?

---

### Post by Daveth on 2013-02-10
I think the Forum requires a bit more intelligence on your problem. Does it crash when you do anything in particular, or does it just seem to be a random event? Did it always do this, or is it a new problem?

---

### Post by woodp on 2013-03-25
I'm getting frequent crashes as well and the only common factor I can see if that Firefox with a number of plugins are active. These errors started about a week ago. Thinking maybe it was something I had done, I did a clean install of Ubuntu yesterday. Immediately the crashes started up again.

Nobody else seeing these crashes?

---

### Post by gifford on 2013-03-25
From what you posted it seems there is a problem with Intel video driver. Can you provide more information about your computer hardware?
Also, have you installed additional proprietary drivers?

---

### Post by woodp on 2013-03-27
It's a Lenovo T series with the Intel 3000 chipset and no proprietory drivers, but I don't think that's relevant as it seems many others are experiencing the exact same problem. The code appers fixed in 13.04 but until then the options are a) turning off apport or b) rolling back to a previous kernal. I went back to 3.5.0-17 and all seems fine for now.

More information here: [http://ubuntuforums.org/showthread.php?t=2128425](http://ubuntuforums.org/showthread.php?t=2128425)

Guess I'm going to hang out until April 2013 and 13.04 ...

---

