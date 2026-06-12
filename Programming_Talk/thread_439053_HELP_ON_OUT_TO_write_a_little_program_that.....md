---
title: "HELP ON OUT TO write a little program that...."
date: 2007-05-10
forum: Programming Talk
---

### Post by sarium on 2007-05-10
Hi 

I am not an expert on linux /ubuntu and this is my problem:

I want to keep my wireless card ( BCM43 broadcom) in Monitor mode, I am able to set it that way but the card goes back after a little (1-2minutes) to managed mode.

since no one so far  knows  out to solve that I though to write a little routine that run every 60sec or so the instruction

sudo iwconfig eth1 mode monitor  

like if there was someone typing it in the terminal...

is it possible and how could I do that...? ...

thank you


Raf

---

### Post by qix on 2007-05-10
I know you can make scheduled events with crontab. I'd assume you "just need to" make a .sh script and make root execute it every minute through crontab.

It's just a lead. I'm no expert myself.

---

### Post by bobbocanfly on 2007-05-10
This shouls work but you would need to enter your SU password every time you run the script

```
while [ 1 ]; do
  # Commands here.
done
```

---

### Post by kpatz on 2007-05-11
> **bobbocanfly said:**
> ```
while [ 1 ]; do
  # Commands here.
done
```That will hog resources as it'll run the command over and over ad infinitum with no pause in between.  It would be better to use:

```
while sleep 60; do
  # Commands here.
done
```

Change the 60 as needed depending on how often the command needs to run.  Save it as a script and run it with sudo.

---

