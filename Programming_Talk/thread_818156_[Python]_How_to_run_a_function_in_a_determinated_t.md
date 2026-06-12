---
title: "[Python] How to run a function in a determinated time?"
date: 2008-06-04
forum: Programming Talk
---

### Post by lameiro on 2008-06-04
I everyone!

I would like to know how can I control time in python. The idea is to play a sound in a givn time interval, or blink a text or grab info about the system in a determined time interval, etc. In "suma", how do I control time/realtime with python ???

thanks for your time

Lameiro

---

### Post by escapee on 2008-06-04
You'll need a flux capacitor for that :)

Import the time library and you should be good to go for what you need.

---

### Post by lameiro on 2008-06-04
thanks escapee, but I think that this lib is for time in the calendar way, I need to control the timing inside python code.

---

### Post by strider1551 on 2008-06-04
I think the datetime module is more of a calender-ish time

> The idea is to play a sound in a given time interval
Why not use time.sleep()?

```

import os
import time

interval = 60
while True:
    os.system("play sound.wav")
    time.sleep(interval)

```
Of course, you'll need to add a way to stop the loop.  If other stuff needs to happen in the meantime, just put the loop in a thread.

Edit after re-read
hmm... unless you want to play a sound for x seconds and then stop.  I was thinking that you want a sound to play every x seconds.  Still, it should be doable with the time module and a thread.

---

### Post by Can+~ on 2008-06-04
> **lameiro said:**
> how do I control time/realtime with python ???

Lameiro, You're not thinking fourth dimensionally!

---

### Post by lameiro on 2008-06-04
din't get it... Joke?

of course I dont want to control time! I just want to control functions during the program run...

---

