---
title: "can I install an applet that monitors cpu temperature?"
date: 2018-09-26
forum: New to Ubuntu
---

### Post by sususudio on 2018-09-26
Ideally have it float on my screen?

---

### Post by mastablasta on 2018-09-26
sure. why not? 

though i suggest you have a look at and install psensors instead.

---

### Post by sususudio on 2018-09-26
What are desklets called in the latest Ubuntu?

---

### Post by NM5TF on 2018-09-26
I agree with mastablasta.....

try psensors....tho it won't "float"  on your screen...go here for more info....[https://wpitchoune.net/psensor/]("https://wpitchoune.net/psensor/")
there is a screenshot showing what it might look like for you...

tommy

---

### Post by QIII on 2018-09-26
After installing your sensors, you might look in to using conky.  It sits on your desktop and is effectively part of the background.  It doesn't get in the way of other stuff.

You can find an image of my desktop [here]("https://imgur.com/a/HpZBZ2E").  The text to the right in green is my conky display.  It might be a bit hard to make out, but it gives me a lot of info.

You probably don't need anything that detailed.

---

### Post by sususudio on 2018-09-26
How do I install psensors? The linked site gives me a 404

---

### Post by QIII on 2018-09-26
Try

```
sudo apt install psensor
``` 

to get it from the Canonical repo.

Then you will have to run (I think this works for psensors.  I use lm-sensors.)

```
sudo sensors-detect
```

---

### Post by deadflowr on 2018-09-26
> **arkas2 said:**
> How do I install psensors? The linked site gives me a 404

Forum fault (or some other misguided thing), it added an http to it and already had an https so the link went to http//https which does not exist.
Try again. Link fixed.
[https://wpitchoune.net/psensor/]("https://wpitchoune.net/psensor/")

---

### Post by sususudio on 2018-09-26
Hey I did it, thanks!
It doesn't look anything as nice as QIII's setup, but it works!

---

### Post by NM5TF on 2018-09-30
I agree with Qlll...

if you really want to monitor what is happening inside your PC, conky is the way to go.....
fully customizable to whatever you desire & whatever your hardware supports.....

here is my desktop running several conkys simultaneously....weather forecasts complete
with satellite images & system monitor.....scrolling news feed & worldwide seismic activity...



larger image here [https://imgur.com/a/JC1yOb6]("https://imgur.com/a/JC1yOb6")

---

