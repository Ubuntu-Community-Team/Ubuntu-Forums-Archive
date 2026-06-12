---
title: "TechniSat Skystar 2 Serial IR Remote Issues."
date: 2008-05-22
forum: New to Ubuntu
---

### Post by mercera_13 on 2008-05-22
Ok, to start with I'm not sure if this is the correct section to post this in, If not direct me please. Also I know this isnt Ubuntu but you guys are awesome :)

I am using a TechniSat Skystar 2 remote and I am trying to install it on knoppmyth. I am trying to follow this guide:

[http://www.mythtv.co.nz/mythtv//?page_id=55](http://www.mythtv.co.nz/mythtv//?page_id=55)

But as soon as I get too:

irrecord -d /dev/lirc0 TTS35AI

I get this following error:

irrecord: could not init hardware (lircd running ? --> close it, check your permissions)

I have tryed everything but can NOT work out how to close lircd (if thats even the problem)

Any help would be awesome as to why I am getting that error.

Cheers,
Andrew

---

### Post by mercera_13 on 2008-05-22
bump :confused:

---

### Post by psavva on 2008-06-23
Normally you would need to be a root user

try 

```
sudo irrecord -d /dev/lirc0 TTS35AI
```

> **mercera_13 said:**
> Ok, to start with I'm not sure if this is the correct section to post this in, If not direct me please. Also I know this isnt Ubuntu but you guys are awesome :)

I am using a TechniSat Skystar 2 remote and I am trying to install it on knoppmyth. I am trying to follow this guide:

[http://www.mythtv.co.nz/mythtv//?page_id=55](http://www.mythtv.co.nz/mythtv//?page_id=55)

But as soon as I get too:

irrecord -d /dev/lirc0 TTS35AI

I get this following error:

irrecord: could not init hardware (lircd running ? --> close it, check your permissions)

I have tryed everything but can NOT work out how to close lircd (if thats even the problem)

Any help would be awesome as to why I am getting that error.

Cheers,
Andrew

---

