---
title: "Create a fan curve using lm-sensors &quot;fan control&quot;"
date: 2020-10-29
forum: New to Ubuntu
---

### Post by jcdenton1995 on 2020-10-29
Hello all,

So I've ordered my first graphics card which by all accounts has great potential, but comes with a god awful default fan curve which literally results in a hot burning smell, as the fan slows right down as temps approach 90 degrees Celsius. Nobody knows why it shipped like this, mine might be fixed, but still.

I'm aware of CoreCtrl but I was thinking I would rather use the lm-sensors 'fancontrol' module, and create a configuration for my GPU fan that way instead. Can anyone tell me if this is an appropriate use of fancontrol?

---

### Post by ActionParsnip on 2020-10-29
What GPU / Graphics card do you have please?

---

### Post by jcdenton1995 on 2020-10-29
> **ActionParsnip said:**
> What GPU / Graphics card do you have please?

It's a Powercolor RX 5600 XT ITX, to be fair to it I've been playing Metal Gear Solid V at 2K, max settings, putting out a constant 60 fpsand it has been fine so far. Temperatures generally go from 70 to ~77 degrees Celsius, but as it's an ITX / small form factor card, they obviously will run a little hot. I can't comment on it yet as there are some reviewers online who highlighted a problem with the stock fan curve that allows the card to reach 90 plus degrees and makes it literally smell like burning - it's possible this has been remedied (the reports were from around May 2020) but I have to mention I have not experienced this *yet* (and I actually have a health condition that would 100% make me the first person on earth to notice this). I mustn't trash the card when I haven't owned it for even a few hours.

Anyway I would like to use fancontrol to set up a more suitable cooling profile if possible, as I'd like to trade some quietness for cool temperatures and longevity!

---

### Post by CatKiller on 2020-10-29
I think you probably can use fancontrol for that; as I understand it, although I don't have an AMD card to test it, AMD cards expose the temperature information and fan speed controls through the interfaces that fancontrol is expecting. The curve in fancontrol is only two or three control points, though: it's better than a curve set to the wrong values, but it's not as good as a good curve.

---

