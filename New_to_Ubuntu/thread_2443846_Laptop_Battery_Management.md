---
title: "Laptop Battery Management"
date: 2020-05-21
forum: New to Ubuntu
---

### Post by dimitargeorgiev5 on 2020-05-21
I am new to Ubuntu and Linux (obviously), and i am quite concerned about the way the OS manages the laptop battery. Ii have followed one of those tutorials "XX things you need to do after you install Ubuntu", and somewhere there was an advice that stated that i should turn the Suspend option off, i did so. Every now and then i check to see what the battery is up to and sometimes it charges, sometimes its full, sometimes it stays at 95%. Please tell me what is the proper thing to do in order to prolong the battery life and keep it in good health.

Thanks.

---

### Post by Autodave on 2020-05-21
I imagine that you will get many different ideas, but this is what I have done for the past 10+ years:

Normally, I keep the battery charged and ready to go.  Maybe once every 2 months, when I know that I will not need it to run purely on the battery, I let it run down to about 10%.  I then fully charge it and repeat the process 2 more times.

That was recommended years ago with nickel cadmium batteries.  I know that they are no longer used, but I have kept with the same routine and have had very little problems.  I have even resuscitated some "bad" batteries by doing this.

---

### Post by GhX6GZMB on 2020-05-21
IMHO, that's an unnecessary concern. I've now run 19.04, 19.10 and am running 20.04 with no issues. The battery discharges during battery operation and charges reliably when the laptop is plugged in.
Disabling Suspend is a red herring and probably comes from a fear of doing a discharge to 0%.
Ubuntu will turn off the laptop completely when a certain discharge state has been reached (default 5%). You can set  it to 10% or 20% if it makes you feel better.
Everything else regarding battery management is handled by hardware/firmware and does not involve the OS.

---

### Post by Impavidus on 2020-05-21
I've never done anything for better battery life. I bought my current laptop in 2011 and have used it almost every day since. When I first used it, I got about 3:30 hour battery life, which is to be expected, given the capacity of the battery and the power of the CPU at idle. CPU is the largest energy user in the computer. I keep the battery in the laptop at all times and keep it charged. I don't use battery power very often. Nowadays I still get 3:30 hour battery life, with a 9 year old battery. I no longer believe those people who say that a battery breaks after 3 years, even if you don't use it. But maybe I've been lucky.

I've never followed any of those X-things-to-do-after-installing-Ubuntu tutorials. Some have some useful tricks, but don't follow them blindly.

---

### Post by ajgreeny on 2020-05-21
If you simply want to try to extend the hours you get from a full charge you may wish to install **tlp**.

I always add it to my laptops but have never actually measured whether or not it adds any time to the running period from each charge, so this may be unnecessary, but it will certainly do no harm.

---

