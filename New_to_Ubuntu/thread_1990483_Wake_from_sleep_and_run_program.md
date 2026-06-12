---
title: "Wake from sleep and run program?"
date: 2012-05-29
forum: New to Ubuntu
---

### Post by bug67 on 2012-05-29
Hello Community,

Really trying to find alternative ways to do things comming from Windows and Mac.  On Windows, I could use Task Manager to wake the computer from sleep and launch Pandora Radio. On Mac, I used iCal to do the same thing.

Is there a way to do the same thing on Xubuntu?  BTW, I'm using Pithos as my Pandora client.

---

### Post by bug67 on 2012-05-30
Bump

---

### Post by Rodney9 on 2012-05-30
```
sudo rtcwake -m mem -t `date +%s -d"2011-01-11 07:30"`
```

```
sudo rtcwake -m mem -t `date +%s -d"tomorrow 04:30"`
```

Those commands will wake your PC from sleep at either 7:30 on the 11 of the 1st or at 4:30 everyday, change to what you want.

You can start programs at specific times in a variety of ways, I use cron to start Clementine playing music every morning as my alarm clock.

```
33 04 * * * clementine --play
```

Rodney

---

### Post by bug67 on 2012-05-30
> **Rodney9 said:**
> ```
sudo rtcwake -m mem -t `date +%s -d"2011-01-11 07:30"`
```

```
sudo rtcwake -m mem -t `date +%s -d"tomorrow 04:30"`
```

Those commands will wake your PC from sleep at either 7:30 on the 11 of the 1st or at 4:30 everyday, change to what you want.

You can start programs at specific times in a variety of ways, I use cron to start Clementine playing music every morning as my alarm clock.

```
33 04 * * * clementine --play
```

Rodney

Thanks.  I'll give it a shot.  Question; if I run this one:
```
sudo rtcwake -m mem -t `date +%s -d"tomorrow 04:30"`
```
will it every day at the specified time or, is it a one day at a time thing?

---

### Post by Rodney9 on 2012-05-30
> will it every day at the specified time or, is it a one day at a time thing?

Each day you run it, it will wake at 04:30 next day. I use it in the terminal last thing each night when I retire.

You could put it also into cron to automate it, it would have to run as root.

---

### Post by bug67 on 2012-05-30
I don't suppose there is a GUI option for all this?  Not that I don't mind working in terminal, it is efficient, I would just prefer a set it and forget it option like Task Manager for Windows.

---

### Post by Rodney9 on 2012-05-30
> **bug67 said:**
> I don't suppose there is a GUI option for all this?  Not that I don't mind working in terminal, it is efficient, I would just prefer a set it and forget it option like Task Manager for Windows.

There is Alarm Clock which will run things at specific times but  will not wake your computer.

Also gWakeOnLan, I haven't tried it.

Also Wakeup 
[https://launchpad.net/wakeup](https://launchpad.net/wakeup)
seems to be some bugs with it though, you could give it a try.

All these are in the Software Centre with reviews.

I have tried some of them and found pasting a command in the terminal once, then using the up arrow to find it again each day easier.

Rodney

---

### Post by bug67 on 2012-05-30
Alright.  Thanks!

---

